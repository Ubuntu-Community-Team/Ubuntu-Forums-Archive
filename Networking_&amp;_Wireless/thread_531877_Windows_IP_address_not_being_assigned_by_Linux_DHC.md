---
title: "Windows IP address not being assigned by Linux DHCP server"
date: 2007-08-22
forum: Networking &amp; Wireless
---

### Post by WedgeWouldUseLinux on 2007-08-22
I'm try to network my Windows XP laptop with my Ubuntu Linux desktop set up as the server. When I set the XP laptop to obtain its IP address from the server, through the 192.168.0.1 gateway, it ends up setting the IP address to 192.168.0.1 - the exact same as the server it was supposed to get its address from. I have installed DHCP server and Samba, although I don't think Samba has much to do with this problem.

When I set my client IP address to static at 192.168.0.2, I can successfully ping both from the client to server, and vice-versa, but Samba and ICS still don't work. 

Anyone else had this problem?

Thanks in advance.

---

### Post by Seti on 2007-08-22
Correct me if I'm wrong but you also need some kind of DNS service going, even if you have an IP and network connectivity.

---

