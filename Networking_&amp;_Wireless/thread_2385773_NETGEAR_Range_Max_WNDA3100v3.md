---
title: "NETGEAR Range Max WNDA3100v3"
date: 2018-02-24
forum: Networking &amp; Wireless
---

### Post by minibush on 2018-02-24
I looked up an old thread that told me how to add this to Ubuntu, using 16.04 which I have.

[https://ubuntuforums.org/showthread.php?t=2321779](https://ubuntuforums.org/showthread.php?t=2321779)

I cannot get it to work, though, following all steps as shown. I'm getting an error while compiling the driver:

inlined from 'rt_ioctl_iwaplist' at /home/ganondorf/Netgear-a6210/os/linux/../../os/linux/sta_ioctl.c:549:2:
./include/linux/string.h:305:4 error: call to '__read_overflow2' declared with attribute error: detected read beyond size of object passed as 2nd parameter
__read_overflow2();

Any ideas what's going on with it? New to Ubuntu, so any help would be nice. :D

---

### Post by deppgirl on 2018-04-19
I have the same wifi dongle and after doing research sounds like it'll never work and best bet is to buy something new. :(

---

### Post by 1mastermason9 on 2018-11-28
I've been reading continusly and trying all these different ways of getting my darn, Netgear3100v3 USB WIFI APT working!
NDISWRAPPER - DID NOT WORK
[https://github.com/jurobystricky/Netgear-A6210](https://github.com/jurobystricky/Netgear-A6210) - DID NOT WORK
----

I can say I did get it to work on Gentoo a long time ago with the same Netgear3100v3 with ndiswrapper, never been able to do it again after that though. Anyways
Id like to share the SOLUTION I found just now for me....

FOR NetGear3100v3:
[https://github.com/kevinfessler/MediaTek-Drivers](https://github.com/kevinfessler/MediaTek-Drivers)
Im sharing it uploaded just incase that link dies.[CENTER]
**MediaTek-Driver**

[COLOR=#24292E][FONT=-apple-system]This driver is a kernel module for the Mediatek USB wireless devices
To Install...[/FONT][/COLOR]
[COLOR=#24292E][FONT=-apple-system]Simply copy the ".ko" file to /lib/modules/(kernel version)/kernel/drivers/net/wireless[/FONT][/COLOR]
[/CENTER]
BTW, Check your chipset code and go download the .KO files and install them // move them w/e
[https://wikidevi.com/wiki/Netgear_WNDA3100v3](https://wikidevi.com/wiki/Netgear_WNDA3100v3)
IE: 
     
[LIST]
[*][Working Linux driver]("https://github.com/jurobystricky/Netgear-A6210") (**mt7662u_sta**) [AU]("http://askubuntu.com/questions/740227/how-to-install-wifi")    <-------- NETGEAR3100v3
[/LIST]
--
Alright folks I dont have anything else to say about it other than that.... Good luck !
P.S. DONT FORGET TO REBOOT! ;) 
......ALSO BTW: [FONT=monospace][COLOR=#000000]$ uname -a[/COLOR]
Linux desktop 4.18.0-11-generic #12-Ubuntu SMP Tue Oct 23 19:22:37 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux
UBUNTU 18.10[/FONT]

---

