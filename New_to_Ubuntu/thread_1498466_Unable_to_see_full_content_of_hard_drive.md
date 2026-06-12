---
title: "Unable to see full content of hard drive"
date: 2010-05-31
forum: New to Ubuntu
---

### Post by Jelle1880 on 2010-05-31
Hi :)

I recently downloaded Ubuntu 10.04 and am figuring it out at the moment.
Everything seems to be working fine, apart from the fact that I can not see the full content of my hard drive.
I have a laptop with a hard drive that is partitioned into two parts, one where I have my programs on (C:) and one which I use for music, movies, video clips,... (D: )

Now, I installed the NTFS Configuration Tool to automatically mount the drive, that works.
But when I open it don't see any of the data that should be on there.
All I see, if I access it through Computer or through the icons on the desktop, tons of maps related to Ubuntu or Windows.

Now, when I installed Ubuntu I installed it on the D-drive (C-drive is the one with my Windows install). I did this because this was the one with the most free space on it.
If I use NTFS Configuration Tool I get the following options:

/dev/sda1 which is called PQSERVICE (39.0GB)
/dev/sda2 which is called A23E9AD93E9AA637 (129.8GB)
/dev/sda3 which is called host (126.3GB)
/dev/sda4 which is called sda4 (3.0GB)
They are all ticked and both 'Enable write support for external device' and 'Enable write support for internal device' are ticked too.

Might there be anyone who knows what the issue is ? :)

---

### Post by Kirkland14 on 2010-05-31
I just installed Linux as well and have the same question.  I have been searching around but can't find anything to tell me how much disk space I have left

---

### Post by dFlyer on 2010-05-31
Open a terminal and enter: free -tom (will tell you how much memory and swap used. To see how much disk space used enter df -H for the drives and du -h for directories.

---

### Post by nhasian on 2010-05-31
all of your partitions should be readable in ubuntu.  you just need to make sure to mount the partition you want to access.  lets see what your hard disk looks like with this terminal command:

```
sudo fdisk -l
```

we'll also need the output of:

```
sudo blkid
```

now lets take a look at your fstab:

```
cat /etc/fstab
```

paste back all the output here and please use the quote and code tags to format it to make your output easy to read :wink:

---

### Post by Jelle1880 on 2010-06-01
```
sudo fdisk -l
```

```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x839777f1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        5091    40893426   12  Compaq diagnostics
/dev/sda2   *        5092       22035   136098816    7  HPFS/NTFS
/dev/sda3           22035       38522   132428800    7  HPFS/NTFS
/dev/sda4           38522       38914     3147776   17  Hidden HPFS/NTFS

```

```
sudo blkid
```

```
/dev/loop0: UUID="33e7f84b-604e-43c8-9772-38fecf264187" TYPE="ext4" 
/dev/sda1: LABEL="PQSERVICE" UUID="32600439E49BED2A" TYPE="ntfs" 
/dev/sda2: UUID="A23E9AD93E9AA637" TYPE="ntfs" 
/dev/sda3: LABEL="DATA" UUID="58588A61588A3E2E" TYPE="ntfs" 
/dev/sda4: UUID="F4E4009EE40064E8" TYPE="ntfs" 

```

```
cat /etc/fstab
```

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	nodev,noexec,nosuid	0	0
/dev/sda3	/host	ntfs-3g	defaults,nosuid,nodev,locale=en_US.utf8	0	0
/dev/sda2	/media/A23E9AD93E9AA637	ntfs-3g	defaults,nosuid,nodev,locale=en_US.utf8	0	0
/dev/sda1	/media/PQSERVICE	ntfs-3g	defaults,locale=en_US.utf8	00
/dev/sda4	/media/sda4	ntfs-3g	defaults,locale=en_US.utf8	0	0
/host/ubuntu/disks/root.disk	/	ext4	loop,errors=remount-ro	0	1
/host/ubuntu/disks/swap.disk	none	swap	loop,sw	0	0

```

Like this ? :)

---

