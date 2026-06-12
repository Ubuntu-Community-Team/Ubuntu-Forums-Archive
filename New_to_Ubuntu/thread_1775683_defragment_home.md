---
title: "defragment /home ?"
date: 2011-06-05
forum: New to Ubuntu
---

### Post by neil_1 on 2011-06-05
Here is a picture of the existing partitions i have

I want to allocate more space to Shared partition(sda4,ntfs) from /home (sda7,ext4)
how do i defragment /home to allocate ~30 gb to Shared ?
also,by doing this will data from any of the partitions get corrupted by any chance ?
if not , how do i go about it ?

---

### Post by redbook4574 on 2011-06-05
Linux is not windows, you do not need to defrag the partition. I would suggest using a tool such as gparted to shrink your home partition and move the result to your shared partition.
Make sure you back up first although I have never had any issues doing this and partition changes carry an element of risk.

---

### Post by coffeecat on 2011-06-05
First, you don't have to defragment /home. It's an ext4 partition. Linux filesystems are not prone to (significant) fragmentation until more than about 90% full. I think you may be thinking of the common advice to defragment Windows C: partitions before resizing them. That is sensible because Windows the Windows NTFS filesystem tends to fragment files much more.

What you want is doable but slightly complicated by the fact that your sda7 home partition is a logical one and the sda4 Shared partition is a primary. Fortunately they are adjacent, which makes the task possible.

In outline, what you have to do is to boot the live Ubuntu CD and use Gparted. You won't be able to do what you want to do from within your permanent installation using Disk Utility (or Gparted for that matter). Once you've booted the live CD and opened Gparted, you need to right-click on the sda6 swap partition and choose "swapoff". This will unlock the extended partitition (which I assume will be sda3). Then shrink the extended partition by the amount you want to transfer from home to Shared. Now shrink your sda7 home partition by the same amount. Finally, enlarge sda4 by that amount.

Before you start, I suggest you boot the live CD and post a screenshot of Gparted so that we can double-check that my assumptions about partition numbers are correct. A Disk Utility doesn't show all the information that Gparted does. Then we can see if there are any other potential problems.

---

### Post by neil_1 on 2011-06-07
sorry for late reply
here is the image

---

### Post by coffeecat on 2011-06-07
Hi. First my apologies. I made a careless error in my previous post here:

> **coffeecat said:**
> Then shrink the extended partition by the amount you want to transfer from home to Shared. Now shrink your sda7 home partition by the same amount. 

That's the wrong way round. You need to shrink sda7 before you can shrink the extended partition. What you need to do from Gparted in the live CD, is:

1 - Right-click on swap and choose 'swapoff'.
2 - Shrink sda7,
3 - Shrink sda3, the extended.
4 - Enlarge sda4 to the left.

I've left out the details of using Gparted. When you want to resize a partition, highlight it by clicking on it, then choose Resize/Move from the Partition menu. You can type figures in the three boxes but much simpler is to drag the right or left margins as appropriate of the box representation of the partition just above the three number fields. Post back if you need help.

CAUTIONARY WARNING. Manipulating partitions has the potential for things to go wrong. When things go wrong when you are resizing partitions, they go wrong spectacularly badly. Backup as much as you can before you start. Also, resizing partitions can take a long time. Enlarging the sda4 NTFS partition is likely to take the longest. Expect hours rather than minutes.

---

### Post by neil_1 on 2011-06-08
hi coffeecat,
im a bit confused here,
why do we need to hit swapoff ,and what will it do ?
also
the shared partition is ntfs,i used it under linux though,will it be fragmented ?

---

### Post by coffeecat on 2011-06-08
> **neil_1 said:**
> why do we need to hit swapoff ,and what will it do ?

When you boot up a live CD it will automatically enable swap in any swap partition it finds. If the swap partition, which is a logical partition in your extended partition, is enabled this locks the extended partition so that you will not be able to resize it. Since resizing the extended partition is one of the steps you need to take, selecting swapoff is essential. This is a common catch when people try to resize partitions using Gparted from the live CD and they wonder why they can't resize a partition.

> **neil_1 said:**
> the shared partition is ntfs,i used it under linux though,will it be fragmented ?

Your NTFS partition will most likely be fragmented but I believe this should not be a problem since you are enlarging it. It can become an issue when you shrink a fragmented NTFS partition.

---

### Post by neil_1 on 2011-06-08
i am not running ubuntu on a live disc, i have installed gparted ,do i still need to swapoff ?

---

### Post by Paqman on 2011-06-08
> **neil_1 said:**
> i am not running ubuntu on a live disc, i have installed gparted ,do i still need to swapoff ?

You need to be running from a Live CD. You can't modify any partitions that are in use, such as /home. If you boot into a Live CD and swapoff, then no partitions on your disk are mounted and you can make all the changes you want.

---

### Post by coffeecat on 2011-06-08
> **neil_1 said:**
> i am not running ubuntu on a live disc, i have installed gparted ,do i still need to swapoff ?

> **Paqman said:**
> You need to be running from a Live CD. You can't  modify any partitions that are in use, such as /home. If you boot into a  Live CD and swapoff, then no partitions on your disk are mounted and  you can make all the changes you want.

+1. @neil_1, this is important. You probably missed this in an earlier post:

> **coffeecat said:**
> In outline, what you have to do is to boot the live Ubuntu CD and use Gparted. **You won't be able to do what you want to do from within your permanent installation using Disk Utility (or Gparted for that matter).**

---

### Post by neil_1 on 2011-06-12
alright, i'll backup my stuff and try it in a few days and post back :)

---

