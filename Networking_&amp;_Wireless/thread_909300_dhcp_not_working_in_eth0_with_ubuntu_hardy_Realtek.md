---
title: "dhcp not working in eth0 with ubuntu hardy Realtek RTL8168B"
date: 2008-09-03
forum: Networking &amp; Wireless
---

### Post by leaphion on 2008-09-03
Hi! I'm kinda new to the linux and decided to install Ubuntu 8.04 to my newly bought laptop, which is Asus F6A. It has Realtek RTL8168B as an ethernet controller but I'm having some difficulties with it. I managed to connect it through a switch to my desktop (running UbuntuStudio) and when I assigned them both with static IPs (192.168.0.13 and 192.168.0.14) it worked fine. 

The problems start when I try to access internet with it and try to get an IP through DHCP. It doesn't find any DHCPOFFERS and in conclusion I can't even connect to my desktop anymore by assigning the static IP again.

I noticed that dmesg says the following (pretty many times):
NETDEV WATCHDOG: eth0: transmit timed out
r8169: eth0: Link up

Any ideas?

---

### Post by leaphion on 2008-09-03
Have to bump. Sorry. I'm just a wee bit desperate. :(

---

### Post by leaphion on 2008-09-04
Ummm... Okay. It just started working. Out of nowhere. Sorry for the disturbance.

---

