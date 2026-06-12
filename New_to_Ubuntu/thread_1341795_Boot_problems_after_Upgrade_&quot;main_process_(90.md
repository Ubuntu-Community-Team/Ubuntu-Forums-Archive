---
title: "Boot problems after Upgrade &quot;main process (909) terminated&quot;"
date: 2009-11-30
forum: New to Ubuntu
---

### Post by cheph on 2009-11-30
Hello all, I know I was hear yesterday but I have managed to mess up my ubuntu 2 days in a row. I am having trouble booting ubuntu. you see I upgraded to ubuntu 9.10 recently but accidentally left my ubuntu 9.10 install CD in my disck trey and now whenever I try to boot Ubuntu I get the following error (after grub but before login screen): "init: mountall main process (909) terminated with status 3 mount of filesystem failed" does anyone e any ideas on how to rescue my ubuntu?

Cheph

---

### Post by kita on 2009-11-30
Again whats the output of your fdisk -l ?

---

### Post by cheph on 2009-11-30
Disk /dev/sda: 120.0 GB, 120034123776 bytes 
255 heads, 63 sectors/track, 14593 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Disk identifier: 0x6914ecfa 

Device     Boot     Start     End     Blocks         Id     System 
/dev/sda1     1     6     48163+         de     Dell Utility 
/dev/sda2 *     7     14201     114021337+     7     HPFS/NTFS 
/dev/sda3     14202     14593     3148740     f     W95 Ext'd (LBA) 
/dev/sda5     14202     14593     3148708+     dd     Unknown Disk 

/dev/sdb: 750.2 GB, 750156374016 bytes 
255 heads, 63 sectors/track, 91201 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Disk identifier: 0x00038216 

Device    Boot     Start     End     Blocks         Id     System 
/dev/sdb1     1     3891     31250000     82     Linux swap / Solaris 
/dev/sdb2 *     3892     91201     701317575     83     Linux

---

### Post by kita on 2009-11-30
Perhaps try

```
sudo fsck /dev/sdb2
```

---

### Post by cheph on 2009-11-30
Well, this is what happened:

it started with this

```
fsck from util-linux-ng 2.16 e2fsck 1.41.9 (22-Aug-2009) /dev/sdb2 contains a file system with errors, check forced. Pass 1: Checking inodes, blocks, and sizes 
```

then said all this, i kept typing yes, it looked promising

```
 nodes that were part of a corrupted orphan linked list found.  Fix<y>? yes  Inode 37732365 was part of the orphaned inode list.  FIXED. Inode 37732366 was part of the orphaned inode list.  FIXED. Inode 37732369 was part of the orphaned inode list.  FIXED. Inode 37732373 was part of the orphaned inode list.  FIXED. 
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity 
Pass 4: Checking reference counts Pass 
5: Checking group summary information 

---

Inode bitmap differences:  -(37732364--37732366) -37732369 -37732373 Fix<y>? yes  Free inodes count wrong for group #4606 (8152, counted=8157). Fix<y>? yes  Free inodes count wrong (43520636, counted=43520641). Fix<y>

```

So after all that ended. I restarted the computer and I still had the same issues!!

---

### Post by Johnny19734 on 2009-11-30
Have you tried to install grub again? By any chance did you manually install video drivers.(Not in the the Ubuntu repos?)

---

