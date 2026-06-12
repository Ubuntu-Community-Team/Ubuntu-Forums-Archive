---
title: "Router/Dns problem"
date: 2008-04-27
forum: Networking &amp; Wireless
---

### Post by il3dsm on 2008-04-27
Hello, right now I have the following setup: wireless router, server with the wireless card, router and my computer. 

Server should connect to the wireless router (192.168.254.xxx) and route packets to my computer (192.168.2.xxx) I haven't gotten that far yet and trying to access my router (192.168.2.1) from my computer. So far, I am able to ping it but when I try to access it using mozilla, galeon or konqueror, it can't open the page (I enter 192.168.2.1).

I am using an smc7004vbr router with 3c905cx-txm ethernet card. When I first connect, the packets 'recieved' are zero, packets only come when I ping 192.168.2.1

The network does not work on windows XP also, so the OS shouldn't be the problem. Any ideas? :(

---

### Post by superprash2003 on 2008-04-27
it could be a DNS problem. try changing DNS servers to opendns.. read this [http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html)

---

