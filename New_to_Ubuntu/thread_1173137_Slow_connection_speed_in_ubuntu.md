---
title: "Slow connection speed in ubuntu"
date: 2009-05-29
forum: New to Ubuntu
---

### Post by ttr398 on 2009-05-29
Hello all

First post here! I'm relatively new to ubuntu, been running it for under a month I think, but really liking it so far, slowly getting used to using the terminal a bit etc but still got a long way to go.


Anyway, have noticed that since I installed it, my connection speed has dropped considerably. On Vista before I would comfortably get 700kB/s down, whereas now I get, at most, 150.

I have a wireless connection via a usb dongle, which is a NetGear, Inc. WG111 WiFi (v2).

It worked out of the box so I have not played around with ndiswrapper etc, however I did look into this and could not find the relevant drivers for it.

However, I have also noticed a staggering drop in signal strength, which seems to be very very low in ubuntu whereas it was pretty high in Vista.


Any help would be awesome, cheers in advance!

---

### Post by TeoBigusGeekus on 2009-05-29
As I always post for wireless problems...get rid of network manager and install wicd.
```
sudo apt-get install wicd
```

---

