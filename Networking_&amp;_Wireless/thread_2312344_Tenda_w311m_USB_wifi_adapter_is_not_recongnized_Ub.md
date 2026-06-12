---
title: "Tenda w311m USB wifi adapter is not recongnized Ubuntu 14.04"
date: 2016-02-03
forum: Networking &amp; Wireless
---

### Post by stefani2 on 2016-02-03
[COLOR=#111111][FONT=Ubuntu]Hello guys I have a problem with my wifi usb adapter. I am a newby for Linux and this lap top doesn't have a wifi card. I bought tenda w311m USB wifi adapter but it's not recognized. I ask the guys at the store and told me it should be recognized straight away...

[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]The output from {lsusb} in the terminal is[/FONT][/COLOR]
Bus 001 Device 005: ID 148f:7601 Ralink Technology, Corp.
[COLOR=#111111][FONT=Ubuntu]Any solutions or ideas would be great. Thank you in advanced. :)

[/FONT][/COLOR]
T: Bus=01 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#= 2 Spd=480 MxCh= 0
D: Ver= 2.01 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs= 1 
P: Vendor=148f ProdID=7601 Rev=00.00 
S: Manufacturer=MediaTek S: Product=802.11 n WLAN 
S: SerialNumber=1.0 C: #Ifs= 1 Cfg#= 1 Atr=80 MxPwr=160mA I: If#= 0 Alt= 0 #EPs= 8 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)

Linuc stefi 4.2.0-27-generic #32~14.04.1-Ubuntu SMP Fri Jan 22 15:32:27 UTC 2016 i686 i686 i686 GNU/Linux

---

### Post by howefield on 2016-02-03
Thread moved to the "*Networking & Wireless*" forum.

---

### Post by Geoffrey_Arndt on 2016-02-03
__See this thread:  [http://askubuntu.com/questions/568747/impossible-to-install-ralink-rt5370-driver-on-xubuntu-14-10](http://askubuntu.com/questions/568747/impossible-to-install-ralink-rt5370-driver-on-xubuntu-14-10)

Check the input from Chili555 (especially his modprobe).

..............................................................................................................

If the thread above doesn't help, you can always get (for about $10 USD) a nano style
dongle from Panda Wireless (check Amazon, NewEgg, etc.)

The Panda devices are very linux friendly re "plug & play" . . no compiling needed.

[http://www.pandawireless.com/](http://www.pandawireless.com/)

---

