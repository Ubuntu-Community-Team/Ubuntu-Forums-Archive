---
title: "Resize partitions"
date: 2009-05-01
forum: New to Ubuntu
---

### Post by rgotten on 2009-05-01
I have 3 500 gb hard drive on software raid with the following configuration, a primary partition with raid 1 of 125 MB where I have the boot. Then I have an extended partition of 465 gb where had 3 raid, one is raid 1 2 gb for swap, one raid 5 for system of 10 gb, and the rest for data is a raid 459 gb. I was trying to resize the boot area for a bigger size, but it is saying me that there is not enough space. I shrink the data raid 5, but still the boot area is saying that there is  not enough space to increase the size, I am wondering if this is related to the primary partition and extended partition, any help will be appreciated

rgotten

---

### Post by drs305 on 2009-05-01
I don't run a RAID setup but in general you cannot take space from an extended partition or logical partition and give it to a primary partition. You first have to shrink the extended partition (and a logical partition within it if there is no existing free space). Once that free space is outside the extended partition and adjacent to a primary partition it can be incorporated.

---

### Post by rgotten on 2009-05-01
Thanks, guess i will have to dreformat everything and reisntall everything....

---

