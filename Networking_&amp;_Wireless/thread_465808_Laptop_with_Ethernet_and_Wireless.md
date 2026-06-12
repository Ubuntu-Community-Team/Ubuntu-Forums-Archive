---
title: "Laptop with Ethernet and Wireless"
date: 2007-06-06
forum: Networking &amp; Wireless
---

### Post by boucek on 2007-06-06
Hi, this is my first post on the forums. 

I have a Fujitsu-Siemens Lifebook S Series running Debian Etch. It currently has two working NICs; one PCMCIA Belkin wireless card, and one 10 Mbit Ethernet. Each works perfeclty independently, but I cannot seem have both active simultaneously.

I also have a desktop system running Debian Etch with a 10 Mbit Ethernet connection, perfectly functioning.

I am attempting to use my laptop as an intermediary "proxy" server, updating the packages on the desktop via the Ethernet to the laptop to wireless connection. In other words, a debian solution to something like AnalogX Proxy for Windows XP.

Desktop:
Eth0: 10.0.0.100

Laptop:
Eth0: 10.0.0.101
Wlan0: 192.168.0.50

Wireless Router: 192.168.0.1

Verbose, step-by-step solutions, or links to such guides would be greatly appreciated. Thanks,

---

### Post by boucek on 2007-06-06
I solved the issue.

1. Set gateway on desktop as ethernet IP of laptop
2. Change /proc/sys/net/ipv4/ip_forward from "0" to "1"

---

