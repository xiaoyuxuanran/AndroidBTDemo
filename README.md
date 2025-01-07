# 这是一个基于Android的蓝牙手机APP

### 0.参考文档

- 主要代码参考AndroidStudio官方
  - 路径:Develop->Reference->Packages->android.bluetooth
  - https://developer.android.google.cn/reference/android/bluetooth/package-summary
- 部分优化的代码参考自通义灵码插件的建议
  - 通义灵码：https://lingma.aliyun.com/lingma

### 1.主要功能：

1. 根据已配对的蓝牙进行连接
2. 按下按键发送指令给硬件的蓝牙模块（HC-06）
3. 蓝牙模块发送数据信息后根据内容显示在相应位置

### 2.蓝牙协议指令

1. APP——>HC06
   - 电机：
     - 选中路数之后，相应的按钮变为黄色，如不点击，则默认为1路  
     - 按下正转之后  
     - 01 03 00 XX YY FF---------- 01 03 帧头 00表示电机 XX为电机号， 01-06 YY为正转反转00反转 01正
       转00反转  
   - 称重传感器  
     - 0103 01 XX FF FF---------------------01 03 帧头 01表示称重 XX表示传感器号码  
   - 溢满传感器  
     - 01 03 02 XX FF FF------------同上  
   - 红外传感器  
     - 01 03 03 XX FF FF  -----------同上  
   - 条形码
     - 01 03 04 01 FF FF  
   - 传送带电机  
     - 01 03 05 XX YY FF ----------------- XX数据 YY为00或01 00反转， 01正转  
2. HC06——>APP
   - "W010000.00" W:代表称重传感器 01代表路数 0000.00代表数值  
   - "Y010" Y:代表溢满传感器 01代表路数 0代表数值  
   - “R010” R：代表红外 01代表路数， 0代表状态  
   - “T”  条形码

### 3.运行效果图

![838fe947f43b907501583d225c71d1f](https://raw.githubusercontent.com/xiaoyuxuanran/images/main/838fe947f43b907501583d225c71d1f.jpg)

### 4.写在最后

- 有问题可以发邮件联系xiaoyuxuanran@163.com
- 本人主要以嵌入式开发为主，Android是练手的，如果代码上的蠢操作还请海涵，大佬放过