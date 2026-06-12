---
title: "Re-installing Ubuntu"
date: 2009-12-17
forum: New to Ubuntu
---

### Post by joolz1234 on 2009-12-17
My harddisk is partitioned as follows: A small partition for the bootloader, about 100 Gb for Windows 7 and about 90 Gb for the Ubuntu OS. Then there's 13 Gb for swap and roughly the same amount for ext. I'm trying to reinstall Ubuntu, but the installer side-to-side configuration leaves me with a smaller windows and *two *small Ubuntus. Should I proceed manually and delete ALL the existing ubuntu partitions?

---

### Post by Bigtime_Scrub on 2009-12-17
> **joolz1234 said:**
> My harddisk is partitioned as follows: A small partition for the bootloader, about 100 Gb for Windows 7 and about 90 Gb for the Ubuntu OS. Then there's 13 Gb for swap and roughly the same amount for ext. I'm trying to reinstall Ubuntu, but the installer side-to-side configuration leaves me with a smaller windows and *two *small Ubuntus. Should I proceed manually and delete ALL the existing ubuntu partitions?



If you want a fresh install of Ubuntu I would delete the partition it is on and when I would go through the install, on the partition set up I would tell it to use "all continuous free space". Also, I doubt you really need 13 gigs of swap space, really you only need what is equal to your RAM but to each his own.

Just be sure when you delete the Ubuntu partition you leave the Windows one alone. I'd hate to see disaster strike.

---

### Post by bodhi.zazen on 2009-12-17
Use manual partioning and select the existing partitions (you do not need to delete them).

---

