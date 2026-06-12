---
title: "Can't connect outside with WG311v2"
date: 2007-08-29
forum: Networking &amp; Wireless
---

### Post by jgillick on 2007-08-29
I just upgraded from Dapper to Feisty (7.04), and my WiFi card (Netgear WG311v2) can't seem to connect to the outside world.  I can, however, connect to it from my other computer over SSH.  When I try to ping yahoo.com, for example, I get the following output:

$ ping yahoo.com
ping: unknown host yahoo.com

So it seems like it's connecting through the router OK, but cannot get outside of the house.

Do I need to mess around with the ACX firmware again ([http://www.doctort.org/adam/nerd-notes/netgear-wg311v2-wireless-lan-and-ubuntu-dapper.html](http://www.doctort.org/adam/nerd-notes/netgear-wg311v2-wireless-lan-and-ubuntu-dapper.html)) like I did for Dapper?  I thought this was resolved in Ubunty Feisty Fawn (7.07).

When I connect the machine straight to the router through an Ethernet cable, the internet connection works great.

---

### Post by jgillick on 2007-08-30
- I posted this too soon, see next post -

After digging around further I found that the problem was with the DNS lookup.  Adding "dns-nameservers 192.168.0.1" to the wlan0 section of /etc/network/interfaces seemed to fix the problem:
```

auto wlan0
iface wlan0 inet static
address 192.168.2.10
netmask 255.255.255.0
gateway 192.168.2.1
wireless-essid  XXXXX
wireless-key    XXXXX
wireless-channel    6
wireless-mode       managed
dns-nameservers 192.168.0.1
```

This line essentially just points to the router, which takes care of the DNS lookup.

---

### Post by jgillick on 2007-08-31
After reboot, it breaks again.  It seems to only work after I run:
```
 sudo ifup wlan0
```

What can I do to fix this on reboot?

---

