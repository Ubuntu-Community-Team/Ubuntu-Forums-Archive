---
title: "What happens if my main drive dies?"
date: 2020-05-04
forum: Networking &amp; Wireless
---

### Post by josephchrzempiec on 2020-05-04
Hello I have ubuntu 20 latest. I have setup 4 drives as a file sharing drives. Two of them are in raid 0 for mirroring and the other two drives are setup in raid 0 morning also. All drives are in software raid. The problem I’m facing dense I don’t. Have any more SATA ports to put a redundant drive on the main drive what happens if my main drive dies, Do I lose the raids on all drives can they be recovered if I put in a new main drive? I just don’t want to lose what I have if the main drive fails.


Joseph

---

### Post by CelticWarrior on 2020-05-04
[https://en.wikipedia.org/wiki/Standard_RAID_levels#RAID_0](https://en.wikipedia.org/wiki/Standard_RAID_levels#RAID_0)

---

### Post by josephchrzempiec on 2020-05-04
Hello thank you for that. But. I understand what happens in a raid but I&#8217;m wondering if the main drive drives what happens to the raid drives once I replace the main drive with a new one? Is the raid of the other drives are still intacted or I lose everything?

---

### Post by SeijiSensei on 2020-05-04
If the drive with the root filesystem is separate from the arrays, they won't be affected by its replacement.  I've moved arrays between machines without a problem.

I think being concerned about the integrity of your arrays and choosing RAID0 is a bit contradictory.

---

### Post by josephchrzempiec on 2020-05-04
I&#8217;m sorry it&#8217;s raid 1 for redundancy not raid 0. I was refereeing to.


Joseph

---

### Post by josephchrzempiec on 2020-05-04
Hello thank you. I&#8217;m just worried that my kids pictures and homemade movies of my kids growing up will be gone if I lost the main drive.


Joseph

---

### Post by CelticWarrior on 2020-05-04
To avoid losses you should have backups.
RAID is no substitute for backups.

---

### Post by TheFu on 2020-05-04
> **CelticWarrior said:**
> To avoid losses you should have backups.
RAID is no substitute for backups.

+1000.   There are many failures that raid1 doesn&#8217;t handle where only wiping and a fresh restore from backups is required.
Backups are always necessary.

I've also moved SW-RAID arrays between systems with little issues. Even changed disk controllers a few times.

---

### Post by Tr1p on 2020-05-21
You can always clone your main disk with dd

---

### Post by kurt18947 on 2020-05-21
> **josephchrzempiec said:**
> Hello thank you. I’m just worried that my kids pictures and homemade movies of my kids growing up will be gone if I lost the main drive.


Joseph
For irreplaceables like this, I'd want more than one backup, perhaps one in the 'cloud'.

---

