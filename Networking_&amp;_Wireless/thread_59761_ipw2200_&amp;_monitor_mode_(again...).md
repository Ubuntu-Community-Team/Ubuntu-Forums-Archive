---
title: "ipw2200 &amp; monitor mode (again...)"
date: 2005-08-25
forum: Networking &amp; Wireless
---

### Post by roots on 2005-08-25
hi there,

my ipw2200 is working fine in 'normal mode' with 1.0.4 driver and 2.3 firmware and wpa enabled, but when i try to enable monitor mode, i do get the following error:

```
root@acid:~ # iwconfig eth0 mode monitor
Error for wireless request "Set Mode" (8B06) :
    SET failed on device eth0 ; Invalid argument.
``` 

this problem has already been posted, but somehow was paid no further attention to.

this is obviously NO pure hardware problem, as netstumbler is working fine under winxp.

any suggestions???

cheers
.roots

---

### Post by luca_linux on 2005-08-25
Try to update to ipw2200 1.0.6.

---

### Post by roots on 2005-08-25
yeaaaaaaaaaaaaaaaaah - with 1.0.6 IT WORKS! :grin: 

BIG cheers,
.roots

---

### Post by luca_linux on 2005-08-26
I'm glad to have helped you out.

Cheers,
Luca

---

### Post by Radi0ShacK on 2005-09-08
hi,
i ve upgraded to ipw2200 driver ver 1.0.6 and using firmware 2.3
but when i try to iwconfig eth0 mode monitor i get this same error whar shall id can you help me :)
> Error for wireless request "Set Mode" (8B06) :
    SET failed on device eth0 ; Invalid argument.

i am sure that i am using ipw2200 driver ver 1.0.6 from "dmesg | grep ipw2200"  and i ve copied firmware to /usr/lib/hotplug/firmware ??!? plz can any one help meeeee  ](*,)

---

### Post by Radi0ShacK on 2005-09-09
Hi,
sorry i ve fixed the problem  :roll:

---

### Post by Mint Sauce on 2005-09-09
[QUOTE=Radi0ShacK]Hi,
sorry i ve fixed the problem  :roll:[/QUOTE]

How?

---

### Post by Radi0ShacK on 2005-09-10
well i ve reinstalled :) "ieee80211, ipw2200 firware and driver" search for ipw2200+wpa thread by luca_linux it is excellent "all you need" but be patient and read till the end :)

---

