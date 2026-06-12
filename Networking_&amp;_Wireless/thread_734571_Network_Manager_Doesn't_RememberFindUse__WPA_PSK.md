---
title: "Network Manager Doesn't Remember/Find/Use  WPA PSK"
date: 2008-03-24
forum: Networking &amp; Wireless
---

### Post by mootpoint on 2008-03-24
OS: Linux Mint -- Gutsy with a few bells and whistles
HW: Broadcom 4211 builtin wireless card on a Compaq F572US laptop.
Driver: ndiswrapper with bcmwl5 driver from Compaq support website.

Problem Description: The card is working fine -- I set it up using the No-Fluff method elsewhere in the forums. I can connect to open, WEP, and WPA networks. But when I configure my home WPA network in the network manager applet and reboot, it does not connect ... the interface is up and running, but DHCP fails and it will not work if I set a static IP. It can, however, see available wireless networks and correctly lists the encryption types.

If I open Network Manager, re-enter the WPA key, and let it reconfigure the interface, everything works fine ... until the next reboot. 

I'm no expert, but I assume this might possibly perhaps be a problem with the keyring manager. I do not remember ever getting a keyring manager prompt when I set up the network in network manager. ps aux lists the keyring daemon. gnome-keyring-manager starts OK, and lists "login" and "session" keyrings. 

What keyring is network manager supposed to use, and how can I help it find the WPA key and work the way it's supposed to?

TIA,
mootpoint

---

### Post by Eiríkr on 2008-03-25
Network Manager is known to be very limited in functionality, and there are *numerous* posts on this board about exactly your problem.  Many of the solved threads recommend replacing Network Manager with WICD, which unfortunately is not included in the Ubuntu repositories and must therefore be downloaded from [its Sourceforge page]("http://wicd.sourceforge.net/").  

HTH,

Eiríkr

---

