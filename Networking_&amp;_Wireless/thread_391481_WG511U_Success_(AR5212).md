---
title: "WG511U Success (AR5212)"
date: 2007-03-23
forum: Networking &amp; Wireless
---

### Post by jrmann1999 on 2007-03-23
After an evening of pure hell trying to get my Netgear WG511U(Atheros 5212 chipset) to associate with my AP, I figured out what was wrong, I thought I'd post my success in case others are having issues as well.

```

sudo iwconfig ath0 essid <your ssid here>
sudo iwconfig ath0 key <your hex key here> restricted
sudo iwpriv ath0 mode 3
sudo iwpriv ath0 authmode 2
sudo dhclient ath0

```

The above will enable your AR5212 based device to use shared wep authentication to associate with an AP.  The mode 3 line above will force it into 802.11g mode, not sure if this is necessary, but I do it out of habit.

Good luck!

---

### Post by tgalati4 on 2007-03-28
Dear jrmann1999

Your script works great!  Where is the best place to put these jewels?  There are so many boot up scripts that I get confused.   I'm running Dapper 6.06.1.

The community appreciates your efforts.

Terry

---

