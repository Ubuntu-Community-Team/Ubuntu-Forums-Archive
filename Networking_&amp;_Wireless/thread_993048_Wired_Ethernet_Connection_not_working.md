---
title: "Wired Ethernet Connection not working"
date: 2008-11-25
forum: Networking &amp; Wireless
---

### Post by synthesilica on 2008-11-25
Hi everyone, last time I used Ubuntu was back in 6.10 and I used to connect to the internet via pppoe because my modem only acted as a bridge. Lately though, it's been replaced by a router that automatically connects so I only need to be connected to it via network to get internet. It works fine on WinXP of the same computer but it won't connect at all in Ubuntu 8.10.

"ifconfig eth0" gives the details of the modem but "ifup eth0" gives something like "ignoring unknown interface eth0=eth0". Using the network manager just times out.

My mobo's lan chipset is the Marvell Yukon 88E8056 which is listed in supported hardware page. The modem is a Zyxel 600 from my ISP.

---

### Post by calamanthus on 2008-11-25
Same here, same integrated ethernet, installed twice with no luck. Gave up and installed my copy of Gutsy, perfect. Then tried the Intrepid cd live in my other box with a Realtek card, worked fine.

---

