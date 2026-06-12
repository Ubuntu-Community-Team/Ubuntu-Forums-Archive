---
title: "PPTP VPN plugin not listed in Network Connections"
date: 2013-10-29
forum: Networking &amp; Wireless
---

### Post by lildigiman on 2013-10-29
Ubuntu 12.04:

Under Network Connections->VPN->Add PPTP is not listed as an option. I have openconnect, openvpn, and vpnc listed, but I also have the pptp plugin installed as well, and it just won't show up. I rebooted my computer and reinstalled all of the plugins and pptp refuses to show up. Any ideas?

---

### Post by TheFu on 2013-10-29
Isn't pptp the protocol that has been hacked like 3 times?  Just sayin'.
[https://www.schneier.com/blog/archives/2012/08/breaking_micros.html](https://www.schneier.com/blog/archives/2012/08/breaking_micros.html) - yep.

---

### Post by lildigiman on 2013-10-29
TheFu, that's probably true, but it is an inappropriate answer to the problem this thread is trying to solve.

---

### Post by houstonbofh on 2013-10-29
You need all of the following packages;

network-manager-pptp
network-manager-pptp-gnome
pptp-linux

---

### Post by lildigiman on 2013-10-29
houstonbofh, Yes, all those packages are in fact installed and I have restarted since then to make sure the changes updated. However, PPTP still does not show up as an option for VPN connectivity.

---

### Post by lildigiman on 2014-03-04
Not sure what I did, but this does appear to be working after a few weeks have gone by. I've done a few updates (which none appear to be vpn related(?)) and a restarted PC. Still confused on this, but nonetheless it's working.

---

