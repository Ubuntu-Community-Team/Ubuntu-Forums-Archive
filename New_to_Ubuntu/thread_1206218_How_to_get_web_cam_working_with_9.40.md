---
title: "How to get web cam working with 9.40"
date: 2009-07-06
forum: New to Ubuntu
---

### Post by gordon33 on 2009-07-06
Hello All 

How do I get the HP labtop's **web cam** to work.  I don't know where to start.   Other threads asked for results for the following.

Gordon33


gordon@gordon-laptop:~$ lsusb
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 046d:c51b Logitech, Inc. 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 04f2:b091 Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
gordon@gordon-laptop:~$ dmesg | tail
[   52.395957]  domain 0: span 0-1 level MC
[   52.395959]   groups: 0 1
[   52.395964] CPU1 attaching sched-domain:
[   52.395966]  domain 0: span 0-1 level MC
[   52.395968]   groups: 1 0
[   55.224824] wlan0: authenticate with AP 00:24:b2:05:d5:80

---

### Post by esalnoj on 2009-07-06
Not even Cheese webcam Booth (add/remove applications->search "cheese") will detect it?

Using cheese with my 9.04 worked.

---

### Post by anystupidname on 2009-07-06
Well, this is your cam:
Bus 001 Device 003: ID 04f2:b091 Chicony Electronics Co., Ltd
I couldn't find conclusively that your cam is supported with a quick search, but generally, if there is a module/driver that supports it in the default ubuntu kernel, the cam should be assigened to /dev/video0 or /dev/video1 (depending on how many v4l type devices you have) If such a device is present, you can just install "cheese" and see if it works. Otherwise, you'll have to hunt for a driver and possibly compile it.

---

### Post by gordon33 on 2009-07-07
Hello

Chees did it.

gordon33

---

