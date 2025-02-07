# nvjdc


## 提示

由于我自己的环境是centos x86，arm不支持

这是打包过的 不要fork

不是热更新 每次修改配置需要重启容器


## 安装教程

如果你是装过NVjdc 先看看后面1.2以前如何更新之1.2升级说明

1拉源码

国外
```
git clone https://github.com/xomdeh/nvjdcdocker.git /etc/nolanjdc
```


2 拉取基础镜像
```
sudo docker pull xomdeh/nvjdc:2.3
```

3 执行命令

```
yum install wget unzip -y
```

4创建一个目录放配置

```
cd /etc/nolanjdc
```
```
mkdir -p  Config && cd Config
```

5下载config.json 配置文件 并且修改自己的配置 不能缺少


```
wget -O Config.json  https://raw.githubusercontent.com/xomdeh/nvjdcdocker/main/Config/Config.json
```

6 回到nolanjdc目录创建chromium文件夹并进入

```
cd /etc/nolanjdc && mkdir -p  .local-chromium/Linux-884014 && cd .local-chromium/Linux-884014
```

7下载 chromium 

```
wget https://mirrors.huaweicloud.com/chromium-browser-snapshots/Linux_x64/884014/chrome-linux.zip && unzip chrome-linux.zip
```

8删除刚刚下载的压缩包 

```
rm  -f chrome-linux.zip
```

9回到刚刚创建的目录

```
cd  /etc/nolanjdc
```



10启动镜像

```
sudo docker run   --name nolanjdc -p 5701:80 -d  -v  "$(pwd)":/app \
-v /etc/localtime:/etc/localtime:ro \
-it --privileged=true  xomdeh/nvjdc:2.3
```

11查看 日志 

```
docker logs -f nolanjdc 
```

  

出现 NETJDC  started 即可 



删除容器
```
docker rm -f nolanjdc 
```
然后从步骤9开始即可

后续更新只需要按照下方代码更新即可


## 更新

```
cd /root/nolanjdc
```
```
docker stop nolanjdc
```
```
git pull
```
```
docker start nolanjdc
```

## 特别声明:

* 本仓库涉仅用于测试和学习研究，禁止用于商业用途，不能保证其合法性，准确性，完整性和有效性，请根据情况自行判断.

* 本项目内所有资源文件，禁止任何公众号、自媒体进行任何形式的转载、发布。

* Nolan对任何代码问题概不负责，包括但不限于由任何脚本错误导致的任何损失或损害.

* 间接使用本仓库搭建的任何用户，包括但不限于建立VPS或在某些行为违反国家/地区法律或相关法规的情况下进行传播, Nolan对于由此引起的任何隐私泄漏或其他后果概不负责.

* 请勿将本项目的任何内容用于商业或非法目的，否则后果自负.

* 如果任何单位或个人认为该项目的脚本可能涉嫌侵犯其权利，则应及时通知并提供身份证明，所有权证明，我们将在收到认证文件后删除相关代码.

* 任何以任何方式查看此项目的人或直接或间接使用本仓库项目的任何脚本的使用者都应仔细阅读此声明。Nolan 保留随时更改或补充此免责声明的权利。一旦使用并复制了任何本仓库项目的规则，则视为您已接受此免责声明.

**您必须在下载后的24小时内从计算机或手机中完全删除以上内容.**  </br>
> ***您使用或者复制了本仓库且本人制作的任何脚本，则视为`已接受`此声明，请仔细阅读***

## 多谢

