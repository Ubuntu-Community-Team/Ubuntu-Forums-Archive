---
title: "Moving an Ubuntu Linux partition"
date: 2010-08-06
forum: New to Ubuntu
---

### Post by newport_j on 2010-08-06
When I run Gparted on my hard drive it comes up with a display that shows the Linux partition on the far left, then the Windows partition in the middle and finally a lot of unallocated space on the far right. Now I want to increase the partition size for the Linux partition, but it is not adjancent to the unallocated space. 
 
So how can I do this? I think that I can just copy and paste the Linux partition on the unallocated space. Perform that task first and then delete the old linux partion on the far left. It should work, but the new Ubuntu partition now in the middle will be named "copy of". I do not want that, so how do I get rid of the "copy of" words.
 
Newport_j

---

### Post by cjack007 on 2010-08-06
i think your partitions are somewhat like this 
Linux |windows|free space(unpartitioned)
to increase linux partition you have 2 options 
1. shrink windows partition from its begining and then extend linux one to take its place.
2. move entire windows partion towards right and then extend your linux partion.

you will need a ubuntu live cd or a gparted live cd for this.

---

### Post by aeiah on 2010-08-06
copying the linux partition would be a bad idea.. /etc/fstab, the file that describes where partitions are, would need editing, and when you're done you'll have free space at the beginning, no?

move the windows partition to the end, check that it works, then extend the linux partition.

if its possible to backup the whole drive, id do it. if not, backup your important documents. the process will take a long time and you dont want it messing up halfway through.

---

### Post by iShurtugal on 2010-08-06
What your proposing is risky, I tried moving my linux partitions around, and ended up reinstalling ubuntu.  I did get the partitions moved, but moving partition can easily corrupt data and also mess up your /etc/fstab  if your abdolutly sure, go with aeiah's solution or  cjack's first suggestion, his second one is extremely risky.

---

### Post by ajgreeny on 2010-08-06
That's a whole lot of palaver for very little advantage,

Why not just make the free space at the end of the drive into a new ntfs partition, mount it at boot time with a quick manual edit of /etc/fstab, and use it as a /data partition in both operating systems?

It will be very quick to do, there is little risk to anything already on disk , and it will work brilliantly for both systems.

---

### Post by S.R on 2010-08-06
Using the space as NTFS is the best idea. I went back and looked at some your old post. From one of your threads it looked like you only had a small bit of unallocated space at the end of your Windows partition and then your swap. Is this still the case?

If you are going to do anything to your Windows partition then defrag it first and adjust the size of the windows partition with in windows. 

Right click Computer ... Left click Manage ... Left click Storage ... Right click on the windows partition and chose shrink volume. From there you can dictate how much space in front of and behind the partition.

---

### Post by cjack007 on 2010-08-06
well it depends on you. 
if you want to create a partition for storing data just create a ntfs partition of your free space but i suggest that you create an extended  partition of your free space so you can create as many partitions in it.
but if you want to increase your linux partition(probably you want to install more programs to it) take my first suggestion its safe and quick too.

---

