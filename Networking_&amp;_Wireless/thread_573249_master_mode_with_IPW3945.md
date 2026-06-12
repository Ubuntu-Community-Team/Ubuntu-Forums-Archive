---
title: "master mode with IPW3945"
date: 2007-10-11
forum: Networking &amp; Wireless
---

### Post by band-aid on 2007-10-11
Is there any way I can get master mode for my IPW3945 wireless card? It doesn't appear to be supported with the current IPW3945 driver that ships with ubuntu. Is it possible to run this card with hostap? I am trying to start an ad hoc connection... any suggestions?

---

### Post by chili555 on 2007-10-11
Are you sure you don't want:```
sudo iwconfig eth1 mode ad-hoc
```Works for my ipw3945. I have no other wireless setup to actually try an ad hoc connection, but the card surely goes into ad hoc mode.

---

### Post by michael003 on 2007-10-15
The IPW3945 driver doesn't seem to support master mode. I managed to setup an ad-hoc connection as follows:

```

sudo iwconfig eth1 mode ad-hoc
sudo iwconfig eth1 channel 1
sudo iwconfig eth1 essid mynetwork
sudo ifconfig eth1 192.168.1.1
```

I then ran a DHCP server on eth1 to provide the other computer with an IP address.

---

