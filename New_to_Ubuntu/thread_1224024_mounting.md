---
title: "mounting"
date: 2009-07-26
forum: New to Ubuntu
---

### Post by cross1010 on 2009-07-26
i'm unable to mount my drives except my c drive and hence unable to browse through the drives . what am i supposed to correct this problem

---

### Post by Crafty Kisses on 2009-07-26
I'm not sure what you're asking? So your able to mount your C drive, do you mean your Windows drive. (NTFS drive). I'm kind of confused. Paste this command into the Terminal **(Applications->Accessories->Terminal)**:
```
sudo fdisk -l && sudo fdisk -lu
```
Then please paste the results back here on the forum, and I or somebody else can get to the root of the problem, but first do that. Thanks.

---

### Post by cross1010 on 2009-07-26
yes . my windows drive only .i'm using both windows and linux.i ran your command in my terminal and what it said was this


Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe1fae1fa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    61432559    30716248+   c  W95 FAT32 (LBA)
/dev/sda2        61432560   312560639   125564040    f  W95 Ext'd (LBA)
/dev/sda5        61432623   143347994    40957686    7  HPFS/NTFS
/dev/sda6       225263493   312560639    43648573+   7  HPFS/NTFS
/dev/sda7       143348058   148038974     2345458+  82  Linux swap / Solaris
/dev/sda8       148039038   224877869    38419416   83  Linux
/dev/sda9       224877933   225263429      192748+  83  Linux

Partition table entries are not in disk order

---

### Post by Crafty Kisses on 2009-07-27
Well, when you try to mount the drive in question, what is the exact error?

---

### Post by ~sHyLoCk~ on 2009-07-27
Post o/p of:
```
cat /etc/fstab
```

---

