# CQ-picfinder-robot-add-on

给Tsuk1ko的CQ-picfinder-robot V2.11做了几个小挂件，基本稳定，至少目前看起来很稳而且从没翻车
   
   **注意！！！**
1. main基于V2.11修改，2.11可以直接复制main.js，2.11版以外的版本需要把main_edit.js里面的东西复制到main的290行左右  
  并且在开头添加  
  import weibo from './modules/plugin/weibo';
  import bilibili from './modules/plugin/bilibili'
  import dice from './modules/plugin/dice';  
  然后最末尾添加两行  
  weibo.checkWeibo(replyMsg);
  setTimeout(() => bilibili.checkBiliDynamic(replyMsg), 10000);
  
2. 需要安装MongoDB，没装的参考官方教程https://docs.mongodb.com/manual/installation/ ，端口是默认端口不要改，然后需要安装mongodb nodejs api，直接在机器人的目录npm install mongodb就行


## 部件列表  
正在缓慢更新中
TODO:  群内小游戏  

### 1. 看微博，B站动态  
用 “看看**谁谁上条**微博/B站”，谁谁是要看的人的名字，上条可以改，可以要求看置顶，上条，上上条，上上上条.....，也可以直接写第x条，x范围是0~9
也可以用 **看看微博/B站 url**，url为单条微博的网址，在微博app里，分享微博的时候选分享链接就好

### 2. 订阅微博，B博订阅
用 “订阅**谁谁**微博/B站”就好，取消订阅用“取消订阅**谁谁**微博/B站”，每5分钟检查一次  
用**查看订阅微博/B站**来检查目前群里订阅了哪些微博账号
  
### 3. 骰子  
可以扔出任意面数（<1000），任意个数(<10)的骰子，可以指定最小值，自动统计总分  
用法的话，参考  
.dice6  扔一个D6  
.dice8x5  扔5个D8  
.dice16,10  扔1个最低为10的D16  
.dice20x3,10  扔3个最低为10的D20  

### 4.简单直接宝可梦  
**注意！！！** 使用前必须先将下载dump然后用mongorestore存进mongoDB
  发送**旅行**来投骰子，  
  **旅行团在哪**确定当前骰子，  
  用**捕捉**来抓宝可梦，  
  用**对战 @群里的人**进行对战
     
## 以下内容因为版本更迭暂不支持  
### 2. 图片分类  
可以请求不同种类的P站图片，数据库为本地储存的MongoDB，setu_database里是我自己扒了10多个tag并手工删减了一些不太行的，可以用MongoDB恢复到数据库，不需要的话可以自己用pxer扒  

### 3. 看漫画  
实现了自动翻页，暂停自动翻页，跳页，手动翻页之类的功能  
可以和狗群员一起看漫画，没什么卵用，语句是 看看漫画  
需要指定本地漫画的地址（对你得把漫画下载到本地），从1.jpg开始

### 4. 获取少前新人/皮肤的大破图  
来源是少前台服官网，需要手动触发，语句为“康康新枪/皮肤”

### 6. 少前帮助  
问问题可以给出对应的NGA的网址链接  
（偷懒直接写main里面了）

### 7. 少前战区分数统计(能用，有bug，几率报错)  
也用了MongoDB...可以输入分数然后查看分数（写了一半！）
@机器人 然后用以下格式  
战区 游戏名称:xxxx；分数：xxxxxx；排行：xx  
（不用打百分号，注意用分号隔开每项内容）
