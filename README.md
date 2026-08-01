# 个人博客

深色主题个人技术博客，部署在 GitHub Pages。

## 技术栈

- 纯 HTML / CSS / JavaScript，无构建步骤
- 使用 [marked.js](https://cdn.jsdelivr.net/npm/marked/marked.min.js) 渲染 Markdown
- 响应式设计，适配移动端
- 深色主题 (#0d1117)

## 目录结构

```
blog/
├── index.html              # 首页（文章归档列表）
├── post.html               # 通用文章渲染页（读取 ?p= 参数加载 .md）
├── README.md
├── assets/
│   ├── css/style.css       # 全局样式（含文章页样式）
│   └── img/avatar.svg      # 头像
└── posts/
    └── eg-connect-linux-deploy.md  # 文章（Markdown 格式）
```

## 如何更新文章

### 编辑已有文章

直接编辑 `posts/` 目录下的 `.md` 文件即可。

### 新增文章

1. 在 `posts/` 目录下创建新的 `.md` 文件，例如 `posts/my-new-post.md`
2. 文件头部使用 YAML front matter 声明元信息：

```markdown
---
title: 文章标题
date: 2026-02-01
tags: Linux K8s
---

正文内容从这里开始...
```

3. 在 `index.html` 的文章列表中添加一条链接：

```html
<li class="post-item">
    <time datetime="2026-02-01">2026/02/01</time>
    <a href="post.html?p=posts/my-new-post.md" class="post-title">文章标题</a>
    <span class="tags">Linux&nbsp;K8s</span>
</li>
```

4. 提交并推送：

```bash
git add -A
git commit -m "新增文章：文章标题"
git push
```

GitHub Pages 会自动重新构建并更新线上页面。

## 本地预览

由于文章通过 fetch 加载 Markdown 文件，需要使用本地服务器（不能直接双击打开 HTML）：

```bash
python -m http.server 8000
```

然后访问 `http://localhost:8000`

## 部署

推送到 GitHub 仓库 `main` 分支即可，GitHub Pages 已自动启用。
