# GPT Image 2 Studio for GitHub Pages

一个纯静态的 GPT Image 2 API 调用器，可部署到 GitHub Pages。界面参考 ChatGPT 网页端：左侧对话历史、接近 GPTs 位置的预设区、中间图片对话区、底部输入框与横向参数菜单。

## 功能

- 设置页支持填写 API 站点 / 中转站与 API Key；API 站点留空时默认 `https://api.openai.com`。
- API Key 可选择保存到本地浏览器；不保存时只在当前页面会话中使用。
- 调用 `/v1/images/generations` 与 `/v1/images/edits`。
- 支持 GPT Image 2 常用可调参数：`model`、`prompt`、`size`、`quality`、`output_format`、`output_compression`、`background`、`n`、`moderation`、`stream`、`partial_images`、`user`，编辑接口支持多参考图和 mask。
- 分辨率提供 Auto、1K、2K、3K、4K、常用横竖比例与自定义宽高；前端会按 GPT Image 2 的尺寸约束校验。
- 使用 IndexedDB 本地保存对话记录、输入图片、生成图片和预设。
- 支持删除指定对话、删除全部对话、清除本应用保存的所有数据。
- 预设支持保存 / 编辑 / 删除，可自定义所有主要参数与提示词模板。

## 部署到 GitHub Pages

1. 新建一个 GitHub 仓库，例如 `gpt-image2-studio`。
2. 把本目录中的 `index.html`、`styles.css`、`app.js`、`README.md` 上传到仓库根目录。
3. 在仓库中打开 **Settings → Pages**。
4. Source 选择 **Deploy from a branch**，Branch 选择 `main` / `/root`。
5. 保存后访问 GitHub Pages 给出的地址。

## 使用

1. 打开页面后点击左下角或右上角的「设置」。
2. 填入 API Key；API 站点留空则使用官方站点，也可填入兼容 OpenAI Images API 的中转站。
3. 输入 prompt。
4. 在输入框下方横向参数菜单中调整接口、尺寸、质量、格式等参数。
5. 使用编辑接口时先上传 1 到 16 张参考图；mask 为可选 PNG。
6. 点击「发送」。生成结果会保存到本地历史记录中，并可下载。

## 安全说明

这是静态网页，不能隐藏 API Key。请不要把 Key 写进源码，也不要把已填 Key 的浏览器环境共享给别人。公开部署时建议使用你自己控制的中转站或受限 Key，并确认其 CORS、额度和权限策略。

## 本地数据

本项目的数据存储在当前浏览器的 localStorage 与 IndexedDB 中。换浏览器、清理站点数据或点击「清除保存的所有数据」都会删除历史与预设。

## 官方文档参考

- OpenAI Image generation guide: https://developers.openai.com/api/docs/guides/image-generation
- GPT Image 2 model page: https://developers.openai.com/api/docs/models/gpt-image-2
- Image API generation reference: https://developers.openai.com/api/reference/python/resources/images/methods/generate/
- Image API edit reference: https://developers.openai.com/api/reference/python/resources/images/methods/edit/
