---
title: "Network Manager overwrites interfaces"
date: 2007-01-24
forum: Networking &amp; Wireless
---

### Post by hey_ygbsm on 2007-01-24
Fellow Ubunti:  Got my wireless up & running last night.  Today, when I boot, Network Manager has a red 'x' and shows 'no connections available'.  I traced the problem to my /etc/network/interfaces file.  It appears to have been over written on shutdown (or during all my troubleshooting in terminal mode today).  Near as I can tell, this is all I need in there when using N-M, because this applet uses the settings from System>>Administration>>Networking

auto lo
iface lo inet loopback

Your help/thoughts would be appreciated.  Thanks!

---

### Post by hey_ygbsm on 2007-01-24
Just rebooted & everything was working fine.  Network Manager launched correctly and nagged me for my password.  Any way to bypass that?

---

