---
title: "Can't Mount HPFS/NTFS drive"
date: 2010-06-16
forum: New to Ubuntu
---

### Post by jfluckey on 2010-06-16
[LEFT]When I search my Disk Utility, I see under peripheral devices my external hard drive. Under _Drive_ it is missing information in the "Location", Write Cache", "World Wide Name", and "Rotation Date".  Everything else is filled in (btw, Device: /dev/sdd).  Under _Volumes_, it is missing information for "Usage", "Partition Flags", and "Partition Label".  The partition type is listed as HPFS/NTFS (0x07) and the device is /dev/sdd1.

When I type 'blkid -o list', that path (/dev/sdd) is not present. How do I get my external drive mounted?

Thanks,
Juston
[/LEFT]

---

### Post by TeoBigusGeekus on 2010-06-16
Have installed ntfs-3g for ntfs support?

---

### Post by jfluckey on 2010-06-16
Synaptic tells me I have the latest version installed.

---

