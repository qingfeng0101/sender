# msg-sender

- [邮件API](https://github.com/qist/msg-sender/blob/master/email/README.md)

- [企业微信API](https://github.com/qist/msg-sender/blob/master/wechat/README.md)

## cfg.json 是纯json格式

> ```json
>{
>    "debug": true,
>    "http": {
>        "listen": "0.0.0.0:4000", //监听ip端口
>        "allow":["*"],// 填写ip，"*" 代表允许全部
>        "deny":[]
>    },
>    "smtp": {//邮件配置
>        "address": "smtp.exmail.qq.com:25",//邮件发送服务器地址
>        "username": "qist@example.com",
>        "password": "123456",
>        "authtype":"LOGIN"//认证类型/CRAM-MD5/LOGIN/PLAIN,默认PLAIN
>    },
>    "wechat":{//企业微信配置
>        "CorpID":"ww2085a342", //企业ID
>        "AgentId":1000002,//应用id，通过新建企业微信应用>获取
>        "Secret":"5WsjwD2DqyR4PMTWnJJp_qvyOothRjDAZs>aKc"//密串，企业微信应用中可以得到
>    }
>}
>```

## 测试方法

>```shell
>curl -d "to=test@qq.com,test@sina.com&subject=test&content=测试报文体" "http://10.1.1.202:4000/sender/mail"
>curl -d "to=qist&&content=测试报文体" "http://10.1.1.202:4000/sender/wechat"
>markdown格式"msg_type": "markdown"
>curl -H 'Content-Type: json'  -d {"to":"wangGang","content": "您的会议室已经预定，稍后会同步到`邮箱 \n  **事项详情** \n 事　项：<font color=\"info\">开会</font> \n 组织者：@miglioguan>参与者：@miglioguan、@kunliu、@jamdeezhou、@kanexiong、@kisonwang> \n 会议室：<font color=\"info\">广州TIT 1楼 301</font> \n日　期：<font color=\"warning\">2018年5月18日</font> \n 时　间：<font color=\"comment\">上午9:00-11:00</font> > \n 请准时参加会议。> \n 如需修改会议信息，请点击：[修改会议信息](https://work.weixin.qq.com)" ,"msg_type": "markdown"}' "http://10.1.1.202:4000/sender/wechat"
>```

```git
echo "# msgsender" >> README.md
git init
git add README.md
git commit -m "first commit"
git remote add origin https://github.com/qist/msg-sender.git
git push -u origin master
```
