---
title: "Hardest Part When Getting Started: ..Partitioning"
date: 2009-01-04
forum: New to Ubuntu
---

### Post by tedted on 2009-01-04
First off, I'm new to the forum and am excited to start participating.  And thanks for all your help.

I've trying to decide between Ubuntu and Fedora and I'm going to go with Ubuntu (maybe xubuntu). But I want to keep XP mostly because of iTunes,I have an iPod and have paid for many CDs, after the partition. So I'm going to shrink XP on the HD (however you do that) and then hopefully everything will be cool (I hope).

So this is what I'm dealing with.  I think Ubuntu will be appropriate.
Intel Celeron CPU 2.60 GHz Processor
504MB DDR SDRAM (put 2 sticks of 256 but it only gave me 504)
40GB HD is what the box says but C: says 31.78GB
with 22.2GB Used and 9.41GB Free.

So any tips and tricks for getting this done?  How much should I partition for XP and everything else?  Just a simple link to another post or something else is welcome as well.  Thanks Again.

---

### Post by tanis143 on 2009-01-04
Well, first off the reason you are only seing 504 is 8 megs is being used for your onboard video card, hince 504+8 = 512. Also, with the hard drive, there are many different ways storage space is measured. HD vendors use one way, windows uses another. With only 9 gigs free, thats gonna be an really small area to install linux. Is this a desktop or laptop? If its a desktop you might want to invest in a second hard drive and use it for your linux. Another 40gig drive won't set you back that much. If its a laptop, well then you might only want to use 4 gigs of that space to put linux in. Just use the install CD, it will autosize the remaining space on your hard drive for you. That would probably be your best bet. And linux will setup a boot screen so you can choose which o/s you want to boot into.

---

### Post by jamesrl on 2009-01-04
If the only thing that is keeping you to windows is itunes, I highly recommend trying the amazon.com music store (very similar to itunes but no DRM on the files, so they can be played in any OS/hardware).  Also if you look into myFairTunes7 or QTFairUse6 you can remove the digital rights management from an Itunes m4p that you have rights to play (within windows).  (This is in violation of the Itunes EULA, however under Fair Use copyright laws it is (probably) not illegal if done for personal use (e.g., to use in other OS, mp3 players or backups).  You are not allowed to sign away legal rights via clicking an EULA, as there is no way of enforcing who originally clicked the EULA.)

---

### Post by jamesrl on 2009-01-04
The difference in hardware size is due to computers liking to use powers of 2 (being binary in nature), so a kilobyte is 1024 bytes (2^10 bytes) rather than 1000 bytes (10^3) which humans like to use (as we have 10 fingers).  New language has been introduced to differentiate the two, kibibyte being 1024 bytes, kilobyte 1000 bytes (and similar mebibyte = (1024)^2=2^20, gibibyte=1024^3=2^30).
So if your hardware manufacturer says you have 40gb, you should have at least 37.25 = 40*(1000/1024)^3 Gib.  If you bought a Dell or other pre-packaged computer it is likely that you have a hidden recovery partition, that basically is a backup of all the data on your computer as it was originally installed (with about 3-4Gb used).  If you do not need that recovery partition you can erase it.

---

### Post by jamesrl on 2009-01-04
I should add that the ubuntu installation guide recommends at least 8 Gb of disk space free for the installation.  

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

I also would not try running windows with less than 1 Gb of free space.  [You need space for the windows swap file, as well as room to install new things, also windows will get fragmented really quickly and take a while to defrag with very little room available.]

There are other lightweight versions of linux that are designed to be installed really small (e.g., damn small linux which can run from a 50 Mb USB stick) but they are usually minimalist by nature (e.g., by default run very lightweight web browser rather than firefox, etc.).

---

