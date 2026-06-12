---
title: "fdisk seems to not finish"
date: 2009-12-29
forum: New to Ubuntu
---

### Post by steveM49 on 2009-12-29
I want to repartition a hard drive, format and mount it.  I started with fdisk (sudo fdisk /dev/sdd).  It seemed to work but after I wrote the new partition fdisk stopped and returned me to the terminal prompt.  When I tried to format (sudo mke2fs -j /dev/sdd1), I was told that the file seemed to be in use.  I ran fdisk again, saw my partitions and quit. The file was still in use. I rebooted. /dev/sdd1 did not exist. Both mke2fs and ls failed to see the new partitions.  When I reran fdisk, I could see them via print; but again the file /dev/sdd1 was in use.  Again I rebooted and again /dev/sddx was missing.

Can anyone suggest another route for me to take?

Steve

---

### Post by thane1 on 2009-12-29
I think some of your problem might possibly be, that the drive is already mounted and therefor cannot be partitioned as desired until it has been unmounted.

---

### Post by falconindy on 2009-12-29
Try a different program such as cfdisk or another method entirely such as [SysRescueCD](http://www.sysresccd.org/Main_Page).

There's also a small chance that the drive is fubar.

---

