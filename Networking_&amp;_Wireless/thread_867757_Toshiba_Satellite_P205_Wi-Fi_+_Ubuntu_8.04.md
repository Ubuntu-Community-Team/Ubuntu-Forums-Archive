---
title: "Toshiba Satellite P205: Wi-Fi + Ubuntu 8.04"
date: 2008-07-23
forum: Networking &amp; Wireless
---

### Post by blondeMatrix on 2008-07-23
Hi,

Reading the sticky above, it appears that my wireless connection should perhaps be recognised/functional upon OS installation.  However, it isn't working.  Here are the relevant details...

Laptop: Toshiba Satellite P205-S7457
Wi-Fi hardware: 05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
Linux distro: Ubuntu V8.04

Any advice to get this working would be greatly appreciated, as all else appears fine following install (including screen resolution and sound).

Thanks & regards,

Chris Dodunski.
(New Zealand)

---

### Post by chili555 on 2008-07-23
Doctor 3945 is here to help. What have you tried so far? When you click the two little computer icon (Network Manager applet), do you see networks to connect to? Do you see yours? When you give any encryption details, does it attempt to connect?

Please hook up the ethernet cable and do, in a terminal:```
sudo apt-get install linux-backports-modules-hardy-generic
```There is evidently a better driver for your 3945ABG in there.

Finally, Network Manager will not want to activate your wireless if you have a working ethernet connection, so detach the wire before you attempt to connect wirelessly.

---

