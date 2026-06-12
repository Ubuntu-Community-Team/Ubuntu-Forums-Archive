---
title: "what has to be update for linux-swap??"
date: 2009-07-24
forum: New to Ubuntu
---

### Post by eshant_engineer on 2009-07-24
I have changed the location of swap area now it is of 256 MB but it is still showing 950 MB which i had earlier. Now what i ahve to update to correct this?

Thank You

---

### Post by ajgreeny on 2009-07-24
What do you mean by "changed the location of swap"?  Did you use gparted to change the partition you originally had by shrinking it, or did you just make a new smaller partition for swap.  Whichever you did, I think you will probably need to edit /etc/fstab for the new swap to be used at boot.

Can you show us the output from 
```
sudo fdisk -l
sudo blkid
cat /etc/fstab
```each line is a separate command and will give an output in terminal.  Copy that here for more help.

---

### Post by eshant_engineer on 2009-08-11
Yes i had used Partition Editor for changin g the location of swap area. Right now "System Monitor is showing me swap area size of 712.3 MB but the actual size in GParted is 94.3 MB```
root@eshant-desktop:~# fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdba3dba3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         994     7984273+  83  Linux
/dev/sda2             995        1006       96390   82  Linux swap / Solaris
/dev/sda3   *        1007        3276    18233775    7  HPFS/NTFS
/dev/sda4            3277        9729    51833722+   f  W95 Ext'd (LBA)
/dev/sda5            3277        5370    16820023+   7  HPFS/NTFS
/dev/sda6            5371        6080     5703043+   7  HPFS/NTFS
/dev/sda7            6081        9729    29309536    7  HPFS/NTFS

Disk /dev/sdb: 1995 MB, 1995440128 bytes
39 heads, 38 sectors/track, 2629 cylinders
Units = cylinders of 1482 * 512 = 758784 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        2630     1948606+   6  FAT16
root@eshant-desktop:~# blkid
/dev/sda1: UUID="80087003-469d-4f95-abd7-11c4a6db98ff" TYPE="ext4" 
/dev/sda2: TYPE="swap" UUID="36afdb65-d9ee-4ce1-831f-d7071983ff41" 
/dev/sda3: UUID="82CACC02CACBF089" TYPE="ntfs" 
/dev/sda5: UUID="768CA9F28CA9ACD5" TYPE="ntfs" 
/dev/sda6: UUID="A8448C38448C0B70" LABEL="DISK_VOL3" TYPE="ntfs" 
/dev/sda7: UUID="8ED28E54D28E4087" LABEL="DISK1_VOL3" TYPE="ntfs" 
/dev/ramzswap0: TYPE="swap" 
/dev/sdb1: SEC_TYPE="msdos" UUID="1A2B-50D3" TYPE="vfat" 
root@eshant-desktop:~# cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=80087003-469d-4f95-abd7-11c4a6db98ff /               ext4    relatime,errors=remount-ro 0       1
# swap was on /dev/sda2 during installation
UUID=36afdb65-d9ee-4ce1-831f-d7071983ff41 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

---

### Post by eshant_engineer on 2009-08-15
please respond here.

---

### Post by Barrucadu on 2009-08-15
Try this, and see what happens:

```
sudo swapoff -a
sudo swapon -a
```

---

### Post by colau on 2009-08-17
> **eshant_engineer said:**
> I have changed the location of swap area now it is of 256 MB but it is still showing 950 MB which i had earlier. Now what i ahve to update to correct this?

Thank You
How did you change the location of swap area?

---

