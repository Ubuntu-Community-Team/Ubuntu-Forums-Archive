---
title: "2nd internal drive mounting problems"
date: 2011-02-22
forum: New to Ubuntu
---

### Post by Loki57701 on 2011-02-22
Alright guys, I need some help here.

I've done this before without problems, but for some reason I just can't get this to work.

I have a second internal drive in my computer.
I want to mount the drive and use it for storing pics, vids..whatever.

fdisk -l output:
```
Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00018cf8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60802   488385536   83  Linux

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000af8ef

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13995   112412672   83  Linux
/dev/sda2           13995       14594     4805633    5  Extended
/dev/sda5           13995       14594     4805632   82  Linux swap / Solaris
```The disk I want is /dev/sdb

I tried to format the disk with mkfs.ext3 /dev/sdb, but I kept getting problems - so I installed Gparted and formatted the whole drive as ext3.

I created the mount point in /media called storage, so: mount point = /media/storage

I did:
```
chown nobody:nogroup storage
chmod 770 storage
```next I did:
```
mount /dev/sdb1 /media/storage
```Then I added the following to /etc/fstab
```
/dev/sdb1 /media/storage ext3 defaults 0 0 
```In the past this has worked with no problems, and this time it actually worked through reboot, but now it doesn't work at all. When I mount the drive nothing happens. 

Can anyone point me in the right direction here?

---

### Post by TeoBigusGeekus on 2011-02-22
No error messages when you mount it manually?

---

### Post by Ben Page on 2011-02-23
Download NTFS configuration tool

```
sudo apt-get install ntfs-config
```

Try with it, it has auto configure and drive detection options, it can also set up drives to automount, give read write permissions etc. (writes correct lines to /etc/fstab).

Edit> Yeah, it's for NTFS volumes, you can format your drive to NTFS FS...

---

### Post by aeiah on 2011-02-23
> **Ben Page said:**
> Download NTFS configuration tool

```
sudo apt-get install ntfs-config
```

Try with it, it has auto configure and drive detection options, it can also set up drives to automount, give read write permissions etc. (writes correct lines to /etc/fstab).

Edit> Yeah, it's for NTFS volumes, you can format your drive to NTFS FS...

this has nothing to do with NTFS

---

### Post by aeiah on 2011-02-23
> **TeoBigusGeekus said:**
> No error messages when you mount it manually?

yea what he said.

if you aren't getting any errors when you mount manually (and it doesnt work either) i guess you could check your logs.

```
grep sdb /var/log/messages

```

---

### Post by cjv8888 on 2011-02-23
Have you tried using UUID instead in the /etc/fstab

> UUID=xxxxxxxxxxxxxxxxx  /media/storage ext3 defaults 0 0


> blkid

---

