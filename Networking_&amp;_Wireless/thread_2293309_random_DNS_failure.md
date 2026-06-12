---
title: "random DNS failure"
date: 2015-09-04
forum: Networking &amp; Wireless
---

### Post by SebastianoS on 2015-09-04
Good morning All, 

I've recently been experiencing an annoying situation. My ubuntu laptop suddenly stops resolving DNS domains, both via WI-FI and wired connections. Most of the times I just need to disconnect and reconnect, but that does not always solve the trouble. I've tried manually setting Google DNS in network manager but solved nothing, leading me to think it's a problem on my PC rather than my network. I'll paste my info below. Anyone experiencing the same trouble?

Thanks

---

### Post by TheFu on 2015-09-04
The last few weeks, I'm seeing the same issue - but I don't reconnect, I just wait.  I think it is my internal DNS server getting "stuck" on a query and not being able to answer the following queries. Usually there is a firefox addon stuck at the same time - but I know that isn't it, outside the browser, ping google.com can't resolve either. That mean DNS.  I also have ZERO dropped packets and don't use wifi at home.

---

### Post by dmoss on 2015-12-11
I've got the same problem with Lubuntu 15.04.
Modifing network properties from "Only automatic addresses (DHCP)" to "Automatic (DHCP)" solve the ping problem, web is now ok, but Lubuntu software center still fails DL new packages...
Any idea?

---

### Post by dmoss on 2015-12-11
Solved by sudo apt-get update !

---

