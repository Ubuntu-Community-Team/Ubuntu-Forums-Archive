---
title: "Ethernet active No internet"
date: 2007-01-31
forum: Networking &amp; Wireless
---

### Post by tical2756 on 2007-01-31
I have a Thinkpad R30, with Intel 82557 Ethernet Pro 100 card,
I'm trying to connect through a cable modem connecet to a Belkin wireless router
internet works fine using MS XP

I have eth0 configured to DHCP and set to default
ifconfig
Link encap:Ethernet HWasddr 00:00:E2:6D:4C:05
inet6 addr: fe80::200:e2ff:f26d:4c05/64 Scope:Link
UP Broadcast multicast mtu:1500 Metric:1
rx packets:0 errors:0 dropped:0 overruns:0 frame:0
collisions:0 txqueuelen:1000
RX bytes:0 (0,0 b) TX bytes: (0.0 b)

I tried entering static IP address from XP
192.168.2.1
255.255.255.0
192.168.3.1
Neither worked

---

### Post by tical2756 on 2007-02-07
i finally figured out what's wrong.  I had to add irqpoll to my boot/grub/menu file 

Without irqpoll, my network card is recognized, but i cannot connect. I just get the DHCP sleeping error message.

With irqpoll enabled, my computer takes forever to boot, and seems to run incredibly slow. Plus I get an error message saying that some of the GNOME graphics cannot load...

What is irqpoll, and why do I need it to connect to the internet? Why would it slow down my computer so much?

---

