---
title: "Dual boot, two partitions"
date: 2009-03-11
forum: New to Ubuntu
---

### Post by saltytheseadog on 2009-03-11
I have an acer laptop I would like to dual boot. The hard drive is partitioned into C: and D: of 60 Gb each.The D: is completely empty except for 1 Mb which is hidden and may be recovery files or something vital to the machine. I was installing Ubuntu and when I got to the page where the partitions are formatted and it had seemed to automatically formatted just the way I would have liked it ,with ubuntu taking all but 1% of the D partition.I however backed down from the installation at the last page when I was warned that any data on the drives that were being formatted would be lost. Anyone with experience with this type of configaration?

---

### Post by x33a on 2009-03-11
you should format the whole d drive. i don't think that 1 mb is for recovery, might be system volume information or something like that. it shouldn't affect windows imo.

---

### Post by mlentink on 2009-03-11
Actually, there's no such thing as a 'D:-drive', that is simply the way the Windows filesystem designates a partition. Fire up the LiveCD and unmount all partitions on your internal disk, delete the second partition (which should be empty, your 'D:-drive'). 
Then start the installer and let Ubuntu use the largest empty space to install in.
Before you make any changes to partitions, it is always a good idea to back up your data.

see also: [https://help.ubuntu.com/8.10/switching/installing-partitioning.html](https://help.ubuntu.com/8.10/switching/installing-partitioning.html)

---

