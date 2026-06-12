---
title: "K3B says Could not determine size of resulting image file"
date: 2009-02-19
forum: New to Ubuntu
---

### Post by mr.big_gun on 2009-02-19
k3b shows an error just before trying to burn and this is the debuging output





System
-----------------------
K3b Version: 1.0.5

KDE Version: 3.5.10
QT Version:  3.3.8b
Kernel:      2.6.27-11-generic
Devices
-----------------------
UNKNOWN 16X52X32X52COMBO 110G (/dev/scd1, ) [CD-R, CD-RW, CD-ROM, DVD-ROM] [DVD-ROM, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R]

HL-DT-ST DVD-RW GSA-H11N JG03 (/dev/scd0, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite]
K3bIsoImager
-----------------------
mkisofs print size result: 0 (0 bytes)

Used versions
-----------------------
mkisofs: 1.1.8

mkisofs
-----------------------
/usr/X11R6/bin/genisoimage: No such file or directory. Failed to open VIDEO_TS.IFO
/usr/X11R6/bin/genisoimage: Can't open VMG info for '/tmp/kde-root/k3bVideoDvd0/'.
/usr/X11R6/bin/genisoimage: Unable to parse DVD-Video structures.
/usr/X11R6/bin/genisoimage: Could not find correct 'VIDEO_TS' directory.
/usr/X11R6/bin/genisoimage: Unable to make a DVD-Video image.
Possible reasons:
  - VIDEO_TS subdirectory was not found on specified location
  - VIDEO_TS has invalid contents
/usr/X11R6/bin/genisoimage: No such file or directory. Failed to open VIDEO_TS.IFO
/usr/X11R6/bin/genisoimage: Can't open VMG info for '/tmp/kde-root/k3bVideoDvd0/'.
/usr/X11R6/bin/genisoimage: Unable to parse DVD-Video structures.
/usr/X11R6/bin/genisoimage: Could not find correct 'VIDEO_TS' directory.
Possible reasons:
  - VIDEO_TS subdirectory was not found on specified location
  - VIDEO_TS has invalid contents

mkisofs calculate size command:
-----------------------
/usr/X11R6/bin/genisoimage -gui -graft-points -print-size -quiet -volid K3b data project -volset  -appid K3B THE CD KREATOR (C) 1998-2006 SEBASTIAN TRUEG AND THE K3B TEAM -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-root/k3bK6Y79a.tmp -no-cache-inodes -udf -iso-level 1 -path-list /tmp/kde-root/k3bZI3wdc.tmp -dvd-video -f /tmp/kde-root/k3bVideoDvd0 







what do i do??? help.

---

### Post by robajz on 2011-10-30
Hi, I know this is an old post, but it's frustrating to google questions without answers. The other thread that might have the answer is [http://ubuntuforums.org/showthread.php?t=1486562](http://ubuntuforums.org/showthread.php?t=1486562)

Essentially, there might be a file with invalid characters in the name.

---

### Post by oldos2er on 2011-10-30
Closed. Please don't bump old threads.

---

