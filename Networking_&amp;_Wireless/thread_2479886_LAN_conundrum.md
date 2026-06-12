---
title: "LAN conundrum"
date: 2022-10-11
forum: Networking &amp; Wireless
---

### Post by jvglynnjr on 2022-10-11
My LAN is based on a wifi/DSL router (ZyXel) which has ethernet ports. There are 8 computers connected, 3 by ethernet and 5 by wifi. One of the wifi computers is in another building and connects through a repeater. The repeater also has ethernet ports (also ZyXel).

So this set-up works fine, and all the computers can connect to each other and the file server. The problem is, when I tried to connect a 9th computer in the other building, it could reach the internet through the ethernet port, but could not connect to any of the other computers on the LAN, including the file server. I should mention that this is an older computer that doesn't have wifi, so that's why I connected by ethernet. 

Why should this make any difference? When I connect it by ethernet to the main router, it works fine, but not when connected by ethernet to the repeater. Is this a configuration problem that I can fix?

---

### Post by TheFu on 2022-10-11
I'd contact a Zyxel forum with the exact modules involved so someone with expertise in that networking gear can consider.
I assume you are fully patched on the Zyxel hardware. They've had some nasty security issues the last few years, as most small-biz network devices do.

If the system works fine on the other connection, it isn't an ubuntu issue. Look at the network equipment settings.

---

### Post by thebearak on 2022-10-13
can it ping the other devices?  Or is it just things like SMB shares that are not working?

---

