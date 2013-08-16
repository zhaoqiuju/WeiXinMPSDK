DLL说明
----------
Senparc.Weixin.MP.dll：Senparc.Weixin.MP 微信SDK核心库

Senparc.Weixin.MP.MvcExtension.dll：在Senparc.Weixin.MP.dll基础上，为MVC4.0项目提供的扩展库，简化判断和输出。如果使用Webforms或Wcf等方式与维新服务器通讯，可以忽略这个dll。

Senparc.Weixin.MP.MvcExtension更新日志见：https://github.com/JeffreySu/WeiXinMPSDK/blob/master/Senparc.Weixin.MP.MvcExtension/readme.md


Senparc.Weixin.MP.dll升级记录
----------
v2.3 /2013-8-5

完善菜单类型，添加在线菜单编辑器

v2.2 /2013-8-5

优化菜单事件处理，解决菜单编码问题

v2.1 /2013-8-5

升级自定义菜单类型

v2.0 /2013-8-5

完成微信5.0 自定义菜单升级


v1.5 /2013-8-4

这是一个重要更新。

为MessageHandler提供了一个DefaultResponseMessage的抽象方法，
DefaultResponseMessage必须在子类中重写，用于返回没有处理过的消息类型（也可以用于默认消息，如帮助信息等）；
其中所有原OnXX的抽象方法已经都改为虚方法，可以不必每个都重写。若不重写，默认返回DefaultResponseMessage方法中的结果。

v1.4 /2013-7-23

为HttpUtility下方法提供Encoding选项。

v1.3 /2013-7-9

封装System.Web.HttpUtility下HTML及Url的Encode及Decode方法

v1.2 /2013-7-8

独立封装RequestUtility.GetQueryString方法，将Dictionary<string,string>类型数据转为QueryString格式。

v1.1 /2013-7-6

添加HttpPost提交方法，支持更多数据提交格式，为实现P2P更多扩展做准备。


v1.0 /2013-6-25

微信4.5 API正式稳定版。修复ResponseMessage生成的XML节点顺序问题。

v0.9 /2013-6-23

开始添加自定义菜单操作；

去掉ResponseMessageNews中的Content属性。


v0.8 /2013-5-21

添加IMessageHandler接口。


v0.7 /2013-5-14

完善通用接口http://mp.weixin.qq.com/wiki/index.php?title=通用接口文档 ，增加内置模拟Post及文件上传功能。


v0.6 /2013-5-7

优化MessageHandler：

废弃UserName，改为WeixinOpenId；

添加CancelExcute属性，以便在执行过程中及时中断处理程序；

添加`CreateResponseMessage<TR>()`方法，用于快捷生成以当前RequestMessage为基础的ResponseMessage。

v0.5 /2013-5-2

GpsHelper中添加了根据实际距离（KM）计算经度和纬度差的方法。

v0.4 /2013-5-1

EntityHelper中添加CreateResponseMessage<T>静态方法。

添加Senparc.Weixin.MP.HttpUtility.RequestUtility.IsWeixinClientRequest()方法，用于判断请求是否发起自微信客户端的浏览器。

v0.4.* /2013-5-1

版本号中的生成号和修订号开始使用.net自动编号方式。主版本和次版本决定版本功能比较大的差异。
也就是说从现在起只需要关注如0.4这两位主、次版本号，后面的2位生成号和修订号只是针对功能改进及记录编译次数，功能及方法上不会有太大变化，多数情况下可以不用同步更新。

v0.4.2 /2013-4-26

完善用户信息上下文。

MessageHandler中加入了OnExecuting和OnExecuted两个方法，分别在Execute()触发前/后运行。


v0.4.0 /2013-4-26


添加用户信息上下文，WeixinContext，可以很方便地跟踪某个用户的会话，并可以临时储存信息。

原先实现MessageHandler的类，如：

```C#
    public class MyMessageHandler : MessageHandler
```

现在需要在MessageHandler后加上“微信上下文”的泛型，如：
```C#
    public class MyMessageHandler : MessageHandler<MessageContext>
```
其中MessageContext可以是继承IMessageContext的任何子类，这里的MessageContext是SDK中的一个默认的简单实现。

v0.3.5 /2013-4-17

添加RequestMessageLink用于接收处理link类型的信息。同时MessageHandler也增加了对应的OnLinkRequest处理方法。

v0.3.4.2 /2013-4-17

修改GoogleMapHelper.GetGoogleStaticMap()方法，将List<Markers> markersList类型改为IList<Markers>。


v0.3.4 /2013-4-8

将IRequestMessageBase及IResponseMessageBase下的MsgType设为只读，这样所有子类的MsgType都会在开发的时候被确定下来，不用初始化之后再重复设置。

v0.3 /2013-4-5

添加MessageHandler处理类，简化二次开发时对信息的处理流程。

v0.3.1 /2013-03-19


新增自定义菜单等相关类型。


为access_token验证做好准备，提供简便的Http请求和Json转换方法。
