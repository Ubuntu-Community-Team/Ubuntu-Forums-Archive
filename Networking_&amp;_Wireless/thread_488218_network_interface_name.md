---
title: "network interface name"
date: 2007-06-29
forum: Networking &amp; Wireless
---

### Post by mhanraha on 2007-06-29
I'm attempting to use airodump-ng,  I have an intel IPW3945 wireless card.  When I use airodump-ng ipw3945
it says not a network interface

iwconfig doesn't seem to have any information that I can deduce the name of my wireless card, any ideas where I can look?

---

### Post by spd106 on 2007-07-01
Try 
```
dmesg | grep ipw
```
or 
```
sudo lshw -class network
```

---

