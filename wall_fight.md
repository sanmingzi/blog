# Wall fight

[XX-Net](https://github.com/XX-net/XX-Net)

We deploy the proxy server to google cloud platform and we install the proxy client in our machine, so we can fight the wall.

## Deploy proxy to google cloud platform

The preconditions of this is we can visit the free internet.

### Create appids

[How to create my appids](https://github.com/XX-net/XX-Net/wiki/how-to-create-my-appids)

### Deploy proxy server

- [Download](https://github.com/XX-net/XX-Net/blob/master/code/default/download.md) package。
- 下载完毕后解压缩文件夹，运行文件夹中start.vbs文件。
- 打开部署页面http://127.0.0.1:8085/?module=gae_proxy&menu=deploy，输入appids用‘|’隔开，例如（zhiming-safe-00|zhiming-safe-01）,点击开始部署。
- 部署的过程当中需要登陆google账号。

## How to use GAE-Proxy

### Enable IPv6

Sometimes we can not search the IPv4 google ips, we should enable ipv6.

[使用Teredo隧道,提前感受IPv6](https://www.longsays.com/844.html)

我们可以通过这个[test-ipv6](http://test-ipv6.com/)来测试自己的机器是否已经支持IPv6。访问网站之后，如果看到：

```
你在網際網路上的IPv6位址 2001:0:53aa:64c:45c:28d7:3550:ba9c
你的 IPv6 連線服務是透過: Teredo
測試 IPv6 (跳過DNS)	 	
成功 (0.240s) 使用 ipv6 Teredo
```

说明机器已经支持IPv6。

- 使用管理员身份运行cmd
- netsh interface teredo set state server=teredo.remlab.net
- netsh int ter set state enterpriseclient
- netsh interface ipv6 show teredo

如果上述方法失败，尝试将teredo.remlab.net更换成其他的teredo地址。

- teredo.remlab.net/teredo-debian.remlab.net (法国) (Miredo 默认设置)
- teredo.autotrans.consulintel.com (西班牙)
- teredo.ipv6.microsoft.com (美国 雷蒙德) (Windows XP/2003/Vista/7/2008 系统默认设置)
- teredo.ngix.ne.kr (韩国)
- teredo.managemydedi.com (美国 芝加哥)

### Install proxy client

[Reference](https://github.com/XX-net/XX-Net/wiki/%E4%BD%BF%E7%94%A8Chrome%E6%B5%8F%E8%A7%88%E5%99%A8)

- [Download](https://github.com/XX-net/XX-Net/blob/master/code/default/download.md) package。
- 下载完毕后解压缩文件夹，运行文件夹中start.vbs文件。
- 启动之后，右下角会出现托盘图标，右键单击图标，选择“取消全局代理”。
- 打开XX-Net/SwitchyOmega文件夹；打开浏览器的扩展程序页面 chrome://extensions 。把SwitchyOmega.crx文件拖放到浏览器扩展程序页面安装。
- 导入bak文件，该bak文件里面包含了一些Proxy规则。点击“GAE-Proxy自动切换”，然后点击“立即更新情景模式”。我们还可以为该情景模式自定义一些Proxy规则。
- 点击SwitchyOmega，切换成“GAE-Proxy自动切换”。
- 打开http://localhost:8085/?module=gae_proxy&menu=config，输入appids，多个用“|”隔开，例如（zhiming-safe-00|zhiming-safe-01）。
