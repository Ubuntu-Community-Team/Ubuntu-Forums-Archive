---
title: "Need all kinds of help!"
date: 2009-10-29
forum: New to Ubuntu
---

### Post by shadowhawk2020 on 2009-10-29
So after avoiding Linux like the plague, I decide I want to dual boot Ubuntu and Windows XP.  So, I print a how to, and watch a video on the subject.

The video shows an option for side by side install, which was not an option when I went through the install process.  So I went to the step by step printout, which told me to change the size of the partition I wanted to use.  I only have one harddrive split into two partitions.  The second partition is 60 GB, I changed the size of the partition to 25GB and hit next.  The next thing I know, I have a 25gb  partition, and 35gb of unallocated unusable space.  

I cannot get any program to reallocate that space.

So two questions::

1.  Does anyone have a working guide for ubuntu dual boot

and

2.  How do I get my 35GB back?

---

### Post by autocrosser on 2009-10-29
1. The 60G is separate to your "normal" XP install--Yes?
2. What "side by side" tutorial did you use?
3. I normally install the / (root) system to it's own partition & /home (user's folder) on a separate partition & you will need to add a swap partition--So..
4. When you get to the partitioner--you will need to do manual partitioning--keep the 25G you have made as your / partition--click on the "unallocated" space & use 32G of it for your /home & then click on the remaining 2G--set it up as swap

The new tutorial is not ready yet (as far as I know), but the older one for 9.04 will give you a better idea... [https://help.ubuntu.com/9.04/installation-guide/i386/index.html](https://help.ubuntu.com/9.04/installation-guide/i386/index.html)

More questions--PM me--I'm around the forums most evening Pacific time.

---

### Post by Technoviking on 2009-10-29
Sounds like you shrunk your 60GB Windows partition to 25GB. Just install Ubuntu in that 35GB of unallocated space.

T-V

---

### Post by The Cog on 2009-10-30
> **Technoviking said:**
> Sounds like you shrunk your 60GB Windows partition to 25GB. Just install Ubuntu in that 35GB of unallocated space.

T-V

Agreed - so now you have two partitions:
C:  Unknown size
D:  25G
and 35G un-allocated. 

You can just tell the installer to use the unallocated space - it will make its own partitions in the 35G unallocated part. If you feel you want D: to be bigger, you can probably re-size it again with the installer - I would suggest leaving 10G unallocated for Ubuntu, so D: could go up to around 50G.

---

