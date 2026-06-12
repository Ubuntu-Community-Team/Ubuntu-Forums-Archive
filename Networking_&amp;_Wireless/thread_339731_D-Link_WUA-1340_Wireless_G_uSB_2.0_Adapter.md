---
title: "D-Link WUA-1340 Wireless G uSB 2.0 Adapter"
date: 2007-01-16
forum: Networking &amp; Wireless
---

### Post by sageb1 on 2007-01-16
Will this adapter work with V6.06?

---

### Post by hal10000 on 2007-01-16
Look here: [http://www.ubuntuforums.org/showthread.php?t=270756](http://www.ubuntuforums.org/showthread.php?t=270756)
It seems to work with ndiswrapper.

---

### Post by midia on 2007-01-17
Ubuntu comes with ndiswrapper on the dvd but not as part of the install.  You have to add the cdrom to apt-get's sources.list:

sudo apt-cdrom add

Then

sudo apt-get update

then

sudo apt-get install ndiswrapper

Follow the ndiswrapper setup instructions located here:

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation")

Word of advice: You have to read it through first before doing them.
Once you have your device set up the way they say, the d-link device should work fine.

---

