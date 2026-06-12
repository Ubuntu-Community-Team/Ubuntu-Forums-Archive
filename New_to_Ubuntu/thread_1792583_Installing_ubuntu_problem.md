---
title: "Installing ubuntu problem"
date: 2011-06-28
forum: New to Ubuntu
---

### Post by anemone42 on 2011-06-28
I want to install ubuntu 11.04 from cd alongside windows 7.

I get to the choose partition screen, which looks like this.

                                                                   Size                Used
dev sda     
dev sda1        ntfs                                      314 MB          105 MB
dev sda2        ntfs                                      301501 MB    39823 MB
dev sda3        ntfs                                      16106 MB      13282 MB
dev sda4        fat32                                    2142 MB        32 MB

When I click Install Now, I get this error message.

No root file system is defined
Please correct this from the partitioning menu.

---

### Post by amjjawad on 2011-06-28
> **anemone42 said:**
> I want to install ubuntu 11.04 from cd alongside windows 7.

I get to the choose partition screen, which looks like this.

                                                                   Size                Used
dev sda     
dev sda1        ntfs                                      314 MB          105 MB
dev sda2        ntfs                                      301501 MB    39823 MB
dev sda3        ntfs                                      16106 MB      13282 MB
dev sda4        fat32                                    2142 MB        32 MB

When I click Install Now, I get this error message.

No root file system is defined
Please correct this from the partitioning menu.

You do have 4 Primary Partitions. You can't install UNLESS you delete one partition, create an Extended Partition and inside that extended one, you need to create minimum two other Logical Partitions.

---

### Post by Mark Phelps on 2011-06-29
You need to do the following BEFORE you attempt an install of Ubuntu ...

1) Use the Win7 Backup feature to create and burn a Win7 Repair CD.  This will allow you to repair the Win7 boot loader -- should it become corrupted during your Ubuntu install.

2) Use the Win7 Disk Management utility to shrink the Win7 OS to make room for Ubuntu.

3) Decide which existing partition you can afford to remove.  This will be really HARD, since my guess is that sda3 is your Recovery partition -- and if you remove that, you will no longer be able to restore Win7 to its original state.

---

### Post by anemone42 on 2011-06-29
I decided wubi was a better way for me. But thanks for the help!

---

### Post by amjjawad on 2011-06-29
> **anemone42 said:**
> I decided wubi was a better way for me. But thanks for the help!

All the best :)

---

