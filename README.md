# 原作者已经挺更，更新了Erope的修改版
https://github.com/Erope/baidupcs-web/releases
Docker Hub：https://hub.docker.com/r/hdtv720p/baidupcs-web


# 离线百度网盘下载Docker版
Docker Hub：https://hub.docker.com/r/superng6/baidupcs-web  
GitHub：https://github.com/SuperNG6/docker-baidupcs-web  
博客：https://sleele.com/2020/01/06/在群晖nas上离线下载百度网盘/  



PS：docker hub的用户是无法看到GitHub中的图片，会显示为框框，具体图文详情可以在我的博客上浏览

# 本镜像的一些优点
- 做了usermapping，使用你自己的账户权限来运行，这点对于群辉来说尤其重要
- 纯BaiduPCSGo，没有包含多于的服务
- 可选择上海时区 Asia/Shanghai
- 最新版本BaiduPCSGo


# Changelogs
## 2019/12/19

      1、首次提交，基于BaiduPCSGo 3.7.0

# Document

## 挂载路径
``/config`` ``/root/Downloads``
## 群晖开启SSL反向代理教程
控制面板 => 应用程序门户 => 反向代理 => 编辑刚才添加的条目 => 自定义标题 => 点小箭头 => WebSocket (来自[creepsnail](https://github.com/creepsnail))



## 关于群晖

群晖用户请使用你当前的用户SSH进系统，输入 ``id 你的用户id`` 获取到你的UID和GID并输入进去

![HAuTo6](https://cdn.jsdelivr.net/gh/SuperNG6/pic@master/uPic/HAuTo6.jpg)
![9dvvpb](https://cdn.jsdelivr.net/gh/SuperNG6/pic@master/uPic/9dvvpb.jpg)
![zFmSGs](https://cdn.jsdelivr.net/gh/SuperNG6/pic@master/uPic/zFmSGs.jpg)

### 权限管理设置
对你的``docker配置文件夹的根目录``进行如图操作，``你的下载文件夹的根目录``进行相似操作，去掉``管理``这个权限，只给``写入``,``读取``权限
![FJ9bL9](https://cdn.jsdelivr.net/gh/SuperNG6/pic@master/uPic/FJ9bL9.jpg)


## Linux

输入 ``id 你的用户id`` 获取到你的UID和GID，替换命令中的PUID、PGID

__执行命令__
````
docker run -d \
  --name=baidupcs-web \
  -e PUID=1026 \
  -e PGID=100 \
  -e TZ=Asia/Shanghai \
  -p 5299:5299 \
  -v /path/to/appdata/config:/config \
  -v /path/to/downloads:/root/Downloads \
  --restart unless-stopped \
  superng6/baidupcs-web
  ````
docker-compose  
  ````
version: "2"
services:
  aria2:
    image: superng6/baidupcs-web
    container_name: baidupcs-web
    environment:
      - PUID=1026
      - PGID=100
      - TZ=Asia/Shanghai
    volumes:
      - /path/to/appdata/config:/config
      - /path/to/downloads:/root/Downloads
    ports:
      - 5299:5299
    restart: unless-stopped 
````

# Preview
![uQdDxb](https://cdn.jsdelivr.net/gh/SuperNG6/pic@master/uPic/uQdDxb.jpg)
