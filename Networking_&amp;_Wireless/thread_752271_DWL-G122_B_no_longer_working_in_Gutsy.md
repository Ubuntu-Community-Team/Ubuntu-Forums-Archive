---
title: "DWL-G122 B no longer working in Gutsy"
date: 2008-04-11
forum: Networking &amp; Wireless
---

### Post by Sixten on 2008-04-11
I have an Ubuntu box I'm using as a PVR (with MythTV), connected to the net with a DWL-G122 B (because it's in the living room, WAY away from wired access). As a consequence, it takes a while between upgrades, because it's such a pain.

Anyway, I upgraded from Feisty to Gutsy a few days ago, and now the wireless network doesn't want to work. Under 7.04, it was using ndiswrapper. After the upgrade, it looks like the system recognized the adapter, and is using rt2500, configured as wlan0.

I can't ping anything outside of the box itself. Not the access point, not my router, not my other PCs.

Every thing I know to look for looks OK. Both ifconfig and iwconfig both show wlan0 as configured, and finding the access point. The network is all static config, so it's not a DHCP failure. The output of dmesg shows the system authenticating and associating with the access point. (I'm not posting any of that, because the machine's not on the 'net, and I only type so fast.) And, of course, other machines can use the network without any issues.

What am I missing?

It seems like if the rt2500 drivers weren't going to work, the failure would be much earlier in this process. But maybe I need to go back to ndiswrapper for this adapter?

---

### Post by acad1 on 2008-04-11
[http://ubuntuforums.org/showthread.php?t=739139&page=3](http://ubuntuforums.org/showthread.php?t=739139&page=3)

If your USB device is DWL G122 H/W Ver B1 F/W Ver 2.03, then please have a look at the above link. I installed the RT2570 driver in Ubuntu 7.10 and with a lot of help, eventually got the wireless device to work. I had used 7.04, prior to that and had no problems connection wirelessly with a straight install from the CD. I am not well versed in Linux so would find it difficult to guide you through the install process.

---

### Post by Sixten on 2008-04-11
I was really hoping not to have to download anything else, but I guess it may be time to cart the machine into the other room and hook it up to the wired network. :-(

Still confuses the hell out of me that I can get the thing to associate to the AP, but still not be able to reach anything.

---

### Post by acad1 on 2008-04-12
If you have a USB stick, you could download the required files on another machine and then transfer them to the desktop, as I did.

---

