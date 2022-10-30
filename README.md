# 小米运动自动刷步数

> 小米运动自动刷步数

## Github Actions 部署指南

### 一、Fork 此仓库

### 二、设置账号密码

添加名为 **USER**、**PWD**、**OPEN_GET_WEATHER**、**AREA**、**PAT** 的变量

> Settings-->Secrets-->New secret

| Secrets |  格式  |
| -------- | ----- |
| USER |   小米运动登录账号,仅支持小米运动账号对应的手机号,不支持小米账号|
| PWD |   小米运动登录密码,仅支持小米运动账号对应的密码|
| OPEN_GET_WEATHER |   开启根据地区天气情况降低步数**False**关闭,**True**开启。（当前存在问题，请设置为**False**）|
| AREA |   设置获取天气的地区（上面开启后必填）如：**北京**，当**OPEN_GET_WEATHER**为**False**时填写**NO**。（当前存在问题，请设置为**NO**）|
| PAT |   此处**PAT**需要申请，值为github token，教程详见：https://www.jianshu.com/p/bb82b3ad1d11 ,需要repo和workflow权限,此项必填，避免git push的权限错误。 |

### 三、多账户(用不上请忽略)

多账户请用 **#** 分割 然后保存到变量 **USER** 和 **PWD**

#### 例如

**13800138000#13800138001** 变量 **USER**

**abc123qwe#abcqwe2** 变量 **PWD**

### 四、自定义启动时间

编辑 **.github/workflows/run.yml**

找到 cron: 0 10 * * *

修改其中的10为你需要修改的时间

需要运行的时间-8就是UTC时间，比如上午9点，9-8=1，则cron: 0 1 * * *

### 五、启动

> Actions-->点击“I understand my workflows, go ahead and enable them”-->All workflows-->刷步数-->点击“Enable workflow”

## 注意事项

1. 每天运行一次，在下午 6 点

2. 多账户的数量和密码请一定要对上 不然无法使用!!!

3. 启动时间得是UTC时间!

4. 如果支付宝没有更新步数,到小米运动->设置->账号->注销账号->清空数据,然后重新登录,重新绑定第三方
