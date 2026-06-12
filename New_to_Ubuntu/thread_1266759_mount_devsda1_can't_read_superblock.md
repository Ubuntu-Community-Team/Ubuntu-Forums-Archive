---
title: "mount: /dev/sda1: can't read superblock"
date: 2009-09-15
forum: New to Ubuntu
---

### Post by lovelyboy on 2009-09-15
[SIZE=2]After i format C: in the DOS(from ntfs to fat32,XP was installed in C:/),and mount C partition in the linux(ubuntu 8.04 is installed in D:/) as below:
[/SIZE][SIZE=2]root@lewisping-laptop:/home/lewisping[/SIZE][SIZE=2]# mount -t vfat /dev/sda1 /media/sda1,
error comes out as below:
mount: /dev/sda1: can't read superblock

necessary info as belows:
root@lewisping-laptop:/home/lewisping# fdisk -l
Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf0b1ebb0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1275    10241406    c  W95 FAT32 (LBA)
/dev/sda2            1276        6717    43712865    f  W95 Ext'd (LBA)
/dev/sda3            6718        7296     4650817+   7  HPFS/NTFS
/dev/sda5            1276        3532    18129321    7  HPFS/NTFS
/dev/sda6            3533        4797    10161081    7  HPFS/NTFS
/dev/sda7            4798        6655    14924353+  83  Linux
/dev/sda8            6656        6717      497983+  82  Linux swap / Solaris

root@lewisping-laptop:/home/lewisping# ls -l /media
total 132
lrwxrwxrwx 1 root root        6 2008-04-07 06:43 cdrom -> cdrom0
drwxr-xr-x 2 root root     4096 2008-04-07 06:43 cdrom0
-rw-r--r-- 1 root root      512 2009-09-13 21:21 linux.lnx
drwxr-xr-x 2 root root     4096 2009-09-14 14:46 sda1
drwxrwx--- 1 root plugdev 45056 2009-09-03 17:35 sda3
drwxrwx--- 1 root plugdev 45056 2009-09-14 16:08 sda5
drwxrwx--- 1 root plugdev 28672 2009-09-14 16:44 sda6
drwxr-xr-x 2 root root     4096 2009-09-14 11:07 sda7

root@lewisping-laptop:/home/lewisping# ls -all /dev/disk/by-uuid
total 0
drwxr-xr-x 2 root root 160 2009-09-15 19:52 .
drwxr-xr-x 6 root root 120 2009-09-15 19:52 ..
lrwxrwxrwx 1 root root  10 2009-09-15 19:52 0E3C-12F5 -> ../../sda1
lrwxrwxrwx 1 root root  10 2009-09-15 19:52 3C7C45727C4527CA -> ../../sda5
lrwxrwxrwx 1 root root  10 2009-09-15 19:52 4602c8e6-5946-4e4a-a4be-9862430d9de9 -> ../../sda8
lrwxrwxrwx 1 root root  10 2009-09-15 19:52 485477BD5477ABF6 -> ../../sda6
lrwxrwxrwx 1 root root  10 2009-09-15 19:52 4ead4b57-547e-44ab-8fed-be883e2bef8b -> ../../sda7
lrwxrwxrwx 1 root root  10 2009-09-15 19:52 6E03414E6351D5FE -> ../../sda3
lewisping@lewisping-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=4ead4b57-547e-44ab-8fed-be883e2bef8b /               ext3    defaults,errors=remount-ro 0      0 
# /dev/sda3
UUID=6E03414E6351D5FE /media/sda3     ntfs    defaults,umask=007,gid=46 0       0 
# /dev/sda5
UUID=3C7C45727C4527CA /media/sda5     ntfs    defaults,umask=007,gid=46 0       0 
# /dev/sda6
UUID=485477BD5477ABF6 /media/sda6     ntfs    defaults,umask=007,gid=46 0       0 
# /dev/sda8
UUID=4602c8e6-5946-4e4a-a4be-9862430d9de9 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

#/dev/sda1
UUID=0E3C-12F5 /media/sda1  vfat,user,auto,umask=002,umask=007,gid=46,utf8 0 0



[/SIZE]

---

### Post by talsemgeest on 2009-09-15
Try running chkdsk on the partition from windows.

---

### Post by lovelyboy on 2009-11-10
> **talsemgeest said:**
> Try running chkdsk on the partition from windows.
Thanks! i have solved the problem after i format it again to ntfs .

---

### Post by talsemgeest on 2009-11-10
> **lovelyboy said:**
> Thanks! i have solved the problem after i format it again to ntfs .
Glad to hear it :)

---

