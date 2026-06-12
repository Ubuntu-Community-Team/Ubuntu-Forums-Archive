---
title: "Ubuntu obtains inet6 address"
date: 2005-08-20
forum: Networking &amp; Wireless
---

### Post by Kushou on 2005-08-20
Hi there,

Not sure if somebody has asked this kind of questions. I did a search and didn't find the answer.

Basically, I just install Ubuntu on my PC wich connect to my home router, sharing internet access with other PCs. The router has DHCP enabled. When I obtain IP address from the Ubuntu box, seems it got something **[COLOR=Red]inet6[/COLOR]** addr: xxxx::xxx<and so on>**/64**. I didn't change anything during setup. I can only ping the local loopback 127.0.0.1. The router is always unreachable. Just wondering what could go wrong. Have tried SuSE and Mandrike, both are working fine.

Any advice is greatly appreciated, thanks in advance.

- Kushou

---

### Post by heimo on 2005-08-21
To disable ipv6:
 ```
sudo gedit /etc/modprobe.d/aliases
#change: 
alias net-pf-10 ipv6
#to:
alias net-pf-10 off
``` 
restart

---

### Post by Kushou on 2005-08-22
Thanks heimo for the help. I did the modification and it no longer obtain ipv6 address. But it still cannot get a ipv4 address. I managed to install a copy of win2k, and it cannot obtain ip address either. Thought now the problem is with the network interface card, the driver may not be correct. I will try to figure it out. Thanks again for your help.

---

