---
title: "Installing 8.10 64Bit on 1.7TB RAID 5 hangs at partitioner"
date: 2009-02-25
forum: New to Ubuntu
---

### Post by Falanx on 2009-02-25
Good morning,

I've been trying, and failing to set up a nice, new dual boot on a new RAID 5 array build from 4× Western Digitial 640GB Caviar Black, on AMCC/3Ware 9590SE 8ML.

Initial installion of Vista 32bit (the games drive) on the 180GB first partion went smooth and trouble free, as did the initial stages of installation setup of Ubuntu.

The partioner starts up and to preserve the Vista partition, Ubuntu is to be installed on the next contiguous space, which is essentially an uninterrupted ~1.6TB partition. The setup of that goes smoothly too, until the installe rmoves onto formatting the partition for ext3. 

I appreciate that 1.6TB is a big partition to format, so it's a little difficult to see at what point the hanging *actually* occurs, but the progress bar never shifts from 5% done.

The rest of the system is built around an ASUS A32SLI deluxe board, AMD64 4200+ X2 oc'ed mildly to 2.42GHz, and Corsair TwinX2048-4400 running at 500MHz.

Any ideas?

---

### Post by blueridgedog on 2009-02-27
When you reboot has the partition been created?

Perhaps you can try manually making them them with fdisk (advanced - so beware if you are new).

Also, did you install special drivers in Windows to see the array?

---

