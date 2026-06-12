---
title: "Difference between GParted and Gnome DU"
date: 2009-04-02
forum: New to Ubuntu
---

### Post by Michael Dooley on 2009-04-02
I have a screenlet called Sysmonitor running on my desktop that displays the partitions mounted and, presumably, the percentage of each that is used. /dev/sda6 (my file system) displays a usage of 11%. /dev/sda8 (my home partition) displays a usage of 24%. 

Gnome disk usage reports that my total sda6 filesystem capacity is 40.3 GB and that 36.1 Gb of that is available. Gnome du also reports that my total sda8 home capacity is 29.3 GB and 22.6 Gb of that is available. Gnome Disk Usage appears to roughly agree with the Sysmonitor screenlet.

However, if I start GParted, it reports something entirely different for my sda6 filesystem partition. GParted says that sda6 is 55.39 GiB of which 19.28 GiB is used leaving 36.11 GiB unused. Sda8 is 29.52 GiB of which 6.87 is used leaving 36.11 GiB unused. It appears as if the sda8 partition is being described as agreeing with what Gnome du reprts but the sda6 partition has a great deal more capacity *and* usage than is being reported by Gnome Disk Usage - 15.9 GiB more capacity and 15.08 GiB more usage of the filesystem partition.

What accounts for the discrepancy in the reports from GParted and Gnome Disk Usage as far as my root partition? 

Obviously I wouldn't arrange my partitions relying on Gnome to be accurate but I'd like to know what's going on with my system.

---

### Post by SunnyRabbiera on 2009-04-02
The gnome disk usage application and gparted use different methods of seeing the contents of a hard drive from what I undertstood, gparted tends to be more accurate.
I heard its how the modules are set up that makes them different.

---

### Post by Michael Dooley on 2009-04-02
Thanks for the reply SunnyRabbiera.

Are there other ways of determining the actual disk usage?

Does anyone have any idea why both the total system disk amount and the usage amount reported by GParted varies by almost the same (if not the same) value from Gnome du? It's as if something is present that Gnome Disk Usage doesn't detect or is not concerned with. When it comes to determing the volume of a partition, this kind of discrepancy is not just funny, but creepy.

I hope someone comes along to shed more light on this.

---

