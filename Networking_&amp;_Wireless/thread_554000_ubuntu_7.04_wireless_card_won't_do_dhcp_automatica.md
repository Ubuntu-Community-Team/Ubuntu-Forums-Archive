---
title: "ubuntu 7.04 wireless card won't do dhcp automatically"
date: 2007-09-18
forum: Networking &amp; Wireless
---

### Post by carljm on 2007-09-18
I have a Netgear MA401 wireless PCMCIA card on a fresh Ubuntu 7.04 install.  I used to use the orinoco driver under Ubuntu 6.06 for over a year and it always worked great.  7.04 tried to load the hostap driver instead (which I gather has some more features) but hostap module totally hangs the system (Dell Inspiron 1100 laptop) as soon as it loads, so I blacklisted it in /etc/modprobe.d/blacklist and am still using orinoco.

The card works, but it won't automatically go get a DHCP address when inserted (or the computer is booted with the card in).  If I do a "sudo dhclient eth1" (or a "sudo ifdown eth1; sudo ifup eth1") it happily gets an address and works fine, or if I do a "sudo /etc/init.d/networking restart" it takes a long time trying all the interfaces, but in the end works fine too.

My internal Broadcom ethernet on eth0 doesn't have any trouble picking up a DHCP address automatically from the same network.  How can I get my wireless card to run DHCP automatically?

My /etc/network/interfaces file:

```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

auto eth1
iface eth1 inet dhcp
wireless-essid mccoln

```

(I've also tried removing the wireless-essid line to put it in "roaming mode", but that doesn't make any difference).

Thanks in advance for any help!

---

