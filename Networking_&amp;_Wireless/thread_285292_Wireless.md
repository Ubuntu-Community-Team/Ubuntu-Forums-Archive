---
title: "Wireless"
date: 2006-10-26
forum: Networking &amp; Wireless
---

### Post by dmsn on 2006-10-26
Hey i installed today new ubuntu and got wierd problems with my wlan card =/ I have laptop HP nx7400 with intel wlan card.
It worked by the older ubuntu version but no the new one =(
You know anything what i can do?


dmesg |grep Wireless
17179600.176000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.1.0mp
[17179601.408000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection

iwconfig
lo no wireless extensions.

eth0 no wireless extensions.

sit0 no wireless extensions.


iwlist scan
lo Interface doesn't support scanning.

eth0 Interface doesn't support scanning.

sit0 Interface doesn't support scanning



Thanks for your help.

---

### Post by Henry Rayker on 2006-10-26
I believe that some of the wireless cards that worked in Dapper no longer work in Edgy. There was a little talk on the forums about whether or not people thought the release should be postponed...you've probably fallen victim to that.

Either you can wait for an update that will fix it, try to find a way to fix it (tough, I know) or back off to Dapper and wait for it to fix.

---

### Post by janbockaert on 2006-10-26
this should help:

[http://www.digitalvampire.org/blog/articles/2006/09/29/ubuntu-edgy-eft-on-a-thinkpad-x60s-how-to-make-ipw3945-work](http://www.digitalvampire.org/blog/articles/2006/09/29/ubuntu-edgy-eft-on-a-thinkpad-x60s-how-to-make-ipw3945-work)

---

### Post by dmsn on 2006-10-27
Nice ;)
But where do i find the ipw3945d ?

dmsn@lappen:~$ locate ipw3945d
dmsn@lappen:~$


dmsn@lappen:~$ locate ipw3945
/lib/modules/2.6.17-10-generic/kernel/drivers/net/wireless/ipw3945
/lib/modules/2.6.17-10-generic/kernel/drivers/net/wireless/ipw3945/ipw3945.ko
/lib/firmware/2.6.17-10-generic/ipw3945.ucode
/usr/src/linux-headers-2.6.17-10-generic/include/config/ipw3945
/usr/src/linux-headers-2.6.17-10-generic/include/config/ipw3945/promiscuous.h
/usr/src/linux-headers-2.6.17-10-generic/include/config/ipw3945/module.h
/usr/src/linux-headers-2.6.17-10-generic/include/config/ipw3945/debug.h
/usr/src/linux-headers-2.6.17-10-generic/include/config/ipw3945/monitor.h
/usr/src/linux-headers-2.6.17-10/drivers/net/wireless/ipw3945
/usr/src/linux-headers-2.6.17-10/drivers/net/wireless/ipw3945/Makefile
/usr/src/linux-headers-2.6.17-10/drivers/net/wireless/ipw3945/Kconfig
dmsn@lappen:~$


Thanks

---

### Post by dmsn on 2006-10-27
downloaded it and runned it ;)

dmsn@lappen:~$ sudo /sbin/ipw3945d 
Password:
ipw3945d - regulatory daemon
Copyright (C) 2005-2006 Intel Corporation. All rights reserved.
version: 1.7.22
Intel PRO/Wireless 3945ABG Network Connection found at:
 /sys/bus/pci/drivers/ipw3945/0000:10:00.0
Daemon launched as pid 4834.  Exiting.


dmsn@lappen:~$ ifconfig eth1
eth1      Link encap:Ethernet  HWaddr 00:13:02:C3:EA:2C  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:28 errors:0 dropped:1 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:177 Memory:f4000000-f4000fff 

dmsn@lappen:~$ 



But now the wlan lamp doesnt light on my laptop and iwlist scan 
doesnt work either the network manager for eth1.

dmsn@lappen:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

sit0      Interface doesn't support scanning.

eth1      No scan results
dmsn@lappen:~$

---

### Post by sonny on 2006-11-03
I get this error:
```
sonny@Inspiron:~$ sudo /sbin/ipw3945d
Password:
ipw3945d - regulatory daemon
Copyright (C) 2005-2006 Intel Corporation. All rights reserved.
version: 1.7.22
2006-11-03 14:44:53: ERROR: Could not find Intel PRO/Wireless 3945ABG Network Connection
```
What can I do to fix it?, my wireless is suppossed to be on, it's on in my bios,  but the light doesn't  show.

---

