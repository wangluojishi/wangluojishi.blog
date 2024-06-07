---
title: "Chevereto-搭建你的私人图床！"
categories: [ "网络" ]
tags: [ "wordpress","图床" ]

date: "2020-03-22T16:06:00+08:00"
draft: false
slug: "1429"
---

自从搭建博客后，一直在寻找图床解决方案，从onedrive到sm图床到新浪图床（已添加了防盗外链），最后选择了Chevereto

Chevereto, 是一款采用 PHP 语言开发的网络相册脚本程序，支持多语言，提供中文语言包的下载的开源在线图片存储分享服务系统，支持本地上传和在线获取两种图像上传方式。

Chevereto 这套程序可以像WordPress 一样搭建在任何空间上。而它的功能除了一般图片空间单纯的从电脑上传图片外，也可以利用网址也可以上传。

## 第一步：我们先去下载 chevereto 程序，这里我们介绍免费版给大家官网承诺永久免费版本

<img class="aligncenter" src="/images/2020/04/16/20160819171634.png" alt="" width="472" height="293" />

下载地址：<a href="https://www.lucktang.com/wp-content/themes/begin/go.php?url=aHR0cHM6Ly9naXRodWIuY29tL0NoZXZlcmV0by9DaGV2ZXJldG8tRnJlZQ==" target="_blank" rel="external nofollow noopener noreferrer">https://github.com/Chevereto/Chevereto-Free</a>

官网下载：<a href="https://chevereto.com/get-started" target="_blank" rel="noopener noreferrer">https://chevereto.com/get-started</a>  这里是一个installer.php文件（反正就是PHP文件）

第二步：我们把压缩包的文件 FTP 上传到网站的根目录。环境面板不同根目录地址各不相同我就不介绍了。总之上传到网站根目录下。

第三部：访问你的域名/installer.php

<img class="aligncenter" src="/images/2020/04/16/chevereto.png" alt="" width="736" height="470" />

许可证选择跳过

<img src="/images/2020/04/16/chevereto2.png" alt="填写管理员账号密码" width="726" height="511" /> 填写管理员账号密码

<img src="/images/2020/04/16/chevereto3.png" alt="填写数据库信息" width="727" height="639" /> 填写数据库信息

&nbsp;

<img class="aligncenter" src="/images/2020/04/16/chevereto4.png" alt="" width="768" height="350" />

<img src="/images/2020/04/16/chevereto5.png" alt="" width="758" height="823" /> 安装完成

&nbsp;

出现404解决方法

1.首先在网站目录下把index.php（看你从官网下载的是什么名字）文件授权777
2.然后，访问http://你的网站/index.php就能正常安装了

附上伪静态规则代码
    location / {
                if (-f $request_filename/index.html){
                    rewrite (.*) $1/index.html break;
                }
                if (-f $request_filename/index.php){
                    rewrite (.*) $1/index.php;
                }
                if (!-f $request_filename){
                    rewrite (.*) /index.php;
                }
                try_files $uri $uri/ /api.php;
            }
            location /admin {
                try_files $uri /admin/index.php?$args;
            }