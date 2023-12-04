---
layout:     post
title:      群晖安装Docker-Compose
subtitle:    ""
date:       2023-08-28
author:     Dr Gua
header-img: img/post-bg-2015.jpg
catalog: true
tags:
    - 生活
---


## 安装 Compose V2

在开始之前，我们先将 Com­pose 更新到 V2 版本吧！因为老版本今年 6 月就要被淘汰停止使用惹！！

你可以在官方文档（传送门）查看具体的教程。

下面的命令均为 root 用户。

这里演示一下卸载，避免这里安一个那里安一个，搞得乱七八糟的。假如之前安装过，先检查一下 docker-compose 的位置：
```
docker info --format '{{range .ClientInfo.Plugins}}{{if eq .Name "compose"}}{{.Path}}{{end}}{{end}}'
```
如果输出如下内容：
```
/root/.docker/cli-plugins/docker-compose
```
那么就直接删除：
```
rm /root/.docker/cli-plugins/docker-compose
```
然后开始安装最新版 Com­pose，这里我们直接为所有用户安装 Com­pose。

先创建文件夹：
```
mkdir -p /usr/local/lib/docker/cli-plugins
```
接着下载 Com­pose：
```
curl -SL https://github.com/docker/compose/releases/download/v2.20.3/docker-compose-linux-x86_64 -o /usr/local/lib/docker/cli-plugins/docker-compose
```
如果下载不动，在链接前加上 https://ghproxy.com/ 加速下载，即：
```
curl -SL https://ghproxy.com/https://github.com/docker/compose/releases/download/v2.20.3/docker-compose-linux-x86_64 -o /usr/local/lib/docker/cli-plugins/docker-compose
```
赋予权限：
```
chmod +x /usr/local/lib/docker/cli-plugins/docker-compose
```
Com­pose V2 就安装好啦～

测试一下是否能用：
```
docker compose version
```
输出 Docker Compose version v2.20.3 的话，就没问题啦！！
---

## 在群晖上使用 Docker Compose

群晖使用 Docker Com­pose 很简单，在已经安装好 Docker 套件、开启 SSH 的前提下，进入 SSH 终端。下面用 root 账号进行演示：

进入 docker 文件夹
```
cd /volume1/docker
```
这里需要解释一下为什么是 /volume1/docker 而不直接是 /docker 。

简单地说，我们在群晖 Filesta­tion 上看到的是虚假的路径，只有在文件夹的属性中才能看到该文件夹的真实路径。



## 后记

从今天起，可以开启我的吃瓜之旅，愿我们每天都能有一份好心情。

—— Dr Gua 记于 2023.07


