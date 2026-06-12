---
title: "problems installing ubuntu 8.10"
date: 2008-12-05
forum: New to Ubuntu
---

### Post by djyoung4 on 2008-12-05
ok so I went to partition my hard drive and I get an error saying that it can't be partitioned.  has anybody had a similar experience?  I have tried defragging, CHKDSK, CHKDSK/F.  nothing seems to help.  any other suggestions would be very helpful

---

### Post by Michael.Godawski on 2008-12-05
Can you please post the output of these commands:

```
sudo fdisk -l
cat /etc/fstab
```

---

### Post by nhasian on 2008-12-05
are you trying to partition your drive from Windows or Ubuntu?  what tool are you using?  fdisk or gparted?

---

### Post by djyoung4 on 2008-12-05
sorry I am currently running Windows XP SP3 and I am trying to reduce Windows partition and use it for Ubuntu but I get an error.  I have a Live CD and I am using Gparted when I try to partition it.

cat /etc/fstab
aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0

sudo fdisk -l
disk /dev/sda: 120.0GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280
Disk identifier: 0x282d282d
   Device Boot    Start       End     Blocks  Id  System
/dev/sda1   *         1     12924  103811998+  7  HPFS/NTFS
/dev/sda2         12926     14462   12345952+  c  W95 FAT32(LBA) 
/dev/sda3         14463     14593    1052257+ d7  Unknown

---

