---
title: "Understanding how to faultfind wireless network"
date: 2007-01-16
forum: Networking &amp; Wireless
---

### Post by jnorris235 on 2007-01-16
I have read and tried various things for weeks. Computer will not see the network. Would love a clear guide to how to fault find.
Ubuntu Edgy with KDE.
Belkin pre-N FN8010 card in a desktop computer.
Computer works fine on the net with ethernet.
Laptop, also Edgy connects to network and internet fine.
Have used ndiswrapper and ndiswrapper-util-1.8 and used netani.inf etc from Belkin.

Testing
KWiFiManager for eth2 shows no networks found.
Networking shows Wireless connection , Essid : CHINA, Address: DHCP for eth2, enabled
Wireless Assistant shows no networks
Windows Wireless Drivers (the gui for ndiswrapper, I guess? shows netani (the driver) present and the hardware present

Konsole: iwconfig eth2 says: IEEE 802.11b ESSID:"". Mode auto
iwconfig essid "CHINA" says unrecognised wireless request "CHINA"

ifconfig eth2 says lots but mostly with noughts

So................what can I do to actually test things? It seems the hardware is there and the drivers, they seem to know of the network but maybe I told them How can I do a step by step test please?

---

### Post by peabody on 2007-01-16
Do both computers use the same make of network card?

---

### Post by jnorris235 on 2007-01-16
No - the laptop uses a different built in one.

---

### Post by peabody on 2007-01-16
Sorry, I'm stumped too.

The only random piece of advice that I can give that may be related to your problem is that sometimes there are open source drivers that interfere with ndiswrapper.  That was the case with a WG111 usb stick I was using as a wireless adapter.  I had to black list some kernel modules to get it to work.

---

