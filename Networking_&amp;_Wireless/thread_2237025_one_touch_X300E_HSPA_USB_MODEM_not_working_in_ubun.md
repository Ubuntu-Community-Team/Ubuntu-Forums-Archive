---
title: "one touch X300E HSPA USB MODEM not working in ubuntu 13.04"
date: 2014-07-30
forum: Networking &amp; Wireless
---

### Post by rchod on 2014-07-30
[SIZE=3][COLOR=#333333][FONT=UbuntuRegular]i put the modem in the usb port, the light is orange and not stable. when i do these commands i get this:
[/FONT][/COLOR][/SIZE]
```
$ lsusb
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 002: ID 0930:021d Toshiba Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 1bcf:0007 Sunplus Innovation Technology Inc. Optical Mouse
Bus 001 Device 005: ID 04ca:7012 Lite-On Technology Corp. 

$ usb-devices
....
T:  Bus=03 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  3 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1bbb ProdID=f000 Rev=00.00
S:  Manufacturer=USBModem
S:  Product=HSPA Data Card
S:  SerialNumber=1234567890ABCDEF
C:  #Ifs= 1 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=(none)
....
```

[SIZE=3][COLOR=#333333][FONT=UbuntuRegular]is it because Driver=(none) ? if that's the problem where can i get a driver for this modem.[/FONT][/COLOR][/SIZE]

---

### Post by praseodym on 2014-07-30
Did you install "usb-modeswitch"? Do you know this thread:

[http://ubuntuforums.org/showthread.php?t=1831649&highlight=umts+checklist](http://ubuntuforums.org/showthread.php?t=1831649&highlight=umts+checklist)

BTW: 13.04 is outdated, please install 14.04 instead!

---

