---
title: "Can not mount ext2 drive"
date: 2009-03-02
forum: New to Ubuntu
---

### Post by LostMagix on 2009-03-02
I am getting an error saying that my system does support ext2 file systems...

---

### Post by taurus on 2009-03-02
Did you mount it from a terminal or click on the partition?

```
sudo fdisk -l
cat /etc/fstab
df -h
uname -a
```

---

### Post by LostMagix on 2009-03-02
```
:~$ sudo fdisk -l

Disk /dev/sda: 20.0 GB, 20003880960 bytes
255 heads, 63 sectors/track, 2432 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00082154

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2432    19535008+   b  W95 FAT32

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x43434343

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       20546   165035713+   7  HPFS/NTFS
/dev/sdb2   *       20547       30025    76140067+  83  Linux
/dev/sdb3           30026       30401     3020220    5  Extended
/dev/sdb5           30026       30401     3020188+  82  Linux swap / Solaris


VV this one VV

Disk /dev/sdc: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x80808080

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        4865    39078081   83  Linux
/dev/sdc4   *           1           1           0    0  Empty
Partition 4 does not end on cylinder boundary.
Note: sector size is 4096 (not 512)

Disk /dev/sdd: 7971 MB, 7971016704 bytes
35 heads, 41 sectors/track, 1356 cylinders
Units = cylinders of 1435 * 4096 = 5877760 bytes
Disk identifier: 0x20202020

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1        1357     7783940    b  W95 FAT32

```


```
:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=a79ab3f1-c535-432b-967c-ac43590f703a /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=9eb05ab3-1293-45d6-9752-a6d1580e8bf0 none            swap    sw              0       0

```


```
:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb2              72G   64G  4.8G  93% /
tmpfs                 505M     0  505M   0% /lib/init/rw
varrun                505M  260K  504M   1% /var/run
varlock               505M     0  505M   0% /var/lock
udev                  505M  2.8M  502M   1% /dev
tmpfs                 505M  312K  504M   1% /dev/shm
lrm                   505M  2.0M  503M   1% /lib/modules/2.6.27-12-generic/volatile
/dev/sda1              19G  5.0G   14G  27% /media/disk
/dev/sdd1             7.5G  4.4G  3.1G  59% /media/IPOD
/dev/sdb1             158G   21G  138G  13% /media/disk-1

```

```
:~$ uname -a
Linux lost-desktop 2.6.27-12-generic #1 SMP Thu Feb 5 09:26:35 UTC 2009 i686 GNU/Linux

```

Everything is kinda jumbled right now, I have been doing some spring cleaning.

---

### Post by taurus on 2009-03-02
Are you trying to mount the /dev/sdc1?

```
sudo mkdir /media/sdc1
sudo mount -t ext2 /dev/sdc1 /media/sdc1
df -h
```

---

### Post by LostMagix on 2009-03-02
Yes /sdc is the drive im having problems with

```

:~$ sudo mkdir /media/sdc1

:~$ sudo mount -t ext2 /dev/sdc1 /media/sdc1

mount: unknown filesystem type 'ext2'

```


It was working fun just a few days ago :/

---

### Post by taurus on 2009-03-02
```
sudo blkid
```
Is there anything on /dev/sdc1?

---

### Post by LostMagix on 2009-03-02
Yes, the data is irreplaceable

 

```
:~$ sudo blkid
/dev/sda1: UUID="495F-D238" TYPE="vfat" 
/dev/sdb1: UUID="2C60FEF76DFEEAE3" TYPE="ntfs" 
/dev/loop1: UUID="a9542f58-e823-47d8-beba-25f0ad7685d8" TYPE="ext3" 
/dev/ramzswap0: TYPE="swap" 
/dev/sdc1: UUID="f76a8c9a-ea21-4e44-9020-642ca2a553e2" TYPE="ext2" 
/dev/sdd1: LABEL="IPOD" UUID="3141-5926" TYPE="vfat" 
/dev/sdb2: UUID="a79ab3f1-c535-432b-967c-ac43590f703a" TYPE="ext3" 
/dev/sdb5: TYPE="swap" UUID="9eb05ab3-1293-45d6-9752-a6d1580e8bf0" 

```

---

### Post by LostMagix on 2009-03-02
I rebooted twice and it seems to be working now..

dont know :/

---

### Post by The Cog on 2009-03-02
Make a backup. Now.

---

