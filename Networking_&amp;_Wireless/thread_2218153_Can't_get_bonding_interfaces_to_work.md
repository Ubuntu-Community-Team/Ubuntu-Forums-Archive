---
title: "Can't get bonding interfaces to work"
date: 2014-04-19
forum: Networking &amp; Wireless
---

### Post by maazmahmood on 2014-04-19
Everytime I put in the following code (below). The problem is that network devices become unmanaged. I set the managed to true. That didn't work. when I do the ifconfig it is missing the "bond0" ip address information

```
[FONT=arial]bonding mode=0 miimon=200[/FONT][FONT=arial]
[/FONT]
[FONT=arial]auto lo
[/FONT]
[FONT=arial]iface lo inet loopback

[/FONT]
[FONT=arial]auto eth2
[/FONT]
[FONT=arial]iface eth2 inet manual
[/FONT]
[FONT=arial]bond-master bond0

[/FONT]
[FONT=arial]auto eth3
[/FONT]
[FONT=arial]iface eth3 inet manual
[/FONT]
[FONT=arial]bond-master bond0

[/FONT]
[FONT=arial]auto bond0
[/FONT]
[FONT=arial]iface bond0 inet static
[/FONT]
[FONT=arial]address 192.168.0.10
[/FONT]
[FONT=arial]netmask 255.255.255.0
[/FONT]
[FONT=arial]gateway 192.168.0.254
[/FONT]
[FONT=arial]dns-nameservers 192.168.0.1
[/FONT]
[FONT=arial]bond-mode 0
[/FONT]
[FONT=arial]post-up ifenslave bond0 eth2 eth3
[/FONT]
[FONT=arial]pre-down ifenslave -d bond0 eth2 eth3[/FONT]
```

---

