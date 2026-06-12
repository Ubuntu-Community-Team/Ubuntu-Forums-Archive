---
title: "[SOLVED] need help understanding /etc/network/interfaces"
date: 2007-07-16
forum: Networking &amp; Wireless
---

### Post by slimjim83 on 2007-07-16
I don't seem to understand why there are so many entries in my /etc/network/interfaces file.  I have a TravelMate 2480 laptop with a modem, 10/100 ethernet card, and a Broadcom 4318 wireless card.  Here's the output of /etc/network/interfaces...
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
```
Here's what I don't understand:
- Why are there 3 eth entries
- What is ath0 (my thoughts are my modem, but I'm not sure)
- Why do I have a wlan0 entry if its not used.

The reason I say that wlan0 isn't used is that when I am connected to a wireless network, if I look at my "connection information" in network manager, it shows my interface as "Wireless Ethernet (eth0)".  I would think that eth0 would be my 10/100 NIC, wlan0 would be Broadcom wireless card, and I don't have the slightest idea what my modem should show up as.

Can somebody please explain this to me?

Also, should there be 3 entries (modem, ethernet, wifi) in /etc/iftab?  Here is the output for it
```
eth0 mac 00:17:c4:01:7f:a9 arp 1
eth1 mac 00:16:36:c7:48:92 arp 1
```
(eth0 is my wireless card's mac)

slim

BTW: I am using NDISWrapper for my wireless.

---

### Post by kevdog on 2007-07-16
Is your wireless working???

If everything is working, you can remove the extra interface names from the /interfaces file with no problem.  
Iftab is used to lock the interface name (wlan0, eth0) to a certain MAC address.  If you are missing an entry you can add it by hand, but its not necessary.  

ath0 is simply notation for atheros cards that typically associate themselves with the ath interface name.  I dont believe modem in any way relate to the interface file, because the have a different config file.

---

### Post by slimjim83 on 2007-07-23
Thank you so much, that was what I needed to know.

---

