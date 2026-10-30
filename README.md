# 本质（benzhi）

丢一句话、一个观点或一个现象进来，它用维特根斯坦式的眼光把这句话说穿：看词在日常里怎么被用、句子缺了哪一头、问题是不是语法造的。说穿以后，它会再挂一段「历史上」：历史上谁论证过同一件事，人们又是怎么解的。不判对错，不陪聊，不说教。

> 原话：适当的虚荣能让人进步
>
> **本质：「虚荣」和「进步」说的可能是同一件事，被人看着的时候叫虚荣，事后回头看叫进步。**
> - 「进步」这个词总要有人来宣布。完全没人看见的进步，我们几乎不知道该怎么说它。
> - 所以这句话其实是在说：我们说"进步"的时候，已经把一个看客放进句子里了。
> - 问题不是虚荣能不能带来进步，而是没有虚荣的那种"进步"长什么样，我们说不出来。
>
> **它成全你的叫：**
> **获得客体存在感，从而反馈自我认知。**
>
> **它绑住你的叫：**
> **以他者凝视为前提，才能确证自我。**
>
> **历史上：**
> - 黑格尔《精神现象学》：自我意识要靠他者承认才站得住——点名了「看客」这一头。
> - 拉康镜像阶段：自我形象先在外部映象里成形——同构于「被人看着才叫进步」。
> - 解法侧：庄子《齐物论》把「彼」与「此」收成同一把尺子——想取消看客，往往先得改计分游戏本身。

## 安装

把这句话发给你的 agent（Claude Code、Codex、Grok、Trae、豆包等能在电脑上执行命令的都可以）：

```text
帮我安装 https://github.com/zhangke668/benzhi
```

装好后新开一个对话就能用。

## 怎么用

- `/benzhi 越熟的人越容易说狠话`：给这句话下判词。
- 也可以直接说「这句话的本质是什么：……」「一句话说穿：……」。
- 用过一次之后，接着丢新的句子就行，不用每次都打 `/benzhi`。追问或反驳时，它先用大白话回答；说"退出"就回到普通对话。
- 每条判词后面会自动挂一段「历史上」，2 到 4 行，像注脚：谁看见过同一件事，最后一条写历史上怎么解。吃不准出处的会标「待核实」。
- 说「不要历史」：这一轮和之后都不再挂历史段，直到你说要。
- 说「历史再展开」「谁还论证过」：把历史段写成稍长的笔记，仍控制在一屏以内。
- 说「出卡」：把这次对话的起点、演化和落点做成一张总结卡片。

## 给 AI agent 的安装说明

用户让你安装这个仓库时，按下面的顺序试，前一步成功就不用做后面的。下文的 `~` 指用户主目录，Windows 上是 `C:\Users\<用户名>`。

### 1. 用 skills 安装器（推荐，需要 Node.js）

```bash
npx -y skills add zhangke668/benzhi -g -y
```

它会把 skill 装到 `~/.agents/skills/benzhi/`，并自动链接到本机已有的 Claude Code、Grok、Trae 等 agent 目录。输出里如果有 `PromptScript does not support global skill installation`，可以忽略，不影响其他 agent。

### 2. 没有 Node.js，或安装器失败：直接克隆

把仓库克隆到你自己读取 skill 的目录，文件夹名必须是 `benzhi`，`SKILL.md` 直接放在里面，不要多套一层：

| Agent | 目录 |
|-------|------|
| Claude Code | `~/.claude/skills/benzhi/` |
| Grok | `~/.grok/skills/benzhi/` |
| Trae / Trae CN | `~/.trae/skills/benzhi/` 或 `~/.trae-cn/skills/benzhi/` |
| Codex、豆包，以及其他读通用目录的 agent | `~/.agents/skills/benzhi/` |

```bash
git clone --depth 1 https://github.com/zhangke668/benzhi.git ~/.claude/skills/benzhi
```

连不上 GitHub 时，告诉用户网络不通，请用户自己下载 <https://github.com/zhangke668/benzhi/archive/refs/heads/main.zip> 发给你，再解压到上表的目录，并把解压出来的 `benzhi-main` 改名为 `benzhi`。

### 3. 你不能在电脑上执行命令

比如手机 App 或网页聊天。读取 <https://raw.githubusercontent.com/zhangke668/benzhi/main/SKILL.md>，在当前对话里按它的方法回答用户，并告诉用户：这样只在本次对话有效，想长期用，需要装到能执行命令的 agent 里；「出卡」功能这时用不了。

### 装完以后

1. 确认 `benzhi/SKILL.md` 存在，开头写着 `name: benzhi`。
2. 告诉用户：新开一个对话（或重启 agent）后，输入 `/benzhi 一句你想看穿的话` 试试。

## 更新和卸载

- 更新：`npx -y skills update benzhi -g -y`；手动克隆的，在 `benzhi` 文件夹里执行 `git pull`。
- 卸载：`npx -y skills remove benzhi -g -y`；手动装的，直接删掉 `benzhi` 文件夹。

## 致谢

「历史上」那段按结构同构检索的思路，参考了 [dbskill](https://github.com/dontbesilent2025/dbskill) 里的历史同构研究方法。
