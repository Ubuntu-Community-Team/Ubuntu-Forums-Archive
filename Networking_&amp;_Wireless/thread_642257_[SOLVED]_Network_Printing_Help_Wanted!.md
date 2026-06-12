---
title: "[SOLVED] Network Printing Help Wanted!"
date: 2007-12-16
forum: Networking &amp; Wireless
---

### Post by Rich930 on 2007-12-16
Hey guys, im back with more problems! lol,

I have a Hp Deskjet 970Cxi connected via parallel on port 1 on a netport express print server.  The ip address is 192.168.1.6 which i have no problem connecting to via my web browser to configure it e.t.c. Only problem is, i have no idea how to connect to it properly to print from it in Ubuntu. It definatley works, coz i can get my windows machines to use it fine. But ive tryed System>Admin>Printing>Internet printing protocol(IPP) and i entered the IP into "Host" but it just sits there and says "Scanning" and does nothing more.

I dont know any commands to print from terminal or anything. 

Please help!

Thanks. :D

---

### Post by HermanAB on 2007-12-16
It probably uses IPP on port 9100.  Use telnet and see if it answers:
$ telnet 192.168.1.6 9100

Cheers,

Herman

---

### Post by Rich930 on 2007-12-21
hey thanks, s'all sorted now!

---

