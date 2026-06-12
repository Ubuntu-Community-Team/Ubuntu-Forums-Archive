---
title: "Brasero can't check disk size?"
date: 2010-01-08
forum: New to Ubuntu
---

### Post by kapi on 2010-01-08
Morning all,

have been burning disks on and off for past few weeks without any apparent problems. This morning I went to complete a backup of some video files and was left with 'unknown error' in brasero. So I installed K3b to see if it was brasero. No! 

K3b kindly pointed out the error but I'm not sure what to do next.

here is the print out of the feed back it it helps:  Thanks

---------------------------------------------------------------------
Devices
-----------------------
MATSHITA DVD-RAM UJ-850S 1.05 (/dev/sr0, CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL) [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, Restricted Overwrite, Layer Jump] [%7]

K3b::IsoImager
-----------------------
mkisofs print size result: 0 (0 bytes)

System
-----------------------
K3b Version: 1.68.0
KDE Version: 4.3.2 (KDE 4.3.2)
QT Version:  4.5.2
Kernel:      2.6.31-17-generic

Used versions
-----------------------
mkisofs: 1.1.9

mkisofs
-----------------------
/usr/bin/genisoimage: No such file or directory. Invalid node - 'php academy/Tutorials/10.'.

mkisofs calculate size command:
-----------------------
/usr/bin/genisoimage -gui -graft-points -print-size -quiet -volid php academy -volset  -appid K3B THE CD KREATOR (C) 1998-2007 SEBASTIAN TRUEG -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-craig/k3bfl3312.tmp -rational-rock -hide-list /tmp/kde-craig/k3byH3312.tmp -joliet -joliet-long -hide-joliet-list /tmp/kde-craig/k3bqP3312.tmp -no-cache-inodes -full-iso9660-filenames -iso-level 3 -path-list /tmp/kde-craig/k3bmj3312.tmp

---

### Post by ukripper on 2010-01-08
Can you rename directory "php academy" to php-academy and then burn on dvd/cd.

---

### Post by kapi on 2010-01-08
Thanks for the help, it was something similar within the php directory. when naming a file I must have inadvertently added a space.

Thanks and have a great day!

---

