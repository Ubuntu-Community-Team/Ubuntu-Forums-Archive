---
title: "Embarrasing question"
date: 2005-09-23
forum: Networking &amp; Wireless
---

### Post by deltablaze on 2005-09-23
Um how do you....find your local ip? THanks O:)

---

### Post by Gobbla on 2005-09-23
ipconfig

---

### Post by deltablaze on 2005-09-23
that was for windows, doesnt work for me on ubuntu

---

### Post by bsussman on 2005-09-23
New Way:
```
> ip addr ls
``` 
Old way:
 ```
> ifconfig
```

---

### Post by El Cubano on 2005-09-23
/sbin/ifconfig will show you all the active interfaces on your system and their respective addresses.

---

### Post by 23meg on 2005-09-23
how about "sudo ifconfig"?

---

### Post by wmcbrine on 2005-09-23
I dunno an i*p*config (except on Windows?), but i*f*config works. Edit: Oops, beat me to it. Let me just add that you don't need to sudo ifconfig to get the info -- only if you want to set it.

You might want to elaborate on what you mean by "local IP". 127.0.0.1 always works, but only for talking to yourself, so I'm guessing that's not what you want. :) LAN IP? ifconfig is one solution. You can also check from the menu: Applications, System Tools, Network Tools, and pick the correct interface under "Network device" (usually eth0). The address you present to the outside world? There are many choices for finding it, such as the ever-popular web site IPChicken.com.

Mac OS X Tiger comes with a nice little Dashboard widget that shows you both the "inside" (LAN) and "outside" (WAN) addresses. There are probably similar things for Linux, but I'm not familiar with them.

Edit 2: Hmm, the "Network Tools" program misses some info that ifconfig reports, with the same privileges -- netmask, broadcast, hardware address. But it does get the IP.

---

### Post by deltablaze on 2005-09-24
Thanks guys. It's just I wanted to forward bittorrent ports/
Thanks again, I'm lovin Ubuntu :grin:

---

