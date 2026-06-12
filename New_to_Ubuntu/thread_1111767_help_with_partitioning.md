---
title: "help with partitioning"
date: 2009-03-31
forum: New to Ubuntu
---

### Post by zxy on 2009-03-31
I need help with partitioning 

Ubuntu wants all my space even though i only want to give 20gb


it doesnt give me that option of moving the "=" to change how much to give....

heres my sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe56bbab0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         192       38913   311025664    7  HPFS/NTFS
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$

---

### Post by talsemgeest on 2009-03-31
If you are doing a clean install, simply resize and delete partitions as you see fit using the partition editor, then choose to install to the free space.

---

### Post by zxy on 2009-03-31
how do I know which partition to delete, and what if i delete the vista one >.>

---

### Post by Moop on 2009-03-31
You could try using Vistas partitioner to shrink the Vista partition and then install Ubuntu to the unused space. 

Sda2 is ntfs so that must be where Vista is.

---

### Post by zxy on 2009-03-31
[IMG]http://i8.photobucket.com/albums/a9/mppaki/partitioning.png[/IMG]


i turned off linux when the partioning stayed at 0% so i think that may have gave me the error but which one should i remove.

also moop are you on voide.org?

---

### Post by Moop on 2009-03-31
I don't think you need to delete any of the partitions. You just need to shrink your Vista partition (sda2) to make some free space. If it's not full of data you should be able to resize it. Defragmenting it (in vista) first will help.

Resizing takes a long time. It may seem like it's stuck but you just need to let it work. 

I'm not familiar with voide.

---

### Post by talsemgeest on 2009-03-31
Yes, if you have vista, you should boot that, use the vista partition editor (from the control panel) to shrink the vista partition, then boot the ubuntu live cd to install ubuntu onto the space you just freed up.

---

### Post by kansasnoob on 2009-03-31
> **talsemgeest said:**
> Yes, if you have vista, you should boot that, use the vista partition editor (from the control panel) to shrink the vista partition, then boot the ubuntu live cd to install ubuntu onto the space you just freed up.

+1! That's the right way to do it!

---

