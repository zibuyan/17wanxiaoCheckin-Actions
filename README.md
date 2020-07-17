# 🏹17wanxiaoCheckin-Actions

> 基于Github-Actions的完美校园健康打卡

## 你可以在此项目中学到的东西

1、模拟器使用httpcanary抓包（其实还可以使用fiddle进行抓包）

2、httpcanary的初步使用

3、GitHub Actions自动化部署Python脚本

4、......

## 复杂的食用方法

### 一、模拟器抓包获取数据

#### 1、模拟器配置及使用

- 天翼网盘：https://cloud.189.cn/t/VRZryeb2aIBr（含雷神模拟器、完美校园、httpcanary安装包）
- 解压雷神模拟器压缩包并点击绿化
- 绿化完成点击桌面图标启动
- 拖动apk文件到模拟器窗口完成app的安装

![](https://s1.ax1x.com/2020/07/18/UcEUKJ.png)

![](https://s1.ax1x.com/2020/07/18/UcEdbR.png)

![](https://s1.ax1x.com/2020/07/18/UcEtv4.png)

#### 2、httpcanary的配置及使用

- 安装证书并移动到根目录
- 设置目标应用为完美校园APP

![](https://s1.ax1x.com/2020/07/18/UcViM4.png)

![](https://s1.ax1x.com/2020/07/18/UcV9RU.png)

![](https://s1.ax1x.com/2020/07/18/UcVpGT.png)

#### 3、开始抓包

- 打开完美校园app，进入健康打卡并设置相关信息（不提交）
- 切换到httpcanary，开启抓包
- 切换完美校园提交信息，打卡成功
- 切换httpcanary，停止抓包

![](https://s1.ax1x.com/2020/07/18/UcVFsJ.png)

#### 4、抓包分析

- 翻阅找到sass字样的链接，点击进去（如果有多个点靠上面的）
- 第一个框为请求连接，第二个框为此网络请求为post请求
- 点击请求一栏，并在底部选择text，即可查看自己所填写的数据（记下来，或者复制出去）
- 点击响应一栏，并在底部选择text，即可查看响应结果（成功则为打卡成功，打卡频繁则失败）
- 至此我们就获得了我们绝大多数的数据了

![](https://s1.ax1x.com/2020/07/18/UcVGdI.png)



### 二、Server酱服务的申请

#### 1、申请一个GItHub账号

- Github官网：https://github.com/ （使用邮箱注册并验证）

#### 2、注册Server酱服务，并绑定微信

- 使用刚注册的Github账号登录
- 微信绑定，扫码关注即可绑定
- 测试一下是否能推送成功，并复制下自己的SCKEY
- 至此我们就获得了我们的最后一个数据，接下来就是了解如何使用此项目文件了

![](https://s1.ax1x.com/2020/07/18/UcZE6g.png)

![](https://s1.ax1x.com/2020/07/18/UcZVXQ.png)

![](https://s1.ax1x.com/2020/07/18/UcZA1S.png)

![](https://s1.ax1x.com/2020/07/18/UcZkp8.png)

![](https://s1.ax1x.com/2020/07/18/UcZiff.png)

### 三、项目fork与部署

#### 1、点击链接进入项目文件并fork到自己的GitHub上

- 此项目地址：https://github.com/ReaJason/17wanxiaoCheckin-Actions

- 点击右上角的fork即可将项目文件拉到自己的库中

![](https://s1.ax1x.com/2020/07/18/UcncB4.png)

![](https://s1.ax1x.com/2020/07/18/UcngHJ.png)

#### 2、设置Secrets，输入项目运行的数据

- 找到自己fork的库，点击Settings->Secrets->New sceret

- 字段名使用大写，下面的值则填写自己的值，总共12个，细心填写这关乎之后的成功与否

- ```
  # 设置如下secret字段
  """
  TEXT(学院专业班级信息)                例：林学院-林学(陶铸实验班)-2017林学(陶铸实验班)1班
  DEPTID(未知id字段)                   例：141670
  ADDRESS(详细地址)                    例：非常富贵
  ADDTEXT(省-市-县/区)                 例：江西省-南昌市-高新区
  CODE(盲猜邮编)                       例：360192
  STUNUM(学号)                        例：20170101
  USERNAME(姓名)                      例：小冯
  PHONENUM(电话)                      例：...自己电话...
  USERID(完美校园分配的用户id)          例：6274894
  EMERGENCY(紧急联系人)                例：紧急人
  EMERGENCYPHONE(紧急联系人电话)        例：23667712771
  SCKEY(Server酱微信推送)
  """
  ```

![](https://s1.ax1x.com/2020/07/18/UcnWNR.png)

![](https://s1.ax1x.com/2020/07/18/UcnRE9.png)

![](https://s1.ax1x.com/2020/07/18/UcnIgK.png)

#### 3、开启Actions

- 找到自己fork的库，点击Settings->Action->I understand...

- 回到项目主页，修改README.md触发Actions

![](https://s1.ax1x.com/2020/07/18/Ucnx8P.png)

![](https://s1.ax1x.com/2020/07/18/UcnHDe.png)

![](https://s1.ax1x.com/2020/07/18/UcnbHH.png)

![](https://s1.ax1x.com/2020/07/18/Ucn7uD.png)

![](https://s1.ax1x.com/2020/07/18/UcuSv8.png)

#### 4、查看结果

- 通过Update README.md -- > build -- > HealthCheckin
- 手机微信推送查看
- 成功了一次之后则开启了自动化部署（每天早上六点自动打卡）
- 如果失败，则在运行状况的HealthCheckin中查看报错情况，解决不了可以提issue

![](https://s1.ax1x.com/2020/07/18/UcuCDg.png)

<img src="https://s1.ax1x.com/2020/07/18/Ucu9KS.jpg" style="zoom:33%;" />

### 四、Actions具体流程

> Tips：actions配置文件在\.github\workflows\run.yml中
>

#### 1、参数设置(secret)

```python
# 设置如下secret字段
"""
TEXT(学院专业班级信息)                例：林学院-林学(陶铸实验班)-2017林学(陶铸实验班)1班
DEPTID(未知id字段)                   例：141670
ADDRESS(详细地址)                    例：非常富贵
ADDTEXT(省-市-县/区)                 例：江西省-南昌市-高新区
CODE(盲猜邮编)                       例：360192
STUNUM(学号)                        例：20170101
USERNAME(姓名)                      例：小冯
PHONENUM(电话)                      例：...自己电话...
USERID(完美校园分配的用户id)          例：6274894
EMERGENCY(紧急联系人)                例：紧急人
EMERGENCYPHONE(紧急联系人电话)        例：23667712771
SCKEY(Server酱微信推送)
"""


# 相关参数设置即对应下面的数据输入
"""
python3 17wanxiao.py <<EOF
${{secrets.TEXT}}
${{secrets.DEPTID}}
${{secrets.ADDRESS}}
${{secrets.ADDTEXT}}
${{secrets.CODE}}
${{secrets.STUNUM}}
${{secrets.USERNAME}}
${{secrets.PHONENUM}}
${{secrets.USERID}}
${{secrets.EMERGENCY}}
${{secrets.EMERGENCYPHONE}}
${{secrets.SCKEY}}
EOF
"""
```

#### 2、计划时间参数

```python
schedule:
   - cron: 0 22 * * * # 表示每天6点进行任务
# cron后面的时间为国际事件
# 五位数(空格分隔)分别为分钟、小时、天、月、一个星期的第几天
# 国际时与北京时的查询网站：http://www.timebie.com/cn/universalbeijing.php
```

#### 3、Install Python

```python
# 为虚拟机安装python3环境
run: |
    sudo apt update && \
    sudo apt install python3
# 由于使用的是Ubuntu的虚拟机，因此执行的是linux语句
```

#### 4、Pip install requests

```python
# 为py程序的执行安装第三方库requests
run: |
    pip3 install requests -i https://pypi.tuna.tsinghua.edu.cn/simple
```

#### 5、HealthCheckin

```python
# 运行py脚本文件
run: |
    python3 17wanxiao.py <<EOF
    ${{secrets.TEXT}}
    ${{secrets.DEPTID}}
    ${{secrets.ADDRESS}}
    ${{secrets.ADDTEXT}}
    ${{secrets.CODE}}
    ${{secrets.STUNUM}}
    ${{secrets.USERNAME}}
    ${{secrets.PHONENUM}}
    ${{secrets.USERID}}
    ${{secrets.EMERGENCY}}
    ${{secrets.EMERGENCYPHONE}}
    ${{secrets.SCKEY}}
    EOF
```

> 感谢你的使用，觉得可以的话，可不可以给个免费的star✨