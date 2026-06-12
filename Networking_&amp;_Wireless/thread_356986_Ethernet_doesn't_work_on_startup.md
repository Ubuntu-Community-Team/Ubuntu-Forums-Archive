---
title: "Ethernet doesn't work on startup"
date: 2007-02-09
forum: Networking &amp; Wireless
---

### Post by bdkoehler on 2007-02-09
Strange problem.

On startup, the eth0 interface claims to be on and "netstat -r" prints a routing table, but I cannot ping my gateway server.  However, if I run /etc/init.d/networking stop and then start everything works fine.

Anybody have an idea on what I'm missing?


/etc/network/interfaces
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.4
netmask 255.255.255.0
gateway 192.168.1.1

#auto eth1
#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp

```

---

### Post by ukripper on 2007-02-09
Try DHCP instead to compare the result. If DHCP resolves it then probably DNS is falling back.

---

### Post by bdkoehler on 2007-02-11
DHCP had the same issue.  As an experiment I swapped out the card (an LNE100TX v2.0) with a newer one from a different computer (LNE100TX v5.1).  The newer card has no issues, so it must be something about the old revision.

I'm actually impressed that the rev 2 card worked at all, since when I put that card in a Win2k box I couldn't get it to work at all.

---

### Post by ukripper on 2007-02-12
> **bdkoehler said:**
> Strange problem.

On startup, the eth0 interface claims to be on and "netstat -r" prints a routing table, but I cannot ping my gateway server.  However, if I run /etc/init.d/networking stop and then start everything works fine.

Anybody have an idea on what I'm missing?


/etc/network/interfaces
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.4
netmask 255.255.255.0
gateway 192.168.1.1

#auto eth1
#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp

```







Your eth0 is set to auto in interfaces that should force eth0 to start during kernal loading automatically. I see nothing wrong with interface file, try below though:


iface eth0 inet static
address 192.168.1.4
netmask 255.255.255.0
gateway 192.168.1.1
auto eth0

---

### Post by bdkoehler on 2007-02-12
The original interfaces file works fine.  Just seems to be an issue with the old revision of the Linksys card.  The greenboard had a v2.0 on it, and wouldn't work at all in a Win2l box I tried.  I've put a newer card with v5.1 on the greenboard in and works fine with no issues.

Thanks for the help.

---

