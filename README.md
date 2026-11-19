# Serial Debugger · 串口调试工具

> 为硬件工程师打造的现代化串口调试台 —— 从一根串口线，到完整的协议调试工作流。

![Version](https://img.shields.io/badge/version-0.1.6-3ddc84)
![Platform](https://img.shields.io/badge/platform-macOS%20%7C%20Windows-59c2ff)
![Electron](https://img.shields.io/badge/Electron-33-ffb454)
![License](https://img.shields.io/badge/license-Proprietary-8b98a9)

厌倦了陈旧的串口助手？Serial Debugger 把现代桌面应用的体验带到串口调试里：优雅的界面、脚本化的协议解析、实时曲线、多实例并行调试 —— 同时保留你熟悉的所有底层能力。

## ✨ 功能特性

### 📡 报文收发
- **ASCII / HEX 双模式**，结束符可选（`\r\n` 等），支持**定时发送**
- RX / TX 独立字节统计，方向一目了然
- 收发报文带时间戳，时序问题不再靠猜

### 🔍 过滤与查找
- 多规则**高亮过滤**，规则可保存复用（胶囊式管理）
- **正则查找 + 快速导航**，海量报文里秒级锁定目标帧
- 过滤/查找收进弹出面板，界面零占位

### 🧬 JS 脚本引擎
- `on_rx(data)` / `on_line(line)` 钩子：每个报文自动流经你的代码
- 协议解析、数值提取、**自动应答**、指令编排，全部脚本化
- 脚本保存为文件，支持原地保存 / 另存为 / JSON 批量导入

### 📈 脚本解析曲线
- 脚本返回的数值直接绘制成**实时曲线图**
- 传感器波形、电压电流趋势、温度变化，原生图表视图呈现

### 🖥 终端模式
- 真实终端体验：本地**历史命令**上下召回，Ctrl+U 清行
- `Ctrl+L` 本地清屏，`Alt+↑/↓` 原样透传方向键
- 与 readline 类交互设备的命令行完美适配

### 🪟 多开实例
- 同时调试多台设备，每实例**独立配置、独立日志**（按实例分文件）
- macOS Dock 数字徽标标识实例编号

### 📚 共享指令库
- 常用指令保存、搜索、一键下发
- 指令库**全实例实时同步**，原子写入，跨实例不丢数据

### 🔐 离线激活授权
- 30 天全功能试用，无需注册账号
- **Ed25519 离线激活码**，绑定机器、永久/按年两种授权，无需联网验证
- 终端模式 / JS 脚本 / 曲线 / 多开 为授权功能

## 📥 下载

前往 [Releases](https://github.com/youngManFire/serial-debugger/releases) 页面下载最新版本：

| 平台 | 文件 | 说明 |
|------|------|------|
| macOS Apple Silicon | `SerialDebugger-x.y.z-arm64-mac.zip` | M 系列芯片，解压即用 |
| macOS Intel | `SerialDebugger-x.y.z-mac.zip` | Intel 芯片，解压即用 |
| Windows | `SerialDebugger Setup x.y.z.exe` | 安装版（NSIS 向导） |
| Windows | `SerialDebugger x.y.z.exe` | 便携版，免安装 |

> Windows 首次运行如遇 SmartScreen 提示，点击「更多信息 → 仍要运行」即可（应用暂未做代码签名）。

## 🚀 快速上手

1. 连接 USB 串口设备，打开「串口设置」选择端口与波特率（默认 115200 8N1）
2. 点击「打开串口」，在底部输入框发送指令，报文区实时查看收发
3. 进阶玩法：
   - 常用指令存入**指令库**，一键下发
   - 写一段 `on_rx` 脚本解析私有协议，返回数值自动生成**曲线**
   - 需要同时调试多台设备？点左下角「多开」

## 🛠️ 技术栈

- **Electron 33** + **Vue 3.5**（`<script setup>`）+ **TDesign Vue Next** + **Vite 6**
- **serialport v12**（Node IPC 桥接，渲染层零原生依赖）
- CodeMirror 6（脚本编辑器）
- 离线授权：Ed25519 签名验证（`@noble/curves` 同源方案，Node crypto 原生实现）

```bash
# 开发调试
npm install
npm run start:mock     # 模拟串口模式（/dev/mock0，自动回显 + 应答）
npm run start          # 真实串口模式

# 打包（macOS + Windows）
npm run dist
```

## 📁 数据目录

| 内容 | 位置 |
|------|------|
| 配置 / 脚本 / 指令库 / 日志 | `~/Documents/串口调试工具/` |
| 授权文件（多实例共用） | `~/Library/Application Support/serial-debugger-license/` |

## ❓ FAQ

**Q: 为什么我的串口列表是空的？**
检查是否插入了 USB 串口设备；Windows 下确认驱动已安装（CH340 / CP210x 等）。

**Q: 试用期结束后还能做什么？**
基础串口收发、过滤查找、指令库永久免费；终端模式、JS 脚本、曲线、多开需要激活。

**Q: 换了电脑 / 重装系统怎么办？**
激活码与机器绑定，联系作者（微信：`staticObject`）重新签发即可。

**Q: 如何获取激活码？**
打开应用，点击右上角授权状态胶囊，复制机器码发送给作者，付款后即回发激活码。

## 💛 支持作者

你的打赏 = 更多轮迭代 + 更快修 bug。从串口收发到脚本引擎，每一行都用心。

- 微信：`staticObject`
- 邮箱：`673557662@qq.com`

---

梦和路就在远方，奥利给 🙏
