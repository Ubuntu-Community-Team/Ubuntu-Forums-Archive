---
title: "[SOLVED] How to undo USB Startup Disk? (It's Read-Only)"
date: 2008-12-28
forum: New to Ubuntu
---

### Post by JAYCEE1 on 2008-12-28
I made a USB startup disk using the Live CD of Ubuntu 8.10. (Under Admin>Create a USB Startup disk.) I made it on a 2GB Cruzer thumb drive that mounts at /media/disk. I now want to clear out this USB drive but the filesystem is read-only. 

How can I erase this read-only startup disk?

Thanks!


sudo fdisk -l
```


[sudo] password for user1: 

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00027d78

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9541    76638051   83  Linux
/dev/sda2            9542        9729     1510110    5  Extended
/dev/sda5            9542        9729     1510078+  82  Linux swap / Solaris

Disk /dev/sdb: 2000 MB, 2000682496 bytes
64 heads, 63 sectors/track, 969 cylinders
Units = cylinders of 4032 * 512 = 2064384 bytes
Disk identifier: 0x000a3264

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         969     1953439+   6  FAT16


```

sudo blkid

```


/dev/sda1: UUID="90c12719-683c-4cb9-b555-8a715bc42bdb" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="e3ff2d9e-34ee-4d26-a2e6-96dc7a758694" 
/dev/sdb1: SEC_TYPE="msdos" UUID="4C6B-0F85" TYPE="vfat" 

```

cat /etc/fstab

```


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=90c12719-683c-4cb9-b555-8a715bc42bdb /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=e3ff2d9e-34ee-4d26-a2e6-96dc7a758694 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
u

```


df -h
```


Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              73G  8.9G   60G  13% /
varrun                252M  112K  252M   1% /var/run
varlock               252M  4.0K  252M   1% /var/lock
udev                  252M   64K  252M   1% /dev
devshm                252M   12K  252M   1% /dev/shm
lrm                   252M   38M  215M  15% /lib/modules/2.6.24-16-generic/volatile
gvfs-fuse-daemon       73G  8.9G   60G  13% /home/user1/.gvfs
/dev/sdc1             1.9G  248M  1.7G  13% /media/disk
/dev/sdb1             1.9G 1017M  891M  54% /media/disk-1




```


id
```

uid=1000(user1) gid=1000(user1) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),107(fuse),109(lpadmin),115(admin),1000(user1)

```

---

### Post by Crooksey on 2008-12-28
Hey there try..

```

sudo su -
cfidsk /dev/sdb

```

Then use the cfdisk program to delete all partitions, then make a new partition out of all the free space, with the vfat or fat32 format.

---

### Post by cariboo on 2008-12-28
It is all one partition, so you can use nautilus as root, use gparted or practice using the rm command to clear the drive.

The easiest way is to make sure you have gparted installed, it is available in the repositories, then go to System-->Administration-->Partition Editor and just delete the partition and create a new one.

To use nautilus as root, press Alt-F2 and type:

```
gksu nautilus
```

Then navigate to /media/disk-1, and delete all the files.

To use the rm command, have a look at:

```
man rm
```

Jim

---

### Post by JAYCEE1 on 2008-12-28
> **cariboo907 said:**
> It is all one partition, so you can use nautilus as root, use gparted or practice using the rm command to clear the drive.

The easiest way is to make sure you have gparted installed, it is available in the repositories, then go to System-->Administration-->Partition Editor and just delete the partition and create a new one.

To use nautilus as root, press Alt-F2 and type:

```
gksu nautilus
```

Then navigate to /media/disk-1, and delete all the files.

To use the rm command, have a look at:

```
man rm
```

Jim


Thanks Cariboo!

I pressed Alt-F2 and typed gksu nautilus. Then I clicked on my USB drive and saw all of the files on the USB drive. I right-clicked each file and selected "Move to Trash." 

In order to get my memory back on the stick, I had to then click on the trash icon and click empty trash. After that, I had my memory back.

Thanks!

---

