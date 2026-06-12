---
title: "MAC Addresses and network (general question)"
date: 2008-06-08
forum: Networking &amp; Wireless
---

### Post by MadMax2 on 2008-06-08
This is a general question. I looked in the router page and saw LAN, WAN and wireless with MAC numbers. I'm curious as to where/which these devices are. I have a cable modem (ISP says it's "invisible to network"(?)) and a wireless router. None of the MAC numbers are the desktop or laptop. Is the MAC for WAN the broadband modem  and to addresses for the router (LAN + router)?

---

### Post by Mgiacchetti on 2008-06-09
you could try  192.168.100.1 and see if that page shows a mac, if so, match it up with your numbers...

---

### Post by jetsam on 2008-06-09
Most consumer routers are just little special purpose Linux based computers with two or three interfaces and a switch.  I'm pretty sure the mac addresses you're seeing are the addresses of the router's interfaces.  
WAN--> The WAN (Wide Area Net) side interface that should be connected to the broadband modem.
LAN--> The LAN (Local Area Net) side interface that connects to all the devices wired to the switch.  
wireless--> The wireless interface.  

If you type **arp -n** in a terminal, you should see if you look at the mac address belonging to your gateway's ip (generally 192.168.0.1 or 192.168.1.1) that it's the same as either the LAN or the wireless interface you see in the router's admin page.

---

### Post by MadMax2 on 2008-06-10
Yes thanks for that. I typed arp -n in a terminal and saw the MAC for the wireless which I'm on now (eth1). That will do for now.

---

