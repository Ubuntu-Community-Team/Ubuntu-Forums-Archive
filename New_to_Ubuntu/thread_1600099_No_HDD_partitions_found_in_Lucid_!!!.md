---
title: "No HDD partitions found in Lucid !!!"
date: 2010-10-18
forum: New to Ubuntu
---

### Post by ghumanob on 2010-10-18
I'm facing a problem that seems weird to me & have no idea that any1 has faced it so far.

Neway, i've installed **Ubuntu 10.04** (my 1st linux) just a few days ago. after that, ubuntu doesn't show any of my HDD partitions except FILESYSTEm. there are 4 partitions (one of'em is used for xp) in the hdd & besides i've used two separate partitions for ubuntu (16 & 2 GB).

even, the disk utility shows none of the partitions. the hdd is only 1 mnth old (fully functional too :) ) & has no problem in running XP. i've tried to reinstall ubuntu bt the prob remained the same every time.

**_Queries:_**
1. what can I do now ??
2. can the disks be mounted using terminal ??

---

### Post by jtarin on 2010-10-18
Can you open a terminal and enter the command ```
sudo fdisk -l
``` and post the reults here.

---

### Post by srs5694 on 2010-10-18
Please make that:

```

sudo fdisk -lu

```

This changes the reporting unit to sectors, which might be important for this problem. Please post the output between a [noparse]```
[/noparse] string and a [noparse]
```[/noparse] string for legibility.

---

### Post by ghumanob on 2010-10-27
> **jtarin said:**
> Can you open a terminal and enter the command ```
sudo fdisk -l
``` and post the reults here.
[B][U]
it has the following output[/U][/B]:

> Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x5518ddc8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7649    61440561    7  HPFS/NTFS
/dev/sda2            7650       20397   102398310    7  HPFS/NTFS
/dev/sda3           20398       39460   153123547+   7  HPFS/NTFS
/dev/sda4           39461       60801   171421552    f  W95 Ext'd (LBA)
/dev/sda5           39461       58582   153597433+   7  HPFS/NTFS
/dev/sda6           58583       60564    15920383+  83  Linux
/dev/sda7           60565       60801     1903671   82  Linux swap / Solaris


---

### Post by ghumanob on 2010-10-27
> **srs5694 said:**
> Please make that:

```

sudo fdisk -lu

```This changes the reporting unit to sectors, which might be important for this problem. Please post the output between a [noparse]```
[/noparse] string and a [noparse]
```[/noparse] string for legibility.

**_the code segment has the following output_**:

> Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x5518ddc8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   122881184    61440561    7  HPFS/NTFS
/dev/sda2       122881185   327677804   102398310    7  HPFS/NTFS
/dev/sda3       327677805   633924899   153123547+   7  HPFS/NTFS
/dev/sda4       633924961   976768064   171421552    f  W95 Ext'd (LBA)
/dev/sda5       633924963   941119829   153597433+   7  HPFS/NTFS
/dev/sda6       941119893   972960659    15920383+  83  Linux
/dev/sda7       972960723   976768064     1903671   82  Linux swap / Solaris


---

### Post by ironic.demise on 2010-10-27
> **ghumanob said:**
> **_the code segment has the following output_**:
 you have /dev/sda1 to /dev/sda7.
Type man mount for information on mounting in Terminal
I thiink that it would be along the lines of 
```

mkdir ~/Desltop/newhdd
mount /dev/sda2 ~/Desktop/newhdd
```

---

### Post by srs5694 on 2010-10-27
I don't see any problems with your partition table. In such cases, one cause that seems to crop up is old RAID data on the drive. Have you ever tried configuring the disk as part of a RAID array? If so, you could try removing the dmraid package; that seems to help some people.

---

### Post by amjjawad on 2010-10-27
[https://help.ubuntu.com/community/Partitioning%20issues?action=show&redirect=Partitioning](https://help.ubuntu.com/community/Partitioning%20issues?action=show&redirect=Partitioning)


This is might help for more understanding.

---

### Post by lavinog on 2010-10-27
can you post a screenshot of what disk utility shows?

---

