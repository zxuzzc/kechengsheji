# JLU Daily Reporter



本项目基于TechCiel/jlu-health-reporter[链接](https://github.com/TechCiel/jlu-health-reporter)进行少量修改

为吉林大学本科生每日打卡所作的自动机器人。（一测温一点名版）

以 WTFPL 授权开源。

## 免责声明

本自动程序适用于 2020-2021 秋季学期吉林大学本科生每日健康打卡（一测温一点名），不保证按时更新。研究生打卡是否适用未经测试。

**使用本程序自动提交打卡，你必须实际完成一日一测温，在指定时间回到寝室，并在身体状况出现异常时立刻联系校医院和辅导员。**

__**如运行本程序，您理解并认可，本自动程序的一切操作均视为您本人进行、或由您授权的操作。本程序作者对您因使用此程序可能受到的损失、处罚以及造成的法律后果不负任何责任。**__

## 使用说明

需要 Python 3 ，先 `pip3 install requests` 。

运行之前**先登录平台提交一次打卡**，务必确保信息准确。

参照 example-config.json 建立配置文件 config.json ，填入登录信息和对应表单项（目前校区、公寓楼、寝室号和部分同学的班级需要程序每次指定）的值（注意均使用字符串值）。

**请一定要正确配置config文件，因为没有正确配置造成的一切后果与程序作者无关**

校区id和公寓楼id也可以在上传的json里查找


目前尚未适配校外居住 请见谅

```json
{
	"transaction": "BKSMRDK",
	"users": [
		{
			"username": "zhangsan2120",
			"password": "password",
			"fields": {
				
				"fieldSQxq": "1",//校区号（要填写的内容请自行f12查找不详细写了
				"fieldSQgyl": "1",//公寓号
				"fieldSQqsh": "1088",//寝室号
				"fieldSQnj": "2118",//学号前四位
				"fieldSQnj_Name": "2018",//入学年份
				"fieldSQbj": "881",//班级id需要自行抓包
				"fieldSQbj_Name": "211827"//班级名称严格按照学号前四位+班级的形式
			}
		},
		{
			"username": "lisi2120",
			"password": "password",
			"fields": {
				"fieldSQxq": "1",
				"fieldSQgyl": "1",
				"fieldSQqsh": "1088",
				"fieldSQnj": "2118",
				"fieldSQnj_Name": "2018",
				"fieldSQbj": "881",
				"fieldSQbj_Name": "211827"
			}
		}
	]
}

```



Crontab 模式：

//可能需要将` jlu-daily-reporter.py `中的CONFIG更改为绝对路径

```
10 11,21 * * * /usr/bin/python3 /path/to/jlu-daily-reporter.py >> reporter.log 2>&1
# 10分开始避免服务器时间略有偏差导致失败,以及服务器高峰期
```

手动模式（请在时段内启动）：

```
./jlu-daily-reporter.py
```

## 更新预告

期末结束后可能会写一个web端自动生成json

**敬请期待**

## 联系

欢迎开 issue / pr ，随缘处理。

项目讨论请到[@JLU_LUG](https://t.me/JLULUG)
