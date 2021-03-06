# ShadowsocksR c# 版本3.0 #

下载链接：[http://www.mediafire.com/download/3n4cum20pkbmibc](http://www.mediafire.com/download/3n4cum20pkbmibc)  
官方网站：暂无，本版本目前不提供固定更新下载地址，只能通过自动更新提示的方式更新  

本系列版本正式更名为ShadowsocksR，R是revolution缩写。因更名，主版本号直接跳至3.0。  
从2.3.1.8版本开始<font color=red>支持代理UDP（以TCP转发或UDP转发均可），需要服务端更新</font>  
这个版本支持配合使用`SocksCap64/SocksCap/ProxyCap`等工具把需要TCP和UDP代理的程序通过本版本程序转发。  
即不需要折腾`OpenWrt`或路由器即可获得UDP转发的能力，配置容易了很多，是游戏玩家的福音  
如果你是用户，可向你的ss站长提议更新后端。  
如果你是站长，可从[https://github.com/breakwa11/shadowsocks/tree/manyuser](https://github.com/breakwa11/shadowsocks/tree/manyuser)获取最新的多用户分支代码，与原版本兼容。  
在linux上可安装git后执行  
`git clone -b manyuser https://github.com/breakwa11/shadowsocks.git`  
如有任何问题可发issue到github。

站长注意：

	此版本支持UDP over TCP，以及原版的UDP relay
	此版本的TCP relay和UDP relay支持包长度混淆
	避免首个数据包长度过于固定带来的被认证风险
	目前OpenWrt和Android版本的ss客户端使用原版的UDP relay
	UDP over TCP目前仅本C#分支从2.3.1.6起支持
	UDP over UDP目前仅本C#分支从2.3.1.8起支持

如需测试某Socks5代理能否支持UDP转发，可使用以下DNS工具测试  
[https://github.com/breakwa11/dnsproxy](https://github.com/breakwa11/dnsproxy)  
修改config.json然后直接运行test.py即可

#### 配置术语说明： ####
1. UDP over UDP （建议打钩）  
打钩即以UDP方式发送UDP包，不打钩则把UDP包在TCP里发送  
如果在发送UDP数据失败，可能是服务器只支持较早版本的UDP，去掉钩尝试。如果服务器支持则最好打钩。此选项不会影响浏览网页（TCP）
2. 混淆TCP协议头 （建议打钩）  
用于避免TCP包每次连接时发送的长度过于固定带来的被认证风险。如服务器支持最好打钩。如服务器不支持同时打了钩，会导致网页打不开。

#### 快捷操作提示： ####
1. 双击图标弹出服务器配置窗口，而右键图标弹出菜单
2. 连接统计窗口点击服务器会切换当前服务器
3. 连接统计窗口双击服务器会打开服务器配置窗口
4. 点击连接统计窗口列标题可排序（部分列不允许排序）
5. 连接统计窗口，在连接状态的错误记录三列，双击则重置错误数，双击百分比列则重置本服务器的所有信息
6. 连接统计窗口，在连接状态的“开”一列，鼠标点击切换开关状态（随机时有效），红色为关闭
7. 连接统计窗口，右键弹出清空所有的菜单
8. 连接统计窗口，双击连接数，断开该节点现有的连接（不会立即清零，双击过就行了）

提示：随机选择低延迟服务器功能，适用于网页浏览，不适用于看视频或下载等需要大流量的环境。如需下载请在连接统计窗口通过下载测速测试速度最快的服务器然后单独连接之。  
连接统计窗口“空连”是指发送了数据但无返回数据，或连接被重置，可能为ss密码错误，也可能是实际访问的结果，有返回数据时即会归0

本版本基于主干2.3.1版本进行开发，所有网络请求除启动时一次自动更新时连接至github外，均为用户或用户程序主动发出。<font color=red>（转发请保留此文档）</font>

#### 更新记录： ####
版本3.0  
1.软件更名  
2.修正UDP over UDP的加解密错误

版本2.3.2  
1.修正ipv4连接的问题  
其它：目前已知使用pc版微信发图发文件会导致polipo崩溃，建议改用Provixy，具体使用方法可以参考网上教程

版本2.3.1.9  
1.修正http连接会出现连接失败的问题（同时修正了自动更新和pac更新）  
2.增加连接管理，双击连接数即可断开该节点现有连接  
3.增强UDP连接兼容性  
4.更新地址可以配置窗口点击  

版本2.3.1.8  
1.支持TCP协议头混淆（需服务端更新支持）  
2.UDP包混淆（需服务端更新支持）  
3.<font color=red>支持UDP包通过UDP Relay转发（需服务端更新支持）</font>  
4.<font color=blue>支持Socks4/Socks4a协议</font>（使用时最好开启TCP混淆）  
5.局域网共享时支持同时监听IPv4/IPv6  
6.配置添加UDP包通过方式  
7.配置添加TCP协议头混淆

版本2.3.1.7  
1.IPv6连接修正  
2.随机时“按次序”方式的bug修正  
3.IPv6地址显示方式调整  
4.空连统计包含连接重置等错误  
5.服务器连接统计列排序功能  
6.取消自动关闭无效服务器，防误判  
7.手工检查更新

版本2.3.1.6  
1.增加随机选择服务器的方式  
2.连接数统计修正  
3.<font color=red>支持代理UDP（以TCP转发），需要服务端更新</font>，多用户使用  
[https://github.com/breakwa11/shadowsocks/tree/manyuser](https://github.com/breakwa11/shadowsocks/tree/manyuser)，  
与原manyuser分支完全兼容（单用户使用本链接的master分支），建议使用SocksCap64/SocksCap/ProxyCap使需要UDP转发的程序（如各类网游）走代理（不能使用Proxifier）

版本2.3.1.5  
1.调整配置窗口的设置体验  
2.软件自动更新支持  

版本2.3.1.4R2  
1.修正polipo某些情况下运行异常  
2.修正连接统计窗口一些错误  
3.修正部分dns错误未处理的问题  
4.三次错误后自动关闭无效服务器  
5.增加ChnIPList的pac，国内不代理，国外全走代理  
6.调整连接统计窗口列顺序  
7.节点自动重连尝试（开启随机选择服务器时，第一次重连相同节点，第二次、第三次选择其它节点）  
8.从剪贴板复制多行文本地址功能修正  
9.服务器配置显示二维码，增加列表高度

版本2.3.1.4  
1.polipo配置修正  
2.使用当前目录运行polipo，完美支持多开（端口同时支持socks5和http协议）  
3.增加当前下载速度统计，以及最大下载速度记录  
4.连接统计窗口优化显示效率  
5.服务器配置显示ss链接，以便快速复制  
6.连接统计窗口支持手工调整列宽  

版本2.3.1.3  
1.服务器的DNS缓冲（TTL=600），让直接填写域名与写IP一样稳定  
2.服务器连接状态记录，含上传下载流量，连接延迟统计，连接错误统计  
3.服务器独立开关，在连接状态的“开”一列，鼠标点击之，红色为关闭  
4.连接记录清除，在连接状态的错误记录三列，双击则重置错误数，双击百分比列则重置本服务器的所有信息  
5.统计列表标题显示监听方式及端口（方便多开的时候对应上）  
6.从剪贴板复制地址，方便从ss://xxxx这种格式快速输入  

版本2.3.1.2  
1.允许程序多开  
2.延迟统计，自动在低延迟服务器之中选择（高延迟的也会有低概率选取到）  
3.二维码菜单位置变动  
4.偶然会程序崩溃的问题不确定解决了没有，如还有发生请联系作者  

版本2.3.1.1  
1.随机选择服务器
