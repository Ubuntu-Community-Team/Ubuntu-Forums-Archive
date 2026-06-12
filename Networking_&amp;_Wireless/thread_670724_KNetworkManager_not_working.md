---
title: "KNetworkManager not working"
date: 2008-01-17
forum: Networking &amp; Wireless
---

### Post by KhaaL on 2008-01-17
A while ago my KNetworkManager stopped working and I've made a few futile attempts at reviving it.

I know there's something that's supposed to be done in /etc/network/interfaces but i'm not sure what... here's the contents of mine:

```
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0


iface eth0 inet dhcp

auto eth0

```

Thanks

---

