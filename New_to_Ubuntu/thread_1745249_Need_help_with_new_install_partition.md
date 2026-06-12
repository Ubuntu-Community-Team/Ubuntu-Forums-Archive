---
title: "Need help with new install partition"
date: 2011-04-30
forum: New to Ubuntu
---

### Post by helbonikster on 2011-04-30
Hi, I am trying to install Ubuntu 11.04 alongside windows 7, but I am being told that I need to partition more space, but I have no idea which partitions to adjust. 

Ideally, I'd like to make my windows partition a bit smaller, in order to give ubuntu about 40 gigs or so. 

I am attaching some screenshots to show what is going on.

[ATTACH]190583[/ATTACH]

[ATTACH]190584[/ATTACH]

[ATTACH]190585[/ATTACH]

[ATTACH]190586[/ATTACH]

---

### Post by jmcbri on 2011-04-30
Wow, great documentation of what you're doing.  Makes things  easier.

You have a BUNCH of partitions on this drive, is that what you expect?  Anyway, you have two partitions that appear to be "Windows" in that they are NTFS (I'm ignoring the small FAT16 partition that you have). One partition is smaller, /dev/sda2 and the other is larger /dev/sda3.  The sizes should be consistent with what you expect.  IF THEY ARE NOT, DON'T GO FORWARD.  Installing and using Linux and Ubuntu in particular is not that hard, but this step is a big one if you screw it up.  If you make a mistake you can lose data.  

Anyway, you can probably resize the larger one to a smaller size assuming that you have unused space.  Once you've resized, making the partition smaller, in the *now unused* space, put a ext3 or ext 4 partition and set it to mount as '/'.  NOTE that it will have a completely different name/number.  You'll need at least a few GB, but you should give it 30 GB if you want to really use it for anything.  Once the new partition is formatted 
and marked to mount as /, you'll be able to proceed.

Hope this helps.  You should really make sure that you have the data backed up (I've overwritten drives doing this because I wasn't paying attention).  

Hope this helps.  Good luck.

---

### Post by Quackers on 2011-04-30
Your root partition for Ubuntu is too small at 984MB.
If you want to find more space you can resize the Windows main partition (sda3) but you should do it from within Windows. If you have Windows Vista or Windows 7 you should shrink the partition with the Disk Management Console. But you should first defragment the drive at least once and reboot. Twice would be better.

---

### Post by helbonikster on 2011-04-30
thanks..will give it a try

---

### Post by helbonikster on 2011-05-01
Thank you both for your helpful replies. I am now happily up and running alongside my windows install. 

One question: is there anyway to change the order of the OS choices in the boot menu?

Also, any other tips you can give a noob are much appreciated. 

Thanks again!

---

