---
title: "network-admin phone #"
date: 2007-04-05
forum: Networking &amp; Wireless
---

### Post by markhh on 2007-04-05
I am using a PCMCIA 3G device on Ubuntu 6.06 to connect to the internet. Everything works fine except that I keep having to re-enter my ISP phone # in the network-admin dialog. I have located the number correctly saved in /etc/chatscripts/ppp0 (ATDT*99#) but it won't load into the entry widget of the dialog. If I edit the ppp0 file & remove the leading '*' the numbers '99' will show, but not the '#'. So it appears as though only numeric characters are allowed to be loaded. If I manually enter the ISP #, I can activate the connection. I am using the stock 6.06 release with the pppd executable @ V2.4.4b1. I have seen on the internet that some people have upgraded & that their 3G connection no longer works, so I am reluctant to follow this route in order try to resolve my problem. Any ideas please?

---

