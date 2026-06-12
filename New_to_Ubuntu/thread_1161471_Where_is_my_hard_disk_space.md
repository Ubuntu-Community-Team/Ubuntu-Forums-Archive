---
title: "Where is my hard disk space?"
date: 2009-05-16
forum: New to Ubuntu
---

### Post by crank_it_up on 2009-05-16
My laptop has a 160GB SATA HDD. I had Vista installed and installed Ubuntu, I only have 143GB space on the filesystem.I'm curious, where is the other 17GB? Not sure what I did when I partitioned the disk installing, I was not trying to keep Windows so I probably reduced one of the bars to it's smallest possible length. Everything is working fine so I'm not bothered about it but I would like to know

---

### Post by Joeb454 on 2009-05-16
160GB is actually 149GiB :) So that looks about right actually.

Hard drives list space as GB, whereas the computer works in binary, which is GiB :)

[This link]("http://is.gd/AwOI") may help :)

---

### Post by larryfroot on 2009-05-16
To check your partitions and see if there is any unformatted space - which may account for your missing 17 Gb - try system > administration > partition editor. If its not there then 

sudo apt-get install gparted

in a terminal window.

When you open it (assuming you may have usb drives plugged in, make sure that the disk you are looking at is your internal hard drive rather than an external one. You can do this with the drop down menu on the top right of the app. 

It came in handy for me just the other day when I lost a good chunk of disk space after a re-install...if you do use it beyond just a fact finding mission handle with care. I once managed to wipe a load of good things from my ext drive by not double checking that the drive I was looking at was the one I wanted to format. Yes, I stood in teh corner with a dunces cap on my head. Deservedly.

---

### Post by jakupl on 2009-05-16
> **crank_it_up said:**
> My laptop has a 160GB SATA HDD. I had Vista installed and installed Ubuntu, I only have 143GB space on the filesystem.I'm curious, where is the other 17GB? Not sure what I did when I partitioned the disk installing, I was not trying to keep Windows so I probably reduced one of the bars to it's smallest possible length. Everything is working fine so I'm not bothered about it but I would like to know

Well one explanation is probably that cooperations name their units differently to make it sound bigger.

One REAL GB is 1024 MB, and this is how most programs in ubuntu count it. However the cooperations often pretend that one GB is 1000 MB.

As there was uncertainties about the units, a new unit came. KiB MiB and GiB.

To cut this short.
160 fake GB = 160000 fake MB = 152587.890625 REAL MB (MiB) = _149.01161193847656_ REAL GB (GiB) 

So you are not missing it, you never got it from the manufacturer... you have been cheated.
As for the rest, ext3 as far as I know, reserves some space for journaling.
So there you have it.

---

### Post by crank_it_up on 2009-05-16
Thanks for those replies. Why does ubuntu not use GiB as the unit when you check the disk space by right-clicking on 'filesystem' though?
I installed the partition editior and it shows 

/dev/sda1 146.10 GiB
/dev/sda2 2.86 GiB
/dev/sda5 2.86 GiB

---

### Post by SuperSonic4 on 2009-05-16
Dolphin (kubuntu file manager) says it in GiB (and my home directory has a nice 91.1GiB free)

What is the output of ```
sudo fdisk -l
``` (note that is a lower case l and not a 1 (one).

---

### Post by crank_it_up on 2009-05-16
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x47bb47bb



   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19084   153292198+  83  Linux
/dev/sda2           19085       19457     2996122+   5  Extended
/dev/sda5           19085       19457     2996091   82  Linux swap / Solaris
```

---

### Post by Joeb454 on 2009-05-16
> **crank_it_up said:**
> ```

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19084   153292198+  83  Linux

```

That is the line you want to look at.

With a rough calculation (it's listed in bytes) I work that out to be 146.19 GiB :)

---

### Post by jakupl on 2009-05-16
Well it seems as nothing is lost.
I forgot to mention that ubuntu altso needs some swap space, that's this:
/dev/sda5 2.86 GiB 

So to add it all up.

2,86 GiB (Swap)
_+ 146,10 GiB (/)_
= 148.96 GiB
= 159.94 (fake) GB

---

### Post by crank_it_up on 2009-05-16
Thanks for that everyone, I understand now.

---

### Post by drs305 on 2009-05-16
Arrived late to the party, but the link to "Recover Lost Disk Space" in my signature line explains it and also gives commands for researching such problems.

---

