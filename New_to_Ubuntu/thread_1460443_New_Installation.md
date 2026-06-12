---
title: "New Installation"
date: 2010-04-22
forum: New to Ubuntu
---

### Post by fugaki on 2010-04-22
I am setting up a new server, and I am having a little trouble.

I have two 1.5 TB WD drives I put in, and I set my raid controller to RAID 0 (mirroring), and when I try to partition and format the drives, the partitions get created, and the swap partition is complete, but the ext4 partition never formats.

Partition table is 12.2 GB swap primary, logical partition of the rest
(installer estimates it to 1.5 TB)

I just deleted the array, and I set up a new partition table using the two disks
15 GB swap
~1.5 TB / ext4
1.5 TB /audio ext4

And I am running into the same problem.

I am going to try next to exactly specify the partition size for the disk holding the swap area, and see if it solves this, but is there anything I need to know about formatting drives this large?

Ext4 is supposed to work with up to 16 TB...

This is my first time using a disk this large, every other server I have set up has user 320-500 GB drives, and the formatting process took no time, so waiting over an hour I called it thinking it had frozen.

Any ideas?

--EDIT

I tried specifying manually the exact size and I ended up with the same problem...

Found the problem, the raid controller only supports drives up to 500 GB...

lame...

---

