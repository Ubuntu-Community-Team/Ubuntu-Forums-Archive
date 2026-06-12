---
title: "how to partition with window disk management?"
date: 2011-05-28
forum: New to Ubuntu
---

### Post by Matrix01 on 2011-05-28
someone suggested me to check this out:  

[https://help.ubuntu.com/community/HowtoResizeWindowsPartitions](https://help.ubuntu.com/community/HowtoResizeWindowsPartitions)

and...i read this;
window disk management is easy and fast to partition hard drive.
does anyone familiar with window disk management?

---

### Post by webofunni on 2011-05-28
Yes, it is easy partition using windows disk manager. But it is a basic tool. There are many advanced partition managers available both in windows and Linux

---

### Post by srs5694 on 2011-05-28
***Do not use Windows' Disk Management tool to create new partitions for Linux!!!!!***

This program has the unfortunate tendency to turn partitions into "dynamic disks" (aka Logical Disk Manager, or LDM, volumes) with little or no warning given to the user. The trouble is that LDM is a Microsoft-only technology. Although Linux has some basic LDM support, you can't modify LDM volumes in Linux, and installing Linux to an LDM volume is difficult or impossible. (I've not looked into it in enough depth to know which.) This problem seems to be most likely to arise when you raise the number of partitions on the disk above 4, but I don't know the exact trigger conditions -- if that *always* happens, or only if all the original partitions were primaries, or whatever.

There have been many threads here from people who've fallen into this trap. Getting out of it requires either a complete disk backup/restore operation or running a partitioning tool that can do the reverse conversion. At least two Windows programs are supposed to be able to do this, but I don't know how well they work or how safe or reliable this reverse conversion is. It's best to avoid the trap rather than rely on such tools.

---

### Post by webofunni on 2011-05-28
I never faced this with windows partitioner. But what you said is correct. downgrading the dynamic disk to basic requires erasing everything 

[http://en.wikipedia.org/wiki/Logical_Disk_Manager](http://en.wikipedia.org/wiki/Logical_Disk_Manager)

---

### Post by Matrix01 on 2011-05-29
so...
i use HP Mini, and had downloaded ubuntu in flash drive for a while ago,
  
ubuntu has gparted....
is this gparted way to partition hard drive?

---

### Post by oldfred on 2011-05-29
Use the windows tools for windows and the Linux tools for Linux.

So you should use windows disk management to shrink the windows partition, but then use gparted to create new partitions for Linux.

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

### Post by Wim Sturkenboom on 2011-05-29
+1 for oldfred's suggestion

don't forget to defrag first in windows

---

### Post by Allavona on 2011-05-29
Agreed. Using the windows manager is the way to go when sizing windows disks. Defraging first is an excellent suggestion.

Gparted just does what its designed to do... You want a resize, you got it. I have never had any problems using it on both, but I have heard the horror stories!!

+1 oldfred and +1 Wim Sturkenboom

---

### Post by webofunni on 2011-05-29
Yes, it is always good to use Linux tools for linux

---

### Post by Matrix01 on 2011-05-29
i read thinkren's threads...

i learned, 
i won't to use disk management in window 7, and shrink volume of hard drive prior to ubuntu installation.

thank u to all.

---

### Post by taidaniel on 2011-05-29
You might want to read further. Many Vista and 7 users have not been able to boot into windows after resizing. Windows protection thingy. So you want to be prepared if you're gonna resize your windows partition.

---

