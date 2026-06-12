---
title: "[SOLVED] Automount ext 3 with privs?"
date: 2008-12-03
forum: New to Ubuntu
---

### Post by nakama85 on 2008-12-03
I am trying to auto mount an Ext3 HD with privs to read and write. I know it has something to do with fstab but I don't know where to go from there. Thanks for any help.

---

### Post by nakama85 on 2008-12-03
I tried adding the lines
> dev/sdb1      /mnt      ext3     user,rw    0     0
dev/sdb2      /mnt      ext3     user,rw    0     0

But it did not seem to work.

can anyone help?

---

### Post by kpkeerthi on 2008-12-03
No thats incorrect. Are you sure the HDDs are identified as sdb1 and sdb2. Post the output of
```
sudo fdisk -l
```

---

### Post by kpkeerthi on 2008-12-03
See [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by nakama85 on 2008-12-03
> **kpkeerthi said:**
> No thats incorrect. Are you sure the HDDs are identified as sdb1 and sdb2. Post the output of
```
sudo fdisk -l
```
> 
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe397e397

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2432    19535008+  83  Linux
/dev/sda2           60291       60801     4104607+  82  Linux swap / Solaris
/dev/sda3            2433       60290   464744385   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xadd5add5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        2607    20940696   83  Linux
/dev/sdb2            2608       19444   135243202+  83  Linux

I am sure those are the ones I want to auto mount with privs.

The first(20g) for backup
the second for wine,vbox, and movies

---

### Post by kpkeerthi on 2008-12-03
It should be /dev/sdb1 and /dev/sdb2. Not dev/sdb1.
I suggest you read the link I posted earlier and recommend using UUID as udev might change the device identifier.

---

### Post by nakama85 on 2008-12-03
Ok so these are my new lines however I still don't have write access.
can someone please tell me what I am doing wrong?

> UUID=9d1e9f7d-38d1-4e3e-82bb-2385b4f340b6 /home/nakama/Backup ext3 relatime	  0	  2
# /dev/sdb1
UUID=f20e9c4a-2a63-4cd1-809b-3941f45dc0b7 /home/nakama/Media ext3 relatime        0       2
# /Dev/sdb2

---

### Post by nakama85 on 2008-12-03
> **Wickd said:**
> Well there is an easier way of doing this:

1) Open a terminal and type: sudo Nautilus
2) Mount the drive and go to properties
3) Ubder the permissions tab change the Owner to your username
4) close

That should fix your problem :)

Cherio

I saw This On Another Post. It did the trick. thanks Wickd

---

