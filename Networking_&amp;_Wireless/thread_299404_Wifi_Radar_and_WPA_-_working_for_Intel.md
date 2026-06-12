---
title: "Wifi Radar and WPA - working for Intel"
date: 2006-11-14
forum: Networking &amp; Wireless
---

### Post by davebed on 2006-11-14
For those of us wanting to use WifiRadar with WPA, I found some info.

1. Make sure wpa_supplicant is installed (it's in Synaptic)
2.In WPA driver for WifiRadar  if you have an Intel card, put **ipw**

For other cards, open a terminal and type
```
wpa_supplicant
``` and look at the top of the info it lists. You'll see **driver** type the code corresponding to your card.

Good luck!

---

