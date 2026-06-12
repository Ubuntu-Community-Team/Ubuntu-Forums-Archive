---
title: "Problem Installing Ubuntu"
date: 2009-05-18
forum: New to Ubuntu
---

### Post by Jamiesonbrady on 2009-05-18
I recently completely deleted Windows off of my computer in attempt to install Ubuntu. My computer has a single 750 GB hard drive. When i try to partition Ubuntu onto the entire disk, the partition reaches about 5% then it doesn't really do anything from that point. I tried several times and let it sit for around 8 hours and it still didn't pass 5%. I re-tried, this time designating only 100 GB of my hard drive to Ubuntu, and the installation was successful, so i know that my CD works. Is 750 GB too much for the operating system?  Or should i break it up into multiple partitions? I'm not really sure what to do because i want to utilize my hard drive as efficiently as possible.

---

### Post by nhasian on 2009-05-18
from your description it sounds like you have a bad hard disk.  for example you were able to partition the first 100 gigs, but you were unable to partition the entire drive so there must be some bad sectors after the 100 gig mark.

---

### Post by Jamiesonbrady on 2009-05-18
Well if my hard drive was corrupted that would suck, considering i bought my computer brand new only 8 months ago.

---

### Post by Jamiesonbrady on 2009-05-18
Does it normally take a very long time to install Ubuntu onto large hard drives?

---

### Post by SunnyRabbiera on 2009-05-18
> **Jamiesonbrady said:**
> Does it normally take a very long time to install Ubuntu onto large hard drives?

It can take a while, the larger the drive the longer the install.

---

### Post by ramjet_1953 on 2009-05-18
Hi, there!

Firstly, before starting the install, did you check the integrity of the install disk?

This can be done by booting with the disk and selecting the check disk option.

If all is OK with the above, it may be a good idea to download a stand-alone iso of Parted Magic 4, burn the iso to CD and then try partitioning your HDD.

You can get the image from here:

[http://partedmagic.com/download.html](http://partedmagic.com/download.html)

Don't forget that when burning an iso image to disk, do it SLOWLY.
Around 4 X is a good speed, if your blank CD can be burnt at that speed.

Also, remember to burn it as an iso, not just a data disk.

Most burning software has that option in the menus.

Regards,
Roger :D

---

### Post by XaresRomeo on 2009-05-19
I think it formatting a huge amount of disk space to EXT3 or EXT4 can take a while.
I have a 320 GB Seagate Barracuda hard drive 7200 RPM and it takes 2-3 minutes.

but 8 hours for a 750 GB hard drive? 
Something must be wrong either with CD or ISO Drive,
try to check the integrity of the disk in the boot menu options

---

### Post by nhasian on 2009-05-19
> **Jamiesonbrady said:**
> Well if my hard drive was corrupted that would suck, considering i bought my computer brand new only 8 months ago.

On the contrary, it doesnt suck at all if your hard disk is still under manufacturer warranty.  I bought a brand new HP and my hard disk failed during the 2nd month.  HP shipped me a new drive, as well as the packaging and postage to return the defective drive back to them.  pretty hassle free.  

I strongly encourage you to run some diagnostics on your hard disk.  The manufacturer or your computer as well as the manufacturer of the hard disk both provide free tools you can download to check your hard disk.

[QUOTE=SunnyRabbiera]It can take a while, the larger the drive the longer the install. [/QUOTE]

Actually I find the OPPOSITE to be true.  older (smaller) hard disks take much longer to install to because they are slower.  The higher the physical density of the sectors on the platters, the faster the read/write access is.

---

