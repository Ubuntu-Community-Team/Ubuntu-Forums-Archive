---
title: "Using USB Modem 3G Problem D-Link DWM-156"
date: 2022-12-08
forum: Networking &amp; Wireless
---

### Post by soleyman on 2022-12-08
Hello All


I have just made a fresh installation of Ubuntu Server on Raspberry Pi


> 
Welcome to Ubuntu 22.04.1 LTS (GNU/Linux 5.15.0-1021-raspi aarch64)

  System information as of Wed Dec  7 20:03:46 UTC 2022

System load:  0.080078125        Processes:             144
  Usage of /:   27.8% of 13.91GB   Users logged in:       0
  Memory usage: 24%                IPv4 address for eth0: 192.168.1.11
  Swap usage:   0%                 IPv4 address for eth0: 10.10.10.11
  Temperature:  52.1 C

0 updates can be applied immediately.


I need to use subject modem for Internet mobile sim card with operator AP.

Any help would be appreciated !
Armen 


BTW: I can use command line only and tried with this command too:

> ubuntu@ubuntu:~$ usb-devices


T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 1
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=05.15
S:  Manufacturer=Linux 5.15.0-1021-raspi dwc2_hsotg
S:  Product=DWC OTG Controller
S:  SerialNumber=3f980000.usb
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   4 Ivl=256ms


T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 4
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=02 MxPS=64 #Cfgs=  1
P:  Vendor=0424 ProdID=2514 Rev=0b.b3
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=2mA
I:  If#= 0 Alt= 1 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=02 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   1 Ivl=256ms


T:  Bus=01 Lev=02 Prnt=02 Port=00 Cnt=01 Dev#=  3 Spd=480 MxCh= 3
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=02 MxPS=64 #Cfgs=  1
P:  Vendor=0424 ProdID=2514 Rev=0b.b3
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=2mA
I:  If#= 0 Alt= 1 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=02 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   1 Ivl=256ms


T:  Bus=01 Lev=03 Prnt=03 Port=00 Cnt=01 Dev#=  4 Spd=480 MxCh= 0
D:  Ver= 2.10 Cls=ff(vend.) Sub=00 Prot=ff MxPS=64 #Cfgs=  1
P:  Vendor=0424 ProdID=7800 Rev=03.00
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=2mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=00 Prot=ff Driver=lan78xx
E:  Ad=02(O) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=81(I) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=83(I) Atr=03(Int.) MxPS=  16 Ivl=1ms
ubuntu@ubuntu:~$ usb-devices


T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 1
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=05.15
S:  Manufacturer=Linux 5.15.0-1021-raspi dwc2_hsotg
S:  Product=DWC OTG Controller
S:  SerialNumber=3f980000.usb
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   4 Ivl=256ms


T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 4
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=02 MxPS=64 #Cfgs=  1
P:  Vendor=0424 ProdID=2514 Rev=0b.b3
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=2mA
I:  If#= 0 Alt= 1 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=02 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   1 Ivl=256ms


T:  Bus=01 Lev=02 Prnt=02 Port=00 Cnt=01 Dev#=  3 Spd=480 MxCh= 3
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=02 MxPS=64 #Cfgs=  1
P:  Vendor=0424 ProdID=2514 Rev=0b.b3
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=2mA
I:  If#= 0 Alt= 1 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=02 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   1 Ivl=256ms


T:  Bus=01 Lev=03 Prnt=03 Port=00 Cnt=01 Dev#=  4 Spd=480 MxCh= 0
D:  Ver= 2.10 Cls=ff(vend.) Sub=00 Prot=ff MxPS=64 #Cfgs=  1
P:  Vendor=0424 ProdID=7800 Rev=03.00
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=2mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=00 Prot=ff Driver=lan78xx
E:  Ad=02(O) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=81(I) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=83(I) Atr=03(Int.) MxPS=  16 Ivl=1ms




> ubuntu@ubuntu:~$ sudo ls /dev/serial/by-id
usb-D-Link_Inc_D-Link_DWM-156-if02-port0
usb-D-Link_Inc_D-Link_DWM-156-if03-port0
usb-D-Link_Inc_D-Link_DWM-156-if04-port0
usb-D-Link_Inc_D-Link_DWM-156-if05-port0


ubuntu@ubuntu:~$ sudo ls /dev/serial/by-path
platform-3f980000.usb-usb-0:1.1.2:1.2-port0
platform-3f980000.usb-usb-0:1.1.2:1.3-port0
platform-3f980000.usb-usb-0:1.1.2:1.4-port0
platform-3f980000.usb-usb-0:1.1.2:1.5-port0





[I try this commands too]("https://discourse.ubuntu.com/t/configure-cellular-connections/19928") 

but this is result :
> 
ubuntu@ubuntu:~$ sudo modem-manager.mmcli -L
error: couldn't get bus: Could not connect: Permission denied




and this too
> 
ubuntu@ubuntu:~$ sudo modem-manager.mmcli -m 0
error: couldn't get bus: Could not connect: Permission denied


---

