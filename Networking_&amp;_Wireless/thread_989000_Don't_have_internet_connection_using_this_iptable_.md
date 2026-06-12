---
title: "Don't have internet connection using this iptable rules"
date: 2008-11-21
forum: Networking &amp; Wireless
---

### Post by jennifer.ayag on 2008-11-21
Can anyone please help me? I want to ask if my rules are correct.

Here's my setup:

IP ADD provided by the ISP: 121.x.x.133
ROUTER'S IP (ALSO AS GATEWAY): 192.168.1.1
External IP: 192.168.1.98
Internal IP: 192.168.1.99
Subnet Mask: 255.255.255.0

Please see attached images re my iptables (rules).

POSTROUTING (Default:ACCEPT)

SNAT if output interface is ETH0 (IP for SNAT is 121.x.x.133)

Rules above won't allow me to access any sites in my web browser. Also my email.

Thanks in advance.

---

### Post by superprash2003 on 2008-11-21
if you think it is iptables which is causing the problem.. you could flush iptables [http://prash-babu.blogspot.com/2008/10/how-to-flush-or-remove-all-iptables.html](http://prash-babu.blogspot.com/2008/10/how-to-flush-or-remove-all-iptables.html)

---

