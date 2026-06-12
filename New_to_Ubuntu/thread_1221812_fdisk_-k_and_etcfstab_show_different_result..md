---
title: "fdisk -k and /etc/fstab show different result."
date: 2009-07-24
forum: New to Ubuntu
---

### Post by shaoxiao on 2009-07-24
I use command fdisk -l and less /etc/fstab to see the layout of many harddisk .It is really surprising that 

there are something different between them. The fdisk -l show my swap in sda6 and / in sda7 (I think this 

is right)But /etc/fstab show swap in sda7 and / in sda8 . Is this right ?:( These below are the result of  

them.

lou@lou-laptop:~$ sudo fdisk -l
[sudo] password for lou: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x624aa2e0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2432    19535008+   7  HPFS/NTFS
/dev/sda2            2433       19457   136753312+   f  W95 Ext'd (LBA)
/dev/sda5            2433        7296    39070048+   b  W95 FAT32
/dev/sda6            7297        7545     2000061   82  Linux swap / Solaris//Please pay attention to this and
/dev/sda7            7546       12160    37069956   83  Linux //this
/dev/sda8           12161       19457    58613121    b  W95 FAT32


# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda8 during installation
UUID=e6490683-c3cd-4752-86c3-3fe76f8d7de1 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=bd9bb463-ed38-4116-85b3-f31f8971c730 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by gastly on 2009-07-24
It says > # / was on /dev/sda8 during installation

Maybe you have changed it after the install? or added or removed any partition after installing?

---

### Post by shaoxiao on 2009-07-24
> **gastly said:**
> It says 

Maybe you have changed it after the install? or added or removed any partition after installing?
I am sure that i don't change it . It is really confusing.

---

### Post by frunns on 2009-07-24
Not quite sure how you can be sure of what device is mounted where. And the layout of the harddisk you technically only get from fdisk, fstab only contains how partitions are used. Try
```
vol_id -u bd9bb463-ed38-4116-85b3-f31f8971c730
```
You'll probably get /dev/sda6.

---

### Post by shaoxiao on 2009-07-24
> **frunns said:**
> Not quite sure how you can be sure of what device is mounted where. And the layout of the harddisk you technically only get from fdisk, fstab only contains how partitions are used. Try
```
vol_id -u bd9bb463-ed38-4116-85b3-f31f8971c730
```You'll probably get /dev/sda6.

err..It does not work !

lou@lou-laptop:~$ sudo vol_id -u bd9bb463-ed38-4116-85b3-f31f8971c730
bd9bb463-ed38-4116-85b3-f31f8971c730: error opening volume

---

### Post by drs305 on 2009-07-24
To add on what frunns said, you can't necessarily tell which device (sda) things are mounted on in fstab by looking at the *comments*. Those comments were placed in fstab when you installed the system, and if partitions change the comments don't - i.e. they are never updated. So even though the comment (#) says something is in sdXX, you really have to verify it with other commands.

To see where they actually are, you can use the following to get them all:
```
sudo blkid
```

---

### Post by Cheesemill on 2009-07-24
> **shaoxiao said:**
> But /etc/fstab show swap in sda7 and / in sda8.

No it doesn't. It tells you that that is where they were when you first installed Ubuntu.
Partition numbers can change without you having to do anything, that's why fstab refers to them by their UUID's not their partition number (because a UUID will never change).

---

### Post by shaoxiao on 2009-07-24
> **drs305 said:**
> To add on what frunns said, you can't necessarily tell which device (sda) things are mounted on in fstab by looking at the *comments*. Those comments were placed in fstab when you installed the system, and if partitions change the comments don't - i.e. they are never updated. So even though the comment (#) says something is in sdXX, you really have to verify it with other commands.

To see where they actually are, you can use the following to get them all:
```
sudo blkid
```

lou@lou-laptop:~$ sudo blkid
/dev/sda1: UUID="709C21839C214546" LABEL="XIU" TYPE="ntfs" 
/dev/sda5: LABEL="STUDY" UUID="71BF-7C47" TYPE="vfat" 
/dev/sda6: TYPE="swap" UUID="bd9bb463-ed38-4116-85b3-f31f8971c730" 
/dev/sda7: UUID="e6490683-c3cd-4752-86c3-3fe76f8d7de1" TYPE="ext3" 
/dev/sda8: LABEL="SOURCE" UUID="7D64-9D2C" TYPE="vfat" 

 err...I think i have figured it out .Thanks all of you. :)

---

