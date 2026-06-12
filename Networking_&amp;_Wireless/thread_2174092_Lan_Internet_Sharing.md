---
title: "Lan Internet Sharing"
date: 2013-09-12
forum: Networking &amp; Wireless
---

### Post by WWWXXX on 2013-09-12
Hi:

I am new to Ubuntu, currently I have a linux machine with three network cards.
eth0 is connected to the internet, and I hope to set static IP for eth1 and eth2 for example 192.168.0.x and both of them can access to the internet.

I have tried [https://help.ubuntu.com/community/Internet/ConnectionSharing#GUI_Method_via_Network_Manager_.28Ubuntu_12.04.29](https://help.ubuntu.com/community/Internet/ConnectionSharing#GUI_Method_via_Network_Manager_.28Ubuntu_12.04.29) but none of them really works...

Thanks.

---

### Post by newbie-user on 2013-09-13
All you really have to do is set ip forwarding and a single default route. To set ip forwarding, edit /etc/sysctl.conf and uncomment this line:
```
#net.ipv4.ip_forward=1
```

Your eth0 should be the default route since it is connected to the Internet. Just make sure you don't set any routes for the other two network cards.

---

