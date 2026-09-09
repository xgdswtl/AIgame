# 摘星之旅

一款纯 HTML5 Canvas 制作的 2D 平台解谜游戏。玩家操控主角**小星**，在精灵**露露**的引导下，穿越一座座漂浮的星空浮岛，踩下悬空法阵、借用空间裂缝传送，收集散落的星星。

## 玩法

- 操控小星在浮岛间跳跃、奔跑。
- 站上**空间裂缝**并按空格，可传送到另一座浮岛。
- 踩下**悬空法阵**，会触发别处浮石移动，打开通往星星的道路。
- 解开环环相扣的谜题链，收集每一关的星星。
- 通关进度保存在浏览器本地（localStorage），返回主页可继续选择已解锁关卡。

## 操作

| 按键 | 动作 |
|---|---|
| `A` / `D` 或 `←` / `→` | 左右移动 |
| `空格` | 跳跃 / 在裂缝上传送 |
| `E` 或 `空格` | 推进对话 |

> 游戏在电脑浏览器中使用键盘操作，暂未适配触屏。

## 目录结构

```
摘星之旅/
├── title-screen/
│   ├── title.html            # 主页（选关 / 设置 / 开始）
│   └── assets/               # 主页背景图
├── cg-opening/
│   ├── opening-cg-player.html# 开场 CG 播放器
│   └── video/                # 开场 CG 视频分镜
├── prototype-ch1.html        # 第一关
├── prototype-ch2.html        # 第二关
├── prototype-ch3.html        # 第三关
├── 第一关精灵*.mp3 …         # 关卡内露露配音
├── CG精灵*.mp3               # 开场 CG 配音
└── README.md
```

## 本地运行

纯静态页面，无需构建。任选其一：

1. 直接用浏览器打开 `title-screen/title.html`。
2. 或在项目根目录起一个静态服务器（推荐，可避免个别浏览器的本地文件限制）：

```bash
# Python
python -m http.server 8000

# 或 Node
npx serve .
```

然后访问 `http://localhost:8000/title-screen/title.html`。

## 部署到 GitHub Pages

1. 在 GitHub 新建仓库，把本目录（含所有 `.html`、`.mp3`、`assets/`、`video/`）推送到仓库。
2. 仓库 `Settings → Pages`，将 `Source` 设为 `Deploy from a branch`，分支选 `main`，目录选 `/ (root)`。
3. 保存后稍等片刻，即可通过 `https://<用户名>.github.io/<仓库名>/title-screen/title.html` 访问。

> 已提供根目录 `index.html` 自动跳转到 `title-screen/title.html`，因此仓库根 URL 与 `.../title-screen/title.html` 均可直接进入游戏。

## 技术说明

- 纯前端，无后端、无构建依赖，零第三方运行时。
- 关卡逻辑、物理碰撞、角色与精灵均用 Canvas 绘制。
- 音频使用原生 `Audio`，音量设置持久化在 `localStorage`（`zxz_bgm` / `zxz_sfx`）。
- 字体通过 Google Fonts 加载，加载失败时自动回退到系统字体，不影响游玩。
