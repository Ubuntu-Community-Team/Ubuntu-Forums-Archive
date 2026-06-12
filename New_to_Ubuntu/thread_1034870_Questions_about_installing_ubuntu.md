---
title: "Questions about installing ubuntu"
date: 2009-01-09
forum: New to Ubuntu
---

### Post by Ghost M.D on 2009-01-09
Hi all

I have question about the installing
 
If I want to install ubuntu for example on 4GB 

how to prepare the hard disk for installing

or what the base for preparing

I know for the swap RAM*1.5= swap

but what the base for the root or home

I hope my question is clear now

---

### Post by blazemore on 2009-01-09
The Guided setup is probably best for you. I would reccomend doing that.

If, for whatever reason, you cannot do the guided setup, I would simply have a swap partition of about the same size as your RAM, and the rest as ext3 formatted /

---

### Post by Ghost M.D on 2009-01-09
I install the ubuntu 

& I prepare the hard disk manual from a way I find in the net

but still in my mind what is the base for it 

it was not clear in the way I find

---

### Post by talsemgeest on 2009-01-09
> **blazemore said:**
> The Guided setup is probably best for you. I would reccomend doing that.

If, for whatever reason, you cannot do the guided setup, I would simply have a swap partition of about the same size as your RAM, and the rest as ext3 formatted /
Very good choice. However, 4GB will be straining ubuntu a bit and you will not be able to install many big applications. Please keep this in mind.

---

### Post by sadaruwan12 on 2009-01-09
Theres no real way of partitioning ubuntu just do it the way you want normal the partition table goes like this,

SWAP,
/BOOT,
/ROOT,(root is shown as / in linux)
/HOME,

If you've extra space the go for a /TEMP partition.

Heres my partition table.
```
Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc263c263

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         892     7164958+   7  HPFS/NTFS
/dev/sda2             893        4865    31913122+   f  W95 Ext'd (LBA)
/dev/sda5             893        3442    20482843+   7  HPFS/NTFS
/dev/sda6            3443        3457      120456   83  Linux
/dev/sda7            3458        3706     2000061   82  Linux swap / Solaris
/dev/sda8            3707        4435     5855661   83  Linux
/dev/sda9            4436        4865     3453943+  83  Linux

Disk /dev/sdb: 30.0 GB, 30020272128 bytes
255 heads, 63 sectors/track, 3649 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa7caa7ca

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            1277        3648    19053090    7  HPFS/NTFS
/dev/sdb2               1        1276    10249438+  83  Linux

Partition table entries are not in disk order

```

---

### Post by binbash on 2009-01-09
RAM*1.5= swap is not needed if you dont use functions like hibernate suspend etc, you can make it smaller.Be sure you make the home directory biggest.

---

### Post by talsemgeest on 2009-01-09
> **binbash said:**
> RAM*1.5= swap is not needed if you dont use functions like hibernate suspend etc, you can make it smaller.Be sure you make the home directory biggest.
With a drive size that small I would suggest not having a /home partition, just a swap and / . This will give the best use of the very limited space.

---

### Post by blazemore on 2009-01-09
If you only have 4gb of hard disk space, don't have a large dedicated swap partition at all!
You'll be using up precious space, so make it 256mb or something.
Also if you can, buy an external hard drive on which you store your files (music etc)

---

