---
title: "eth0 doesnt connect at boot or after login w/ nm"
date: 2007-02-23
forum: Networking &amp; Wireless
---

### Post by gr83 on 2007-02-23
did a quiet few upgrades, including kernel and restricted modules and since then eth0 wont automaticly connect to the network at boot or after login via network-manager even though if I select Wired Network from nm or execute "/etc/init.d/networking restart" it works fine.  wifi, eth1, works fine too and nm asks for a password everytime at login for wifi instead of connecting via eth0 when theres a link.

heres my /etc/iftab:
eth0 businfo 0000:07:00.0
eth1 businfo 0000:03:00.0

/etc/network/interfaces:
auto lo
iface lo inet loopback
auto eth0
iface eth0 inet dhcp

---

