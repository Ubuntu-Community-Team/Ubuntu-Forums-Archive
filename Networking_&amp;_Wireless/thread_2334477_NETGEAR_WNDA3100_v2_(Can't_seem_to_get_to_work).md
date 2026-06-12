---
title: "NETGEAR WNDA3100 v2 (Can't seem to get to work)"
date: 2016-08-19
forum: Networking &amp; Wireless
---

### Post by piqle504 on 2016-08-19
Hello I have a NETGEAR WNDA3100 v2 USB stick inserted into my desktop with a fresh install of ubuntu. After attempting to work it out myself I can't seem to get everything in working order. I downloaded the (what I think is driver files from [https://ubuntuforums.org/showthread.php?t=1964173](https://ubuntuforums.org/showthread.php?t=1964173). In his steps he said to get 'ndiswrapper' but I can't seem to get that to install. I do not have access to internet on my ubuntu desktop but I have a USB flash drive in hand and a mac with internet. If someone could help me get through this step-by-step I'd gratefully appreciate it. 
[B]
When running 'lsusb' on the system I get:

[/B]
ID 0846:9011 NetGear, Inc. WNDA3100v2 802.11abgn [Broadcom B CM4323]

---

### Post by piqle504 on 2016-08-19
Update: just found out I downloaded ndiswrapper 1.60, found 1.9 and trying now.
Update 2: that was just the utils I think.. brought up a .deb to install, clicked install and nothing. Could really use some help.

---

### Post by piqle504 on 2016-08-19
and we're online! I finally got the right version (1.59) of ndiswrapper, got it installed and followed the steps from the link above.

---

### Post by piqle504 on 2016-08-19
eh.. nevermind. Now i'm getting a loop asking for the password.

---

### Post by jeremy31 on 2016-08-19
It might be an encryption issue with the wifi router, check ```
iwlist scan | egrep -i 'ssid|cipher"
```

If the cipher under your access points name shows TKIP it may be part of the problem but I would suggest buying a wireless device that works with Ubuntu without ndiswrapper.  My TP-Link WN722N 150 MBps model has worked well for me unless TKIP or WEP encryption is used and with the external antenna it has good signal strength.

I had the WNA3100 (V1) and tried to get it to work in Ubuntu with ndiswrapper and even with ideal encryption settings the device performed badly.

If you have an empty PCI or PCI(e) slot, the Intel wifi cards work well in Ubuntu

---

### Post by piqle504 on 2016-10-12
it's been months and i'm on a fresh install of ubuntu 16.04.1
command doesn't give me anything back, just
> >
>
>
>
still getting authentication loop. can't figure it out.

---

