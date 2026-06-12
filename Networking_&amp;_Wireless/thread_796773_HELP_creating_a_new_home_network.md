---
title: "HELP: creating a new home network"
date: 2008-05-16
forum: Networking &amp; Wireless
---

### Post by twig43 on 2008-05-16
hello forum members im going to be setting up a network for my house but i need some help. i have a cable modem that i will be using  but i need help on configuring a wireless network and sharing a wired network with another computer in the house 
i have a cable modem and a linksys (WRG54T) wireless router.
also will there be any problems sharing a connection with a computer running XP?

---

### Post by mfaust731 on 2008-05-16
not at all, the xp machine doesnt care what else is connectted to the router.
Im not sure I understand what your asking when you say "share the connection" I assume you have the cable modem connected to the WAN port on the linksys, and the ubuntu and XP machines will access the internet and each other through the linksys router. Should be very easy stuff.
Just incase you dont know the computers and the linksys's IP address should be something like 192.168.1.X, where x is different on each device. 1,2,3, etc.   The subnets must all match, set them to 255.255.255.0
and the gateway for the network will be the ip address of the linksys router

---

