---
title: "Changing my current Ubuntu partition"
date: 2009-05-23
forum: New to Ubuntu
---

### Post by RYjet911 on 2009-05-23
I'm a little stuck on a program I can use to change my current Ubuntu partition. I tried GParted, but it won't let me change.

I want to change my current 230 gig partition to three seperate ones, two 100 gig partitions and one 30 gig partition, one of the 100 gig parts retaining my Ubuntu installation. Anyone have any ideas?

---

### Post by Sef on 2009-05-23
> I'm a little stuck on a program I can use to change my current Ubuntu partition. I tried GParted, but it won't let me change.

To change the partitions, download and use the [GParted]("http://gparted.sourceforge.net/") cd.  **Back up **your **data first **as there are no 100% guarantees of success.  I'm not sure, but Ubuntu may be written over.  Have to let someone else answer that part.

---

### Post by graphius on 2009-05-29
I am the opposite. I am finally wanting to nuke my windows partition. I guess I could just format the partition, and mount it as a separate drive, but I would like to just expand my Ubuntu partition to fill the whole drive (less swap of course)

---

### Post by chrisod on 2009-05-29
You can't change partitions while they are mounted. You need to boot off the Live CD and use Gparted from there to edit the partitions.

---

### Post by mikechant on 2009-05-29
> You can't change partitions while they are mounted. You need to boot off the Live CD and use Gparted from there to edit the partitions. 

And even the LiveCD mounts swap partitions, which can prevent you from operating on other partitions. In gparted you need to right click on the swap partition and select 'swapoff' before attempting anything.

Once everything is unmounted, you should be able to stretch, squash and move any ext2/3/4 partitions any way you like. 

As far as the Windows partition is concerned (graphius) you should be able to just right click and 'delete partition' in gparted, then if the Ubuntu partition is next to it just use the resize option to expand it into the the unallocated space. Things get a bit more involved if the partitions you want to merge are not adjacent or one is primary and the other is logical.

Post some screenshots from gparted if you need more specific help.

---

