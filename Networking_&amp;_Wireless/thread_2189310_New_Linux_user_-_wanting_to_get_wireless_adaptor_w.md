---
title: "New Linux user - wanting to get wireless adaptor working"
date: 2013-11-21
forum: Networking &amp; Wireless
---

### Post by jdarby1983 on 2013-11-21
ok, so this week ive taken the step and got ubuntu 13.10 installed alongside windows 8.1. Love it so far but i'm making my first task to get my usb wireless adaptor working before moving on to anything else.

My main issue installing the ndiswrapper and those drivers that i have! Basic shell commands are known such as ls /cd / -i / 

The Netgear adaptor is there:
jdarby1983@jdarby1983-Alienware-X51:~$ lsusb
Bus 002 Device 003: ID 0846:9020 NetGear, Inc. WNA3100(v1) Wireless-N 300 [Broadcom BCM43231]
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 0461:4d65 Primax Electronics, Ltd 
Bus 001 Device 004: ID 04ca:0027 Lite-On Technology Corp. 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
jdarby1983@jdarby1983-Alienware-X51:~$ 

I've got the drivers:

jdarby1983@jdarby1983-Alienware-X51:~/wna3100-drivers$ ls
bcmh43xx64.cat  bcmh43xx.cat  bcmwlhigh5.inf  bcmwlhigh5.sys
jdarby1983@jdarby1983-Alienware-X51:~/wna3100-drivers$ 


I also have the ndiswrapper application downloaded
jdarby1983@jdarby1983-Alienware-X51:~/ndiswrapper-1.58$ ls
AUTHORS    driver   loadndisdriver.8  ndiswrapper.8     README
ChangeLog  INSTALL  Makefile          ndiswrapper.spec  utils
jdarby1983@jdarby1983-Alienware-X51:~/ndiswrapper-1.58$ 


I have already tried to follow the instructions on making an install that came with ndiswrapper, however I must be doing something wrong.

Any help would be greatly appreciated.

---

### Post by Hakunka-Matata on 2013-11-21
Hi jdarby1983,  Welcome to the forum.  Check [this]("http://ubuntuforums.org/showthread.php?t=1965989") post, it may help you out.

regards,

---

