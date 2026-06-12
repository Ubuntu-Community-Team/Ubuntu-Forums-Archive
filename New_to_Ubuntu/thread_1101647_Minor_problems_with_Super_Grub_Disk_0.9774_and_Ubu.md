---
title: "Minor problems with Super Grub Disk 0.9774 and Ubuntu 8.10, 9.04"
date: 2009-03-20
forum: New to Ubuntu
---

### Post by adrian15 on 2009-03-20
Hi Ubuntu forums,

As long as the Ubuntu community is the one that most uses [Super Grub Disk](http://www.supergrubdisk.org) I just wanted to share with you the latest [SGD piece of news](http://www.supergrubdisk.org/forum/index.php?topic=270.0) so that you can give a more accurate advice in new Ubuntu distributions versions.

I will, of course, try to fix the bug but it is not a high priority right now.

adrian15

SGD 0.9774 is the most updated SGD version right now.

SGD 0.9774 gives an error 13 when trying to boot kernels from ubuntu 8.10 or ubuntu 9.04 (and maybe other distributions but I am not aware of any more distributions).

I just want to tell you than when you run:

```

 GRUB => MBR & !LINUX! (1) AUTO  ;-))) 

```

and you get an error 13 that does not mean that the fix of boot has failed! If boot has not been recovered then try the live swap options: 

[http://www.supergrubdisk.org/wiki/GrubHardDiskOrder#How_to_Tweak_Hard_Disk_Boot_Order_in_Super_Grub_Disk](http://www.supergrubdisk.org/wiki/GrubHardDiskOrder#How_to_Tweak_Hard_Disk_Boot_Order_in_Super_Grub_Disk)

---

