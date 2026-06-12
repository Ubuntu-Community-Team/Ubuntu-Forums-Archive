---
title: "FakeRAID - DMRAID not recognizing raid0 / anyone help with metadata header?"
date: 2009-04-27
forum: New to Ubuntu
---

### Post by moodah on 2009-04-27
Hi.

Been trying to get DMRAID working with my raid0.

ubuntu 8.10 intrepid.

I have two 500 gig drives in stripe with XP running on them for performance. XP was working fine. I threw a new 160 gig drive in my pc to run ubuntu since i couldnt get it to detect the raid.  I set the new hdd as the first recognised disk in bios so Ubuntu would install the mbr to the 160gig. However now when in the OS, since it cant detect the raid, it cant detect XP so im kinda screwed.. Been trying a few things though and followed the FakeRAID FAQ and ended up here: [https://help.ubuntu.com/community/FakeRaidDebug](https://help.ubuntu.com/community/FakeRaidDebug)

I have 4 partitions on the raid.  Here are some more details.

----------

terry@ubuntu-TEZ:~$ sudo fdisk -u -l /dev/sda

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x91979197

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   143364059    71681998+   7  HPFS/NTFS
/dev/sda2       143364060   552957299   204796620    7  HPFS/NTFS
/dev/sda3       552957300  1576956464   511999582+   7  HPFS/NTFS
/dev/sda4      1576956465  1781753084   102398310    7  HPFS/NTFS

---------------

terry@ubuntu-TEZ:~$ sudo fdisk -u -l /dev/sdb

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

--------------

terry@ubuntu-TEZ:~$ sudo fdisk -u -l /dev/sdc

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x124b124a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63   300431564   150215751   83  Linux
/dev/sdc2       300431565   312576704     6072570    5  Extended
/dev/sdc5       300431628   312576704     6072538+  82  Linux swap / Solaris

---------------

also.

terry@ubuntu-TEZ:~$ sudo dmraid -r
No RAID disks
terry@ubuntu-TEZ:~$ sudo dmraid -rD
No RAID disks

terry@ubuntu-TEZ:~$ sudo dd if=/dev/sda of=outputfile skip=976771168
2000+0 records in
2000+0 records out
1024000 bytes (1.0 MB) copied, 0.0968202 s, 10.6 MB/s


Im attaching the outputfile so anyone can take a sneakpeek to see if anyone can find out how to fix this for me. (Im sure this happens alot since the debug page says to ask the community for help!)

Thanks in advance!

---

### Post by moodah on 2009-04-27
bump :<

---

