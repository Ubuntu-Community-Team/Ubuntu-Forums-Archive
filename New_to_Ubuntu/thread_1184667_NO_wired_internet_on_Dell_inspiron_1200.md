---
title: "NO wired internet on Dell inspiron 1200"
date: 2009-06-11
forum: New to Ubuntu
---

### Post by lonewolf1222 on 2009-06-11
I just put Ubuntu 9.04 on my friends old Dell Inspiron 1200 and I cannot get the wired connection to work. When I plug the ethernet cable in it will load and try to connect but then it will fail.

---

### Post by briguy47 on 2009-06-13
> **lonewolf1222 said:**
> I just put Ubuntu 9.04 on my friends old Dell Inspiron 1200 and I cannot get the wired connection to work. When I plug the ethernet cable in it will load and try to connect but then it will fail.


If you are using dhcp, I would try this in a Terminal:
```
dhclient eth0
```Assuming your card is at eth0.  You can find out by typing this in a terminal:```
ifconfig
```If that doesn't work, just post your results from running **ifconfig** and we can go from there.  :D

---

