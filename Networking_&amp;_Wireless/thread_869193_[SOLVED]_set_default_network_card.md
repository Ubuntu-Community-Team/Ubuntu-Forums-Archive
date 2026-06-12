---
title: "[SOLVED] set default network card?"
date: 2008-07-24
forum: Networking &amp; Wireless
---

### Post by ilovelinux33467 on 2008-07-24
Hi in one pc I have 3 network cards, 2 which I don't use. Is there any way to set the default network card for roaming mode because at the moment it just selects one of the other 2 I don't use and I have to manually click the network icon and select the one I use. The one I use is eth0 and the other 2 I dont use it eth1 and eth2

---

### Post by Endwin on 2008-07-24
You could stop the other two from coming up by default by removing them from **/etc/network/interfaces** That way they would not come up looking for IPs. To use them you would have to explicitly do so.

---

### Post by ilovelinux33467 on 2008-07-24
> You could stop the other two from coming up by default by removing them from /etc/network/interfaces That way they would not come up looking for IPs. To use them you would have to explicitly do so.

Ok thanks I'll try that

---

