---
title: "Blacklist wireless points?"
date: 2007-08-31
forum: Networking &amp; Wireless
---

### Post by jonesy79 on 2007-08-31
Hi,

There is a wide open wireless network nearby me, no idea who owns it, But everytime ubuntu starts up, it wants to connect to it, and half way through connecting to mine, it always switches over to the open one instead of asking for my password for mine.

Is there anyway to block off these other networks so my laptop can't detect them at all? Would save so much hassle.

Im using gutsy gibbon. fully updated.

Thanks

---

### Post by jonesy79 on 2007-09-01
noone know nowt about it?

---

### Post by spd106 on 2007-09-01
Network Manager should not connect to a network without being told to, unless you have connected to it previously. If that is the case then you can remove the bssid of the AP from the store in gconf.
This wiki page will tell you how [https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager)

---

### Post by jonesy79 on 2007-09-03
thanks, did the trick.

---

