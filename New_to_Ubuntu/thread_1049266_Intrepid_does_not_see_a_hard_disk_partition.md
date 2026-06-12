---
title: "Intrepid does not see a hard disk partition"
date: 2009-01-24
forum: New to Ubuntu
---

### Post by Friccy on 2009-01-24
Hi!
I have a problem with the Intrepid, hope that someone can help.
Sometimes (most of the times) I can not access the partitions because it say:
UNABLE TO MOUNT LOCATION 
Internal error: No mount object for mounted volume

After OK If I am clicking again, it can be opened.
If I forget to open the partitions before using any media player or want to attach a file from these partitions, can not be done. It looks like no hard is available.
Why is that? What can I do to access it from the beginning? It has not been in the older versions of UBUNTU.

---

### Post by taurus on 2009-01-24
Did you have that partition/drive (80GB) mounted when you boot into Ubuntu?  Open a terminal and post the outputs of these commands.

```
sudo fdisk -l
sudo blkid
cat /etc/fstab
df -h
```

---

### Post by Friccy on 2009-01-24
Here are the outpost:

friccy@friccy-laptop:~$ sudo fdisk -l
[sudo] password for friccy: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7e80241d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9716    78041604    7  HPFS/NTFS
/dev/sda2            9716       17097    59288576   83  Linux
/dev/sda3           17098       18512    11365987+   f  W95 Ext'd (LBA)
/dev/sda4           18513       19457     7590712+   7  HPFS/NTFS
/dev/sda5           17238       18512    10238976    7  HPFS/NTFS
/dev/sda6           17098       17237     1124487   82  Linux swap / Solaris

Partition table entries are not in disk order

/dev/sda1: UUID="782C3F106CA2F381" TYPE="ntfs" 
/dev/sda2: UUID="a2601735-26bd-4058-83d6-23beafed7487" TYPE="ext2" 
/dev/sda4: UUID="2C88743C8874071C" LABEL="HP_RECOVERY" TYPE="ntfs" 
/dev/sda5: UUID="664857304856FDED" LABEL="Iratok, Kepek, Zene" TYPE="ntfs" 
/dev/sda6: TYPE="swap" UUID="f25704c0-cf16-4bd1-926b-667b52c4d04b"

friccy@friccy-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=a2601735-26bd-4058-83d6-23beafed7487 /               ext2    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=f25704c0-cf16-4bd1-926b-667b52c4d04b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

friccy@friccy-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2              56G  5.5G   48G  11% /
tmpfs                1012M     0 1012M   0% /lib/init/rw
varrun               1012M  228K 1012M   1% /var/run
varlock              1012M     0 1012M   0% /var/lock
udev                 1012M  2.8M 1010M   1% /dev
tmpfs                1012M  612K 1012M   1% /dev/shm
lrm                  1012M  2.0M 1010M   1% /lib/modules/2.6.27-11-generic/volatile
/dev/sda5             9.8G  8.2G  1.7G  84% /media/Iratok, Kepek, Zene
/dev/sda1              75G   58G   17G  78% /media/disk

---

### Post by taurus on 2009-01-24
Is the 80GB your second harddrive?

---

### Post by Friccy on 2009-01-24
> **taurus said:**
> Is the 80GB your second harddrive?

I have just one hard drive but 5 partitions (1 is for the swap)

---

### Post by taurus on 2009-01-24
So the 79.9GB is your /dev/sda4 then.  What happens if you try to mount it from a terminal?

```
sudo mkdir /media/sda4
sudo mount -t ntfs-3g /dev/sda4 /media/sda4
df -h
```

---

