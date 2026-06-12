---
title: "HDD size representation"
date: 2010-06-12
forum: New to Ubuntu
---

### Post by sungod84 on 2010-06-12
I am having trouble getting an accurate readout on my hard drive usage.I am using Lucid with full install on my HDD(no partion w/ windows) I know for a fact that I have a 250GiB HDD. I checked the tech specs for my computer online to verify. When I use programs such as the Disk Usage Analyzer or the System Moniter, It only reads out that I have about 230GiB and 225.7GiB on my HDD respectively. Another issue is accurate representation of actual size of usage. Again the DUA states I am using 53.6GB while the SysMon shows 49.3Gb. I know for a fact that my downloads and files in my home folder total 90.7 and is soon to increase. My question is why is there such a variance in Disk Space Representation. If I have to keep a close eye on my usage and add it up myself I will but I was hoping a simple utility could show me. Any help is appreciated.

---

### Post by SRST Technologies on 2010-06-12
If you're unsure as to why a 250GB hard disk is being represented otherwise, how do you know for a FACT how big your home folder is any size whatsoever?

---

### Post by terry_gardener on 2010-06-12
if it is the total size of the HDD you talking about then this is totally normal.
reason being that all drives hold a index that contents the location of everything on the HDD so the bigger the drive the bigger the index is going to be. 

i.e. i have 1tb hdd and it shows the total capacity of 916 GB. 

it does matter if the HDD is formatted ext or ntfs you get the same results

---

### Post by quadproc on 2010-06-12
> **sungod84 said:**
> I am having trouble getting an accurate readout on my hard drive usage.
At least two things are happening here:

1. GiB and GB.  One GiB is 2^30 bits while one GB is exactly 10^9 bits.  So a Gib is a somewhat larger unit of measure.  Disk drive makers typically specify GB while everybody else typically specifies GiB.

2. The file system on a disk takes up some space  The amount used varies with the type of filesystem and the directory structure.

There may also be lost space due to unused (inactive) regions adjacent to partitions; this is a function of how the disk was partitioned and might not exist in your setup.

quadproc

---

### Post by Rubi1200 on 2010-06-12
I am not sure why, but I have noticed discrepancies between what > Disk Usage Analyzer or the System Moniter say and for example the following commands which can be run in the terminal.

Use ```
 du -hc --max-depth=1
``` to see the usage for the home directory.

For total disk usage, run the ```
 df -h
``` command.

---

### Post by sungod84 on 2010-06-12
> **terry_gardener said:**
> if it is the total size of the HDD you talking about then this is totally normal.
reason being that all drives hold a index that contents the location of everything on the HDD so the bigger the drive the bigger the index is going to be. 

i.e. i have 1tb hdd and it shows the total capacity of 916 GB. 

it does matter if the HDD is formatted ext or ntfs you get the same results

I figured that my system was taking up space on my hard drive. Maybe its just showing what is left which is all fine by me. :)

> **quadproc said:**
> At least two things are happening here:

1. GiB and GB.  One GiB is 2^30 bits while one GB is exactly 10^9 bits.  So a Gib is a somewhat larger unit of measure.  Disk drive makers typically specify GB while everybody else typically specifies GiB.

2. The file system on a disk takes up some space  The amount used varies with the type of filesystem and the directory structure.

There may also be lost space due to unused (inactive) regions adjacent to partitions; this is a function of how the disk was partitioned and might not exist in your setup.

quadproc


This makes a lot of sense and explains why the SysMon is displaying such a vastly different reading compared with the Disk Usage Anaylyzer. I only have one more question that maybe im just not understanding. Only focusing on the Disk Usage Analyzer(Which gives readings in GB not GiB) It says of my total 229GB and I am using 54.9GB. Now if I right click on my /home folder and click properties it shows that I am using 92.8GB. I took a screeshot for more clarity. I just want to try and understand what is going on so I have a better understanding of what my computer is doing.
  

Thanks to everyone so far who has offered help. It is greatly appreciated.

---

### Post by srs5694 on 2010-06-12
> **quadproc said:**
> 1. GiB and GB.  One GiB is 2^30 bits while one GB is exactly 10^9 bits.  So a Gib is a somewhat larger unit of measure.  Disk drive makers typically specify GB while everybody else typically specifies GiB.

This is correct except that GiB/GB refer to gibi-/giga-*bytes,* not gibi-/giga-*bits.* Typically, 1 byte = 8 bits, 1 bit being what's required to represent a 0 or 1 value. A byte can therefore hold a value of 0-255 (in decimal notation).

Also, at one time "B" was used to refer to bytes, whereas "b" referred to bits, so "GB" would be gigabytes, whereas "Gb" would be gigabits. I'm not sure if that's still accepted practice, but I try to capitalize my "B"s in this sort of context, at least when I mean bytes or multiples thereof.

---

### Post by sungod84 on 2010-06-13
Ok so the Giga,Gibi thing is fairly cleared up. It just seems like there is no congruency throughout the system. I don't see why its so complicated to register how much total hard drive space is available, how much is being used, and then show that in a simple GUI window while keeping the same units of measurement throughout.

---

