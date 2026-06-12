---
title: "WLAN and virtual interfaces"
date: 2007-08-09
forum: Networking &amp; Wireless
---

### Post by Sargon on 2007-08-09
Hi

Since WLAN/WPA2 and a static IP address don't seem to work at the moment (at least not for me), I decided to let DHCP do its magic and add a virtual interface with an IP address I can control.

So I changed /etc/network/interfaces to this:
```

auto eth1
iface eth1 inet dhcp
post-up /sbin/ifup eth1:1

# Static IP for WLAN
iface eth1:1 inet static
address 10.0.0.100
netmask 255.0.0.0
broadcast 10.255.255.255
```

This failed completely and I got no network connection at all. It seems that the NetworkManager Applet doesn't like the "post-up" line. When I remove this line, WLAN/DHCP works normally, but the virtual interface eth1:1 is not available.

Any ideas what else I could try?

Sargon

PS. Using "auto eth1:1" doesn't work, because eth1 is not yet ready when eth1:1 gets initialized and therefore fails.

---

