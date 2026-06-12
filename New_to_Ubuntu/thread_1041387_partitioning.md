---
title: "partitioning"
date: 2009-01-16
forum: New to Ubuntu
---

### Post by Aksha on 2009-01-16
ok i am using live cd 8.10 and i am using the desktop installer im currently at the manual prepare partitions screen, what should i do now? should i make a new partition table?
 
This is what i see

fat32 2%
ntfs 97%

/dev/sda
  /dev/sda2 fat32
  /dev/sda1 ntfs

i want to setup for linux and windows xp i currently have windows xp installed

---

### Post by nhasian on 2009-01-16
first you need to make some room to install linux.  boot off the LiveCD and after ubuntu loads go to System->Administration->Partition Editor and shrink FAT32 or NTFS partition to make some empty space on the drive to install ubuntu to.  detailed instructions here:

[http://www.psychocats.net/ubuntu/dualboot](http://www.psychocats.net/ubuntu/dualboot)

---

