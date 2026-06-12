---
title: "ndiswrapper, WEP and NetworkManager hanging"
date: 2007-05-11
forum: Networking &amp; Wireless
---

### Post by hyperair on 2007-05-11
I have Ubuntu Feisty installed on my system, been using Ubuntu since the release of Dapper, and was running the acx drivr fine. My wireless card is a DWL-520+. Recently, I decided to try getting NetworkManager to work. I set the wlan0 interface to roaming mode, blacklisted acx in the /etc/modprobe.d/blacklist file, and installed and loaded my Windows drivers through ndiswrapper. I managed to connect to my wireless network, which uses a WEP 128-bit ASCII key, but the icon stays with the two green circles and the blue comet-shaped thing orbiting both green circles perpetually. This continues until I log off. If i log on again, the network-manager applet sits there with the "x" sign. When I shutdown, it hangs while stopping NetworkManager. Does anyone know what's wrong and how I can fix this?

EDIT: I just killed the NetworkManager daemon and started it in no-daemon mode.. and it reported something...
```
*** glibc detected *** NetworkManager: double free or corruption (fasttop): 0x0809a668 ***
```

EDIT: I just cleared the immutable flag on /etc/resolv.conf and it seemed that solved the problem. ><

---

