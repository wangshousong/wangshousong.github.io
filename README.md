#  消息中心接口文档
消息中心接口文档
## 消息中心发送接口
### 接口地址

>  集成环境

https://utestmsg.51ykb.com/msg/send

> 生产环境

https://msg.51ykb.com/msg/send

### 请求头

```http
Content-Type: application/json
```
### 请求方法

post

### 请求体

```json
{
    "header": {
        "appId": "rYl8WtAQnYgmEsr7C2yCB47jR7qLH6rOAmfv4ZZN0NVf8VSmwHoDe48slaOFoqgs",
        "appSecret": "AZm5K1eDfwkm270YuQV5yUFwRhDXLHchwhlTp89PNJzW0PbIVOXKGFN8PJ3YySJk"
    },
    "body": {
        "cc": [
            "18171204332"
        ],
        "config": {},
        "msgParams": {
            "name": "king",
            "time": "2020-08-08 08:08:08"
        },
        "templateContent": "",
        "templateId": "1",
        "to": [
            "18171204332"
        ]
    }
}
```
>入参

|参数名|必选|类型|说明|
|---|---|---|---|
|header|是|map|参数头|
|header.appId|是|string|appId-消息中心提供|
|header.appSecret|是|string|秘钥-消息中心提供|
|body|是|map|请求体|
|body.cc|否-邮箱专用|List&lt;String&gt;|抄送人|
|body.to|是|List&lt;String&gt;|发送人|
|templateId|是|String|模板ID-消息中心提供|
|templateContent|否|String|模板内容，预留扩展字段|
|msgParams|是|map|消息模板参数值|
|config|否|map|预留扩展字段|
|config.parse|否|boolean|邮件类型动态解析标识|
|config.html|否|boolean|邮件内容是否是html类型|




>出参

```json
{
    "code": 200,
    "success": true,
    "message": "消息已提交",
    "data": {
        "msgId": "1",
        "errorMsg":"消息发送错误原因",
        "content":"消息内容(模板参数替换后)"
    }
}
```

|参数名|必选|类型|说明|
|---|---|---|---|
|code|是|int|状态码，200正常，其他异常|
|success|是|boolean|true正常，false异常|
|message|是|string|消息|
|data|是|map|返回数据|
|data.msgId|是|Long|消息ID，查看消息发送状态|
|data.errorMsg|是|String|发送成功为空|
|data.content|是|String|消息内容(模板参数替换后)|


## 其他

为了和发送接口区分，新增了2个接口:预览消息，模拟发送消息

### 预览消息

>  集成环境

https://utestmsg.51ykb.com/msg/preview

> 生产环境

https://msg.51ykb.com/msg/preview

* 参数同发送消息接口: body.config.preview 必须为true

### 模拟发送消息

>  集成环境

https://utestmsg.51ykb.com/msg/preview

> 生产环境

https://msg.51ykb.com/msg/preview

* 参数同发送消息接口: body.config.preview 必须为true



