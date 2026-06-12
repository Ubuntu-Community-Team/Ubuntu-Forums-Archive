---
title: "Replacing dhclient with udhcpc as default."
date: 2008-06-06
forum: Networking &amp; Wireless
---

### Post by Lord_Devi on 2008-06-06
Hello.

I wish to change my DHCP client for my eth0 device from dhclient to udhcpc but can not figure out how. From what I am able to learn from /usr/share/docs/ifupdown/examples, man interfaces(5), and google, the following should work as an example: /etc/network/interfaces

```

auto lo
iface lo inet loopback

auto eth0

iface eth0 inet dhcp
   client udhcpc

```

But it still uses dhclient, and a few other small variations i have tried. Can someone tell me what I am doing wrong and, if possible, also link me some better in depth documentation for this mechanism?(I am interested in laptop roaming profile type issues as well).

All of the documentation I have found so far is rather lacking. :( (i.e. [http://www.debian.org/doc/manuals/reference/ch-gateway.en.html]("http://www.debian.org/doc/manuals/reference)./ch-gateway.en.html"))

Thank you all =)

---

### Post by Lord_Devi on 2008-06-07
Bump.

---

