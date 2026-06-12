---
title: "Other Hard Drives?"
date: 2009-03-16
forum: New to Ubuntu
---

### Post by Django1200 on 2009-03-16
I just installed xubuntu today on my pc. I am booting from a scsi drive but have two wd ide drives installed in the same pc. If I try to search for a file with catfish, I can see both drives as possibilities. I cannot search these drives, however. If I go into Thunar I cannot see these drives at all. I can go into /dev/disk and see files that seem to be representative of those drives in file form (Though they are split up into  five files) I want to be able to poke around on these drives (They were from a previous 2000 pro install so they could be NTFS) like I can with my scsi drive. Any suggestions? I am sure that it will be something embarrassingly easy.

---

### Post by Gannon8 on 2009-03-16
To mount a volume, first create a directory for it:
```
sudo mkdir /media/whatever/
```
Then actually mount it:
```
sudo mount /dev/sd** /media/whatever
```

To get your partition layouts, use:
```
sudo fdisk -l
```

---

### Post by Django1200 on 2009-03-16
I keep getting this error. If it&#347; already mounted, how do I explore it?


mount: /dev/sdb1 already mounted or /media/wd1 busy

I tried to use umount to unmount it and it gave me the following:

umount: /dev/sdb1 is not mounted (according to mtab)

Thanks for the help, by the way

---

### Post by carml on 2009-03-16
I took the commands by [http://ubuntuforums.org/showthread.php?t=6937;](http://ubuntuforums.org/showthread.php?t=6937;)
to see if a drive is mounted go to Applications->Accessories->Terminal and type there "mount" or press Alt+F2 type terminal in the search box and you'll have also access to the terminal.:)

---

### Post by Django1200 on 2009-03-18
I appreciate all of the help I&#7743; getting here but I still cannot access these drives. When I try sudo fdisk -l I get: 
Disk /dev/sda: 9105 MB, 9105023488 bytes
255 heads, 63 sectors/track, 1106 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e653f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1053     8458191   83  Linux
/dev/sda2            1054        1106      425722+   5  Extended
/dev/sda5            1054        1106      425691   82  Linux swap / Solaris

Disk /dev/sdb: 30.0 GB, 30020272128 bytes
255 heads, 63 sectors/track, 3649 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3bdab1be

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2        3649    29302560    f  W95 Ext'd (LBA)
/dev/sdb2               1           1        8001    1  FAT12
/dev/sdb5               2        3649    29302528+   b  W95 FAT32

Partition table entries are not in disk order

Disk /dev/sdc: 30.0 GB, 30020272128 bytes
255 heads, 63 sectors/track, 3649 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa26c7190

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        3493    28057491   83  Linux
/dev/sdc2            3494        3649     1253070    5  Extended
/dev/sdc5            3494        3649     1253038+  82  Linux swap / Solaris
 but it will not let me mount them

---

