---
title: "help partitioning, please .."
date: 2009-01-04
forum: New to Ubuntu
---

### Post by Baffo on 2009-01-04
hello guys,

i have 2 partitions on my hard drive, and there are 30 GB of free space between them.
when i select: use free space, the installer creates a single ext3 partition. isn't it supposed to create a swap partition as well?

please help, because im confused about partitioning.

thanks

my pc specs:
[list]
[*]850 mhz cpu
[*]256 mb ram
[/list]

---

### Post by Baffo on 2009-01-04
anyone?

---

### Post by caljohnsmith on 2009-01-04
How about when you go through the Ubuntu installer, use the "manual" partition option so that you can set up a swap partition as well as your main Ubuntu partition. Let me know how that goes.

---

### Post by GoS_ on 2009-01-04
First of all, if you have more than 2GB of RAM you probably don't need a swap partition.  If you want a swap partition (which it sounds like you do), and the automatic partitioner isn't making one for you, select "manual" from the list of options on the partitioning screen.  It is pretty straightforward from here.

Select the hard drive space that you want to install the swap partition on.  Click "edit partition" and it will bring up a screen of options.  Where it says "use as" change it from whatever is there by default to "swap".  Then resize it (you probably want 1000MB or 2000MB or somewhere in that area).  Click OK and you should be good.  Then you have to make your ext3 partition to install Ubuntu on.  For this you probably want to use the rest of the space.  So keep the default size, "use as" ext3, and you might as well choose to format it as well (I think there's an option for that or maybe it's later).  If it asks for mount point (it does somewhere in the installation), use a forward slash like this /. Anyway, that's how I did it.  I have 8.04 though.  Hopefully it works on whatever you're using.  If you're still confused you could search the internet.  I think there's even some youtube videos on the subject.

Good luck!

---

### Post by mick222 on 2009-01-04
you could manually partition the drive giving 1gig to the swap , mount point /swap, or just go with default, swap is not really needed for most apps.

---

### Post by sadaruwan12 on 2009-01-04
OK, To answer your problem I need some information from you. I need to know what version of Ubuntu your using and I need to see your partition table use the below command.

open the terminal
```
sudo fdisk -l
```
and list the out put here.

---

### Post by Baffo on 2009-01-04
[here]("http://img134.imageshack.us/img134/2774/partitiontablewl1.png") is my partition table.

so, as you can see, i have:

[list]
[*]1 ntfs (primary)
[*]unallocated
[*]1 ntfs (extended logical)
[/list]
in the middle you can see the unallocated space: that's where i want to install ubuntu 8.10.

my pc specs:
[list]
[*]850 mhz cpu
[*]256 mb ram
[/list]

ps: how large should the swap partition be ?

---

### Post by kwacka on 2009-01-04
Make sure you have backed up your Windows partitions.

At the partitioning stage, select manual. 

1. On the first & third partition, choose 'NTFS' but do not format. Give a label - for example '/Windows1' and '/Windows2'. Finish with the partitions.

2. Select freespace partition, and create partition. 
Choose either ext3 or resierfs as the format, give it the label '/' and enter the size that you wish the partition to be (e.g. 10 GB). 
Tick the format box.
Finish with the partition.

3. Again select freespace, choose swap as the format. The rule used to be (still is?) double your RAM size, so select 0.5 GB.
Finish with the partition.

4. Again select freespace, again choose ext3 or resiserfs & use the maximum size. Label '/home'. Tick format.

After completing this you will find a warning box, ensure that the two windows partitions will not be formatted before going on.

(steps 2 & 3 are a personal choice, you can have 1 (or more than 2) partitions if you choose. The advantage of a separate /Home partition is that you can re-install (or choose another distribution if you wish) keeping all your settings and data.

---

### Post by Baffo on 2009-01-04
is step 1 necessary? since the 2 partitions alrady exist and are filled with data?

---

