---
title: "Red leds!? Those were green..."
date: 2006-12-28
forum: Networking &amp; Wireless
---

### Post by unwiredbrain on 2006-12-28
Hi guys. I've got a very strange problem: the leds next to the ethernet connector port of my ethernet controller are red i.e. not working.

I've got a Marvell 88E8053 (Yukon) PCI-E Gigabit Ethernet Controller. And worked up to some minutes ago. Suddenly the connection went down and the ugly red lights appeared on the back of my pc.

Strange behaviour, also because the wireless connection still works! That means that it's not a problem dealing with the router, but with the Ethernet card itself...:-k 

```
ifconfig -a
``` outputs the right things, and so does ```
sudo lshw -C network
```

Moreover, linux can see the router, but cannot identify itself inside the dhcp...:confused: 
I mean: I can see the router's MAC but I can't see the IP gateway and all the rest...:confused: :confused: :confused: 

Is my card broken? Or is the router? Or is me -- I messed with something?

I really don't know...

I've got a Linksys WAG200G

Thanks in advance
-- 
unwiredbrain

---

### Post by unwiredbrain on 2006-12-28
Even stranger late behavior: the interface restarted working again an hour later... :-k 8-[ :-\"

---

