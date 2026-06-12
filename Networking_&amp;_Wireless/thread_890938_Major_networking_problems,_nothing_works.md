---
title: "Major networking problems, nothing works"
date: 2008-08-15
forum: Networking &amp; Wireless
---

### Post by Jarre on 2008-08-15
Hi,

problem with Ubuntu Server 8.04.1 (and Desktop 8.04.1). First of all, installation hangs at 'Scanning the mirror', but after killing some processes got around that. 

After booting to newly installed system I see that I get an IP address from ISP and /etc/resolv.conf is correct. Anyway, no packets are transferred; nothing goes. I can ping my modem with it's IP address, but nothing further that doesn't work. Ping, traceroute, http, ssh; nothing is working. 

I've tried with two NIC's: internal motherboard SiS based and external 3Com card at PCI slot. 

Route command's output:

```
$ route -n
Destination  Gateway      Genmask        Flags Metric Ref Use Iface
192.168.0.0  0.0.0.0      255.255.255.0  U     0      0   0   eth0
0.0.0.0      192.168.0.1  0.0.0.0        UG    100    0   0   eth0

```

ifconfig shows that my IP address is 192.168.0.108.

Basically my question would be: what can I do or where to start solving this problem?

See also my previous post on almost same kind of problem: [http://ubuntuforums.org/showthread.php?t=848536]("http://ubuntuforums.org/showthread.php?t=848536")

---

### Post by chili555 on 2008-08-15
Are you sure the modem has an IP address from the ISP? Can you log on to its administration pages with [http://192.168.0.1](http://192.168.0.1) and see if it is actually connected to the ISP? If not, you might power cycle it. Can you get returns from:```
ping -c3 209.85.165.103
```Thanks.

---

