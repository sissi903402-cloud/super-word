# Super Word Skill 使用说明

`super-word` 是一个提示词优化 skill。它会以 Lyra 的身份，把粗略、模糊或不完整的提示词优化成更清晰、更有结构、更适合不同 AI 平台使用的最终提示词。

## 文件位置

当前 skill 保存在：

```text
D:\skill广告库\超级提示词skill\super-word
```

核心文件：

```text
D:\skill广告库\超级提示词skill\super-word\SKILL.md
```

UI 元数据文件：

```text
D:\skill广告库\超级提示词skill\super-word\agents\openai.yaml
```

## 基础调用方法

在 Codex 或支持 skills 的环境中，直接输入：

```text
使用 $super-word 帮我优化这个提示词：
[粘贴你的原始提示词]
```

也可以写成英文：

```text
Use $super-word to optimize this prompt:
[paste your rough prompt]
```

## 指定目标 AI

如果你知道最终提示词要给哪个平台使用，可以直接写出来：

```text
使用 $super-word，目标 AI 是 ChatGPT：
[你的原始提示词]
```

```text
使用 $super-word，目标 AI 是 Claude：
[你的原始提示词]
```

```text
使用 $super-word，目标 AI 是 Gemini：
[你的原始提示词]
```

```text
Use $super-word for Other AI:
[your rough prompt]
```

## 指定优化模式

`super-word` 有两种模式：`DETAIL` 和 `BASIC`。

### DETAIL 模式

适合复杂、专业、商业、技术、教育、广告、长文案、系统提示词等任务。

调用示例：

```text
使用 $super-word，DETAIL 模式，目标 AI 是 ChatGPT：
帮我写一个卖产品的广告提示词
```

DETAIL 模式通常会先问 2-3 个关键问题，例如目标受众、输出格式、语气、使用场景等，然后再产出完整优化后的提示词。

### BASIC 模式

适合快速优化、简单改写、临时使用的提示词。

调用示例：

```text
使用 $super-word，BASIC 模式，目标 AI 是 Claude：
帮我优化这句话，让 AI 写得更专业
```

BASIC 模式不会做太多追问，会直接修复主要问题并给出可复制使用的优化提示词。

## 推荐调用模板

### 中文模板

```text
使用 $super-word：

目标 AI：[ChatGPT / Claude / Gemini / Other]
模式：[DETAIL / BASIC]
我的原始提示词：
[在这里粘贴你的提示词]

我的额外要求：
- 输出语言：
- 输出格式：
- 语气风格：
- 使用场景：
```

### 英文模板

```text
Use $super-word:

Target AI: [ChatGPT / Claude / Gemini / Other]
Mode: [DETAIL / BASIC]
My rough prompt:
[paste your prompt here]

Extra requirements:
- Output language:
- Output format:
- Tone:
- Use case:
```

## 自动模式判断

如果你没有指定 `DETAIL` 或 `BASIC`，skill 会自动判断：

- 简单任务：默认用 `BASIC`
- 复杂或专业任务：默认用 `DETAIL`

它会先告诉你当前选择的模式，并说明你可以覆盖这个选择。

## 产出格式说明

### 简单任务产出

简单任务通常会输出：

```markdown
**Your Optimized Prompt:**
[优化后的提示词]

**What Changed:** [关键改进说明]
```

你可以直接复制 `Your Optimized Prompt` 下面的内容去使用。

### 复杂任务产出

复杂任务通常会输出：

```markdown
**Your Optimized Prompt:**
[优化后的提示词]

**Key Improvements:**
- [主要改进点和好处]

**Techniques Applied:** [使用的优化技巧]

**Pro Tip:** [使用建议]
```

其中最重要的是 `Your Optimized Prompt`。后面的说明用于帮助你理解为什么这样改，以及怎样使用效果更好。

## 适合使用的场景

可以在这些场景调用 `super-word`：

- 优化 ChatGPT、Claude、Gemini 的提示词
- 把一句粗略想法变成完整提示词
- 写系统提示词
- 写广告、营销、短视频、UGC、产品文案提示词
- 写代码生成或技术任务提示词
- 写教学、课程、讲解类提示词
- 写图片生成、视频生成、脚本生成提示词
- 把中文需求改成英文 AI 提示词
- 把模糊提示词改成结构化提示词

## 跨项目调用说明

如果只放在当前目录：

```text
D:\skill广告库\超级提示词skill\super-word
```

那么它主要适合在当前这个 skill 库或当前工作区中使用。

如果希望在其他项目中也能稳定调用，建议把整个 `super-word` 文件夹复制到全局 Codex skills 目录：

```text
C:\Users\Administrator\.codex\skills\super-word
```

全局安装后，在其他项目里也可以直接调用：

```text
$super-word
```

## 跨项目调用示例

在任意项目中输入：

```text
使用 $super-word，DETAIL 模式，目标 AI 是 ChatGPT：
我想让 AI 帮我分析这个项目的代码结构，并给出重构建议
```

或者：

```text
使用 $super-word，BASIC 模式：
帮我优化这个 Midjourney 图片提示词，让画面更商业广告风格
```

## 注意事项

- 不要只写 `$super-word` 后什么都不提供，除非你只是想看到欢迎说明。
- 如果希望结果更准，最好提供目标 AI、模式、输出语言、使用场景。
- 如果是商业、代码、广告、长文案或专业任务，优先用 `DETAIL`。
- 如果只是快速改写一句提示词，用 `BASIC` 就够。
- 根据 skill 规则，优化会话内容不应保存到记忆中。

## 最短可用示例

```text
使用 $super-word，BASIC 模式：
帮我优化这个提示词：写一个关于减肥产品的短视频广告脚本
```

## 最推荐示例

```text
使用 $super-word：

目标 AI：ChatGPT
模式：DETAIL
我的原始提示词：
帮我写一个减肥产品的短视频广告脚本

我的额外要求：
- 输出语言：中文
- 输出格式：Hook、正文、证明点、CTA
- 语气风格：真实、口语化、像真人分享
- 使用场景：TikTok / Reels / Shorts 广告
```
