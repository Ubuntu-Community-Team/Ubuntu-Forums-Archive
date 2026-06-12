---
title: "no root file system is defined"
date: 2009-06-24
forum: New to Ubuntu
---

### Post by maverick_doc on 2009-06-24
"no root file system is defined" this is the message that pops up when trying to install ubuntu.
i am running the machine having Win XP Professional and was trying to install in a vacant partition.
please help

---

### Post by MuH4hA on 2009-06-24
When editing the partition table, you have to select the mount point
" / " (root) for one partition.

This partition should be formatted with ext3 - NTFS or FAT won't work.

---

### Post by tarps87 on 2009-06-24
It can also be formatted to any of the ext family (ext2,ext3,ext4)
ext4 'out of the box' support what introduced in Jaunty 9.04

---

