---
title: "duel booting ubuntu and Vista"
date: 2009-09-19
forum: New to Ubuntu
---

### Post by Ancient Dragon on 2009-09-19
Right now I have ubuntu taking up the entire hard drive.  Next week I want to install Vista as well. From what I've read I will also have to reinstall ubuntu because Vista will destroy that installation. Is there any way around that?  My computer also has a 1.5TB external hd that has very little on it.  If I copy all the files from the current ubuntu installation up to that hd, install both Vista and ubuntu, then can I just simply copy all the files back down to the ubuntu partition?

---

### Post by coldfusion1313 on 2009-09-19
If you make a partition for Vista and install Vista on that partition the only thing that will happen is GRUB will be over written be Vista's MBR, which is easily fixable. You just have to boot off the Live CD and reinstall GRUB, use this thread to help you->[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351). Before you do anything you should backup ALL your stuff on you external hard drive, just in case anything goes wrong.

---

