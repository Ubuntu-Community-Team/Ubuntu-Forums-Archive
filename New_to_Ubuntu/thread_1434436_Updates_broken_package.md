---
title: "Updates: broken package"
date: 2010-03-20
forum: New to Ubuntu
---

### Post by Trandre on 2010-03-20
I got the message(in norwegian)when updating that U have a broken package. 

It said use the filter for locating broken packages to resoulve it. 

Where is this filter?


Trandre
:KS

---

### Post by Trandre on 2010-03-20
error message when updating:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=150742&stc=1&d=1269090230[/IMG]

---

### Post by arochester on 2010-03-20
Synaptic Package Manager

Edit>Fix broken packages

---

### Post by Trandre on 2010-03-20
Deleted to following in available:

```
Package: xserver-xorg-video-cirrus
Priority: optional
Section: x11
Installed-Size: 164
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Version: 1:1.3.1-1ubuntu2
Replaces: xserver-xorg (<< 6.8.2-35), 
Provides: xserver-xorg-video-5
Depends: libc6 (>= 2.4), xserver-xorg-core (>= 2:1.6.2)
Conflicts: 
Size: 48324
Description: X.Org X server -- Cirrus display driver
 This package provides the driver for the Cirrus Logic family of video
 cards.
 .
 More information about X.Org can be found at:
 <URL:http://www.X.org>
 <URL:http://xorg.freedesktop.org>
 <URL:http://lists.freedesktop.org/mailman/listinfo/xorg>
 .
 This package is built from the X.org xf86-video-cirrus driver module.
Original-Maintainer: Debian X Strike Force <debian-x@lists.debian.org>

```

and
```
Package: libmpg123-0
Priority: optional
Section: libs
Installed-Size: 616
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Architecture: i386
Source: mpg123
Version: 1.7.3-0ubuntu1
Depends: libc6 (>= 2.4)gksudo gedit /var/lib/dpkg/status"
Size: 379398
Description: MPEG layer 1/2/3 audio decoder -- runtime library
 Mpg123 is a fast and portable MPEG audio decoder for Unix.  It supports
 MPEG 1.0/2.0 layers 1, 2 and 3 (those famous "mp3" files).
 .
 For full CD quality playback (44 kHz, 16 bit, stereo) a Pentium,
 SPARCstation10, DEC Alpha or similar CPU is required.  Mono and/or reduced
 quality playback (22 kHz or 11 kHz) is even possible on 486 CPUs.
 .
 This package contains the C libraries needed to run executables that use
 the mpg123 library.
Original-Maintainer: Daniel Kobras <kobras@debian.org>

```


The issue is now solved

Thanks


Trandre

---

