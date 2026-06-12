---
title: "Broadcom BCM4306 Problems"
date: 2005-07-19
forum: Networking &amp; Wireless
---

### Post by foo-bar on 2005-07-19
Hello,

I just switched my laptop to Ubunto two days ago, and have been trying to get my Broadcom BCM4306 wireless card running, but with no luck.  I have followed the instructions [here](http://ubuntuforums.org/showthread.php?t=25683) multiple times, and lately I have been getting this error (upon entering the command "sudo modprobe ndiswrapper"):

FATAL: Could not open '/lib/modules/2.6.10-5-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko': No such file or directory

If someone could help me, I would greatly appreciate it.

---

### Post by apollo2011 on 2005-07-19
[QUOTE=foo-bar]Hello,

I just switched my laptop to Ubunto two days ago, and have been trying to get my Broadcom BCM4306 wireless card running, but with no luck.  I have followed the instructions [here](http://ubuntuforums.org/showthread.php?t=25683) multiple times, and lately I have been getting this error (upon entering the command "sudo modprobe ndiswrapper"):

FATAL: Could not open '/lib/modules/2.6.10-5-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko': No such file or directory

If someone could help me, I would greatly appreciate it.[/QUOTE]
 I would try using the directions on the wiki page below:

[https://wiki.ubuntu.com/SetupNdiswrapperHowto?highlight=%28Ndiswrapper%29](https://wiki.ubuntu.com/SetupNdiswrapperHowto?highlight=%28Ndiswrapper%29)

---

### Post by foo-bar on 2005-07-19
Thanks a lot, that fixed it.

I wonder though, I tried to go through that wiki page before, but it didnt work..

Anyways, its working now, so thanks :)

---

