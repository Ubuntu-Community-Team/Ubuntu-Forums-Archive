---
title: "How do I mount a partition at start up?"
date: 2011-06-22
forum: New to Ubuntu
---

### Post by GaryTheCat on 2011-06-22
I've tried experimenting based on what I've read but can't get it to work - I'm trying to mount my sdb1 partition in my home folder at start up ... can someone tell me how?

sudo fdisk -l comes up with:


```

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x71b32ced

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       44629   358474752    7  HPFS/NTFS
/dev/sdb2           44629       60802   129908737    5  Extended
/dev/sdb5           44629       60541   127814656   83  Linux
/dev/sdb6           60541       60802     2093056   82  Linux swap / Solaris

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x78000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          28      224878+  de  Dell Utility
/dev/sda2              29        1334    10485760    7  HPFS/NTFS
/dev/sda3   *        1334       14267   103886844    7  HPFS/NTFS
/dev/sda4           14267       14594     2621440    f  W95 Ext'd (LBA)
/dev/sda5           14267       14594     2620416   dd  Unknown


```

I'm pretty sure I want to edit my fstab to mount it but have no idea how :-(

---

### Post by sanderd17 on 2011-06-22
Can you follow this: 

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by seawolf167 on 2011-06-22
> **sanderd17 said:**
> Can you follow this: 

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

I'm not quite sure what relevance this is to the issue he asked about...


Create the mount point you want to mount it at

```
sudo mkdir /mount/point
```Open /etc/fstab for editing

```
gksu /etc/fstab
```Add the following entry

```
/dev/sdb1     /mount/point     ntfs-3g defaults,locale=en_US.utf8     0     0
```

---

### Post by oldos2er on 2011-06-22
I'm not sure having /home as NTFS would work. If it was me I would backup any data and format sdb1 as ext3 or ext4.

---

### Post by seawolf167 on 2011-06-22
> **GaryTheCat said:**
>  mount my sdb1 partition in my home folder at start up

Am I missing something? I got the impression that the OP didn't want his NTFS partition as his home partition, but rather just mounted inside his home partition?

---

### Post by sanderd17 on 2011-06-22
> **seawolf167 said:**
> Am I missing something? I got the impression that the OP didn't want his NTFS partition as his home partition, but rather just mounted inside his home partition?

Oops, that's why my post is irrelevant, I thought he wanted it as his /home.

---

