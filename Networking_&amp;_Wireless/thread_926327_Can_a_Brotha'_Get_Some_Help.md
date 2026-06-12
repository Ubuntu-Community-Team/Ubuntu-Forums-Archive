---
title: "Can a Brotha' Get Some Help?"
date: 2008-09-21
forum: Networking &amp; Wireless
---

### Post by Torsion on 2008-09-21
Sorry about the title but it's the only way I could get a response! I've been using a EDIMAX EW-7128G which is said to be fully supported. It worked great out of the box and speeds are nice. 

However, for some reason I have to click on the network every 5-10 minutes to reconnect to the router, or else the web browser will just sit there like it has no connection, even though the network bars show 3+.

Is there anything that I can do to tweak the settings? I have a Netgear router WGR614 v6 if that helps. Thank you!

---

### Post by pytheas22 on 2008-09-21
It sounds like a problem with the driver crashing.  I have a card where that happens too--no connection even though Network Manager says it's online.

If you post the output of these commands, we can try to figure out which driver you're using, and whether you can install a better one:
```

lshw -C Network
lspci -nn
lsusb
lsmod
```

---

