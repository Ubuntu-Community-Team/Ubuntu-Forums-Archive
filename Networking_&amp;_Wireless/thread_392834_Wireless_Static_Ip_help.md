---
title: "Wireless Static Ip help"
date: 2007-03-25
forum: Networking &amp; Wireless
---

### Post by zeroo on 2007-03-25
So I installed all my driver for my wireless adapter and i think that works fine.  When I go to wireless network everything shows up.
But i'm running a static ip and I think that is why it will not let me connect.  It just says fails to connect. 
This is what I put under manual:
ip adress: 192.168.1.35
Net Mask: 255.255.255.0 
Gateway:192.168.1.1
Dns: 192.168.1.1

This is what I put for my other windows computers and it works fine.  Also right when I click my network it says fails to connect. I thought that it usually takes a while to attempt the connection.

I dont really know what to put for Gateway and Broadcast.

Does anyone have any ideas why it is not working?

---

### Post by Floppyjoe on 2007-03-25
If you are using network-manager static IP's will not work because it is designed to retrieve IP addresses from DHCP.

---

### Post by zeroo on 2007-03-25
Okay, then what do you recommend I use?

---

### Post by Floppyjoe on 2007-03-25
If you are using a laptop I would recommend staying with network-manager but using dhcp but if this is for a desktop computer I might remove network-manager and either use DHCP or Static which would be set up in the /etc/network/interfaces file.

---

