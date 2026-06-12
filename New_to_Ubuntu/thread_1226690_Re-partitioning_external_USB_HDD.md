---
title: "Re-partitioning external USB HDD"
date: 2009-07-29
forum: New to Ubuntu
---

### Post by mpjf01 on 2009-07-29
I have attached an external USB HDD that was formatted by my Topfield PVR. It is used to store recordings. Despite the fact that it is a 1TB drive it has been formatted to use only 500GB - presumably a characteristic of the PVR firmware.

According to Gparted the drive contains 4 partitions - 3 are jfs and 1 unknown. Sdb1 is jfs for PVR firmware upgrade purposes. The data appears to go in sdb2 - also jfs (but will not mount). Sdb3 purpose is unknown (not jfs) and the unused space has been allocated to sdb4 (along with some firmware configuration data). 

What I wish to do is to resize partitions 2 and 4 to move the unused part of the drive to partition 2 where hopefully the PVR firmware will allow it to be used. I had to install jfsutils to ungrey the Resize/Move menu item in Gparted. When I select any of the 4 partitions and then choose Resize/Move the maximum and minimum partition sizes show the same (the existing sizes) and won't allow alteration. As I have very little idea of what I am doing there may be something basic that I have overlooked here. Any help appreciated.

---

### Post by earthpigg on 2009-07-29
do you have somewhere available that you can back whatever is presently on the drive up to?

if not, i strongly advice against any partitioning whatsoever under any circumstances.

if you do, then you have nothing to lose by trying whatever partition scheme you wish with this pvr and seeing how it goes :D

---

### Post by mpjf01 on 2009-07-29
There's nothing (in the way of data) on the HDD that I wish to keep. The PVR seems to need whatever is in Partitions 1 and 3 so I would not wish to disturb these if at all possible. I can copy the P4 data back to it after the repartitioning process.

My problem seems to be that Gparted won't let me change any of the partition sizes. Do I have to delete a partition first - eg P4?

---

### Post by earthpigg on 2009-07-29
you need to unmount them first :D

click around, the option is there in gparted.

---

### Post by mpjf01 on 2009-07-29
P2 won't mount (and is unmounted), P4 is unmounted. The resize option is apparently available, it's just that the max and min sizes are each the same as the actual size and I can't alter any of them.

---

### Post by laffinet on 2009-07-29
To increase any partition you first have to free up space. This can be done by reducing the size of a partition and using that space or by deleting a partition altogether. 
Be aware that deleting a partition means you will loose any data in that partition.
If reducing the size of a partition is not available it might mean that that partition is full. What does gparted say ?
Can you post a screenshot or the output of "sudo fdisk -l"

---

### Post by mpjf01 on 2009-07-29
Unfortunately, see above, the option to resize any of the partitions is not available. I will delete p2 and p4 and try to create 2 new partitions of the appropriate sizes and see what happens. Thanks for the help.

---

### Post by laffinet on 2009-07-29
oops, just remembered: you can only increase the size of a jfs partition, not reduce it (bit of a quirk of that filesystem). That's why you don't get the option to reduce in gparted

---

### Post by laffinet on 2009-07-29
See here: [http://gparted.sourceforge.net/features.php]("http://gparted.sourceforge.net/features.php")

---

### Post by mpjf01 on 2009-08-01
It seems that the free space has to be adjacent to the partition you want to grow, so I had to delete P3 and P4, then grow P2 and then recreate p3 and 4 with smaller sizes. After much mucking about I have got it to work (got fouled up by default user not having enough power to do stuff). Thank you all for your help.

---

