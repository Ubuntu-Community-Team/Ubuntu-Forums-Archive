---
title: "Upgrade from 7.04 to 7.10 stops wireless from working"
date: 2008-01-15
forum: Networking &amp; Wireless
---

### Post by thursty on 2008-01-15
I previously had WIFI (Atheros) working fine under 7.04 using ndiswrapper and adding the line ```
blacklist ath_pci ath_hal
``` to ```
/etc/modprob.d/blacklist
```

I have just upgraded to 7.10 and WIFI now doesn't work. (I had to add ```
/etc/modprob.d/blacklist
``` to ```
blacklist ath_pci ath_hal
``` again).
The driver seems to still be installed because ```
ndiswrapper -l
``` gives:
```
net5211 : driver installed
        device (168C:001C) present (alternate driver: ath_pci)
```
iwconfig shows no wireless connections. and neither does knetworkmanager

---

### Post by HokeyFry on 2008-01-15
To be honest I have always had problems upgrading, usually I prefer to do a fresh install. I would wait for more responses on this though before trying something as drastic as that.

---

### Post by thursty on 2008-01-15
I have fixed the problem now thanks, by using the net5416 driver instead of the net5211 which worked with 7.04 (now my sound isnt working...!)

---

