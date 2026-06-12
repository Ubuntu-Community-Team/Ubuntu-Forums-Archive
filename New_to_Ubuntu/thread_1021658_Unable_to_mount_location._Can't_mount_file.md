---
title: "Unable to mount location. Can't mount file"
date: 2008-12-25
forum: New to Ubuntu
---

### Post by Panos 123 on 2008-12-25
I have a HP pavilion laptop with 2 seperate hard drives. I recently changed from vista to ubuntu 8.10 and have come across this problem. My 2and hard drive which had all my documents used to work perfectly well. Suddenly it was registered in "computer" as a SCSI drive. When I try to open it I get the message "Unable to mount location. Can't mount file". Tried to reformat it to ext3 but no results. Gparted states that it is unallocated.

Please help

---

### Post by Michaelg14 on 2008-12-25
Do you have documents that you are trying to save or do you want to reformat to EXT3?

If you want to reformat you should be able to select the unallocated space in gparted and create a new partition.  right click on the space and select "New".

---

### Post by taurus on 2008-12-25
Open a terminal and post the outputs of these commands.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

### Post by Panos 123 on 2008-12-26
Thank you for instant reply.

First of all I want to recover my documents and afterwards reformat to EXT3. 

terminal output is:

panos@panos-laptop:~$ sudo fdisk -l
[sudo] password for panos: 

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6f90447d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13995   112414806   83  Linux
/dev/sda2           13996       14593     4803435    5  Extended
/dev/sda5           13996       14593     4803403+  82  Linux swap / Solaris

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x06effa8c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       38158   306504103+  83  Linux
/dev/sdc2           38159       38913     6064537+   5  Extended
/dev/sdc5           38159       38913     6064506   82  Linux swap / Solaris

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0b11e330

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1      121601   976760001    7  HPFS/NTFS
panos@panos-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=8b6732a8-0195-44d9-8694-7d6c63f0d15e /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=82d5a3f2-14a8-442a-88da-797b88b8cd84 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
panos@panos-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             106G  2.8G   98G   3% /
tmpfs                1012M     0 1012M   0% /lib/init/rw
varrun               1012M  108K 1012M   1% /var/run
varlock              1012M     0 1012M   0% /var/lock
udev                 1012M  2.9M 1009M   1% /dev
tmpfs                1012M  140K 1012M   1% /dev/shm
lrm                  1012M  2.0M 1010M   1% /lib/modules/2.6.27-9-generic/volatile
/dev/sdc1             288G  2.3G  271G   1% /media/disk
/dev/sdd1             932G  304G  629G  33% /media/FreeAgent Drive
panos@panos-laptop:~$ 

Thank you

---

