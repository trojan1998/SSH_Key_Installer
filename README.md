# SSH Key Installer

[![LICENSE](https://img.shields.io/github/license/mashape/apistatus.svg?style=flat-square&label=LICENSE)](https://github.com/P3TERX/SSH_Key_Installer/blob/master/LICENSE)
[![GitHub Stars](https://img.shields.io/github/stars/P3TERX/SSH_Key_Installer.svg?style=flat-square&label=Stars)](https://github.com/P3TERX/SSH_Key_Installer/stargazers)
[![GitHub Forks](https://img.shields.io/github/forks/P3TERX/SSH_Key_Installer.svg?style=flat-square&label=Forks)](https://github.com/P3TERX/SSH_Key_Installer/fork)

本脚本能做什么？
一键拉取公钥并安装到你的VPS，使你的服务器拥有密钥登陆的功能，更改你的VPS端口防止默认22端口被字典穷举法爆破，禁止VPS密码登录，即便被爆破无法登录，使用它极大地提高你的VPS小鸡安全性，一举三得，一个代码解决。如果你有大量服务，那么它将无疑大大减少你一个个配置的工作量。

## 第一步、生成你的公钥和私钥
`ssh-keygen -t ecdsa -b 521`

此方法适用于 Win­dows 10 (1803后)的 Pow­er­Shell 或 WSL，Linux 发行版和 ma­cOS 自带的终端，但不仅限于这些环境。

521 位的 ECDSA 密钥比起 RSA 密钥更安全且验证速度更快。

操作完后会在 ~/.ssh 目录中生两个密钥文件，id_ecdsa 为私钥，id_ecdsa.pub 为公钥。公钥就是我们需要安装在远程主机上的,私钥自己保存好，放在电脑本地或者网盘啥的，以后和公钥进行配对验证才能登陆。

~符号代表用户主目录，俗称家目录。其路径与当前登陆的用户有关，在 Linux 中普通用户家目录的路径是/home/用户名，而 root 用户是/root。Win­dows 10 中路径是C:\Users\用户名。在 ma­cOS 中路径是/Users/用户名。自己仔细找找能找到的。

## 第二步、上传你的pub公钥到你的网站根目录或者GitHub上，
如果是你的网站是xxx.xxx那么相应地址就是<http://xxx.xxx/xxx.pub>
GitHub的上传地址是<https://github.com/settings/keys>

## 第三步、安装
使用GitHub上公钥的代码，并改端口为55055，禁止使用密码登录，会自动覆盖原有的公钥证书

`bash <(curl -fsSL git.io/key.sh) -og 你的github用户名 -p 55055 -d`

使用网站上公钥的代码，并修改端口为55055，禁止使用密码登录

``bash <(curl -fsSL git.io/key.sh) -ou 存放公钥的绝对路径 -p 55055 -d``


语法及选项说明
bash <(curl -fsSL git.io/key.sh) [选项...] <参数>
-o - 覆盖模式，必须写在最前面才会生效
-g - 从 GitHub 获取公钥，参数为 GitHub 用户名
-u - 从 URL 获取公钥，参数为 URL
-f - 从本地文件获取公钥，参数为本地文件路径
-p - 修改 SSH 端口，参数为端口号
-d - 禁用密码登录

有什么疑问可以联系原作者P3TERX，以上都是扣来的，谢谢。
