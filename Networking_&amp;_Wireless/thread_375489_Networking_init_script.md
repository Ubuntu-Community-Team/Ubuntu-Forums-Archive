---
title: "Networking init script"
date: 2007-03-03
forum: Networking &amp; Wireless
---

### Post by cliff01 on 2007-03-03
What should be in my "/etc/network/interfaces file? I think I screwed it up. Is there a default I can start with?
Thanks! (NewB)

---

### Post by jglen490 on 2007-03-03
If it'll help this is what mine looks like.

```
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
wireless-essid Aardvark

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhc
```

---

### Post by kirbs on 2007-03-03
hey, i had the same problem just now. I fixed it by deleting the /network/interfaces file, and launching the Network Config applet. It should show your wired/wireless connections as unconfigured, with a [-] in their status.
Click the [-] and it configure the eth for w/e you want, DHCP prolly

hope that works

---

### Post by cliff01 on 2007-03-04
Well that sure cleaned up the file. I also don't see my wireless pci ethernet card when I do the "ifconfig" command. It only gives me the "lo" loopback thingy. I sure do hope that after a while I don't sound like such an IDIOT!
Thanks

---

### Post by kirbs on 2007-03-05
have you installed the drivers for your PCI wireless card?

---

