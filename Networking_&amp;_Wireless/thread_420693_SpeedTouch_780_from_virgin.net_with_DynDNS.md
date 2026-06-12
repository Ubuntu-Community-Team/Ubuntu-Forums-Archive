---
title: "SpeedTouch 780 from virgin.net with DynDNS"
date: 2007-04-23
forum: Networking &amp; Wireless
---

### Post by Clear Line Web Design on 2007-04-23
I'm trying to set up a dapper box at home that I want to be able to access from everywhere.

I've got a SpeedTouch 780 from virgin.net which works fine with the dapper box (and a bunch of XP machines) when all the machines use DHCP to get addresses in 192.168.*.*.

However, when I assign the public IP of the router to the Ubuntu box and restart the networking on that box, the network becomes unreachable. 

Typing "ifconfig" on the dapper box shows that the IP for eth0 is set to the public IP and the correct DNS servers are set in /etc/resolv.conf but I can't access any network services from there. Nor can I ping that IP from any of the XP machines in the network.

Has anyone else had this problem or been able to fix this?

---

### Post by PriceChild on 2007-10-13
I think you should check your netmask and gateway, if these aren't correct then set a static ip on dapper.

---

