---
name: hugo-post-creator
description: 用于在 Hugo 博客中创建符合规范的新文章。当用户要求“写一篇文章”、“新建博客”或“创建 Markdown 文档”时使用。
---

# Hugo 文章创建规范

此 Skill 旨在自动化 Hugo 博客文章的创建过程，确保文件名和内容格式严格遵循项目标准。

## 1. 文件存放位置
所有文章必须创建在 `content/posts/` 目录下。

## 2. 文件命名规则
* **字符限制**：仅使用小写英文或拼音，避免空格和特殊字符。
* **分隔符**：使用连字符 `-` 分隔单词。
* **示例**：`my-first-post.md` 或 `wo-de-di-yi-pian-wen-zhang.md`。

## 3. 内容格式 (Frontmatter)
每篇文章必须以以下元数据开头，日期应为当前请求时间：

```markdown
---
title: "文章标题"
date: YYYY-MM-DDTHH:mm:ss+08:00
draft: false
tags: ["标签1", "标签2"]
categories: ["分类"]
toc: true
---

## 文章内容从这里开始...

这是您的文章内容...
```

## 工作流程
1. **确定标题**：根据用户输入确定文章标题。
2. **生成文件名**：将标题转换为符合规则的英文/拼音文件名。
3. **填充模板**：使用当前日期和默认配置生成 Frontmatter。
4. **撰写内容**：根据用户的主题或指令完成文章主体。
5. **写入文件**：使用 `write_file` 将内容保存到 `content/posts/`。