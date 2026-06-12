---
title: "Reinstalling 9.04 and need help"
date: 2009-09-18
forum: New to Ubuntu
---

### Post by HolyShnikes on 2009-09-18
I have been all over these forums for the past few days trying to find a soulution to my problem. [http://ubuntuforums.org/showthread.php?t=1268268](http://ubuntuforums.org/showthread.php?t=1268268)  <- (Read post 5.)


  I have come to realize it is one of two possible reasons:


1. The graphic driver for my desktop needs to be downgraded (not likely)
2. Its because I have installed Ubuntu with Wubi and that seems to be only to test it out.

SO..... My real problem is this: I tried to install Ubuntu 9.04 a while back before I installed it with Wubi.  The reason I installed it with Wubi was because I could never get past the 50% mark at the "setting up disk" step.  I have 3 hard drives on my computer.  One is a external with 120gigs, and two 500 gig SATA drives (one of which is split in half to seperate all my media).

The external isnt a native external, its a HD with a case I got from Newegg to convert it to an external.  

Does anyone know what may be the problem?  When it gets to 50%, I can go no further.  It hasnt even started to install yet, it only gets to either "setting up disk" or "searching for partiton".  I don't remember off the top of my head.  Can someone help?

---

### Post by LewRockwell on 2009-09-18
Cheerios Mates!```
sudo fdisk -l
```Good Day Mates!

.

---

### Post by OffAxis on 2009-09-18
you can try running with the nvidia proprietary driver or with the open source driver and see if that has any effect.

---

### Post by HolyShnikes on 2009-09-18
Do you mean from the one from the nvidia website?

---

### Post by HolyShnikes on 2009-09-18
> **LewRockwell said:**
> Cheerios Mates!```
sudo fdisk -l
```Good Day Mates!

.

I'll do it when I get home.

---

### Post by HolyShnikes on 2009-09-18
```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x16058cf8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       34693   278668284    7  HPFS/NTFS
/dev/sda2           34693       60802   209715200    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x01076e5c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60801   488384001    7  HPFS/NTFS

Disk /dev/sdc: 120.0 GB, 120034123776 bytes
240 heads, 63 sectors/track, 15505 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0xeb37eb37

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       15506   117218304    7  HPFS/NTFS

```

---

### Post by BlueerSkies on 2009-09-18
Bismillaah.   Peace.   I personally, would defragment the hdd before installation.

---

