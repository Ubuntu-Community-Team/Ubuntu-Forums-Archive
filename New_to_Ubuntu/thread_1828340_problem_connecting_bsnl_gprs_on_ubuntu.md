---
title: "problem connecting bsnl gprs on ubuntu"
date: 2011-08-18
forum: New to Ubuntu
---

### Post by jaj540 on 2011-08-18
hi there, i am using ubuntu 11.4.i hav a samsung gt-e2652 mobile and i want to connect to bsnl gprs. i took network connection-mobile broadband and added a new connection using bsnlnet as access point but i cannot get connection.i suddenly gets notification not connected. pls help me to connect bsnl gprs on ubuntu

---

### Post by raja.genupula on 2011-08-18
the problem is i dont know why but ubuntu not recognizing the modem of samsung mobile to make the connection . because i too have a samsung mobile C3053 , i had tried many times  to connect the internet from it, but it never . you can use any nokia mobile and nokia mobiles modem can be recognized in ubuntu .

---

### Post by im.saravanan on 2011-08-19
Please check and change the settings in the mobile before connecting the mobile to pc. and check the connection by using the command in the terminal.

$ lsusb

 for more info u can use the command 

$usb-devices 

 to check whether the modem is detected and the driver is loaded.

---

### Post by dineshs on 2011-08-20
+1 to im.saravanan.Pl post the results of```
lsusb
dmesg | grep tty
```to see if your phone is detected as modem.

---

### Post by jaj540 on 2011-08-20
this was the result of lsusb and dmesg | grep tty
I hav marked in red the name of samsung.. does it mean my samsung modem is detected????

abel@PandorasBox:~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
[COLOR=Red]Bus 005 Device 004: ID 04e8:6843 Samsung Electronics Co., Ltd [/COLOR]
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0bda:8197 Realtek Semiconductor Corp. RTL8187B Wireless Adapter
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 04f2:b070 Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
abel@PandorasBox:~$ dmesg | grep tty
[    0.000000] console [tty0] enabled
[  124.766845] cdc_acm 5-1:4.1: ttyACM0: USB ACM device
[  637.558309] cdc_acm 5-1:4.1: ttyACM0: USB ACM device
[  921.058072] cdc_acm 5-1:4.1: ttyACM0: USB ACM device
abel@PandorasBox:~$

---

### Post by jaj540 on 2011-08-20
this was the result about samsung in the code usb-devices

Bus=05 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  4 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=02(commc) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=04e8 ProdID=6843 Rev=04.00
S:  Manufacturer=Samsung Electronics Co., Ltd.
S:  Product=GT-TETHYS
S:  SerialNumber=0049990106400000
C:  #Ifs= 6 Cfg#= 4 Atr=c0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 0 Cls=02(commc) Sub=08 Prot=00 Driver=(none)
I:  If#= 1 Alt= 0 #EPs= 1 Cls=02(commc) Sub=02 Prot=01 Driver=cdc_acm
I:  If#= 2 Alt= 0 #EPs= 2 Cls=0a(data ) Sub=00 Prot=00 Driver=cdc_acm
I:  If#= 3 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
I:  If#= 4 Alt= 0 #EPs= 1 Cls=02(commc) Sub=02 Prot=ff Driver=(none)
I:  If#= 5 Alt= 0 #EPs= 2 Cls=0a(data ) Sub=00 Prot=00 Driver=(none)


does it mean whether it  is detected as a  odem or just a storage device...????

---

