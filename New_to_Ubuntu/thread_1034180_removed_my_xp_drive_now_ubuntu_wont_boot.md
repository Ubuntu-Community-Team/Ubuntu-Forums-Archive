---
title: "removed my xp drive now ubuntu wont boot"
date: 2009-01-08
forum: New to Ubuntu
---

### Post by Yemmo2008 on 2009-01-08
I did have xp and ubuntu dual booting but I haven't used xp in sooooo long I decided to format it and remove the drive. Now when I try to boot into ubuntu I get this...

GRUB Loading stage1.5

GRUB Loading, Please wait...
Error2

I have put the drive that was previouly xp back in and it works fine. I've also tried editing the menu.lst file so that it doesn't have xp there any more.

---

### Post by melojo on 2009-01-08
You have removed the mbr on the windows drive that points to the operating system.  You just need to install grub on the the other drive.

Go here

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Make sure the drive is set to be the master and not a slave.

---

### Post by Yemmo2008 on 2009-01-08
Thanks heaps mate, that worked perfectly:D

---

