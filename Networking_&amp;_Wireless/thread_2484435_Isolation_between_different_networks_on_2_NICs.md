---
title: "Isolation between different networks on 2 NICs"
date: 2023-02-26
forum: Networking &amp; Wireless
---

### Post by JimLS on 2023-02-26
Xubuntu 18.04 with 2 NICs.  Purpose was to isolate one network from the local LAN and internet.  It somewhat works in that I have 2 networks with different ranges of addresses - 192.168.1.x and 192.168.2.x.  And the PCs on the isolated network cannot reach the internet.  However, they can reach a web server on the machine with 2 NICs that connects to both networks.  How would I stop that?  I haven't done anything to default settings at this point.

---

### Post by aljames2 on 2023-02-26
Have you checked your port forwarding on the webserver?  You could also check your router to  see if it is denying all in & out traffic on the desired subnet like you want.

---

