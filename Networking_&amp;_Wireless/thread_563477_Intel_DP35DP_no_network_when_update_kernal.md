---
title: "Intel DP35DP no network when update kernal"
date: 2007-09-30
forum: Networking &amp; Wireless
---

### Post by JessXe on 2007-09-30
I recently built myself a computer:

Intel DP35DP motherboard
Intel Core 2 Quad 6600
Seagate 500GB SATA HD
xfx Ge-Force 7300 Video card

Installed Vista and quickly got bored with it and installed Ubuntu 7.04

 no network so I found this thread:
[http://ubuntuforums.org/showthread.php?t=549510](http://ubuntuforums.org/showthread.php?t=549510)

downloaded e1000-7.6.5.tar.gz
extracted and did "make install" got an error but my internet started working then.
did "ifconfig eth0 192.168.1.106"(my ip within my home network)

everything worked fine.  i rebooted, it all still worked.

used ubuntu's automatic updates to upgrade to the 2.6.20-16 kernal.

rebooted and no network.  i tried "modprobe e1000" got nothing tried "insmod e1000"
tried "ifconfig eth0 192.168.1.106" got: "192.168.1.106: error fetching interface information: device not found"

any ideas?

~JessXe

---

### Post by noob12 on 2007-09-30
Yes, the driver would have been wiped out by the kernel upgrade.  The last part of this HOWTO will tell you how you can boot into your prior kernel and do a cross-build:
[http://ubuntuforums.org/showthread.php?t=551720](http://ubuntuforums.org/showthread.php?t=551720)

See the section titled **Building for 2.6.20-16-generic while running 2.6.20-15**
It assumes you have the driver sources in /tmp/e1000-7.6.5/src ; you can substitute your actual location.

---

