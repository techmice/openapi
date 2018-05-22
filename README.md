

<html>
TechMICE v0.0.1
Powered by 会引擎<sup>TM</sup>
</html>


---
### Relationship picture
```
Your EMS = Your Event Management System

Getting start, you can push events which running in internal sytem, such as called EMS...

Your EMS->>会引擎: 推送会议
```

### How to use 会引擎
```

Your EMS->>会引擎: 1.获取token
会引擎->>Your EMS: 2.返回token
Your EMS->>会引擎: 3.获取应用程序入口
会引擎->>Your EMS: 4.返回入口
Your EMS->>会引擎: 5.打开应用程序
会引擎->>会引擎: 6.使用资源至会议完成
```



## 全局说明
### Host
* 测试环境：https://gateway-dev.smarteventcloud.cn
* 正式环境：待定
### 返回值
* 返回值固定结构

    
    {
      "success": true,
      "code": 0,
      "content": "返回的数据",
      "msg": "业务错误信息",
      "error": "异常错误信息,供开发使用"
    }
    
* 全局码

编码 | 编码解释
---|---
0 | 调用成功
500 | 调用发生异常

## 接口说明

### 授权相关

#### 获取token

##### 描述：

* 简述：获取token接口
* 请求URL：/api/foundation/passport/connect/token
* 请求方式：POST，application/x-www-form-urlencoded

##### 参数：

* 入参说明

参数名 | 类型 | 必选 | 说明
---|--- | --- | ---
ent_id | string | 是 | 企业id
user_name | string | 是 | 员工号
client_id | string | 是 | 应用id
client_secret | string | 是 | 应用secret
nounce | UUID | 是 | 36位随机数
signature | string | 是 | 签名

* 入参示例

    ent_id=lkfdjSNMosoamzSoam&user_name=123456&client_id=client.id&client_secret=client.secret&nounce=00000000-0000-0000-0000-000000000000&signature=sadkasdlkjjadkjasdmzcxnlkasdc
    
##### 返回

* 返回示例

    
    {
        "access_token": "eyJhbGciOiJSUzI1NiIsImtpZCI6ImM3MWVmODY2ZGI4ODM5Y2RiMGI1N2UxNzViMDYyOWNmI",
        "token_type": "Bearer",
        "refresh_token": "7c0a0d1fc42b8b0418090523a7c9541a0bb617242592b32be0b0151d6ca7c2c0",
        "userId": "3e293ec3-52a3-11e8-82e3-0242ac142204"
    }

### 应用相关

#### 获取应用入口

##### 描述：

* 简述：获取应用入口接口
* 请求URL：/api/foundation/application/getentry
* 请求方式：POST，application/json

##### 参数：

* 入参说明

参数名 | 类型 | 必选 | 说明
--- | --- | --- | ---
clientId | string | 是 | 客户端id

* 入参示例
    
    
    {
        "clientId":"client.id"
    }

##### 返回

* 返回值说明

参数名 | 类型 | 说明
---|--- | --- 
content | string | h5 app url

* 返回示例

    
    {
      "success": true,
      "code": 0,
      "content": "https://xxx.xxx.com",
      "msg": "",
      "error": ""
    }
    
### 基础数据相关

#### 员工导入

##### 描述：

* 简述：员工导入接口
* 请求URL：/api/foundation/employee/import
* 请求方式：POST，application/form-data

##### 返回

* 返回值说明

参数名 | 类型 | 说明
---|---|--- 

* 返回示例

    
    {
      "success": true,
      "code": 0,
      "content": "",
      "msg": "",
      "error": ""
    }
    
#### 合规餐厅导入

##### 描述：

* 简述：合规餐厅导入接口
* 请求URL：/api/shopkeeper/shop/import
* 请求方式：POST，application/form-data

##### 返回

* 返回值说明

参数名 | 类型 | 说明
---|---|---

* 返回示例

    
    {
      "success": true,
      "code": 0,
      "content": "",
      "msg": "",
      "error": ""
    }
    
#### 医院导入

##### 描述：

* 简述：医院导入接口
* 请求URL：/api/shopkeeper/hospital/import
* 请求方式：POST，application/form-data

##### 返回

* 返回值说明

参数名 | 类型 | 说明
---|---|---

* 返回示例

    
    {
      "success": true,
      "code": 0,
      "content": "",
      "msg": "",
      "error": ""
    }
    
#### 企业车队导入

##### 描述：

* 简述：企业车队导入接口
* 请求URL：/api/resource/car/supplier/import
* 请求方式：POST，application/form-data

##### 返回

* 返回值说明

参数名 | 类型 | 说明
---|---|---

* 返回示例

    
    {
      "success": true,
      "code": 0,
      "content": "",
      "msg": "",
      "error": ""
    }
    
#### 酒店导入

##### 描述：

* 简述：酒店导入接口
* 请求URL：/api/resource/venue/supplier/import
* 请求方式：POST，application/form-data

##### 返回

* 返回值说明

参数名 | 类型 | 说明
---|---|---

* 返回示例

    
    {
      "success": true,
      "code": 0,
      "content": "",
      "msg": "",
      "error": ""
    }
    
### 会议相关

#### 保存会议

##### 描述

* 简述：保存会议接口
* 请求URL：/api/engine/event/mice/save
* 请求方式：POST，application/json

##### 参数：

* 入参说明

参数名 | 类型 | 必选 | 说明
---|--- | --- | ---
miceId | UUID | 否 | 会议id，编辑时必选
tuUserId | UUID | 是 | 办会人
name | string | 是 | 会议名称
type | string | 是 | 会议类型
country | string | 是 | 会议国家
province | string | 是 | 会议省份
city | string | 是 | 会议城市
dtStart | datetime | 是 | 开始日期
dtEnd | datetime | 是 | 结束日期
qtyAttenderInt | int | 是 | 内部参会人数
qtyAttenderExt | int | 是 | 外部参会人数
descr | string | 否 | 备注

* 入参示例

    
    {
      "miceId": "00000000-0000-0000-0000-000000000000",
      "tuUserId": "00000000-0000-0000-0000-000000000000",
      "name": "测试会议",
      "type": "测试会议类型",
      "country": "中国",
      "province": "上海市",
      "city": "上海市",
      "dtStart": "2018-05-22",
      "dtEnd": "2018-05-22",
      "qtyAttenderInt": 1,
      "qtyAttenderExt": 2,
      "descr": "备注"
    }
    
##### 返回

* 返回示例

    
    {
      "success": true,
      "code": 0,
      "content": "00000000-0000-0000-0000-000000000000",
      "msg": "",
      "error": ""
    }
