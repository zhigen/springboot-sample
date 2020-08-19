简体中文 | [English](/README.en-US.md)

# springboot-sample
使用springboot框架的java项目，maven构建，作为后续springboot项目的基础项目

![logo](https://raw.githubusercontent.com/zhigen/specification-document/master/static/logo.png "logo tip")

[![badge](https://img.shields.io/badge/license-WTFPL-blue)](http://www.wtfpl.net/)

# 目录
* [1. 项目背景](#1)
* [2. 安装配置](#2)
    * [2.1. JDK](#21)
    * [2.2. maven](#22)
    * [2.3. idea](#23)
    * [2.4. docker](#24)
* [3. 使用](#3)
    * [3.1. jar包运行](#31)
    * [3.2. docker运行](#32)
    * [3.3. k8s运行](#33)
    * [3.4. git托管代码](#34)
* [4. 相关项目](#4)
* [5. 维护者](#5)
* [6. 贡献](#6)
* [7. 开源协议](#7)

<a id="1"></a>
## 1. 项目背景
记录并分享个人在开发过程中，使用到的技术的用法与示例。

<a id="2"></a>
## 2. 安装配置
开始使用前，需要安装的开发环境与配置。

<a id="21"></a>
### 2.1. JDK
* 安装

        下载安装，安装目录以下配置将会使用

* 配置环境变量

        $ setx JAVA_HOME "E:\jdk"
        $ setx CLASSPATH ".;%JAVA_HOME%\lib;%JAVA_HOME%\lib\tools.jar;"
        $ setx Path "%Path%%JAVA_HOME%\bin;"

<a id="22"></a>
### 2.2. maven
* 安装

        下载安装，安装目录以下配置将会使用

* 配置环境变量

        $ setx Path "%Path%E:\maven\bin;"

* 配置本地仓库

        打开配置文件
        E:\maven\conf\settings.xml
        指定地方加入
        <localRepository>E:\repo</localRepository>

* 配置镜像加速

        配置文件指定地方加入
        <mirror>
          <id>alimaven</id>
          <name>aliyun maven</name>
          <url>http://maven.aliyun.com/nexus/content/groups/public/</url>
          <mirrorOf>central</mirrorOf>
        </mirror>

<a id="23"></a>
### 2.3. idea
* 安装

        下载安装
        
* 配置

        修改默认maven配置：
        File | Other Settings | Settings for New Projects | Build, Execution, Deployment | Build Tools | Maven

<a id="24"></a>
### 2.4. docker
* 安装

        下载安装
        
* 配置
        
        设置共享盘为E盘，用于挂载目录

<a id="3"></a>
## 3. 使用
拉取本项目后，修改项目名，以此项目为基础直接进行开发。

<a id="31"></a>
### 3.1. jar包运行
    进入项目目录
    $ cd .
    执行打包命令（注：需要编译环境，依赖步骤2.1、2.2）
    $ mvn package -Dmaven.test.skip=true
    打包完成后
    $ cd target
    $ java -jar springboot-sample-1.0-SNAPSHOT.jar

<a id="32"></a>
### 3.2. docker运行
    $ cd .
    编写dockerFile
    创建镜像，最后的.不能省略
    $ docker build -t registry.cn-hangzhou.aliyuncs.com/zglu/springboot-sample:1 -f dockerFile .
    启动镜像
    $ docker run --name springboot-sample registry.cn-hangzhou.aliyuncs.com/zglu/springboot-sample:1

<a id="33"></a>
### 3.3. k8s运行
    $ cd .
    编写springboot-maven.yaml
    上传镜像到私有库前需要登录
    $ docker login --username=385861131@qq.com registry.cn-hangzhou.aliyuncs.com
    上传镜像
    $ docker push registry.cn-hangzhou.aliyuncs.com/zglu/springboot-sample:1
    创建k8s容器组
    $ kubectl create -f springboot-sample.yaml

<a id="34"></a>
### 3.4. git托管代码
    $ cd .
    $ git init
    $ git remote add origin https://github.com/zhigen/springboot-sample.git

<a id="4"></a>
## 4. 相关项目
[specification-document](https://github.com/zhigen/specification-document)<br/>

<a id="5"></a>
## 5. 维护者
[@zhigen](https://github.com/zhigen)

<a id="6"></a>
## 6. 贡献
[Pull Request](https://github.com/zhigen/springboot-sample/pulls)

<a id="7"></a>
## 7. 许可证
[WTFPL](/LICENSE) © Lu Zhigen