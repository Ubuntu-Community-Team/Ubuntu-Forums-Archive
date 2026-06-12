---
title: "Changing rules of ip routing"
date: 2014-05-04
forum: Networking &amp; Wireless
---

### Post by smss on 2014-05-04
Hi everybody, 
I have two network with three connections:
1th. Wireless Connection.   -> In order to connecting to WorldNet [Name: ra0] 
2th. Wired Connection 1.     -> In order to connect to other computers ( may be remote virtual computers ) [Name: eth0] 
3th. Wired Connection 2.     -> In order to connect virtual computers directly ( set the Virtual Box settings to Bridge to this )[Name: eth1] 
Now, I need to connect to my virtual servers through eth0 locally as I connect to WorldNet through ra0. 
In other words, I want to browse local virtual servers and worldNet at the same time.  
Note that I have changed wired DHCP ip begining and getway to 192.168.2.2 and 192.168.2.1 respectively.  

Thanks in advanced.

---

### Post by smss on 2014-05-05
Ok, I Solve it.
Just by ```
 ip r
```
I see to how ip r work in different situations and I replace the default routing row with this code ```
sudo ip r change default via `IP` dev ppp0  proto static
``` and it solved.
Thanks in advanced, smss!

---

