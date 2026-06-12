---
title: "Internet just went down......"
date: 2008-09-01
forum: Networking &amp; Wireless
---

### Post by BabyBoy on 2008-09-01
Hey all, 

My internet just went off on my ubuntu machine.
It also did on my windows too but with windows I just right clicked connection and pushed reapir.
Ubuntu just wont come back online!
I am sharing it and have a belkin router its a wired connection its nothing to do with router etc....

I did install firewall on there but I got rid of it after internet went off.... becuase I thought it was that.
I type ifconfig and it does actually get DHCP info from router and stuff. Yet still refuses to come online....

Any help would be great. Oh also I flushed all iptables.
:confused:

---

### Post by BabyBoy on 2008-09-01
Woops sorry I fixed it.

For anyone else having the same problem just type in terminal:

```
sudo ufw disable
```

I guess I need to configure it properly.

:)

---

