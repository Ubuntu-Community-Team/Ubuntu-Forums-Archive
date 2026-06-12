---
title: "Trying to install ubuntu besides Windows 7"
date: 2010-03-04
forum: New to Ubuntu
---

### Post by knowledgestudent on 2010-03-04
Hi all, 
I have several times installed ubuntu on a machine besides windows XP, I used to choose the partitioning manually during the installation, where I saw all the partitions as they are formatted in the windows, 
But when I am trying to install it beside windows 7 , the whole hard disk appears as unused partition, in  addition that I can not do anything to it, during the ubuntu installation !!!!!!!
is this an issue because the windows 7 !!, 
The scenario is as follows:
I am installing the ubuntu from the bootable CD, 
On windows: 2 partitions (C and D) both are NTFS, and the rest of the disk (50 Gs) are not partitioned ( to be used for installation ubuntu),
 
but on the ubuntu installation all are one unused space, but no action can be performed, teh size is the summation of all partitions and the unpartitioned space ( in windows).
 
!! hope I made myself clear 
 
can you help please :| !! Thanks in advance :)

---

### Post by Arijit_Kundu on 2010-03-04
can you run gparted from the ubuntu cd and post a screenshot?

---

### Post by jsriz on 2010-03-04
You might be having a logical partition
Check it by booting up the live cd and running 
```

sudo fdisk -l

```
and post the results
You can use the partitioner given with ubuntu live cd to make more partitions.

If you are not confident of it use the computer management in windows and shrink your windows partition into more primary partitons.
have successfully installed windows 7 and ubuntu 9.10 without any such problems many a times

---

### Post by Robster2 on 2010-03-04
BE CAREFUL IF YOU OVER WRITE THE WRONG PARTITION YOU WILL WIPE YOUR WINDOWS INSTALLATION.

Personally I do not see the attraction of manually creating partitions (Unless you are doing something fancy like having "/" and "/Home" in separate partitions).  The install disk works very well in my experience.  If I were you I would delete the extra partition and let the installer do its work.

If you wanted to do this you should use GParted (This is on the Live CD) as the Windows partitioner cannot create EXT partitions.

You should set up a swap partition as well 1G + Your memory and the rest of the free space as your Ubuntu Ext4 

In Live CD Select the Manual Partition option and select the Ext4 section to install "/" Mount point.

---

### Post by Mark Phelps on 2010-03-04
Since this is A.B.T., I'll go ahead and pass along my standard warning -- do NOT allow the Ubuntu installer to shrink your Win7 OS partition, either manually, or as part of a side-by-side installation.  Doing so runs the risk of corrupting the Win7 OS partition and rendering that OS unbootable.

Use the builtin Win7 Disk Management utility to do the OS shrinkage.

Also, BEFORE you do anything to Win7, use the builtin Win7 Repair CD create/burn function to create a repair CD.  That will come in useful later if you need to repair your Win7 boot or if you want to restore the Win7 MBR.

---

