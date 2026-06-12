---
title: "Partition question"
date: 2009-02-22
forum: New to Ubuntu
---

### Post by mrmcwn on 2009-02-22
I appear to have 2 partitions running different versions on 2 partitions. I am trying to set up one main partition of 20GB, and a 'file' partition of 10GB for storing media, etc. Vice versa would be fine. Just looking for the easiest solution. Any ideas?

I have 2.6.22 in the boot on sda1, and 2.6.24 in boot on sda6.

fdisk:
Disk /dev/sda: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcc17cc17

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1144     9189148+  83  Linux
/dev/sda2            1145        3648    20113380    5  Extended
/dev/sda5            3556        3648      746991   82  Linux swap / Solaris
/dev/sda6            1145        3462    18619272   83  Linux
/dev/sda7            3463        3555      746991   82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by kestrel1 on 2009-02-22
You have two swap partitions that are not really needed you only need one of them.
I would suggest that you have 10gb for the system & nearly 20gb for the /home partition & a small amount for swap 1 to 2gb should be fine.

---

