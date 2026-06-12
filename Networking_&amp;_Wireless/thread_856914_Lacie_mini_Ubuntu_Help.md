---
title: "Lacie mini Ubuntu Help"
date: 2008-07-11
forum: Networking &amp; Wireless
---

### Post by trout256 on 2008-07-11
Ok, here's the problem:

Lacie mini 500GB network disk will not turn on. Dead power supply - I do not have another one - unit is out of warranty.

Took it apart, there is a 500GB Seagate HD in there.

Installed that into an Ubuntu 8.04 box. Ubuntu automatically pulls-up two partitions of the Lacie HD, but not the big portion (465 GB) that I need to get to. Using System->Administration->Disks I see the 465 partition listed, but it says "Innaccessible" - why? I just am not familiar enough with Linux to know what to do next to get at the data that is saved on the 465 GB part.

I am thinking that maybe since the 500GB drive was a network drive, that the embedded linux (ELDK I think I read somewhere) in the Lacie hardware did something to the 465GB partition or part (or share) of the drive so that Ubuntu doesn't see it? I don't know - hopefully someone can help with this!

Thanks for any help!
trout256

---

### Post by attle on 2008-08-03
Lacie put XFS file system on the ethernet disks. Make sure you have XFS support installed on your ubuntu.

By the way, the PSU usually is a standard +5, +12 with common ground. 

My PSU broke down on my lacie so I took an USB to SATA cable PSU and connected it to the last piece of the cable ( ie the part going in to the disk). You can see on the lacie psu the assignments of the pins.

---

