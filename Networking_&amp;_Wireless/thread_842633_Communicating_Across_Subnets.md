---
title: "Communicating Across Subnets"
date: 2008-06-27
forum: Networking &amp; Wireless
---

### Post by Black Mage on 2008-06-27
Hey, I have a router with DHCP and port forwarding(A netgear FVS114) and that router connects to a wireless router. Now for the internal ip of first router it is 192.168.1.x and the wireless is 192.168.182.x. So I'm wondering would I be able to communicate between two computers on different subnets? 

What I am really trying to get done is have computers on the wireless communicate with a printer server on the wired connection.

---

### Post by spd106 on 2008-06-28
This is a bit of an over-complicated set-up, can't you set the Wifi router to Access Point mode? Which effectively turns it into a bridge. Then both networks will use the same subnet and DHCP server, simplifying the configuration and probably giving you a small speed boost too.

The alternative is to find which ports the printer uses and have those forwarded too.

---

### Post by Black Mage on 2008-06-30
Do you mean I should port forward the printer on the router and access it from a url?

---

