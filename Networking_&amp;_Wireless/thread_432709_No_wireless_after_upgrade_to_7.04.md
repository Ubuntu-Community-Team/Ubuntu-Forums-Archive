---
title: "No wireless after upgrade to 7.04"
date: 2007-05-04
forum: Networking &amp; Wireless
---

### Post by bigblop on 2007-05-04
I have just updated to Ubuntu 7.04 on my IBM T40/p and now the wireless does not work.

It worked fine in 6.10. If I open the network program: System -> administration -> Network

It is set to Roaming mode. Since this does not work I have tried to disable this and manually enter ESSID (name of my linksys router which has a fine signal strength) and my password and DHCP. But it still does not work.

Any ideas?

---

### Post by glendavee on 2007-05-04
I have same problem. After upgrading to 7.04 there is a new kernel - 2.6.20.15. If I select the old kernel, 2.6.17.11 at startup, wireless is ok. I've also tried disabling Network Manager and installing Wicd, but this made no difference. Suggest you go back to 2.6.17.11 as a temporary fix.

---

### Post by bigblop on 2007-05-04
this fix worked:


1) Install network-manager-gnome through synaptic.
2) outcomment content of /etc/network/interfaces besides from 
   lines that contain "lo".
3) Create a file:
   gksudo gedit /etc/default/wpasupplicant
   with only content:
   ENABLED=0

In KDE do the same thing and remember to restart.

---

