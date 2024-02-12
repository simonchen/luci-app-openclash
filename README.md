# luci-app-openclash
luci-app-openclash for openwrt

v0.45.157 Forked from (https://github.com/vernesong/OpenClash)

# 安装luci-app-openclash在内存中
安装后的luci-app-openclash管理和内核将会全部运行在内存中，无需扩容/overlay分区！

## 安装方法1（首次本地安装推荐）
在packages目录中找到2个文件:
open_clash.tar.gz
open_clash.sh
用ftp上传至路由器/tmp目录下，在控制台或TTYD网而终端，运行下面命令完成安装:
```
cd /tmp && chmod 777 ./open_clash.sh && ./open_clash.sh
```
注意：如果你确保可以连接github，也可以不上传open_clash.tar.gz，运行上述命令将会自动从github下载并安装最新的包和内核！

## 安装方法2 （本地安装，针对路由器重启、自动恢复已保存的配置）
自行将上述2个文件复制到u盘，插入路由器并挂载，
例如：u盘的挂载根路径是/mnt/media ，下面放置这2个文件。
在系统启动项中，加入下述一行命令：(如果u盘的挂载根路径与示例不同，替换/mnt/media即可）
```
chmod 777 /mnt/media/open_clash.sh && /mnt/media/open_clash.sh
```
**推荐** 使用 如果之前已有保存过clash的配置文件，例如：config.yaml , 请预先将/etc/open克拉什/config/config.yaml先复制到/etc/config/目录下，
然后，修改系统启动项命令：(与上述命令几乎一样，结尾加入要恢复的clash配置文件路径 /etc/config/config.yaml)
```
chmod 777 /mnt/media/open_clash.sh && /mnt/media/open_clash.sh /etc/config/config.yaml
```

## 安装方法3 （远程github自动下载最新安装包，内核，针对路由器重启、自动恢复已保存的配置）
注意：必须确保路由器用curl或wget命令可以从github下载数据！
只需将open_clash.sh文件上传到路由器/root/目录下
在系统启动项中，加入下述一行命令：(如果u盘的挂载根路径与示例不同，替换/mnt/media即可）
```
chmod 777 /root/open_clash.sh && /root/open_clash.sh
```

**推荐** 使用如果之前已有保存过clash的配置文件，例如：config.yaml , 请预先将/etc/open克拉什/config/config.yaml先复制到/etc/config/目录下，
然后，修改系统启动项命令：(与上述命令几乎一样，只是在结尾加入要恢复的clash配置文件/etc/config/config.yaml)
```
chmod 777 /root/open_clash.sh && /root/open_clash.sh /etc/config/config.yaml
```

## 卸载方法
```
cd /tmp && chmod 777 ./open_clash.sh && ./open_clash.sh remove
```

# Revision
~ 覆写设置 - 绑定网络接口 
这个配置将与控制面板管理i/p保持一致，特别对于有多个LAN口的很有必要！
