---
title: "X-Server error setting MTRR"
date: 2011-03-10
forum: New to Ubuntu
---

### Post by Bearest on 2011-03-10
Hey guys,

I work for the CS department at the college I attend. We're using Ubuntu Server to process some mathematics equations through x11vnc for the mathematics department. I have quite a few issues, but the first is when I start X-server I get:

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-25-server i686 Ubuntu
Current Operating System: Linux sun 2.6.32-29-generic-pae #58-Ubuntu SMP Fri Feb 11 19:15:25 UTC 2011 i686
Kernel command line: BOOT_IMAGE=/vmlinuz-2.6.32-29-generic-pae root=UUID=f554369e-9886-4cdc-92cf-8c4e44ce7d02 ro quiet
Build Date: 10 December 2010  05:53:04PM
xorg-server 2:1.7.6-2ubuntu7.5 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support))
Current version of pixman: 0.16.4
        Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Mar 10 14:50:07 2011
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
error setting MTRR (base = 0xfd000000, size = 0x00800000, type = 1) Inappropriate ioctl for device (25)
error setting MTRR (base = 0xfd000000, size = 0x00800000, type = 1) Inappropriate ioctl for device (25)
error setting MTRR (base = 0xfd000000, size = 0x00800000, type = 1) Inappropriate ioctl for device (25)
^Cerror setting MTRR (base = 0xfd000000, size = 0x00800000, type = 1) Inappropriate ioctl for device (25)
 ddxSigGiveUp: Closing log

then everything hangs up and I'm forced to use ^C to exit the task. I'm really new to Linux and have been working on this server for a few weeks with little success. Anytime I seem to fix one problem two more take it's place. Any help is much appreciated.

---

