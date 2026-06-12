---
title: "[SOLVED] cannot ssh from the outside"
date: 2008-09-10
forum: Networking &amp; Wireless
---

### Post by rickfun101 on 2008-09-10
Hi, 

I cannot connect from the internet to my ubuntu server on port 22. The router has been checked and I can ssh from the local lan. 

Output of "netstat -ltn":
tcp6 0 0 : : :22 : : : *  LISTEN

ufw is not loaded

iptables (input chain) record show:
ACCEPT tcp -- anywhere anywhere tcp dpt:ssh

Any ideas?

---

### Post by fwre01 on 2008-09-10
howabout running 

```
sudo tcpdump -i eth**XX** dst port 22 
``` Then make an SSH attempt from outside the network, if you dont see the right packets you know the packets arent reaching the server :-)

---

### Post by rickfun101 on 2008-09-11
Thanks for the reply. 

NAT table on the router was corrupted. Working now.

---

