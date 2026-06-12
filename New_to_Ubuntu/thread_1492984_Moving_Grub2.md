---
title: "Moving Grub2"
date: 2010-05-25
forum: New to Ubuntu
---

### Post by Paul T. on 2010-05-25
I've had some problems with grub2 which although sorted now, usually re-appear when updating Ubuntu. I've just discovered that there's a folder on my Windows 'C' drive labelled "grub" which I assume shouldn't be there? How do I move grub onto the correct partition?


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11151    89570376    7  HPFS/NTFS
/dev/sda2           11152       30401   154625625    f  W95 Ext'd (LBA)
/dev/sda5           11152       30136   152496981   83  Linux
/dev/sda6           30137       30401     2128581   82  Linux swap / Solaris

---

### Post by mikewhatever on 2010-05-26
You should elaborate a bit on why and where you want grub moved. Also, how did grub folder end up in the Windows partition?

---

### Post by wilee-nilee on 2010-05-26
It will realy be best if you post this script in code tags, and give a little description of what is going on. It is unlikely that grub has to be moved just, removed from windows.[noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

