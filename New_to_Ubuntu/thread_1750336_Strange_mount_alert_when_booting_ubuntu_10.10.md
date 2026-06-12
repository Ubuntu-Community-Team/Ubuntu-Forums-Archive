---
title: "Strange mount alert when booting ubuntu 10.10"
date: 2011-05-05
forum: New to Ubuntu
---

### Post by anigodin on 2011-05-05
Hello all,

I'm sorry if I'm re-posting something that was already discussed. I couldn't find anything about this strange problem.

The story is this:
After many months of postponing the upgrade from 10.04 to 10.10 (the computer was begging for a partial upgrade), this week I finally upgraded.
For some strange reason it took me three day to upgrade, because the upgrade program kept asking for the 10.10 install disk for almost every file (out of 1470!. when it was finally done and restarted the computer the grub failed and I got the grub rescue screen.

I managed to fix it, I think, because the computer now boot with grub and into 10,10. but, here's the strange thing, while the system starts when still in the purple screen I get a message about a mount problem:

cant mount /dev/sda1 
prees S to skip or M to mount manually


At first, I pressed M, but the truth is I had no idea what to do after that. so I pressed S and the computer loaded normally.. all the internal drives are there and I can open them..

Trying to see which disk is /dev/sda1 I typed in terminal the following:

sudo fdisk -l

I get this:

Disk /dev/sda: 41.0 GB, 40982151168 bytes
255 heads, 63 sectors/track, 4982 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x99839983

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4982    40017883+   7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x156bd6bd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        3824    30716248+   7  HPFS/NTFS
/dev/sdb2            3825        5040     9764864   83  Linux
/dev/sdb3            5162       19456   114820609    f  W95 Ext'd (LBA)
/dev/sdb4            5040        5162      976896   82  Linux swap / Solaris
/dev/sdb5            7649       19456    94847728+   7  HPFS/NTFS
/dev/sdb6            5162        7648    19972096   83  Linux

Partition table entries are not in disk order


As I understand it, sda is a 41GB internal drive. it had no OS on it, just data and when I skipped the sda mount, I see it and I can reach it.

So, what is the meaning of this message and how do I solve this? it's really annoying to start the computer, go to the other room and come back to see it's still stuck with this message.



By the way, I know this message from my other computer which has mythbubtu 10.10 installed. I have an external drive connected to it and if I forget to disconnect it before I start the computer, the computer is stuck in bios forever.. I tried to define in the bios that it'll look for OS only on a certain drive but it's not working. this computer is old, about 8 year old, so it maybe a part of the problem.. 
If I disconnect the external drive and start the computer, it's looking for the drive and then i connect it, press enter and it's loading.
Any one knows how to solve this??

Many thanks!

---

### Post by andrewthomas on 2011-05-05
post the output of 

```
cat /etc/fstab
```

---

### Post by anigodin on 2011-05-06
Here it is:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	nodev,noexec,nosuid	0	0
#Entry for /dev/sdb2 :
UUID=83615ada-7a34-40db-8357-97b66b66d9a2	/	ext4	errors=remount-ro	0	1
#Entry for /dev/sdb6 :
UUID=ad7a9a66-ebde-43f4-8694-a45bdac89646	/home	ext4	defaults	02
/dev/sda1	/media/BigData	ntfs-3g	defaults,locale=he_IL.utf8	0	0
/dev/sdb5	/media/Data	ntfs-3g	defaults,locale=he_IL.utf8	0	0
/dev/sdb5	/media/Media	ntfs-3g	defaults,locale=he_IL.utf8	0	0
/dev/sdb1	/media/WinXP	ntfs-3g	defaults,locale=he_IL.utf8	0	0
/dev/sda1	/media/sda1	ntfs-3g	defaults,locale=he_IL.utf8	0	0
/dev/sdb1	/media/sdb1	ntfs-3g	defaults,locale=he_IL.utf8	0	0
#Entry for /dev/sdb4 :
UUID=98bf9cf8-671a-4124-b8e6-1bd65a5554cb	none	swap	sw	0	0


By the way, I had a mistake in the first post about the message. the message says something like: An error accrued while mounting /dev/sda1

---

