---
title: "grub does not boot Windows after update to Ubuntu 10"
date: 2010-05-20
forum: New to Ubuntu
---

### Post by MartijnBangor on 2010-05-20
Hi,

I have just updated from Ubuntu 9 to 10. Before the update, I could select either windows XP 64 or ubuntu at the start up. Since the update: if I select windows, a black screen appears + beeping sounds. Any suggestions/ ideas? (the windows (64 bit) partition is still visible from Ubuntu, with all relevant window files)

Thanks,

Martijn

---

### Post by oldfred on 2010-05-20
when you updated, did you see the instructions on install grub to all drives? Drives are not partitions, drives are sda, sdb, Partitions are sda1, sda2, sdb1 etc.

The instructions have been confusing to just about everyone.

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

If that is not your problem post this:
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

Although not a software bug per se there is a bug. If this was your problem please sign up and add to the list of users with the problem.
Kansasnoob bug report:
[http://art.ubuntuforums.org/showthread.php?t=1475385](http://art.ubuntuforums.org/showthread.php?t=1475385)
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724)

---

### Post by MartijnBangor on 2010-05-20
Thank you! That solved my problem.

Cheers,

Martijn

---

