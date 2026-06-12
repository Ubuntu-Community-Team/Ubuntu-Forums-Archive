---
title: "Can I enlarge my Mint 7 partition?"
date: 2009-10-11
forum: New to Ubuntu
---

### Post by SonicMonkey on 2009-10-11
I installed Mint 7 just for the fun of it, with hopes to someday uninstall it and use Vista again. Now that I can't see that happening, I want to expand my Mint 7 partition to around 60 GB. I went into GParted and unmounted the drive that has Vista on it, shrank that volume down by about 50 GB, and now I can't expand my Mint 7 Partition! Do I have to format Mint 7 and resize the partition in order to make it bigger, or can I get around that somehow?
Aside from that point, I've already cut the 50 GB out of the Vista partition (but had to unmount the drive) and after I did that, I can't mount the drive or anything. It's like Gloria thinks it's broken or something, but I can run Vista fine. Right now I'm putting that partition back into it's original size in hopes I can mount it again, but I'd really like to have my Mint partition bigger.

Thanks in advance,
Dan

---

### Post by tuxxy on 2009-10-11
You should be able toe expand the partition in gparted just as you shrank the Vista partition.  Use the graphical tool at the top if your unsure, you can simply expand it by dragging.  Obviously you will need sufficient free space on the drive to expand the partition.

---

### Post by beastrace91 on 2009-10-11
You will need to run gParted from a livecd to change the size of your Mint partition. This is because you can not edit mounted partitions.

~Jeff

---

### Post by SonicMonkey on 2009-10-11
How can I obtain/make a live CD? Is it the same as the CD I made to install Mint 7 in the first place?

And since I'm putting the rest of the unallocated memory back in the Vista partition, can I cancel that operation without any information loss to save some time?

---

### Post by tuxxy on 2009-10-11
> **SonicMonkey said:**
> How can I obtain/make a live CD? Is it the same as the CD I made to install Mint 7 in the first place?

And since I'm putting the rest of the unallocated memory back in the Vista partition, can I cancel that operation without any information loss to save some time?

The LiveCD refers to the testmode on ubuntu CD.  It should say something like try ubuntu without any change to your computer.  This load all files from CD and does not require a hard drive.

[https://help.ubuntu.com/community/LiveCD](https://help.ubuntu.com/community/LiveCD)

---

### Post by y6FgBn)~v on 2009-10-11
I believe gparted is included on the Mint LiveCD.

---

### Post by SonicMonkey on 2009-10-15
Not really problem solved, because when I tried to put the unallocated HDD space back into my Vista partition, my computer complained about missing a BOOTMGR.EXE so I just reformatted to factory defaults. Two hours later I found my LiveCD.

---

