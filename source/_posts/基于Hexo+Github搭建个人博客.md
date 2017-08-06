---
title: 基于Hexo+Github搭建个人博客 
date: 2017-07-30 15:16:20
tags: Hexo
categories: 前端
---

Hexo是一个开源的静态博客生成器,用node.js开发,作者是台湾大学生tommy351。提供丰富的博客主题配置，插件使用，强大易上手。

## 依赖环境 

### Git 
[Github Pages上](https://pages.github.com/)用于免费部署静态页面	

### Node
[Node](http://nodejs.cn/)开发基本环境需求

### Hexo
[Hexo](https://hexo.io)静态博客生成器

### 腾讯云
[申请域名](https://dnspod.cloud.tencent.com/)用于CHAME别名解析
[图片存储](https://cloud.tencent.com/product/cos)存储博客中的图片,对于博客的流量，基本免费

## Github Pages创建
创建一个github仓库，仓库名格式为：github用户名.github.io,如下图：
![repository](http://yorkyu-1253637904.cosgz.myqcloud.com/%E5%89%8D%E7%AB%AF/github-pages.png)

## Hexo 创建静态博客

### Hexo 安装
``` bash
$ npm install hexo -g
$ hexo -v
```

### 配置主题
查看预览已有的[主题](https://hexo.io/themes/),使用git clone下对应的主题到根目录文件夹“themes/主题名”下,本博客使用主题如下：
``` bash
$ cd yorkiyu.github.io
$ git clone https://github.com/maochunguang/black-blue.git themes/black-blue 
```
修改根目录下的主配置文件_config.yml，注意冒号后的空格:
``` bash
theme: black-blue
```
其次，根据需要，可调整主题下的_config.yml文件，修改导航，头像等信息

### 写博客
hexo new [layout] < title >

在站点目录下执行此命令新建一篇文章，layout参数可选，title必填。

Hexo 有三种默认布局：post、page 和 draft，它们分别对应不同的路径，而您自定义的其他布局和 post 相同，都将储存到 source/_posts 文件夹。
post	->	source/_posts
page	->	source
draft	->	source/_drafts

``` bash
$ hexo new page 'about'
$ hexo new 'hello world'
```

### Hexo中的categories与导航路由关系
导航路由在主题配置文件_config.yml中可配置
使用hexo new命令出来的.md文件的头部含有如下代码
```bash
title: 基于Hexo+Github搭建个人博客 
date: 2017-07-30 15:16:20
tags: Hexo
categories: 前端
```
其中tags为标签，可自定义。categories为路由"/categories/分类"中，“分类”的值

### 部署
修改根目录配置文件_config.yml，中的deploy参数，如下：
```bash
deploy:
  type: git
  repo: https://github.com/yorkiyu/yorkiyu.github.io.git 
```
发布执行如下列命令：
```bash
$ hexo clean
$ hexo generate
$ hexo deploy
```
## CHAME别名配置
配置效果，访问[yorkiyu.github.io](https://yorkiyu.github.io)时重定向到[yorkyu.cn](http://yorkyu.cn)
在根目录下的source文件夹下创建CHAME文件如下：
![CHAME](http://yorkyu-1253637904.cosgz.myqcloud.com/%E5%89%8D%E7%AB%AF/CHAME.png)
腾讯云申请域名[yorkyu.cn](http://yorkyu.cn)，并配置域名解析：
![yorkyu.cn](http://yorkyu-1253637904.cosgz.myqcloud.com/%E5%89%8D%E7%AB%AF/yorkyu.cn.png)

## 博客优化

### 功能优化
支持站内搜索（百度），本地搜索，rss订阅
安装插件
```bash
## rss插件
npm install hexo-generator-feed --save
## 站点sitemap生成插件
npm install hexo-generator-sitemap --save
npm install hexo-generator-baidu-sitemap --save
## 本地搜索插件集成
npm install hexo-generator-search --save
```
主配置文件_config.yml添加插件配置：
```bash
Plugins:
  hexo-generator-feed
  hexo-generator-sitemap
  hexo-generator-baidu-sitemap
feed:
  type: atom
  path: atom.xml
  limit: 20
search:
  path: search.json
sitemap:
  path: sitemap.xml
baidusitemap:
  path: baidusitemap.xml
```


### 性能优化
使用hexo-neat插件,压缩html，css，js文件的。hexo-neat插件使用HTMLMinifier、clean-css、UglifyJS插件实现。


## 项目地址
该博客的Github Pages地址[yorkiyu.github.io](https://github.com/yorkiyu/yorkiyu.github.io)
源码地址[yorkyu-blog](https://github.com/yorkiyu/yorkyu-blog)



















			

