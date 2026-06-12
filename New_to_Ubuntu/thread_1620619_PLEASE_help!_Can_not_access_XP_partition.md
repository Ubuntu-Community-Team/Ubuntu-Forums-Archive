---
title: "PLEASE help! Can not access XP partition"
date: 2010-11-13
forum: New to Ubuntu
---

### Post by Txsfld on 2010-11-13
Can any of you experienced Linux users please help this novice? I would sincerely appreciate your help!!! PLEASE?

I've been researching this and trying different things to resolve this problem but am not having any luck. I am new to Ubuntu, and I LOVE IT, but I still need to be able to access my WINXP Partition. 

I have a 2.6Ghz machine, 1.5M of memory and 4 hard drives (3 hdd, 1 usb). I was running XP on the "then" Drive C, and I performed an install of Ubuntu 10.10 on that drive. I can run Ubuntu fine but I can no longer boot XP nor access the XP partition. The drive which that is located is /dev/sdc. When I try to go into Windows Recovery to run CHKDSK /F the system does not even see the drive where XP is and sets it up on another disk. The drive that Ubuntu and ZP is installed is a SATA drive.

Here is the output of "sudo fdisk -l";

Disk /dev/sda: 41.0 GB, 40982151168 bytes
165 heads, 63 sectors/track, 7700 cylinders
Units = cylinders of 10395 * 512 = 5322240 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x04f4cec0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7699    40015048+   7  HPFS/NTFS
/dev/sda2            7700        7700        5197+   c  W95 FAT32 (LBA)

Disk /dev/sdb: 61.5 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe64a4d43

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        7475    60042906    7  HPFS/NTFS

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe785e785

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        6340    50918065+   7  HPFS/NTFS
/dev/sdc2            6340        9730    27231233    5  Extended
/dev/sdc5            6340        6704     2929664   82  Linux swap / Solaris
/dev/sdc6            6704        9730    24300544   83  Linux

Disk /dev/sdd: 250.1 GB, 250059350016 bytes
1 heads, 63 sectors/track, 7752336 cylinders
Units = cylinders of 63 * 512 = 32256 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00d057b1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           2     7752256   244196032+   7  HPFS/NTFS

Here is the contents of FSTAB;
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    nodev,noexec,nosuid    0    0
#Entry for /dev/sdc6 :
UUID=bedb630a-c5a0-4a56-bd09-b864ac948dcf    /    ext4    errors=remount-ro    0    1
#Entry for /dev/sdd1 :
UUID=349C149B9C145A26    /media/Expansion\040Drive    ntfs-3g    defaults,nosuid,nodev,locale=en_US.utf8    0    0
#Entry for /dev/sda1 :
UUID=103CCAA53CCA8566    /media/Shared\040Disk\040Archive    ntfs-3g    defaults,nosuid,nodev,locale=en_US.utf8    0    0
#Entry for /dev/sdb1 :
UUID=A44435FC4435D1B2    /media/Storage    ntfs-3g    defaults,nosuid,nodev,locale=en_US.utf8    0    0
#Entry for /dev/sdc1 :
UUID=1A5CCC2A5CCBFE8F    /media/sdc1    ntfs-3g    defaults,locale=en_US.utf8    0    0
#Entry for /dev/sdc5 :
UUID=b86fe92a-1f9b-43ec-a9d2-457a4036b902    none    swap    sw    0    0

---

### Post by Daniel0108 on 2010-11-13
Hi!
Install gParted:
```
sudo apt-get install gparted
```
And start it.
Look if your partition is broken or something else.
Yours,
Daniel

---

### Post by Txsfld on 2010-11-13
I have installed Gparted but it does not run. It appears to start but does not bring up a screen?!!

---

### Post by Txsfld on 2010-11-13
Looks like there is a known bug with Gparted which prevents me from using it. I just looked at that partition using PartitionManager. This is the result when trying to mount that partition in PartitionManager;

p, li { white-space: pre-wrap; } [FONT= ]Command: mount -v /dev/sdc1 /media/sdc1[/FONT]
 [FONT= ]==========================================================================================[/FONT] [FONT= ]mount: you didn't specify a filesystem type for /dev/sdc1[/FONT] [FONT= ]       I will try type ntfs[/FONT] [FONT= ]$MFTMirr does not match $MFT (record 0).[/FONT] [FONT= ]Failed to mount '/dev/sdc1': Input/output error[/FONT] [FONT= ]NTFS is either inconsistent, or there is a hardware fault, or it's a[/FONT] [FONT= ]SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows[/FONT] [FONT= ]then reboot into Windows twice. The usage of the /f parameter is very[/FONT] [FONT= ]important! If the device is a SoftRAID/FakeRAID then first activate[/FONT] [FONT= ]it and mount a different device under the /dev/mapper/ directory, (e.g.[/FONT] [FONT= ]/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation[/FONT] [FONT= ]for more details.[/FONT]

---

### Post by Txsfld on 2010-11-14
I don't know exactly what step I performed that resolved this issue but I think it was the following;

1 - noticed the Sata drive was set as a raid device in the Phoenix BIOS. I then changed it to "native" mode. 

2 - Booted up UBCD4WIN from the CDROM Drive and was able to see Drive C (which contains the XP And Ubuntu 10.10) partitions. I ran CHKDSK on the drive and at some point, XP booted off of drive C. I then ran CHKDSK and fixed bootrecords and file structure. Performed that twice and ...

XP is now booting from the dual boot disk/as well as Ubuntu 10.10, AND, I can the XP partition from within Ubuntu.

I don't know exactly how the problem was resolved, but it is, and I'm happy.

:P

---

