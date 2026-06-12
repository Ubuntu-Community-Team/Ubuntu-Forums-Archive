---
title: "Incoming ping is not working"
date: 2015-12-09
forum: Networking &amp; Wireless
---

### Post by john492 on 2015-12-09
Hi;

I have installed Ubuntu Server 15.10. There are two network interfaces. One is for global internet, another is for internal network.
Server IP is xxx.xxx.xxx.55

```
ping from server to google.com is OK
ping from server to another IP in same network: xxx.xxx.xxx.56 is OK
```
but

```
ping from another IP in same network to server is not OK
```
So, it seems that outgoing ping is OK but incoming ping is not OK, server is not reachable for incoming connections. 

any idea how to deal? :mad::mad::mad::mad:

---

### Post by newbie-user on 2015-12-09
Did you set up iptables? If so, you would have to allow for ICMP to pass through the firewall.

---

### Post by john492 on 2015-12-10
i have not set up iptables :( can you have any idea how to do it?

---

