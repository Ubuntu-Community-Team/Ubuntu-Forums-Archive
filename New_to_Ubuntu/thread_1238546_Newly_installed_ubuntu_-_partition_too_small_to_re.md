---
title: "Newly installed ubuntu - partition too small to receive updates."
date: 2009-08-12
forum: New to Ubuntu
---

### Post by phillip4672 on 2009-08-12
Dear Forum,

I have newly installed the net book remix of ubuntu 9.04. I've done this by partitioning my harddisk by clicking on the install icon from a memory-stick trial. I neglected to adjust the size of the partition when given the option at installation and now don't have enough space to receive updates. Oops!

I've done a bit of reading around and found and downloaded partman. When I ran this from the terminal it failed because I couldn't unmount. I've tried using the virtual command line but I ended up crashing ubuntu!

I have a Dell Inspiron 1010.

Please help me sort this out. I'll be very grateful.

Kind regards,

Phillip

---

### Post by starcraft.man on 2009-08-12
Please use gparted for partitioning, either use from a live CD in the admin menu or get the gparted custom live CD (see site download section). For partitioning instructions see, [http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php). Use the old section, and read the sections starting from top to bottom till ya think you know enough. 

The solution is simple, make root larger. See resize and move operations for further explanation, easy enough. If you've any questions at all after reading the docs, ask BEFORE making permanent changes to partitions.

I hope I don't need to warn but backup anything you can't live without, even if it isn't likely you do something wrong, it can always happen. There's no such thing as a retroactive backup.

This also is exactly why I hate the automated partitioner. Partitioning just needs to be done by hand, each has his/her own needs.

---

### Post by phillip4672 on 2009-08-13
Hi Starman,

Thank you for your wise words. I've now got a ubuntu partition of 8 gigs, which will do for the time being.

cheers,

Phillip

---

