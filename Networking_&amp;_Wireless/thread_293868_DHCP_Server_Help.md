---
title: "DHCP Server Help"
date: 2006-11-05
forum: Networking &amp; Wireless
---

### Post by cmoney85 on 2006-11-05
Okay here is my setup that i have. I have a linksys router connected to my ubuntu machine and to 2 windows xp pro machines. I want to have my ubuntu box setup to be a dhcp server. I have it all setup and thought i had to ready to go but no internet on the windows xp boxes, granted the ubuntu server is still connected to the router and the windows xp machine is hooked up to the back of the ubuntu server. I think it's a dns issue because i can't ping dns but i can ping the ubuntu dhcp server. I have tried alot of stuff but i just can't figure out what i am doing wrong? ](*,)

---

### Post by cmoney85 on 2006-11-05
no one? :(

---

### Post by dmizer on 2006-11-06
a dhcp server is a router.  as far as handing out ip addresses are concerned, they are the same.  it most likely is an issue with ip conflict.  your router and your ubuntu box are both trying to hand ips to your windows machine.  it's one or the other, but not both.

what is the need for having your ubuntu box as a dhcp server rather than your router?  your router's firewall is (for the most part) a better firewall than a software firewall.  as it's said, "you have to go through a hardware firewall (router), but you just go around a software firewall (ubuntu)."

---

