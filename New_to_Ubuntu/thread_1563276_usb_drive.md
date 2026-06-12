---
title: "usb drive"
date: 2010-08-28
forum: New to Ubuntu
---

### Post by protpisys on 2010-08-28
After much ado I have my external hard drive partitioned into 2 drives; however, Ubuntu only finds one of them. How can I get it to recognize the other drive?

---

### Post by skatinjj on 2010-08-28
> **protpisys said:**
> After much ado I have my external hard drive partitioned into 2 drives; however, Ubuntu only finds one of them. How can I get it to recognize the other drive?

Is the not recognized partition formatted with a file system?  Believe it has to have a file system before it will be seen.

Also, open a terminal and post the output of:

```
sudo fdisk -l
```

---

### Post by protpisys on 2010-08-28
it's not recognizing the swap drive:

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf99b3d64

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *        4059       30402   211600384    7  HPFS/NTFS
/dev/sda3             192        4059    31059969    5  Extended
/dev/sda5             192        3894    29732864   83  Linux
/dev/sda6            3894        4059     1326080   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdc: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xacdd9b22

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       38965   312982218    7  HPFS/NTFS
/dev/sdc2           38965       77826   312147969    5  Extended
/dev/sdc5           38965       77826   312146944   82  Linux swap / Solaris

---

### Post by jtarin on 2010-08-28
> **protpisys said:**
> it's not recognizing the swap drive:


/dev/sda6            3894        4059     1326080   82  **_Linux swap_** / Solaris


   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       38965   312982218    7  HPFS/NTFS
/dev/sdc2           38965       77826   312147969    5  Extended
/dev/sdc5           38965       77826   312146944   82  **_Linux swap_** / SolarisReally?

---

### Post by skatinjj on 2010-08-28
> **protpisys said:**
> it's not recognizing the swap drive:

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf99b3d64

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *        4059       30402   211600384    7  HPFS/NTFS
/dev/sda3             192        4059    31059969    5  Extended
/dev/sda5             192        3894    29732864   83  Linux
/dev/sda6            3894        4059     1326080   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdc: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xacdd9b22

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       38965   312982218    7  HPFS/NTFS
/dev/sdc2           38965       77826   312147969    5  Extended
/dev/sdc5           38965       77826   312146944   82  Linux swap / Solaris

Maybe I am missing something but I see:

2 drives (sda and sdc)

2 linux swap partitions (sda6 and sdc5)

1 partition flagged as boot (sda2)

Should there be a another drive (sdb)?

---

### Post by protpisys on 2010-08-28
> **jtarin said:**
> Really?

well...I can't find the drive to mount it. To this point  Drives just appear w/out intervention by me

---

### Post by jtarin on 2010-08-28
> **protpisys said:**
> After much ado I have my external hard drive partitioned into 2 drives; however, Ubuntu only finds one of them. How can I get it to recognize the other drive?
You start with one drive.......you can partition it into a hundred partitions and you will still only have one drive. Maybe David Copperfield could find the other.:)

---

### Post by protpisys on 2010-08-28
I'm not sure that's right...what I did was actually repartition and deleted an existing partition, which did indeed appear on the desktop and expand the swap file which doesn't appear. I would very much prefer it did.

---

### Post by skatinjj on 2010-08-28
> **protpisys said:**
> I'm not sure that's right...what I did was actually repartition and deleted an existing partition, which did indeed appear on the desktop and expand the swap file which doesn't appear. I would very much prefer it did.

The swap partition is so the OS can write to it while using programs and/or if your physical memory is low.  It does not actually appear where you can see it as a drive.

---

### Post by protpisys on 2010-08-28
so I should re-repartition and shrink it back down again...ah, that makes sense. Thanks

---

### Post by skatinjj on 2010-08-28
> **protpisys said:**
> so I should re-repartition and shrink it back down again...ah, that makes sense. Thanks

No idea, I a, still confused at what exactly you are trying to do.

---

### Post by protpisys on 2010-08-28
that did it I have access to the entire disk, thanks again.

---

