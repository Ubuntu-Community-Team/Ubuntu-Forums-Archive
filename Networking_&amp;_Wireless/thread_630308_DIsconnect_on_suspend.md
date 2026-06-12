---
title: "DIsconnect on suspend"
date: 2007-12-03
forum: Networking &amp; Wireless
---

### Post by cowboy.bebop on 2007-12-03
Hey guys I have an eth0 the connects through roaming but when the computer goes into suspend mode and the screen reappears on user interaction the network is no longer connected, any possible ways to bring this to a halt?

---

### Post by Ptero-4 on 2007-12-03
You can propably put the module for your nic in the script that unloads modules b4 suspending and put it also in the script that loads modules upon waking up (search the forums for instructions on that) so that your conection is safely disabled and reenabled on the suspend/wakeup cycle.

---

