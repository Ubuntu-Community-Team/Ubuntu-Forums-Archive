---
title: "Wireless? Networking Problem"
date: 2007-06-18
forum: Networking &amp; Wireless
---

### Post by rsteinmetz70112 on 2007-06-18
I installed Xubuntu on an old pc. 

I originally had a wired USB ethernet adapter.

I upgraded over the network to Feisty and took the ethernet adapter off.

I installed an Ativa Wireless G USB Adapter AWGUA54 which is as fa as I can tell the same as Belkin F5D7050 v4000 Wireless G USB. 

The Belkin uses the Zydas ZD1211 chipset as can be confirmed, the FCC ID, with is the same on both.

The USB adapter installed as eth1 and the command line utilities work. ping, nslookup etc.,
however whenever I try a X-11  browser (Firefox), I get nothing. 

I can look at ifconfig and see that there are no packets being transmitted. no drpos or error no packets.

Anybody got any ideas?

I think the wireless link is working OK but something is wrong with the network configuration.

---

### Post by Cyber-J on 2007-10-13
This adapter works under Fiesty and Gutsy right out of the box. I use it as a backup wireless adapter to get me online so I can install the necessary drivers for my laptop's built in broadcom wireless chipset. Not a bad little investment for $40 at Office Depot.

---

### Post by frankos44 on 2007-10-13
Try setting the router to use DHCP and set the "Wireless connection"  to roaming in "Network Settings".

I have noticed its also best to set the "Wired Connection" to Roaming too even if you dont intend to use it, for some reason this stopped my wireless conection from working reliable when set to static.

In my case I have a server connected to my network aswell which in needs to be set to static IP address, so i simply made all address from 192.168.0.128 upwards to use DHCP while addresses below this remaim static. 

Not sure if this helps.

---

