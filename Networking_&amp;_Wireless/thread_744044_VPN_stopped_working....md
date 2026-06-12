---
title: "VPN stopped working..."
date: 2008-04-03
forum: Networking &amp; Wireless
---

### Post by olbion on 2008-04-03
I've used VPN to connect to my servers for a long time and it has worked fine, until yesterday that is. Suddenly it stopped working, and I don't know what's wrong.

If I use the same configuration on a Windows machine, it works fine. My hosting company says they havn't changed anything on their end.

I've tried using VPNC as well as Cisco and I get the same result. The client connects fine, but then the network is unreachable. This affects vpn resources as well as the web.

After connecting, if I manually add my local DNS servers to /etc/resolv.conf then I'm able to access the web - but still nothing on the VPN.

What could have happened? This has coincided with some updates that I was encouraged by Ubuntu to install, though I'm not sure if that is related. Is there perhaps some way to downgrade from the latest upgrades?

I'm using Ubuntu 7.10. Your help is much appreciated!

---

### Post by olbion on 2008-04-05
Since I didn't find any solution, I re-installed Ubuntu 7.10 and it's now working again. No idea as to what was wrong prior to the re-install. I also installed all upgrades suggested by Ubuntu and it still works fine.

---

