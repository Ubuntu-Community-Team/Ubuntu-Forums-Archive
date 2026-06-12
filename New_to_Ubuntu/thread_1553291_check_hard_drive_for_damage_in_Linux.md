---
title: "check hard drive for damage in Linux"
date: 2010-08-14
forum: New to Ubuntu
---

### Post by ub9876 on 2010-08-14
is there a terminal command to run a HD integrity test??
9.04

---

### Post by ubudog on 2010-08-14
Type:
```
man fsck
```
and use the options that are provided there to check it.

---

### Post by oldsoundguy on 2010-08-14
To REALLY check out the parameters of any drive .. get the drive utility from the manufacturer of the disk.  It is a boot disk and you can run and test.

or you can download burn and run Hirens .. loads of utilities including drive testing.  

Neither will change any thing on the drive.

---

### Post by ubudog on 2010-08-14
You can also use Palimpset (Disk Utility), but I don't know if it comes with 9.04.  You can probably install it though.

---

### Post by bodhi.zazen on 2010-08-14
Use smart montools

[http://www.cyberciti.biz/tips/linux-find-out-if-harddisk-failing.html](http://www.cyberciti.biz/tips/linux-find-out-if-harddisk-failing.html)

---

### Post by SteelCore on 2010-08-15
If by HD integrity you mean finding bad sectors then the badblocks command can help. Here's how you use it, you can replace /dev/sda with whatever device you want to check:
```
badblocks -sv /dev/sda
```
the s option is to show you progress by giving you the percentage and the v option is for verbose mode (to give better clarity). I hope that helps.

---

### Post by ubudog on 2010-08-15
> **bodhi.zazen said:**
> Use smart montools

[http://www.cyberciti.biz/tips/linux-find-out-if-harddisk-failing.html](http://www.cyberciti.biz/tips/linux-find-out-if-harddisk-failing.html)

I used to use this too.  Very useful tool.

---

### Post by bodhi.zazen on 2010-08-15
> **ubudog said:**
> Type:
```
man fsck
```
and use the options that are provided there to check it.

Although they tend to go together, fsck checks the file system.

---

### Post by metalf8801 on 2010-08-15
try GSmartControl its in the Ubuntu Software Center nice GUI program

---

