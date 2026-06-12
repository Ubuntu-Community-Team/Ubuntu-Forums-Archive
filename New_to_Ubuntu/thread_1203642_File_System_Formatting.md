---
title: "File System Formatting"
date: 2009-07-03
forum: New to Ubuntu
---

### Post by ncc1701e on 2009-07-03
If I were to add an external USB hard drive to my Ubuntu 9.04 system what would be the best filesystem to format it as? It will only be for backup data.

---

### Post by steeleyuk on 2009-07-03
Are you going to use it with your Windows system?

If you are then FAT32 may be the best (except the issue with files >4GB), NTFS is also doable but some people occasionally complain of data loss (I do say occasionally).

If not, then take your pick of file systems. ext3 or ext4 would do nicely. Its also possible to access ext2 and ext3 filesystems in Windows using the ext2fs driver.

---

### Post by earthpigg on 2009-07-03
fat32 if you think you may need to read it on a windows computer.

otherwise: i'd go with ext3.

ext4 may not be readable on a linux system that hasn't been updated in a while (such as an 8.10 or earlier ubuntu live cd, for example).

---

