---
title: "FAT32 external hdd not mounting. 8.10"
date: 2009-03-30
forum: New to Ubuntu
---

### Post by Valefar on 2009-03-30
I've just had a fresh install of Intrepid Ibex, and because of hdd being taken from an xbox [10gb, I kid you not], I'm looking to hook up my 80gb Seagate external hdd.
So far, I've had no luck with pmount, or any sort of mounting.
It is recongised with sudo fdisk -l, but I'm pretty much blocked.

---

### Post by Valefar on 2009-03-30
For what it is worth, this is what comes up with fdisk -l.
```
Disk /dev/sda: 10.2 GB, 10242892800 bytes
255 heads, 63 sectors/track, 1245 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc40bc40b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1186     9526513+  83  Linux
/dev/sda2            1187        1245      473917+   5  Extended
/dev/sda5            1187        1245      473886   82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x64c4874a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9729    78148161    c  W95 FAT32 (LBA)
```

---

### Post by mikechant on 2009-03-30
So what errors do you get when mounting?

E.g. if you type the following in a terminal:

sudo mkdir /media/external
sudo mount -t vfat /dev/sdb1 /media/external

---

