---
title: "To create partation"
date: 2010-10-11
forum: New to Ubuntu
---

### Post by SEECo on 2010-10-11
Hi want to create a partation and want to put my all important files in and then install ubuntu 9.10 in the default partation

---

### Post by celticbhoy on 2010-10-11
So, what is your question?

---

### Post by Rubi1200 on 2010-10-11
If you need more information, you need to be more specific please.

Here are some links that may help:
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

Hope this helps.

---

### Post by PapaNerd on 2010-10-11
> **SEECo said:**
> Hi want to create a partation and want to put my all important files in and then install ubuntu 9.10 in the default partation

Suggest you copy your important files to a separate disk drive or burn them to a CD or DVD first.  Then, when reinstalling, create a separate partition that you can use to backup the files in your /home directory tree.

---

### Post by SEECo on 2010-10-11
I wanted to put all of my important files in the other partation i want to create and then install ubuntu 9.04 in the default the ext4. Did you understanded .......

---

### Post by 23dornot23d on 2010-10-11
Show a screenshot of your existing partitions ...... use gparted just to have a look
and post the screenshot.

If you have a separate /home partition it makes it easier.

But its also possible to resize the existing partition and create a new one in the space
leaving your original safe ...... but as someone previously said ..... the best way to keep
your DATA safe is to back it up to another Drive ..... 

I use USB drives for backups ..... because they are reasonably cheap and easy to plug in and remove.

More information showing how your existing layout looks will help ......

---

### Post by bodhi.zazen on 2010-10-11
> **SEECo said:**
> I wanted to put all of my important files in the other partation i want to create and then install ubuntu 9.04 in the default the ext4. Did you understanded .......

We understand what you want to end with (basically a data partition).

We do not know where you are starting from. How many partitions do you have now ? Are you resizing a partition ? If so, is it a windows partition or linux partition ?

In general, boot a live CD and use gparted.

[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

Be sure you understand Lniux partitioning terminology

[HowTo: Partitioning Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=282018&highlight=partitioning") 

Then install Ubuntu into the target partition.

Note: In general, you need at least a / (root) partition and a swap partition.

---

### Post by SEECo on 2010-10-12
You are still not under standing here is a screenshot..... and make sure that you do not get fooled with the lower panel it is ubuntu 10.04 not vista

---

### Post by fatality_uk on 2010-10-12
I think I get it. Are you saying that you want to create a new partiton, but it doesn't give you the **New** option because that is greyed out?

---

### Post by celticbhoy on 2010-10-12
seeco if you want to re-partition the drive your ubuntu install is on then you will need to boot from a live disk first, and run gparted from there

---

### Post by bodhi.zazen on 2010-10-12
> **SEECo said:**
> You are still not under standing here is a screenshot..... and make sure that you do not get fooled with the lower panel it is ubuntu 10.04 not vista

It appears from the screen shot the partition is mounted. You can not resize a partition while it is mounted.

Boot a live CD and run gparted from there. If you are already on a live CD, unmount the partition.

---

### Post by SEECo on 2010-10-13
After unmounting what should i do....

---

### Post by bodhi.zazen on 2010-10-13
> **SEECo said:**
> After unmounting what should i do....

What is you plan ? How many partitions do you want ?

You then need to make space. You can do this either by deleting or making existing partitions smaller.

Often you need to do it in steps. Make a partition smaller -> apply changes -> make a new partition -> apply changes.

I would caution you, making changes without understanding the basics of partitions can result in data loss.

See if the following links help :

[http://ubuntuforums.org/showthread.php?t=282018&highlight=partitioning](http://ubuntuforums.org/showthread.php?t=282018&highlight=partitioning)

[http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)

You need to read the documentation and have a plan of action.

---

