---
layout: post
title: "基于 Jekyll、GitHub 搭建个人博客"
excerpt: 这里介绍如何在 Mac 上利用 Jekyll 的模板和 GitHub 来快速搭建起一个个人博客，需要懂一些基础的 Git 操作和一个 GitHub 账号。Jekyll 是一个静态网站生成器。GitHub 原生支持 Jekyll，网上有非常多的开源的、精美的 Jekyll 模板，找一个喜欢的模板，修改一些参数，马上就可以发布到 GitHub，博客就这么搭好了。
description: A man is not old as long as he is seeking something.
headline: Jekyll + GitHub + Markdown = Your Blog
category: 程序人生
tags: [Jekyll,博客搭建]
imagefeature: 30043.jpg
comments: true
---

这里介绍如何在 Mac 上利用 Jekyll 的模板和 GitHub 来快速搭建起一个个人博客，需要懂一些基础的 Git 操作和一个 GitHub 账号。Jekyll 是一个静态网站生成器，详细介绍[点这里](http://jekyllrb.com)。

GitHub 原生支持 Jekyll，网上有非常多的开源的、精美的 Jekyll 模板，找一个喜欢的模板，修改一些参数，马上就可以发布到 GitHub，博客就这么搭好了。

这是我的博客用的模板，[效果预览](http://www.pfnotes.cn)。这个模板是基于一个开源模板改的，主要将英文改成了中文，替换 CSS、JS 等静态资源镜像和随着个人喜好改动了一些页面样式。

[一些开源 Jekyll 模板](https://github.com/jekyll/jekyll/wiki/sites)

[我的博客源码](https://github.com/waterzhang0423/waterzhang0423.github.io)

## 本地环境搭建

Jekyll 需要依赖 Ruby、RubyGems、NodeJS、Python。除了 NodeJS 之外，Ruby、Python 这些Mac 的 OS X 都自带了。如果没有安装过 NodeJS，需要先安装 NodeJS，[官方下载链接](https://nodejs.org/en/download/)。选择对应的操作系统的版本下载安装包安装即可。

安装完 NodeJS 之后，直接通过 gem 命令就可以安装 Jekyll，执行如下命令：

`gem install jekyll`

在 OS X 10.11 及以上有可能出现安装失败的问题，一般来说是权限问题，尝试执行如下命令：

`sudo gem install -n /usr/local/bin jekyll`

如果还安装失败，看看 Jekyll 官方的帮助文档，[查看帮助](https://jekyllrb.com/docs/troubleshooting/)。

## 在 GitHub 上建立个人站点

在 GitHub 上新建一个 Repository，Repository 的名字为 `yourusername.github.io`，`yourusername`替换成自己的 GitHub 用户名即可。

[新建 Repository](https://github.com/new)

Repository 创建成功之后，把这个 Repository clone 到本地来，推荐使用 GitHub 的官方客户端，使用起来很方便。

[点击下载  GitHub 客户端](https://desktop.github.com)

把 Repository clone 下来之后，进入那个目录，把下载下来的 Jekyll 模板直接拷贝到 clone 下来的 Repository 文件夹内。到这一步，基本上搭建工作就完成了。接下来要做的就是改掉模板的配置文件，填上自己的信息。打开 `_config.yml` 文件，替换对应的信息即可。详细配置介绍可以参考这里：

[点击查看模板配置帮助](https://github.com/hmfaysal/hmfaysal-omega-theme)

## 本地效果预览

Jekyll 模板可以直接在本地预览效果，在 clone 下来的 Repository 根目录里运行如下命令：

`jekyll build`

Jekyll 会在根目录下生成一个 _site 文件夹，这个文件夹是用来在本地预览的，不需要发布到 GitHub，所以通常建议在根目录下新建一个 `.gitignore` 文件，忽略掉这个目录。如果已经有一个 `.gitignore` 文件，则在里面添加一行内容：`_site`，没有没有这个文件，则新建一个 `.gitignore` 文件，内容填上 `_site` 即可。这样发布（push）到 GitHub 的时候 _site 目录就不会提交上去了。

接下来启动本地服务即可在浏览器预览效果，执行如下命令：

`jekyll serve --baseurl ''`

**注意：** 这个要求 `_config.yml` 文件里 `url` 的值为空。

运行成功之后，控制台会打印出可以访问的 url 地址，复制地址在浏览器访问即可预览效果。

如果运行失败，则可能是 `_config.yml` 里有东西配置错了，一般控制台会给出相应的提示。根据提示修改 `_config.yml` 即可。

效果预览之后，接下来要做的就是把博客发布到 GitHub 上，这个就简单了，push 到远程即可。如果不用 GitHub 的客户端，可能需要执行 git add 命令以及 commit 命令，最后再执行 push 命令。

Push 成功之后，一般 10 分钟以内，打开浏览器，访问 `yourusername.github.io` 即可，`yourusername` 替换成你的用户名这种小事就不用说了吧。如果没看到效果，则修改一下本地的 `_config.yml` 文件，再 push 到远程，这样可以强制 GitHub 重新构建站点。然后再在浏览器里预览效果即可。

## 写作

推荐使用 Markdown 写作。在 Repository 根目录有一个 `_post` 文件夹，里面即是存放博客文章的，文件格式一般用 `yyyy-MM-dd-文章标题.md` 的格式，比如我这篇文章的文件名是 `2016-05-27-基于 Jekyll、GitHub 搭建个人博客.md`，注意年是 4 位数字（好像是废话），月和日都是两位数字。不同的模板可能有不同的格式要求。

写完之后，同样使用 git 命令 push 到远程即可，文章就发布成功了。以后写文章，都只要在 `_post` 文件夹里新建文章文件再 push 到远程即可。

## 将 GitHub 博客指向到自定义域名

通过访问自己的域名直接访问这个 GitHub 的博客也很简单，在这个 Repository 根目录建立一个 `CNAME` 文件，里面写上自己的域名即可，比如我写的是 `www.pfnotes.cn`。注意不要有空行，开始结尾也不要有空格。同样 push 到远程。

然后就是要在域名管理商那里做一下域名解析，不同的域名管理商的配置可能不同，以 DNSPod 为例，新建一条记录，记录名称填写 `www`，记录类型选择 `CNAME`，记录值填写 `yourusername.github.io`，不用说，这个 `yourusername` 是要替换成你自己的。保存即可。我的 DNSPod 解析如下：

```

主机记录    记录类型    线路类型    记录值

www         CNAME       默认      waterzhang0423.github.io

```

到这里，整个搭建就结束了。接下来就是享受写作吧。