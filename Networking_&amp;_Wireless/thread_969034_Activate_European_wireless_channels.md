---
title: "Activate European wireless channels"
date: 2008-11-03
forum: Networking &amp; Wireless
---

### Post by mocho on 2008-11-03
hi all

I'm in the process of leaving windows but i'm having some problems with wlan

i have a hp laptop with broadcom 4321 abg wireless card and using broadcom driver in my ubuntu 8.10.

the problem is that i can only see 11 channels in the 2.4 ghz range (plus the 5 ghz channels) and i cant seem to activate the european channels 12 and 13.

i've tried adding  

```
options cfg80211 ieee80211_regdom=EU
```

to /etc/modprobe.d/options but that didnt work as it worked for some other people
I suspect its due to my system using the broadcom proprietary drivers

i realy need to activate this channels because in my work the AP is set to channel 13 and without this i still have to use windows as where i'm writing this 

regards

---

