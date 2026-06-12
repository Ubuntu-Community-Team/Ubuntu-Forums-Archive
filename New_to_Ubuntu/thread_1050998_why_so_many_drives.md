---
title: "why so many drives?"
date: 2009-01-26
forum: New to Ubuntu
---

### Post by kapi on 2009-01-26
Ok, so I updated from ubuntu 8.04 to 8.10 but (its probably my fault) when the ne version loaded I was left with a 2.1GB, 9.4GB and a 20.0GB. 

The 20GB says it's unmountable. 
The 2.1GB has all the folders you get after installation but the home folder is empty. 
The 9.4GB holds data that was on the last version 

and I can see the file system folder in Nautilus which is referencing some location?

Sorry to be a pain but could someone please explain what is gone on

Thanks

---

### Post by taurus on 2009-01-26
Can you post the outputs of these commands from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

### Post by kapi on 2009-01-26
craig@craig-desktop:~$ sudo fdisk -l
[sudo] password for craig: 

Disk /dev/sda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6c3fa31e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2434    19551073+   7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x22d722d6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1138     9140953+  83  Linux
/dev/sdb2            1139        9729    69007207+   5  Extended
/dev/sdb5            9542        9729     1510078+  82  Linux swap / Solaris
/dev/sdb6            1139        1392     2040192   83  Linux
/dev/sdb7            9355        9541     1502046   82  Linux swap / Solaris
/dev/sdb8            1393        9166    62444623+  83  Linux
/dev/sdb9            9167        9354     1510078+  82  Linux swap / Solaris

Partition table entries are not in disk order
craig@craig-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb8
UUID=223b1acc-12a1-428d-a207-9bb4df076b96 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb9
UUID=dfe182d3-8596-4363-93e8-fc4026cb0b05 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
craig@craig-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb8              59G  4.7G   52G   9% /
tmpfs                 252M     0  252M   0% /lib/init/rw
varrun                252M  108K  252M   1% /var/run
varlock               252M     0  252M   0% /var/lock
udev                  252M  2.7M  249M   2% /dev
tmpfs                 252M  524K  251M   1% /dev/shm
lrm                   252M  2.0M  250M   1% /lib/modules/2.6.27-9-generic/volatile
/dev/sdb1             8.7G  8.2G   91M  99% /media/disk
/dev/sdb6             2.0G  945M  916M  51% /media/disk-1
craig@craig-desktop:~$ 
craig@craig-desktop:~$ 
craig@craig-desktop:~$

---

### Post by taurus on 2009-01-26
Did you install (or reinstall) Ubuntu (or another distro) three times?  That would explain why you have three ext3 partitions with three swap partitions.

---

