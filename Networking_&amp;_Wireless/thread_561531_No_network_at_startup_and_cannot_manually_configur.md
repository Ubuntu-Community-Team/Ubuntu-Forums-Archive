---
title: "No network at startup and cannot manually configure it"
date: 2007-09-27
forum: Networking &amp; Wireless
---

### Post by ericindie on 2007-09-27
When I start gutsy, either from the cd or after I install it, either by CD or updateing through apt-get.it fails to detect my network.

  In Feisty it detects the right ip address via dhcp from my router, but not in gutsy Gutsy tells me my ip, subnet, and broadcast are all 0.0.0.0. I try to manually configure it through network manager, but it doesn't work even after I change the ip, subnet and broadcast to the values that work in Feisty. Also, my network card disappears from the list of devices, and going through the menus it says "no devices detected" after I try to manually configure it.

This has been a problem in all versions of Gutsy up to and including the beta of 9/27/2007.I'm using the AMD64 version on my Pentium Duo.

My network comes up as nVidia Corp MCP55 Ethernet card

---

### Post by noob12 on 2007-09-27
Did you remember if you built your own version of the forcedeth driver earlier for Feisty?    If so, you probably have to build an updated version again for Gutsy. If not, then you should probably file a bug on launchpad.

---

