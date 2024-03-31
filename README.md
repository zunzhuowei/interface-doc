#接口文档
通用url地址部分：http(s)://host:port/{uri}，下面描述的只写{uri}部分。

> 部分接口可以匿名访问，其余需要登录后才可以访问。登录成功后服务端会返回`token`作为之后登录认证使用， 要求客户端在`请求头`中添加 `Authorization` 参数，值为服务端登录返回`token`值。
***

| 接口序号 | 接口名称       | uri地址          | 请求方式 |是否需要登录态 |
|:----:|:----------:|:--------------:|:----:|:----:|
| 1    | 微信登录接口 | api/anon/wechat/login | POST  | 否  |

***
请求参数（参数放到请求体中：RequestBody）

```json
{
  "code": "aaaaa"//微信登录认证code
}
```
返回值

```json
{
    "code": 0,//错误代码
    "data": [
        {
          "nickname"  : user.nickname,//用户昵称
          "headimgurl": user.headimgurl,//头像
          "sex"       : user.sex,//用户的性别，值为1时是男性，值为2时是女性，值为0时是未知。
          "city"      : user.city,//普通用户个人资料填写的城市
          "country"   : user.country,//国家，如中国为CN。
          "province"  : user.province //用户个人资料填写的省份
        },
      "token"// 用于服务器认证的token,往后的请求放到请求头 `Authorization` 参数中
    ]
}
```
***

| 接口序号 | 接口名称       | uri地址          | 请求方式 |是否需要登录态 |
|:----:|:----------:|:--------------:|:----:|:----:|
| 2    | 获取个人用户信息 | api/user/info | GET  |是 |

***
请求参数

```json
无
```
返回值

```json
{
    "code": 0,//错误代码
    "data": {
      "nickname"  : user.nickname,//用户昵称
      "headimgurl": user.headimgurl,//头像
      "sex"       : user.sex,//用户的性别，值为1时是男性，值为2时是女性，值为0时是未知。
      "city"      : user.city,//普通用户个人资料填写的城市
      "country"   : user.country,//国家，如中国为CN。
      "province"  : user.province //用户个人资料填写的省份
    }
}
```
***
| 接口序号 | 接口名称       | uri地址          | 请求方式 |是否需要登录态 |
|:----:|:----------:|:--------------:|:----:|:----:|
| 3    | 登出接口 | api/user/logout | GET  |是 |

***
请求参数

```json
无
```
返回值

```json
{
    "code": 0,//错误代码
    "data": "ok",
}
```
***
| 接口序号 | 接口名称       | uri地址          | 请求方式 |是否需要登录态 |
|:----:|:----------:|:--------------:|:----:|:----:|
| 4    | 获取会员信息 | api/get/vipInfo | GET  |是 |

***
请求参数

```json
无
```
返回值

```json
{
    "code": 0,//错误代码
    "data": {
      "isVip": true,//是否为会员
      "expTime": "yyyy-MM-dd HH:mm:ss"//过期时间
    }
}
```
***
| 接口序号 | 接口名称       | uri地址          | 请求方式 |是否需要登录态 |
|:----:|:----------:|:--------------:|:----:|:----:|
| 5    | 绑定账号密码（用于用户名密码登录）| api/user/binding | POST  |是 |

***
请求参数（参数放到请求体中：RequestBody）

```json
{
  "username": "用户名"，
  "password": "密码"
}
```
返回值

```json
{
    "code": 0,//错误代码
    "data": true,//绑定结果
}
```
***
| 接口序号 | 接口名称       | uri地址          | 请求方式 |是否需要登录态 |
|:----:|:----------:|:--------------:|:----:|:----:|
| 6    | 账号密码登录| api/anon/login | POST  |否 |

***
请求参数（参数放到请求体中：RequestBody）

```json
{
  "username": "用户名"，
  "password": "密码"
}
```
返回值

```json
{
    "code": 0,//错误代码
    "data": [
      {
        "nickname"  : user.nickname,//用户昵称
        "headimgurl": user.headimgurl,//头像
        "sex"       : user.sex,//用户的性别，值为1时是男性，值为2时是女性，值为0时是未知。
        "city"      : user.city,//普通用户个人资料填写的城市
        "country"   : user.country,//国家，如中国为CN。
        "province"  : user.province //用户个人资料填写的省份
      },
      "token"// 用于服务器认证的token,往后的请求放到请求头 `Authorization` 参数中
    ]
}
```
***

