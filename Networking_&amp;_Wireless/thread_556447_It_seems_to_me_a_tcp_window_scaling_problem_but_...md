---
title: "It seems to me a tcp window scaling problem but ..."
date: 2007-09-21
forum: Networking &amp; Wireless
---

### Post by gi0 on 2007-09-21
I intalled feisty on a destop dell inspiron 530s.
The network card was not recognized but I added the right driver downloaded from intel and the connection was up.
I'm able to ping an external ip but I can connect only some server: with firefox I'm able to browse [www.google.com](www.google.com) but if I follow some link from its page some host are not found. 

The same with ping : some host are reachable and some are not. 
Apt-get is not able to reach the repository.

After a google research I found reported the problem of tcp_window_scaling and I tried to apply the workaround suggested : I switched off IPV6 (in modprobe.d) and I disabled tcp_window_scaling with:
echo 0 > /proc/sys/net/ipv4/tcp_window_scaling
but it didn't work!

Please help me!

---

### Post by nixfedex on 2007-09-21
Please correct me if I am wrong, but tcp_window_scaling enabled will give you better results. Linux kernel (2.6?) has this feature of auto tune which should be by default enabled. 

Can it be that your network is slow? Can you try a mtr to say [www.google.com](www.google.com)

---

