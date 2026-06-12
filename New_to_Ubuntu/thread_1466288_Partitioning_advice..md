---
title: "Partitioning advice."
date: 2010-04-30
forum: New to Ubuntu
---

### Post by Paul T. on 2010-04-30
Hi,
I intend to do a clean install of Lucid and would like to know how to partition HD for optimal performance, for example ext3 or ext4?
Also how to create a seperate /home partition?
I read a thread somewhere (which I've now lost) that gave advice as to which side of the drive to create the partitions and in what order?

---

### Post by Ozymandias_117 on 2010-04-30
I would use ext4

Make / Partition 1

Make /home Partition 2

If you plan on ever making more partitions, make your swap space a logical partition, otherwise you can make it partition 3

Sizes depend on your hard drive size, how much ram you have etc. Rule of thumb, make swap 1 to 2 gigs, make / at least 10 gigs (All your installed programs will go there) and make /home whatever you have left

---

### Post by Paqman on 2010-04-30
> **Paul T. said:**
> 
I read a thread somewhere (which I've now lost) that gave advice as to which side of the drive to create the partitions and in what order?

On modern drives the location and positions of the partitions don't make any real difference. Older versions of Windows do like to be on the first partition IIRC, so if you're dual-booting you might want to taken account of that.

---

### Post by P4man on 2010-04-30
Hi.

For performance reasons, on a traditional harddrive its (slightly) better to have your partitions with files you will need often on the beginning of the disk (left side in partition editors) but really this is not a big concern.

You havent mentioned dualboot, so im assuming you;ll only need 1 OS. Then just boot from the cd or usb stick, and in the partitioning screen select **manual** (or is that"advanded", I forgot).

You will need to recreate 3 partitions if you want a separate /home.

First one mountpoint will be "/". This where the OS and most programs install. It needs at least 5GB, but depending how big your drive is, id give it at least 10-20. Ext4 is usually the fastest.

Then you need a /home partition. This is where user files go to. Again ext4 is probably your best bet

finally, a swap partition. Rule of thumb, 2x the amount of ram you have.

As to which goes where. It depends. If you are working often with large (user) files you might want to put your home partition first, on the fastest part of your hdd, but since it will also be the biggest partition and cover most of your disk, you wont see a big boost from this. If you are a "maniac: You can create a small "fast" home partition to the left and a bigger "slow" data partition more to the right, but you will be making life hard and see very little perceptible difference.

If you put the root partition first, it might help a bit in boot performance, but then again lucid boots so fast already and the difference wont exactly be stellar.

IOW, dont worry too much about the speed part of it, but you do have some control over it if you want.

---

### Post by srs5694 on 2010-04-30
> **Ozymandias_117 said:**
> I would use ext4

Make / Partition 1

Make /home Partition 2

If you plan on ever making more partitions, make your swap space a logical partition, otherwise you can make it partition 3

In theory, swap space is best placed in the middle of all your Linux filesystem partitions. This minimizes seek times to reach the swap space. In practice, I doubt if it makes much difference if you've got enough RAM, since swap isn't used much when you've got plenty of RAM. Whether it's primary or logical is irrelevant, at least in terms of swap performance.

---

### Post by Sealbhach on 2010-04-30
> **srs5694 said:**
> In theory, swap space is best placed in the middle of all your Linux filesystem partitions. This minimizes seek times to reach the swap space. In practice, I doubt if it makes much difference if you've got enough RAM, since swap isn't used much when you've got plenty of RAM. Whether it's primary or logical is irrelevant, at least in terms of swap performance.

Especially if you turn down swappiness from the default 60 to a more sensible 10 or 5 or even 1, like I have.:)

.

---

### Post by hortstu on 2010-04-30
This thread helped me immensely, and since one day you may want to try another OS I think it will help you too.

[http://ubuntuforums.org/showthread.php?t=1407147](http://ubuntuforums.org/showthread.php?t=1407147)

---

### Post by hortstu on 2010-04-30
maybe this one will help you too.

[http://ubuntuforums.org/showthread.php?t=1405365](http://ubuntuforums.org/showthread.php?t=1405365)

---

