---
title: "Can't Resize Partition"
date: 2009-06-18
forum: New to Ubuntu
---

### Post by freeman2000 on 2009-06-18
Ubuntu (gparted) refuses to resize/shrink my Ubuntu partition (from 72gb to 40 gb).  I have not found a similar situation in my research, so here goes.  Here's the info from "fdisk"

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9e2d9e2d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8987    72188046    7  HPFS/NTFS
/dev/sda2            8988       18386    75497467+   5  Extended
/dev/sda3           18387       19457     8602807+   7  HPFS/NTFS
/dev/sda5            8988       17997    72372793+  83  Linux
/dev/sda6           17998       18386     3124611   82  Linux swap / Solaris

I'm trying to shrink 'sda5' as it's about 72 gb and I don't need that much space for Ubuntu.  I would like to add some other distros, such as Debian, Fedora, or LinuxMint.  I completely shut down the computer and then restart from a Live CD (9.04).  I go into gparted, and it runs for about 6+ minutes and then gives me an error message that it can't resize the partition.  Here are the messages that I get without all the minor details - note message 4a:

Shrink /dev/sda5 from 72gb to 40gb  -  error 
1.  calibrate /dev/sda5  -  ok
2.  calculate new size & position of /dev/sda5  -  ok
3.  check filesystem on /dev/sda5 for errors & (if possible) fix them  -  ok
3a. run 'e2fsck -f-y-v /dev/sda5  -  ok
4.  shrink filesystem  -  error
4a. resize 2fs /dev/sda5
    resize 2fs  1.41.3
    please run e2fsck -f /dev/sda5 first 
    (what!  that was just run in step 3a & gets run again in step 5a)
5.  check filesystem on /dev/sda5 for errors & (if possible) fix them  -  ok
5a. run 'e2fsck -f-y-v /dev/sda5  -  ok
6.  grow filesystem  fill partition  -  ok
6a. resize 2fs /dev/sda5
    resize 2fs  1.41.03

I have tried to shrink the partition almost 10 times with no luck.  I tried running 'e2fsck' before trying to run the 'resize' option in gparted, also with no luck.  I have also tried to install both Debian & Fedora from their respective live CDs, hoping that those distros could shrink the partition, but also with no luck.  Any ideas/suggestions?   
Thanks!

---

### Post by ramjet_1953 on 2009-06-18
You cannot re-size a partition that is mounted.
It's like trying to change a tyre on a car that is being driven!

The easiest way is to download a stand-alone program like Parted Magic.

You can get it from here: [http://partedmagic.com/](http://partedmagic.com/)

It is an iso, so you need to burn it to a CD and then boot your system from the CD.

Remember when burning an iso to burn it as a image, not a data disk and also burn it SLOWLY. If your blank CD's and burner allow it, around 4X is good.

Regards,
Roger :D

---

### Post by skyjacker on 2009-06-18
I'm not 100% certain, but I think a partition has to be "unmounted" to resize it. Have you tried this?

---

### Post by freeman2000 on 2009-06-18
The partition is 'unmounted' and I'm running gparted from a LiveCD (9.04).  I get the "resize/move" button, which is why I am able to run thru the 6 steps.  You can't do that on a 'mounted' partition.  The problem seems to be somewhere in the steps 3-4 area.  It runs step 3 ok (e2fsck) but then gets to step 4 where it says that you need to run step 3 (e2fsck) first (huh?  I just did that!).  That is what is befuddling me.  I even tried from a Debian & a Fedora Live CDs with no luck.  I appreciate all ideas & suggestions.  Thanks.

---

### Post by cubeist on 2009-06-19
You could try running the commands it is executing in a terminal yourself.
This will probably work, but I would caution running commands that you don't understand fully...so make sure you read the relevant man pages first.
ie, man e2fsck

---

