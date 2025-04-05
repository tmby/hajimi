# 🚀 Gemini API Proxy

基于某论坛上一位大佬[@Mrjwj34](https://github.com/Moonfanz)基于另一位大佬[@Moonfanzp](https://github.com/Moonfanz)的代码的修改修改而来，由于大佬好长时间没有维护，我自己也遇到些bug，就魔改了一下，求star求star求star

这是一个基于 FastAPI 构建的 Gemini API 代理，旨在提供一个简单、安全且可配置的方式来访问 Google 的 Gemini 模型。适用于在 Hugging Face Spaces 上部署，并支持openai api格式的工具集成。
###  使用文档
- [使用文档](./wiki/wiki.md)
###  更新日志
*   v0.0.4
    * 修改版本更新逻辑，现在为每四小时检查一次版本更新
    * 前端界面所有数据数据实现动态更新
    * 新增“单api使用次数统计”，在原API调用统计下方新增可折叠的单api使用次数统计，同时提供进度条查看剩余使用次数
    * 在环境变量中新增`API_KEY_DAILY_LIMIT`，为单api 24小时最大使用次数，默认值为25
    * 在环境变量中新增`BLOCKED_MODELS`，为需要屏蔽的模型名称，多个模型用英文逗号分隔

*   v0.0.3beta
    * 完善了客户端断开连接的处理逻辑（感谢[@warming-afternoon](https://github.com/warming-afternoon)）
    * 新增“假流式传输模式”，该模式默认开启，以解决在某些情况下客户端断开连接的问题。如需关闭，请将环境变量 `FAKE_STREAMING` 设置为 `false`。

*   v0.0.2 修复了在log中错误暴露apikey的问题，修改了客户端断开连接的处理逻辑（感谢[@warming-afternoon](https://github.com/warming-afternoon)）

## ✨ 主要功能：

### 🔑 API 密钥轮询和管理

### 📑 模型列表接口

### 💬 聊天补全接口：

*   提供 `/v1/chat/completions` 接口，支持流式（streaming）和非流式响应，与 OpenAI API 格式兼容。
*   自动将 OpenAI 格式的请求转换为 Gemini 格式。

### 🔒 密码保护（可选）：

*   通过 `PASSWORD` 环境变量设置密码。
*   提供默认密码 `"123"`。

### 🚦 速率限制和防滥用：

*   通过环境变量自定义限制：
    *   `MAX_REQUESTS_PER_MINUTE`：每分钟最大请求数（默认 30）。
    *   `MAX_REQUESTS_PER_DAY_PER_IP`：每天每个 IP 最大请求数（默认 600）。
*   超过速率限制时返回 429 错误。

### 🧩 服务兼容

*   提供的接口与 OpenAI API 格式兼容,便于接入各种服务

## ⚠️ 注意事项：

*   **强烈建议在生产环境中设置 `PASSWORD` 环境变量，并使用强密码。**
*   根据你的使用情况调整速率限制相关的环境变量。
*   确保你的 Gemini API 密钥具有足够的配额。
