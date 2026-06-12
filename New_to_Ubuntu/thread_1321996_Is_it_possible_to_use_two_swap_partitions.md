---
title: "Is it possible to use two swap partitions?"
date: 2009-11-10
forum: New to Ubuntu
---

### Post by utfan2012 on 2009-11-10
I have two hard drives, I am wondering if it is possible use two separate swap partitions (on two different drives). And how i would do it. Thanks in Advanced.

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf0b1ebb0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19295   154987056   83  Linux
/dev/sda2           19296       19457     1301265    5  Extended
/dev/sda5           19296       19457     1301233+  82  Linux swap / Solaris

Disk /dev/sdb: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe2a3e2a3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         256     2056288+  82  Linux swap / Solaris
/dev/sdb2             257         523     2144677+   c  W95 FAT32 (LBA)
/dev/sdb3             524        4998    35945437+  83  Linux

---

### Post by alphaniner on 2009-11-10
Yes, you can use multiple swap partitions.  If you have an existing install, you will need to edit your /etc/fstab file if you want the second swap to be mounted automatically at boot.  See [How to fstab]("http://ubuntuforums.org/showthread.php?t=283131").

---

### Post by kansasnoob on 2009-11-10
Why would you want to?

I've had as many as 8 Linux OS's sharing the same swap.

---

### Post by ranch hand on 2009-11-10
I use two on my external because I format my drives to be just 1 extended partition and put a swap partition on as something that can be recognized by my box (I bricked a couple learning to partition and became nervous).

I can only boot from one of the 2 drives in that external so root is on one and home on the other.  The swap is used on both drives.

---

### Post by alphaniner on 2009-11-10
> **kansasnoob said:**
> Why would you want to?

There are potential performance gains.  Depending on his system it could be 
highly beneficial.

---

### Post by Paqman on 2009-11-10
> **kansasnoob said:**
> Why would you want to?

I've had as many as 8 Linux OS's sharing the same swap.

+1

Ideally, you wouldn't need to use swap at all. I tend to keep one as a backup, it does get used for things like running LiveCDs. But otherwise if you've got enough RAM you won't even dip into swap.

---

### Post by konqueror7 on 2009-11-10
i did also the mistake of making multiple swap partitions, and i just wasted space...i was having a tri-boot and 1 swap partition wasn't even used that much...

if there are specifics that it needs to be for your system, then make additional swap partitions and just add them to your fstab...

---

### Post by bodhi.zazen on 2009-11-10
Just wondering why you would want to use 2 swap partitions. You do understand swap is slow, much much slower then RAM.

How much RAM do you have and is your swap full ?

---

