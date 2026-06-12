---
title: "Help with shrinking Windows-partition"
date: 2010-03-24
forum: New to Ubuntu
---

### Post by Djalmahal on 2010-03-24
Hi,

I just bought this new Computer, it has a 500GB hard drive, and the official Ubuntu Help page for setting it up for dual booting says I should use the Windows & partitioning program as gparted might destroy something. Now the Windows program only lets me shrink the Windows partitiong to a maximum of 220GB, I thought more of giving it 60GB, I defragmented the new computer hard drive, and still the same. ANybody knows how to force Windows 7 to give it only 60GB or anybody has experiences with resizing it with GParted? I can use GParted, I just down want to mess up Windows.

Thanks for that.
Andreas

---

### Post by oldfred on 2010-03-24
It is safer to use the win7 partition tools. Vista and Win7  start at sector 2048 where everyone else XP & linux start at sector 63. If the win7 partition is moved to sector 63 it has to be repaired but should still work after repairs. Besure to reboot windows several times after changing its size so it has recognized to new size, it usually wants to run chkdsk at the minimum.

starting with Vista - MSoft made some changes to the way it installs itself in a partition. Gparted can deal with it but should have the round to cylinder unchecked.
Herman on checkbox
[http://www.uluga.ubuntuforums.org/showpost.php?p=7816261&postcount=17](http://www.uluga.ubuntuforums.org/showpost.php?p=7816261&postcount=17)
Vista and Partitioning - details
[http://www.multibooters.co.uk/partitions.html](http://www.multibooters.co.uk/partitions.html)

This talks about Vista but win7 should be the same:
Resize Vista partition
If problems, try disabling system restore, pagefile, (in advanced settings in computer properties) and hibernate option (in power management). Don’t forget to turn them on back later.
[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/](http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/)

---

### Post by Djalmahal on 2010-03-24
Thanks Old Fred, that looks very detailed, I'll look into it this evening when I have time. Thanks

---

### Post by sixthwheel on 2010-03-24
I installed Ubuntu letting it automaticly partition the drive, and everything went fine.
However I'm a noob so please don't take this as advice, just my experience. 

Although I have XP, so I would have no idea about Vista or 7

---

### Post by Mark Phelps on 2010-03-24
> **sixthwheel said:**
> I installed Ubuntu letting it automaticly partition the drive, and everything went fine.
However I'm a noob so please don't take this as advice, just my experience. 

Although I have XP, so I would have no idea about Vista or 7

And ... lots of others had bad experiences when they did just the same with Vista or Win7.  

Since the OP just mentioned "new computer", it's most likely to have Win7 on it, or maybe, Vista.  So they should NOT do what you did.

---

