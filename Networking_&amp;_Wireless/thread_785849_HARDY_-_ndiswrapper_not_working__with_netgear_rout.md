---
title: "HARDY - ndiswrapper not working  with netgear router"
date: 2008-05-07
forum: Networking &amp; Wireless
---

### Post by npallett on 2008-05-07
Having experimented with both b43 and ndiswrapper in Hardy (Broadcom 4318  Wireless card) ,I am experiencing some weird results.

Using ndiswrapper I can connect reliably with WPA2 security to various Draytek routers.I cannot, however connect at all to netgear DG834GT routers using WPA security.

If I use the b43 driver instead of ndiswrapper, I CAN connect to the netgear routers.

I would be happy to use the b43driver all the time, except for the fact that the speed of the connection is very unreliable.

ndiswrapper worked perfectly with GUTSY, so I'm confused as to why it is less reliable under HARDY - I guess it must be something to do with the new kernel and the ssb module ?

---

### Post by stelmin on 2008-08-01
Hello, I have a Broadcom 4311 Wireless chipset and was having a problem connecting to our Netgear DG834G v4 router under Hardy. Myself and a friend found a simple solution (he also uses Ubuntu and was having no problems with his Intel wireless chipset), we changed the channel on the router (from 11 to 2) and then I could connect to the network.

---

