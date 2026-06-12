---
title: "shared partition issue"
date: 2008-12-12
forum: New to Ubuntu
---

### Post by tadcan on 2008-12-12
I have been following this guide

[http://ubuntuforums.org/showthread.php?t=568731](http://ubuntuforums.org/showthread.php?t=568731)

I seem to have fallen at the last hurdle. I have created the shared partition which windows recognises. I copied the documents and settings over from C:/ to the new partition.

My problem is that I can't see the Ubuntu (8.10) folders in XP(pro SP3) and I cant see the XP folders in ubuntu. 

Here are screen shots of each with properties. Since both partitions are the same seize I presume both are in the same place. 

Due to some other experiments I also have the / (root?) assessable in XP. Which shows me that the document folders are in /home. 

I have zero idea how Linux works. Any ideas?

---

### Post by Duck2006 on 2008-12-12
When you did the ext2ifs drivers in windoze did you give the drive a letter, ie d or e or ect.

---

### Post by Paqman on 2008-12-12
Those screenshots are a bit small to read. Do you have bigger copies, or can you describe the situation a little more?

I'd say double-check that you've got both systems pointing at the right partition.

---

### Post by tadcan on 2008-12-12
Yes its named Drive F: 

I can only confirm that XP is pointing in the right direction. I presumed that /home was in the right place because that where the documents folder lives. Which could well be incorrect. How do I check where the folder is located?
 
I'll try and make the images bigger in gimp.

---

### Post by tadcan on 2008-12-12
Ok I scaled the images down to the right seize. (Maybe they got reduced during the upload) I don't know how they will look until they have been uploaded.

EDIT: It looks the same. Not sure how to make them clearer

The first image shows a partition with the documents folders with the properties window showing a partition seize of 170GB. 

The second image does the same for windows. 

The third images shows the opened root drive with the documents folder included with all the other folders.

What other info is needed?

---

### Post by Duck2006 on 2008-12-12
> It looks the same.

Yep it,s same size.

---

### Post by Paqman on 2008-12-12
> **tadcan said:**
> Yes its named Drive F: 

I can only confirm that XP is pointing in the right direction. I presumed that /home was in the right place because that where the documents folder lives.

So is it your /home partition that you're trying to share? Or a separate partition that you've just linked to in your /home?

On Ubuntu you can see what partitions you have with the command:
```
fdisk -l
```

---

### Post by tadcan on 2008-12-12
Its the /home partition I am trying to share. 

```
tadcan@Quad:~$ fdisk -l
Cannot open /dev/sda
Cannot open /dev/sdb
Cannot open /dev/sdc
```

---

### Post by Duck2006 on 2008-12-12
Try

sudo fdisk -l

---

### Post by Paqman on 2008-12-13
Haha, oops!

:oops:

---

### Post by tadcan on 2008-12-13
To make things a little harder. I have three hard drives. I backed up onto the other ones and kept them out when I did the fresh install and have just put them back in. The drive letters for the Ext3 partitions were removed so I'll go back into XP and reassign those. 

Any more info needed.


```
tadcan@Quad:~$ sudo fdisk -l
[sudo] password for tadcan: 

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4ae65dd7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       38913   312568641    7  HPFS/NTFS

Disk /dev/sdb: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0008e7de

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       64758   520168603+   7  HPFS/NTFS
/dev/sdb2           90958       91201     1959930    5  Extended
/dev/sdb3           89074       90957    15133230   83  Linux
/dev/sdb4           64759       89073   195310237+  83  Linux
/dev/sdb5           90959       91201     1951897+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x310d253f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      121601   976760001    7  HPFS/NTFS
```

---