| 接口序号 | 接口名称       | uri地址          | 请求方式 |是否需要登录态 |
|:----:|:----------:|:--------------:|:----:|:----:|
| 7    | 隐私协议与关于我接口 | api/anon/about | GET  |否 |

***
请求参数 

```json
无
```
返回值

```json
{
    "code": 0,//错误代码
    "data": {
      "privacyAgreement": "隐私协议", //
      "aboutWe": "关于我"
    }
}
```
***
| 接口序号 | 接口名称       | uri地址          | 请求方式 |是否需要登录态 |
|:----:|:----------:|:--------------:|:----:|:----:|
| 8    | 获取商品列表 | api/anon/goods | GET  |否 |

***
请求参数

```json
无
```
返回值

```json
{
    "code": 0,//错误代码
    "data": [
      {
        name  : it.name,//商品名称
        descr : it.descr,//商品描述
        amount: it.amount,/** 销售数量 */
        /** 商品类型，0会员费，1升级次数费 */
        type  : it.type,
        price : it.price //商品价格
      },
      {
        name  : it.name,//商品名称
        descr : it.descr,//商品描述
        amount: it.amount,/** 销售数量 */
        /** 商品类型，0会员费，1升级次数费 */
        type  : it.type,
        price : it.price //商品价格
      }
    ]
}
```
***
| 接口序号 | 接口名称       | uri地址          | 请求方式 |是否需要登录态 |
|:----:|:----------:|:--------------:|:----:|:----:|
| 9    | 获取用户升级次数信息列表 | api/user/upgradeTimes | GET  |是 |

***
请求参数

```json
无
```
返回值

```json
{
    "code": 0,//错误代码
    "data": [
      {
        upgradeAllTimes: e.upgradeAllTimes,//一键升级次数
        upgradeTimes   : e.upgradeTimes,//普通升级次数
        expTime        : e.expTime, //过期时间，0表示永久
        type           : e.type //0初始赠送，1购买
      },
      {
        upgradeAllTimes: e.upgradeAllTimes,//一键升级次数
        upgradeTimes   : e.upgradeTimes,//普通升级次数
        expTime        : e.expTime, //过期时间，0表示永久
        type           : e.type //0初始赠送，1购买
      }
    ]
}
```
***
| 接口序号 | 接口名称       | uri地址          | 请求方式 |是否需要登录态 |
|:----:|:----------:|:--------------:|:----:|:----:|
| 10    | 获取用户升级记录 | api/upgrade/records/{pageSize}/{pageNum} | GET  |是 |

***
请求参数

```json
pageSize：页面条数
pageNum：页码
```
返回值

```json
{
    "code": 0,//错误代码
    "data": [
      {
        id    : e.id,//记录id
        status: e.status,//升级状态，0升级中，1成功，2失败
        info  : e.info //升级数据json
      },
      {
        id    : e.id,//记录id
        status: e.status,//升级状态，0升级中，1成功，2失败
        info  : e.info //升级数据json
      }
    ]
}
```
***
| 接口序号 | 接口名称       | uri地址          | 请求方式 |是否需要登录态 |
|:----:|:----------:|:--------------:|:----:|:----:|
| 11    | 普通升级 | api/upgrade/machine | POST  |是 |

***
请求参数（参数放到请求体中：RequestBody）

```json
{
  "info": "json"，//设备信息，由客户端自定义，服务端原封存储，在客户端需要时读取返还客户端
}
```
返回值

```json
{
  "code": 0,
  //错误代码
  "data": [
    {
      "id": 1,//记录id
      "info": "json"//设备信息，由客户端自定义，服务端原封存储，在客户端需要时读取返还客户端
      "status": 0 //升级状态，0升级中，1成功，2失败 
    }
  ]
}
```
***
| 接口序号 | 接口名称       | uri地址          | 请求方式 |是否需要登录态 |
|:----:|:----------:|:--------------:|:----:|:----:|
| 12    | 一键升级 | api/upgradeAll/machine | POST  |是 |

***
请求参数（参数放到请求体中：RequestBody）

```json
[
  {
    "info": "json"//设备信息，由客户端自定义，服务端原封存储，在客户端需要时读取返还客户端
  },
  {
    "info": "json"//设备信息，由客户端自定义，服务端原封存储，在客户端需要时读取返还客户端
  }
]

```
返回值

