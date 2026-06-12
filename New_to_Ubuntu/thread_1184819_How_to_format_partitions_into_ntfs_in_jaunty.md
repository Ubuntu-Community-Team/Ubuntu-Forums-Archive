---
title: "How to format partitions into ntfs in jaunty?"
date: 2009-06-11
forum: New to Ubuntu
---

### Post by ravi_buz on 2009-06-11
Ha i i just installed ubuntu again and what to have 3 logical partitions in NTFS format.But when i opened gprted it says that my disk does not support ntfs.But thats not true i had windows in it once.I also check my ntfs 3g version and its latest.So what should i do to create a ntfs partition

---

### Post by synapsys on 2009-06-11
Open a terminal and type:

```
sudo apt-get install ntfsprogs
```

Then gparted will have the tools it needs to manipulate ntfs partitions.

---

### Post by 4Orbs on 2009-06-11
The most recent PartedMagic live cd is especially nice. You can find the download link at distrowatch.com and it includes the latest gparted. A must-have tool in my opinion.

---

### Post by ravi_buz on 2009-06-11
Thanks A Lot :KS:KS:KS

---

