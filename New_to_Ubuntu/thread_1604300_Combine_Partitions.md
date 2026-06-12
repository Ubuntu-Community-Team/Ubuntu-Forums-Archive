---
title: "Combine Partitions"
date: 2010-10-23
forum: New to Ubuntu
---

### Post by Melon Bread on 2010-10-23
I had a Dual Boot of Windows 7 and Ubuntu 10.10, but I decided to go full on Ubuntu.
So i deleted the windows partition and now I want to combine it with my Ubuntu side.
I am not a 100% sure of going about it. Here is how it is set up:
[IMG]http://i53.tinypic.com/oktp9f.png[/IMG]

I am in the live CD of Ubuntu 10.4 using GParted


Thank you

---

### Post by marshmallow1304 on 2010-10-23
First unmount (right-click, unmount in GParted) /dev/sda5, then right-click on /dev/sda6 and click swapoff, then umount /dev/sda2.  Then, you can right-click /dev/sda2 and click Resize/Move.  Drag the left slider all the way to the left.  Then do the same with /dev/sda5.  When you've got it all set up, click the Check to apply.  Since you're expanding a partition to the left, this will take a while; all the data will have to be moved from the beginning of the current partition to the beginning of the new partition.

If this is a laptop, remember to check the Power Settings to make sure it won't suspend if you close the lid (been there - no fun).

---

### Post by Melon Bread on 2010-10-23
Ah thank you this worked, it is now doing its thing.
And thanks for the tip about the laptop (even though I am not on one) it is still good advice for the future :)

---

### Post by Melon Bread on 2010-10-23
Quick question: how would I go about making a second smaller partition from my sda5 to be able to boot into another linux distro via GRUB?



EDIT: Sorry Double Post

---

### Post by marshmallow1304 on 2010-10-23
You would shrink the partition on either side (right would be faster) then right-click the unallocated space and create a new partition.

---