```json
{
    "code": 0,//错误代码
    "data": [
      {
        "id": 1,//记录id
        "info": "json"//设备信息，由客户端自定义，服务端原封存储，在客户端需要时读取返还客户端
        "status": 0 //升级状态，0升级中，1成功，2失败 
      },
      {
        "id": 2,//记录id
        "info": "json"//设备信息，由客户端自定义，服务端原封存储，在客户端需要时读取返还客户端
        "status": 0 //升级状态，0升级中，1成功，2失败 
      }
    ]
}
```
***
| 接口序号 | 接口名称       | uri地址          | 请求方式 |是否需要登录态 |
|:----:|:----------:|:--------------:|:----:|:----:|
| 13    | 更新设备记录状态，成功或者失败 | api/update/upgradeRecordsStatus | POST  |是 |

***
请求参数（参数放到请求体中：RequestBody）

```json
  {
    "successIds": [1,2,3,4],//升级成功的记录id
    "failIds": [5,6,7] //升级失败的记录id
  }

```
返回值

```json
{
    "code": 0,//错误代码
    "data": true,//更新成功
}
```
***
| 接口序号 | 接口名称       | uri地址          | 请求方式 |是否需要登录态 |
|:----:|:----------:|:--------------:|:----:|:----:|
| 14    | 更新设备记录状态，成功或者失败 | api/user/doWxPayOrder | POST  |是 |

***
请求参数（参数放到请求体中：RequestBody）

```json
  {
    "goodsId": 1，//购买的商品id
    "outTradeNo": 123455，//订单号，未支付的订单重新发起支付。如果outTradeNo为空，则取goodsId值，生成新订单；
  }

```
返回值

```json
{
    "code": 0,//错误代码
    "data": {
      "sign": "sign",//微信支付参数
      "prepayId": "prepayId", //微信支付参数
      "partnerId": "partnerId", //微信支付参数
      "appId": "appId", //微信支付参数
      "packageValue": "packageValue", //微信支付参数，前端使用时记得要更改为package
      "timeStamp": "timeStamp", //微信支付参数
      "nonceStr": "nonceStr" //微信支付参数
    }
}
```
***
| 接口序号 | 接口名称       | uri地址          | 请求方式 |是否需要登录态 |
|:----:|:----------:|:--------------:|:----:|:----:|
| 15    | 安卓id登录/注册 | api/anon/android/login | POST  |否 |

***
请求参数（参数放到请求体中：RequestBody）

```json
  {
    "androidId": "ddadfawef"，//安卓设备id
  }

```
返回值

```json
{
  "code": 0,//错误代码
  "data": [
    {
      "nickname"  : "androidId",//用户昵称
      "headimgurl": "",//头像
      "sex"       : "",//用户的性别，值为1时是男性，值为2时是女性，值为0时是未知。
      "city"      : "",//普通用户个人资料填写的城市
      "country"   : "",//国家，如中国为CN。
      "province"  : "" //用户个人资料填写的省份
    },
    "token"// 用于服务器认证的token,往后的请求放到请求头 `Authorization` 参数中
  ]
}
```
***
| 接口序号 | 接口名称       | uri地址          | 请求方式 |是否需要登录态 |
|:----:|:----------:|:--------------:|:----:|:----:|
| 16    | Paypal下订单接口 | api/user/doPaypalPayOrder | POST  |是 |

***
请求参数（参数放到请求体中：RequestBody）

```json
{
  "goodsId": 1，//购买的商品id
  "outTradeNo": 123455，//订单号，未支付的订单重新发起支付。如果outTradeNo为空，则取goodsId值，生成新订单；
}
```
返回值

```json
{
  "code": 0,//错误代码
  "data": [
    {
      "orderId"  : "",//订单id
      "link": ""//Paypal支付链接，需要webview打开
    }
  ]
}
```
***
| 错误代码（code） | 代码解读       |
|:----------------:|:--------------:|
| 0  | 成功|
| -1  | 失败|
| 100  | no token|
| 101  | token invalid|
| 102  | token parse error|
| 103  | 未找到相应Realm,无法认证、授权|
| 104  | 账户已存在|
| 105  | param error|
| 106  | 用户不存在|
| 107  | 密码错误|
| 108  | token expired|
| 109  | signature err|
| 110  | signature format err|
| 111  | 微信用户不存在|
| 112  | 关于我等信息未配置|
| 113  | 无vip用户权限|
| 114  | 初始赠送升级次数已存在|
| 115  | 初始化赠送升级次数获取锁失败|
| 116  | 升级余量不足|
| 117  | 扣除余量锁获取失败|
| 118  | 商品不存在|
| 119  | 支付订单已过期|
| 120  | 商品id和订单号不能同时为空|
| 121  | 订单不存在|
| 403  | access denied|

***
