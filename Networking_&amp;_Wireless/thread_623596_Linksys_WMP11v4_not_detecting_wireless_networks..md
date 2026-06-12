---
title: "Linksys WMP11v4 not detecting wireless networks."
date: 2007-11-26
forum: Networking &amp; Wireless
---

### Post by urIkon on 2007-11-26
Brand new, squeaky clean install of Gutsy.  I installed the drivers for the LInksys WMP11v4 PCI wireless adapter (which was tested, working in this machine under the previous XP install)  using ndiswrapper.  

It took the drivers just fine, detected the hardware, was configurable, and kept settings after a reboot.  However it cannot see any wireless networks.  The toolbar applet displays none, and I cannot see any using iwlist.  

The only error messages to appear in /var/log/messages are ones from wlan0 (the card) dealing with setting encryption modes failing, and adding encryption keys failing, which appeared after I tried to configure the card manually entering the ESSID and WEP key.  I do not however think this is the cause I thought encryption happens after you first see then connect to a network.

Any help would be appreciated!

---

