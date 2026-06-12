---
title: "I can see my router but can't connect"
date: 2007-02-04
forum: Networking &amp; Wireless
---

### Post by Notclive on 2007-02-04
I've tried before to get my linux partition on the internet but i gave up, I did manage to get my card working and it can see my routers essid but nothing else, I've tried static and DHCP (I think this might be the problem). I'm using a bt voyager 2091 router wirelessly. Any ideas?

---

### Post by bnuytten on 2007-02-18
The output of the folllowing commands could be very helpfull:
```
ifconfig
iwconfig
route
```

What is your router's IP address?

---

### Post by sdide on 2007-02-18
hey. 

Please post output from:

#iwlist scan 
#iwconfig 
#ip link
#ip neigh

---

