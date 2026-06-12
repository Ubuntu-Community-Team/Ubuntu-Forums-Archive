---
title: "network problem"
date: 2008-06-04
forum: Networking &amp; Wireless
---

### Post by eskay_karthik on 2008-06-04
I am having a problem with my network. I am able to browse internet, but the update manager and synaptics package installer does not work. Recently, I had taken my laptop to a different place, where I changed the ip for that network. but, now back home, I am not able to use package installers. ifconfig shows no ip for eth0. Is that the problem ?? How to solve ??

eskay

---

### Post by SpaceTeddy on 2008-06-04
mhm... first some bacis... 

can you please post the output of the following commands

```
ifconfig
route -n
cat /etc/resolv.conf
cat /etc/network/interfaces
cat /etc/apt/sources.list
sudo iptables -L
```

the first command shows your network cards (as you already know :) )
the second will show your routing table
the third will show what dns servers you have configured
number four shows the boot configuration of your network cards (don't worry if this is almost empty -network manager will then handle the devices)
the fifth will show your software sources and if they are configured correctly
the last one will show if you have any firewall/paket filter rules loaded that prohibit you to access something.

let's see if we can figure this out :)

---

### Post by eskay_karthik on 2008-06-05
hey, 
i resolved the problem. was simple, i did not think of that before. forgot to change the network proxy settings. :)
thanks for explaining me what those commands do. will be helpful in future.
eskay

---

