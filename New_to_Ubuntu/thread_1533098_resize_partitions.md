---
title: "resize partitions"
date: 2010-07-17
forum: New to Ubuntu
---

### Post by rburkartjo on 2010-07-17
note need to resize some partitions they have the lock key on them how do i proceed/tks

---

### Post by linuxman94 on 2010-07-17
You need to unmount the partitions you wish to resize. To do that, right click on the partition and click unmount.  Remember to backup important data first!!  IF you want to resize your ubuntu partitions, you will need to boot from a live cd.

---

### Post by Rubi1200 on 2010-07-17
Only use the LiveCD to work with partitions!

Also, you will need to right-click on the swap partition and select Swapoff.

---

### Post by Elfy on 2010-07-17
> **Rubi1200 said:**
> Only use the LiveCD to work with partitions!

Also, you will need to right-click on the swap partition and select Swapoff.

While this would be true if working with / it's not necessarily true that you can only work on partitions from a livecd.

---

### Post by Rubi1200 on 2010-07-17
> **forestpiskie said:**
> While this would be true if working with / it's not necessarily true that you can only work on partitions from a livecd.

I stand corrected. 

I was just being cautious because the OP does not say what partitions he wants to resize.

---

### Post by rburkartjo on 2010-07-17
for tks that is what i thought also

---

### Post by Elfy on 2010-07-17
> **Rubi1200 said:**
> I stand corrected. 

I was just being cautious because the OP does not say what partitions he wants to resize.

Nothing wrong with being cautious in a partitioning thread :)

---

### Post by techunit on 2010-07-17
Hey I have a video covering Partitioning in Gparted.... It is a basic tutorial covering the different things that you can do in gparted. [http://ubuntuvideotutorials.wordpress.com/install-ubuntu/guide-to-partitioning/](http://ubuntuvideotutorials.wordpress.com/install-ubuntu/guide-to-partitioning/)

---

### Post by rburkartjo on 2010-07-17
boot / is on dev/sda1 ext 4  31.25 gb
/home is on dev/sda4 ext 4 26.20gb

i have unallocated 234.38gb

i want to increase / to 82gb
/ home to 80gb

how to i proceed

---

### Post by rburkartjo on 2010-07-17
note the balance will just be used as a ext4 partition for whatever

---

