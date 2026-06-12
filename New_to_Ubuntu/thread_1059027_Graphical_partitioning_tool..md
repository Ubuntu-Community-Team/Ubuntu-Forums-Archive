---
title: "Graphical partitioning tool."
date: 2009-02-03
forum: New to Ubuntu
---

### Post by melrokz on 2009-02-03
Hi! I need a graphical GUI partitioning tool for creating Ext3 and NTFS partitions. 
I also suggest that the gnome partition editor be included in the Ubuntu CD instead of being a download via apt, since the Live CD can be used to format the HDD partitions without installing Ubuntu.

---

### Post by Tomatz on 2009-02-03
> **melrokz said:**
> Hi! I need a graphical GUI partitioning tool for creating Ext3 and NTFS partitions. 
I also suggest that the gnome partition editor be included in the Ubuntu CD instead of being a download via apt, since the Live CD can be used to format the HDD partitions without installing Ubuntu.

```
sudo apt-get install gparted
```

Its on the live cd also ;)

---

### Post by mlentink on 2009-02-03
> **melrokz said:**
> Hi! I need a graphical GUI partitioning tool for creating Ext3 and NTFS partitions. 
I also suggest that the gnome partition editor be included in the Ubuntu CD instead of being a download via apt, since the Live CD can be used to format the HDD partitions without installing Ubuntu.

Huh??

GParted ***is*** a gui partitioning tool, and ***is*** included in both the installed version and the LiveCD...

Maybe I misunderstood?

---

### Post by minsf on 2009-02-03
when booting from a live cd, go to System>Administration>PartitionEditor and this is exactly gparted. 
it is not installed by default on the HDD, probably because they didnt want people to "accidently" use this and break their system. Also, you have to be sure that you unmount the drives that you want to partition- so that running gparted from HDD makes sense only if you want to partition an external hdd. it makes more sense to run it from a live cd, when the HDD is not mounted.

---

