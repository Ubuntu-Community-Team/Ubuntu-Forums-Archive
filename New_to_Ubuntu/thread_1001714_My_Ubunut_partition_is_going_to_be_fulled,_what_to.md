---
title: "My Ubunut partition is going to be fulled, what to do now?"
date: 2008-12-04
forum: New to Ubuntu
---

### Post by legolas_w on 2008-12-04
Hi
thank you for reading my post.
It looks like that my ubunut partition (43GB) has just 2.8GB free space left. I have no video on this partition, no music,... just my working files and applications.

Is there any safe way to safely extend its size, or somehow move some files to another partition without hurting the linux?

I have a lots of files in /opt/ folder, if I could move these folder somewhere else and also move /home/ to another partition then all of my problems will vanish.

Thanks.

---

### Post by billgoldberg on 2008-12-04
> **legolas_w said:**
> Hi
thank you for reading my post.
It looks like that my ubunut partition (43GB) has just 2.8GB free space left. I have no video on this partition, no music,... just my working files and applications.

Is there any safe way to safely extend its size, or somehow move some files to another partition without hurting the linux?

I have a lots of files in /opt/ folder, if I could move these folder somewhere else and also move /home/ to another partition then all of my problems will vanish.

Thanks.

This might help:

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by halitech on 2008-12-04
this might help for moving your /home position, not sure about the /opt folder

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by posburn on 2008-12-04
Hi!

Have a look here if you have room on another partition to move your home folder to:

[http://www.psychocats.net/ubuntu/separatehome]("http://www.psychocats.net/ubuntu/separatehome")

Otherwise, you can use the Ubuntu LiveCD to run GParted and resize your current Ubuntu partition.  This always has a finite risk associated with it, so back your crucial data up before doing so.

---

### Post by posburn on 2008-12-04
Wow, I must be getting old and slow...;)

---

### Post by porchrat on 2008-12-04
All of you posted the same link within a minute...classic

---

### Post by goldenphoenix713 on 2008-12-04
Another way you can  do this is to download the GParted ISO as a standalone, and boot from that.  Keep in mind that you need unallocated hard drive space, which might mean shrinking another partition.

[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

---

### Post by squeabs on 2008-12-04
The simple route, if your partitions are split with linux and something else: I've been able to just pop in my ubuntu install cd and use the partition editor with it to resize linux.

---

### Post by mister_pink on 2008-12-04
Something I'm surprised noone suggested is trying to free up some space! Have you tried using the Disk usage analyser (in accessories)? This might give you a clue as to whats eating up all your space.

---

### Post by lswest on 2008-12-04
also, I recommend running ```
sudo aptitude autoclean
``` (from the terminal) to remove old archived deb files (just the installers basically), might free up some space if you've been installing a lot.

---

### Post by Paqman on 2008-12-04
[HOWTO: Cleaning up all those unnecessary junk files](http://ubuntuforums.org/showthread.php?t=140920)

40GB is a lot, how much of that is user data and how much is the system?

---

### Post by legolas_w on 2008-12-04
> **Paqman said:**
> [HOWTO: Cleaning up all those unnecessary junk files](http://ubuntuforums.org/showthread.php?t=140920)

40GB is a lot, how much of that is user data and how much is the system?

Thank you all for your help. I will try and let you know the result.

The home folder (/home/) is about 14 gig.
my /opt/ is about 10gig.

---

### Post by Paqman on 2008-12-04
Have you tried using the disk usage analyser to see where the cruft is? Sounds like you've got 16GB or so outside of /home and /opt, which is a lot.

---

### Post by linux_tech on 2008-12-04
You should consider running gparted.  If you have a 40 GB and used a little over half, then you may be able to do some resizing to get more space where you need it such as /home. GParted is a great tool for creating, destroying, resizing, moving, checking and copying partitions, and the filesystems on them. This is useful for creating space for new operating systems, reorganizing disk usage, copying data residing on hard disks and mirroring one partition with another (disk imaging).Its a handy utility to have around.
[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

---

### Post by abn91c on 2008-12-04
> **legolas_w said:**
> Thank you all for your help. I will try and let you know the result.

The home folder (/home/) is about 14 gig.
my /opt/ is about 10gig.
try the easy stuff first, sudo apt-get autoremove

also in you home folder is you have deb files from maybe games, themes, icon sets you installed already go ahead and delete them also components you may not use like bluetooth, tape back up. palm pilot, torrent programs, IM chat uninstall them also

---

### Post by laffinet on 2008-12-04
You might also want to check all your "trash".

Have a look [here]("http://ubuntuforums.org/showthread.php?t=898573"), not only helps with sorting out conflicting usage results, but also helps cleaning up all the trash that gets collected in various spots.

---

