---
title: "Dell dimension 3000"
date: 2008-12-17
forum: New to Ubuntu
---

### Post by tuts69 on 2008-12-17
hi pipol i have some question about dell dimension 3000 i install ubuntu 8.10 to the system now the installation was sucessful but whemn the computer restart problem occured. here's the error said,
 gave up waiting for root device. common problem:
 -Boot args (car /proc/cmdline)
  -check root= (did the system wait long enough?)
  -check root= (did the system wait for right device?)
-Missing modules (cat /proc/modules; ls /dev) 
ALERT! /dev/disk/by-uuid/4711ff2a-e339-49cf-a8df-2a5b6bfbae4 does not exist. dropping to ashell!
 question # 2 is there a intergated graphics driver for dimension 3000? if any where i can get those? hope you can help ,me my problem thanks in advance and appreciate.

---

### Post by Catalyst2Death on 2008-12-17
It looks like grub didn't correctly configure itself during the installation.  Or it installed, and now the hard drive that it was installed to has been removed/disconnected.  Anyway I would try to reinstall grub:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
[http://ubuntuforums.org/showthread.php?t=24113](http://ubuntuforums.org/showthread.php?t=24113)

Or just go through the installation process again, but I would try to fix it first.

---

### Post by tuts69 on 2008-12-17
> **Catalyst2Death said:**
> It looks like grub didn't correctly configure itself during the installation.  Or it installed, and now the hard drive that it was installed to has been removed/disconnected.  Anyway I would try to reinstall grub:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
[http://ubuntuforums.org/showthread.php?t=24113](http://ubuntuforums.org/showthread.php?t=24113)

Or just go through the installation process again, but I would try to fix it first.

thanks buddy i try to fix it first then i let you know i appreciate.

---

