---
title: "Connecting to Windows Network"
date: 2008-03-04
forum: Networking &amp; Wireless
---

### Post by Greyfox67 on 2008-03-04
System Specs:
Dual Boot
Ubuntu 7.10 & Windows Vista basic

Problem:
[B]Vista will connect to the network at work with no problem
Ubuntu will not[/B]

**Ifconfig:**

eth0: inet addr: (using static setup in Network configuration) 10.1.10.117 subnet mask: 255.255.224.0

Matches my ipconfig in windows

lo inet addr: 127.0.0.1 Mask 255.0.0.0

**results Network Interfaces:**
auto lo
iface lo inet loopback

iface eth0 inet static
netmask 255.255.224.0
gateway 10.1.0.1
address: 10.1.10.117

I've also tried an Auto DHCP setting in Network configuration to no avail.


No firewalls or even antivirus for that matter on Ubuntu configuration =. Also, under same configuration this laptop connects just fine whether wired or wireless at home.

Any thoughts anyone?

---

### Post by boeing777 on 2008-03-04
right now i'm at a public library and the wifi isn't working, i'm using my dual boot vista right now.  wireless was working perfectly at home. so i don't really know what my problem is anyone?

---

### Post by Iowan on 2008-03-05
I'm probably missing something important - couldn't be this easy...
Edit **/etc/network/interfaces** file (I like nano) and add an **auto eth0** line.Then run:```
sudo /etc/init.d/networking restart
```

---

