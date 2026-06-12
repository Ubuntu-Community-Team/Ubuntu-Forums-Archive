---
title: "Question about instalation on a H disk with two directories ."
date: 2010-05-07
forum: New to Ubuntu
---

### Post by SonicStar on 2010-05-07
Hello ^__^ . 
I am new to the forum and to Ubuntu .I want to try it out ,but after reading the stuff about how to install it ,i encountered a problem .Since my hard disc is sliced in two directories ( C and D ) in order to secure my data on the pc in case Windows fails ,i just dont know if this will be a problem when i start installing ubuntu .
 Will this leave my directories untouched and simply shrink them to make place for ubuntu ,or will it install it in one of them ( lets say directory D .That is the one with no windows files in it .) The total disc space is 160Gb and directory C is arround 50Gb ..

Sorry ..i am just new to this and dont know how the things on my disc will get placed after the instalation . 

Best regards.

---

### Post by Arla on 2010-05-07
My quick thought, I'd say trying the WUBI installation first, this installs Ubuntu under your current Windows installation, and would allow you to try it out without getting into repartitioning your drives (which opens you up to significant changes to your computer).

By the way, C and D are normally (under windows nonclementure) called Drives (not directories) or Paritions.

Here is a link to the latest WUBI installer

[http://wubi-installer.org/](http://wubi-installer.org/)

---

### Post by cap10Ibraim on 2010-05-07
If you shrink your partitions you will get some free space (unallocated space) so when you boot the Ubuntu CD to install you will see an option to use the unallocated space ,this way  it will not touch you C or D partitions ,  I think thats the best thing to do

---

### Post by Penguin Guy on 2010-05-07
> **SonicStar said:**
> Since my hard disc is sliced in two directories ( C and D )
These are called **partitions**. By default, Ubuntu will shrink your partitions to make space for a new partition, then install it's self to the new partition.

---

### Post by SonicStar on 2010-05-07
Thanks .
 I would not mind if it makes another partition on my disc ,but i really wanna have some free space . I dont want to install in windows and run it from there because it will not run at its top quality . 
It will be great if there was a way that ubuntu could read the files that are in the D drive . That would be great ,but i dont know if this is possible .Will it have access to those files ?

---

### Post by The Cog on 2010-05-07
Ubuntu will be able to read the D drive after installation.

I suggest that you somehow reduce the size of the D drive, leaving 10-20 Gig un-partitioned. Vista seems to be able to do this while it's running. For earlier windows versions you need another way to do it. Partition Magic perhaps. The Ubuntu installer can also resize partitions, but its naming convention is different, and I can't remember if it gives you the choice of which one to shrink. In Linux your partitions will be /dev/sda and /dev/sdb,or perhaps /dev/sdb and /dev/sdc if there is a utility partition there that windows can't see.

After re-sizing D:, you can just tell the Ubuntu installer to use the largest free space, which will be the un-partitioned area left when you shrunk D:.

Make sure you have a good backup first, just in case you make a mistake while editing the partitions.

---

