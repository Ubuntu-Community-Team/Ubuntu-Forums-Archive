---
title: "iptables: redirect to local page"
date: 2022-10-14
forum: Networking &amp; Wireless
---

### Post by oscarcap on 2022-10-14
Hi, best regards

I have a computer with ubuntu server 20.04 which acts as a router, it has 2 network cards where one receives an internet connection and the other uses dhcp and through iptables I mask the packets so that they go out to the internet, up to this point everything works fine.

I want to know if it is possible using iptables that when a LAN client requests a specific page, for example facebook, it is redirected to a local page where a warning is made that it is prohibited to access that site.

I manage to block access to the page using a FORWARD rule as follows:

iptables -I FORWARD -p tcp --dport 443 -m string --string facebook.com --algo bm -j DROP

but in this way I cannot show the user the page that informs him of the prohibition, is there a way to do this redirection?

thanks

---

