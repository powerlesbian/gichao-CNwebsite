# 河畔轩 网站维护参考文档

## 项目概述

- **域名**: 河畔轩.cn (xn--ovw07plww.cn)
- **GitHub 仓库**: https://github.com/powerlesbian/gichao-CNwebsite
- **托管**: GitHub Pages
- **技术栈**: React + TypeScript + Vite + Tailwind CSS
- **内容**: 《福布斯亚洲》2016年10月封面故事 —— 赵世曾与赵式芝专访（简体中文翻译）

---

## 网站结构

```
gichao-CNwebsite/
├── .nojekyll          # 告诉 GitHub Pages 不要启用 Jekyll 处理
├── CNAME              # 自定义域名配置
├── index.html         # 首页入口
├── assets/            # 打包后的 CSS/JS
│   ├── index-xxx.css
│   └── index-xxx.js
├── images/            # 图片资源
│   ├── cover.jpg      # 福布斯封面（约 317 KB）
│   └── mansion.jpg    # Happy Lodge 豪宅照片（约 518 KB）
├── README.md          # 仓库默认说明
└── REFERENCE.md       # 本文档
```

---

## 已配置的设置

### 1. GitHub Pages

- **位置**: 仓库 Settings > Pages
- **Source**: Deploy from a branch
- **Branch**: main /docs
- **Custom domain**: 河畔轩.cn
- **Enforce HTTPS**: ✅ 已启用（GitHub 自动签发 SSL 证书）

### 2. GoDaddy DNS 记录

| 类型 | 名称 | 值 | 状态 |
|------|------|-------|------|
| A | @ | 185.199.108.153 | ✅ 已添加 |
| A | @ | 185.199.109.153 | ✅ 已添加 |
| A | @ | 185.199.110.153 | ✅ 已添加 |
| A | @ | 185.199.111.153 | ✅ 已添加 |
| SOA | @ | ns39.domaincontrol.com | ✅ 保留（不要删除） |
| TXT | _dmarc | v=DMARC1... | ✅ 保留（邮件安全） |

> ⚠️ 不要修改或删除 SOA 和 DMARC 记录。

---

## 如何更新网站内容

### 方法 A：在线编辑（最简单，适合小改动）

1. 打开 GitHub 仓库：https://github.com/powerlesbian/gichao-CNwebsite
2. 找到要修改的文件（如 `index.html`）
3. 点击文件名 → 点击右上角 ✏️ 铅笔图标
4. 编辑内容
5. 滚动到底部，填写提交信息（如 "更新文章段落"）
6. 点击 **Commit changes**
7. 等待 1-2 分钟，刷新 河畔轩.cn 即可看到更新

### 方法 B：替换图片

1. 在 GitHub 仓库中，点击 `images/` 文件夹
2. 点击 **Add file > Upload files**
3. 拖拽新图片（建议不超过 1MB，宽度不超过 1400px）
4. **重要**: 保持文件名一致（`cover.jpg`, `mansion.jpg`），或者同时修改 `index.html` 中的引用路径
5. 点击 **Commit changes**

### 方法 C：本地开发后上传（适合大规模修改）

#### 环境要求
- Node.js 20+
- npm

#### 本地开发流程

```bash
# 1. 克隆仓库
git clone https://github.com/powerlesbian/gichao-CNwebsite.git
cd gichao-CNwebsite

# 2. 如果是从源代码开发（可选）
# 源代码使用 React + Vite 构建
npm install
npm run dev       # 本地预览 http://localhost:5173
npm run build     # 构建到 dist/ 文件夹

# 3. 将 dist/ 中的文件上传到 GitHub
# 注意: 确保上传到 /docs 文件夹（当前 GitHub Pages 配置）
```

#### 构建后需要上传的文件
构建完成后，`dist/` 文件夹中包含：
- `index.html`
- `.nojekyll`
- `assets/`（CSS 和 JS）
- `images/`（图片）

将这些文件上传到仓库的 `/docs` 文件夹，覆盖旧文件即可。

---

## 添加新文章的建议

目前网站是单页结构。添加新文章有两种方式：

### 方式 1：在现有页面追加
直接在 `index.html` 的 `<article>` 区域添加新的段落或章节。

### 方式 2：创建新页面
1. 创建新的 HTML 文件，如 `article-02.html`
2. 上传到仓库根目录（或 /docs 文件夹）
3. 在 `index.html` 中添加导航链接指向新页面

### 未来升级建议
如果计划持续添加内容，建议迁移到 **Markdown 驱动**的架构：
- 每篇文章为一个 Markdown 文件
- 前端自动解析并渲染
- 无需每次修改 HTML 代码

如需此升级，可寻求技术支持。

---

## 常见问题排查

### 网站不显示 / 显示旧版本
- GitHub Pages 部署需要 1-2 分钟，稍等后刷新
- 强制刷新浏览器：`Ctrl + Shift + R`（Windows）或 `Cmd + Shift + R`（Mac）
- 检查 GitHub 仓库的 **Actions** 标签页是否有构建错误

### 图片不显示
- 检查图片文件名是否与 `index.html` 中引用的路径一致
- 检查图片是否已上传到正确的 `images/` 文件夹
- 图片路径为相对路径：`/images/cover.jpg`

### HTTPS 证书错误
- 修改 DNS 后，GitHub 需要几小时自动签发 SSL 证书
- 确认 GoDaddy 的 A 记录已正确添加
- 在 GitHub Pages 设置中确认 "Enforce HTTPS" 已勾选

### 域名无法访问
- 检查 DNS 记录是否正确（使用 dig 或在线 DNS 检查工具）
- 确认 GitHub Pages 的 Custom domain 设置中域名拼写正确
- DNS 全球传播可能需要最长 48 小时（通常几分钟到几小时）

---

## 联系方式与协作

- **仓库地址**: https://github.com/powerlesbian/gichao-CNwebsite
- **域名注册商**: GoDaddy
- **托管服务**: GitHub Pages（免费）

如需技术支持或内容更新，提供此文档即可让他人快速了解项目配置。
