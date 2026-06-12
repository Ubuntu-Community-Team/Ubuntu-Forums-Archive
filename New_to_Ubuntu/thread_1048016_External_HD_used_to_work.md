---
title: "External HD used to work"
date: 2009-01-23
forum: New to Ubuntu
---

### Post by sarum on 2009-01-23
Hi, I've installed a USB HD. I formatted it (ext3) and chmod so I can use it, and it worked fine for an hour or so. Then I shut down for the night and next morning I got:-

Cannot mount Volume.
mount_point cannot contain the following charaters
:newline, G_DIR_SPERATOR (usually /).

Can anyone help please............sarum

---

### Post by Crafty Kisses on 2009-01-23
I need to see your fstab, can you please post it here on the forums:
```
sudo gedit /etc/fstab
```
Then I wouldn't mind seeing the following command, make sure the external HD is plugged in when you run the command:
```
sudo fdisk -l
```
When you post these results, either I or someone else can further assist you on your current problem.

---

### Post by sarum on 2009-01-23
Thankyou Codename for your quick reply. The results are:-

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=54391b07-301b-493b-8e08-707aae3dda42 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=a29c854e-3490-4eaf-90fd-b01003a4af28 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0




cjf@cjf-desktop:~$ sudo fdisk -l

Disk /dev/sda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe757e757

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2315    18595206   83  Linux
/dev/sda2            2328        2434      859477+   5  Extended
/dev/sda5            2328        2434      859446   82  Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x72727272

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1275    10241406   83  Linux
/dev/sdb2            1276        4865    28836675    5  Extended
cjf@cjf-desktop:~$ 
I hope this shows what's wrong. Cheers......sarum

---

### Post by cjv8888 on 2009-01-23
Please also post

> sudo blkid

---

### Post by sarum on 2009-01-23
Thanks cjv, here's the results:-

/dev/sda1: UUID="54391b07-301b-493b-8e08-707aae3dda42" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="a29c854e-3490-4eaf-90fd-b01003a4af28" 

Cheers........sarum

---

### Post by sarum on 2009-01-23
Sorry, I forgot to switch it on:-

cjf@cjf-desktop:~$ blkid
/dev/sda1: UUID="54391b07-301b-493b-8e08-707aae3dda42" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="a29c854e-3490-4eaf-90fd-b01003a4af28" 
/dev/sdb1: UUID="6e18f2d9-4ded-46dc-9c9c-977a30d8d96e" TYPE="ext2"

---

### Post by cjv8888 on 2009-01-23
I think we will try mounting it again.
Try in a terminal

```
sudo mkdir /media/ExternalHD
```
 
```
sudo mount -t ext2 /dev/sdb1 /media/ExternalHD
```

---

