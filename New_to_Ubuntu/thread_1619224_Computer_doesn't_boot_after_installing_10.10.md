---
title: "Computer doesn't boot after installing 10.10"
date: 2010-11-11
forum: New to Ubuntu
---

### Post by karolinger on 2010-11-11
I'm not sure... the problem might be because my boot drive is /dev/sda1 and I installed Ubuntu in my second drive? 
Grub doesn't show, it's just the cursor blinking after BIOS finishes loading.

/dev/sda1 is Windows XP

second hard disk drive:
/dev/sdb1 is Window 7
/dev/sdb2 is "/"
/dev/sdb3 is /home
and the last one is for swap

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 82.3 GB, 82348277760 bytes
224 heads, 19 sectors/track, 37790 cylinders
Units = cylinders of 4256 * 512 = 2179072 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00086787

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       37789    80414982+   7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80032038912 bytes
255 heads, 63 sectors/track, 9730 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00900090

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        5100    40960000    7  HPFS/NTFS
/dev/sdb2            5100        6405    10485760   83  Linux
/dev/sdb3            6405        9208    22515712   83  Linux
/dev/sdb4            9208        9730     4193280   82  Linux swap / Solaris
```Thanks for any help.

---

### Post by kroq-gar78 on 2010-11-11
is it possible that, while installing ubuntu, you installed GRUB (the bootloader) to an external drive (e.g. the ubuntu drive) and didn't set your bios to boot from it?

---

### Post by karolinger on 2010-11-12
I searched and found this [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

I tried to reinstall grub and I get this error:

```
/usr/sbin/grub-setup: warn: Your embedding area is unusually small.  core.img won't fit in it..
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
/usr/sbin/grub-setup: error: if you really want blocklists, use --force.
```I forced it, and still nothing

I have tried with the three possible ways explained in the previous link and still nothing. Except the second one didn't complete, because the --force modifier doesn't seem to work.

---

### Post by Rubi1200 on 2010-11-13
I recommend you click on the link at the bottom of my post and follow the instructions there.

Post the results of the boot info script back here so we can take a look and advise you on the next step.

Thanks.

---

### Post by karolinger on 2010-11-14
Too late... I reinstalled everything. 

Thanks anyway

---

