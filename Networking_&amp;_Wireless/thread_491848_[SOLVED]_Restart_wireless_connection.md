---
title: "[SOLVED] Restart wireless connection"
date: 2007-07-04
forum: Networking &amp; Wireless
---

### Post by borobudur on 2007-07-04
I'm using the following command to restart the network. Is there any other command to restart my wireless connection? This one takes sooooooooooo long to be done with all the stuff it does...

```
 /etc/init.d/networking restart
```

---

### Post by spd106 on 2007-07-05
Not really, this is the safest method as it runs all of the right scripts. You could edit the /etc/network/interfaces file to remove any interface declarations that you don't actually have. e.g. if you don't have an Atheros wifi card remove the ath0 lines.

You can also just restart one interface by chaining these commands together.
```
sudo ifdown eth0 && sudo ifup eth0
```. However, if you have remote file shares mounted this might not unmount them cleanly.

---

