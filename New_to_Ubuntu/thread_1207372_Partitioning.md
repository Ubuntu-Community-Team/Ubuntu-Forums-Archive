---
title: "Partitioning"
date: 2009-07-08
forum: New to Ubuntu
---

### Post by Messyhair42 on 2009-07-08
I'm looking for a program that can divide an existing partition into two and format it into NTFS. Gparted wasn't able to divide one partition into two as far as i know. this is for a trial of Windows 7 b/c there are problems getting it to install on my internal drive

---

### Post by zvacet on 2009-07-08
Download [Gparted live CD.]("http://gparted.sourceforge.net/")

---

### Post by frunns on 2009-07-08
Can't really understand exactly how you mean... How is it partitioned now? And how do you want it partitioned? No, dividing a partition might not be possible, but you could shrink it and create a new which should be exactly the same.

---

### Post by nothingspecial on 2009-07-08
In gparted resize the partition and create a new one in the empty space.

---

### Post by sdlynx on 2009-07-08
in GParted you can shrink the size of your Win7 RC partition (apparently its not safe though so don't do this, instead),and you can also do it from within Win7 (Computer Management), which from a command prompt is compmgmt I think.  Then you can format the unallocated space into NTFS using either partitioner.

---

### Post by Messyhair42 on 2009-07-08
i have a 120 GB external HD i want to try to install W7 on, however about half is taken by sensitive information i can't move or delete. i want to make the free space a partition of it's own and install it there. Gparted cannot find a mount point and the only option under device or partition is create new partition table, which formats the whole thing, i can't resize it from Gparted

---

### Post by indytim on 2009-07-08
Since you're in Window's Land....

defrag, defrag, defrag

Once that is done, back up your critical data to say, a usb stick.

Using the partition editor of your choice, (GParted Live is my strong recomendation), shrink the partition down.  Remember that you will be constraining the ability to add new data to this partition.

Use the new "unallocated" space to plop Win7 into.

Good Luck,

IndyTim

---

