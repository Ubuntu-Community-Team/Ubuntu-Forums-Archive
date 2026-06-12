---
title: "My Internet/Network Woes"
date: 2007-10-28
forum: Networking &amp; Wireless
---

### Post by SupplanterAU on 2007-10-28
Since doing a clean install of Gutsy I have stopped being able to access the internet.

I was using Feisty without any troubles.  I am using a PCI network card connected to an 8 port switch; my adsl modem is connect to it as well as a laptop with Vista.

I am also using static IPs.

I dual boot the same PC in XP and don't have any trouble.

In Gutsy the Network Monitor applet reports a connection, but it says that I am connected via "usb0", not "eth0", and I don't have any usb network adaptors on the PC :-k

In the "network device" list in network tools there are "eth0", loopback, "unknown interface (usb0)" and "unknown interface (usb0:avahi)"

How can I tell Gutsy to use eth0 as the default network device?

---

### Post by SupplanterAU on 2007-10-29
Seems to be related to the network manager, and not the IPv6 problem that others are experiencing.

I don't want to reinstall Feisty:(

---

