---
title: "Offline install PCMCIA wireless Broadcom 4306"
date: 2006-08-30
forum: Networking &amp; Wireless
---

### Post by bertve on 2006-08-30
Hi,
I'd like to get a Motorola WN825G wireless PCMCIA card to work on my Powerbook Titanium under Xubuntu 6.06. This card uses the Broadcom BCM4306 chipset (rev. 03). The ethernet cable port is broken, so I don't have internet access on this machine. I have some experience with the command line and unix, but less so with system configuration under linux.
It would be very nice if someone would be kind enough to give a little help.
Thanks,
Bert

---

### Post by spd106 on 2006-08-30
Start by downloading or otherwise obtaining xubuntu 6.06.1 and update all packages, specifically the kernel upgrade. Click the following link or maybe try a local mirror.
[http://cdimage.ubuntu.com/xubuntu/releases/6.06.1/release.1/](http://cdimage.ubuntu.com/xubuntu/releases/6.06.1/release.1/)

Then install ndiswrapper-utils and use the windows driver supplied with the card. There are howto guides all over the forum and wiki, I suggest you find one you understand and print it. 
eg
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)
[http://www.ubuntuforums.org/showthread.php?t=201902](http://www.ubuntuforums.org/showthread.php?t=201902)
[http://www.ubuntuforums.org/showthread.php?t=25683](http://www.ubuntuforums.org/showthread.php?t=25683)

You may also want to download the ndisgtk deb package from the universe repo,  not sure if it supports powerpc though.

---

