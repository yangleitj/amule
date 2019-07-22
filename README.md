`echo -n 你的密码 | md5sum | cut -d ' ' -f 1` #默认密码 btsynchina.com

`sudo -i` #使用root身份

`apt-get install amule-common amule-daemon git -y` #安装amule

`git clone https://github.com/yangleitj/amule.git /root/.aMule` #使用我的数据库和配置文件

`amuled`

`ctrl+c` #终止命令

`amuleweb -w`

`nohup amuled` #后台运行

>访问 http://ip:9999 到达 aMule



#如果你想手动修改配置文件

`cd /root/aMule`

`vi amule.conf` #编辑配置文件

>[eMule]

>Nick=BTSynChina.com #可以随便改

>Port=5773 #默认4662

>UDPPort=5783 #默认4672

>UPnPEnabled=1 #默认0

>[ExternalConnect]

>AcceptExternalConnections=1 #默认0

>ECPort=5823 #默认4712可以随便改

>ECPassword= #密码的md5编码，开头生成的

>UPnPECEnabled=1 #默认0

>[WebServer]

>Enabled=1 #默认0

>Password= #密码的md5编码

>Port=9999 #默认4711网页登陆端口号可以随便改

>UPnPWebServerEnabled=1 #默认0

`esc+:wq` #保存退出

`vi remote.conf`

>Locale=

>[EC]

>Port=5823 #默认4712可以随便改

>Password= #密码的md5编码，开头生成的

>[Webserver]

>Port=9999 #网页登陆端口号可以随便改

>UPnPWebServerEnabled=1 #默认0

>AdminPassword= #密码的md5编码，开头生成的

`esc+:wq` #保存退出

#通过CloudTorrent从VPS取回下载文件

`wget -qO- https://get.docker.com/ | sh` #安装Docker

>docker run -d --name CloudTorrent \ #安装CloudTorrent

>-p 7777:7777 \

>-v /root/aMule:/downloads \

>--restart always \

>jpillora/cloud-torrent --port 7777

#访问 http://ip:9999 到达 CloudTorrent
