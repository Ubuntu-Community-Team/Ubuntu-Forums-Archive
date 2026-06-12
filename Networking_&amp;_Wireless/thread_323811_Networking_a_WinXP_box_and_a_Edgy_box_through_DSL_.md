---
title: "Networking a WinXP box and a Edgy box through DSL router"
date: 2006-12-22
forum: Networking &amp; Wireless
---

### Post by Ptero-4 on 2006-12-22
Hi. I got DSL a while ago, my setup is like this. My Edgy box and the family's XP box are both connected to the 4 port DSL router (each box in a separate port) using DHCP ethernet and I wanted to know. Is posible to make both computers see each other and share folders and devices without changing the physical setup (which was done by the technician of my DSL ISP)?

---

### Post by maxamillion on 2006-12-22
You should be able to just the way it is. The way home routers work is they create a private LAN and NAT to the outside world through the IP your service provider gives you. Therefore if both computers are connected to the router they will be on the same network and subnet. You should be able to just host files on one and browse with the other via Samba.

Since your physical setup isn't binding I recommend you consult [www.ubuntuguide.org](www.ubuntuguide.org) with your questions and then post back if you come across anything you need help with.

I assume you want to see shared folders that reside on your windows machine while using your ubuntu machine, which can be done from within Nautilus with the network browser feature.

If you would like to host files from your ubuntu machine so that the windows machine may browse them consult this link [http://ubuntuguide.org/wiki/Ubuntu_Edgy#Samba_Server](http://ubuntuguide.org/wiki/Ubuntu_Edgy#Samba_Server)

...hope that helps.

---

