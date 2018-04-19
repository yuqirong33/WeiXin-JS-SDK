# WeiXin-JS-SDK  Demo

使用微信JS-SDK        
1.查看公众号是否有使用JSSDK的权限        
2.登录微信公众平台查看开发>接口权限        

使用JSSDK主要包括:        
1、判断当前客户端版本是否支持指定JS接口        
2、分享接口（微信认证）        
3、图像接口        
4、音频接口        
5、智能接口（识别语音并返回结果）        
6、设备信息（获取网络状态）        
7、地理位置        
8、界面操作        
9、微信扫一扫        
10、微信小店（服务号必须通过微信认证）        
11、微信卡券 （微信认证）        
12、微信支付（服务号必须通过微信认证）        

### 使用JSSDK步骤:        
1.绑定域名        
先登录微信公众平台进入公众号设置的功能设置里填写JS接口安全域名。        

2.引入JS文件        
在需要调用JS接口的页面引入如下JS文件，（支持https）        
http://res.wx.qq.com/open/js/jweixin-1.0.0.js        

3.通过config接口注入权限验证配置                
```javascript
wx.config({
    debug: true, // 开启调试模式,调用的所有api的返回值会在客户端alert出来，若要查看传入的参数，可以在pc端打开，参数信息会通过log打出，仅在pc端时才会打印。
    appId: '', // 必填，公众号的唯一标识
    timestamp: , // 必填，生成签名的时间戳
    nonceStr: '', // 必填，生成签名的随机串
    signature: '',// 必填，签名，见附录1
    jsApiList: [] // 必填，需要使用的JS接口列表，所有JS接口列表见附录2
});
```

4.通过ready接口处理成功验证                
config信息验证后会执行ready方法，所有接口调用都必须在config接口获得结果之后，config是一个客户端的异步操作，所以如果需要在页面加载时就调用相关接口，则须把相关接口放在ready函数中调用来确保正确执行。对于用户触发时才调用的接口，则可以直接调用，不需要放在ready函数中。        

5.通过error接口处理失败验证        
```javascript
wx.error(function (res) {        
     alert(res.errMsg);        
});        
```

6.接口调用        


- 开发文档：http://mp.weixin.qq.com/wiki/7/aaa137b55fb2e0456bf8dd9148dd613f.html
