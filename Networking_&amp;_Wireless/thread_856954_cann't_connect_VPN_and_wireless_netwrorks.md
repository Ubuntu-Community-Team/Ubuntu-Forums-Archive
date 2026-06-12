---
title: "cann't connect VPN and wireless netwrorks"
date: 2008-07-12
forum: Networking &amp; Wireless
---

### Post by giolekva on 2008-07-12
on my sony vaio vgn-fe21b laptop i've installed kibuntu 8.04.1 hardy. i cann't connect to vpn with knetworkmanager (there is no plugin i think). also it cannot detect any wireless networks (i have dlink router and i can connect to it with my itouch). how can i solve both problems?

---

### Post by superprash2003 on 2008-07-12
in your terminal type iwconfig and post output here

---

### Post by giolekva on 2008-07-12
```
lo        no wireless extensions.

eth0      no wireless extensions.


```
i think it hasn't installed wireless driver.

---

### Post by superprash2003 on 2008-07-12
yes.. in your terminal type lshw -class network   to find out which card you have exactly

---

