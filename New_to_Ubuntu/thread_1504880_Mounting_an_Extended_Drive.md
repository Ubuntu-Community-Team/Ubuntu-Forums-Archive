---
title: "Mounting an Extended Drive"
date: 2010-06-08
forum: New to Ubuntu
---

### Post by age99 on 2010-06-08
Hi, I have a dual-boot Win7/Lucid machine that I am accessing remotely. I have some files on the Windows side that I am trying to access, but I can't seem to mount the drive.  

The results from
sudo fdisk -l  

> 
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       93060   747503426    7  HPFS/NTFS
/dev/sdb2           93061      182401   717631582+   5  Extended
/dev/sdb5           93061      178782   688561933+  83  Linux
/dev/sdb6          178783      182401    29069586   82  Linux swap / Solaris


I have tried:

```

sudo mkdir /media/d
sudo mount /dev/sdb2 d/ -t ntfs

```

Withouth success.  I am trying to mount /dev/sbd2 which is Extended, so I know there are some issues with that.  Is there any way to access this data?  I know that with the GUI I can easily access the drive, but I can't figure out how to do it on the command line.

Thanks

---

### Post by RiceMonster on 2010-06-08
try replacing "ntfs" with "ntfs-3g" in the second command you listed.

---

### Post by age99 on 2010-06-08
That didn't work:

> 
NTFS signature is missing.
Failed to mount '/dev/sdb2': Invalid argument
The device '/dev/sdb2' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?


Is there something specific required for the Extended partitions?

---

### Post by RiceMonster on 2010-06-08
Sorry if this is a stupid question, but are you sure /dev/sdb1 isn't the one you want to mount?

---

### Post by age99 on 2010-06-08
I mounted /dev/sdb1, but it isn't the partition that I needed.

---

### Post by reiki on 2010-06-08
> **age99 said:**
> I mounted /dev/sdb1, but it isn't the partition that I needed.

The Extended partition is just a container for logical partitions. You can mount what is INSIDE an extended partition (other partitions) but you can't mount the extended partition itself.

---

### Post by age99 on 2010-06-08
How do I mount what is inside?  Is there a way to list what is inside the partition?

---

### Post by Arla on 2010-06-08
Inside is sdb5 and sdb6 (check the block numbers, you'll see that sdb5 has the same start block as sdb2 and sdb6 has the same finish block as sdb2) 

You have "three" actual partitions with data (sdb1, sdb5 and sdb6) and sdb5 and sdb6 are contained within the extended partition sdb2

---

### Post by age99 on 2010-06-10
Ok, so managed to mount the drive.  Here is how I did for anybody interested. 
```
sudo fdisk -l
```

> 
Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe2fb4c60

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2   *           6        1260    10078208    7  HPFS/NTFS
/dev/sda3            1260      182401  1455015936    7  HPFS/NTFS

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x3b3b02b4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       93060   747503426    7  HPFS/NTFS
/dev/sdb2           93061      182401   717631582+   5  Extended
/dev/sdb5           93061      178782   688561933+  83  Linux
/dev/sdb6          178783      182401    29069586   82  Linux swap / Solaris

Previously, I was trying to mount the wrong disk. This is what worked:

```
cd /media
sudo mkdir e
sudo mount /dev/sda3 e/ -t ntfs

```

---

