---
title: "Wifi-AP works after running ifup ath0, but not on startup?"
date: 2008-07-24
forum: Networking &amp; Wireless
---

### Post by AVT- on 2008-07-24
#wifi
iface ath0 inet static
address 192.168.15.1
netmask 255.255.255.0
pre-up wlanconfig ath0 destroy
pre-up wlanconfig ath0 create wlandev wifi0 wlanmode ap
wireless-essid avtnetwork
up brctl addif br0 ath0
post-up /etc/init.d/hostapd /etc/hostapd/hostapd.conf

On startup, it doesn't work. But, right after startup, if I run ifup ath0 in terminal, it works. Makes absolutely no sense to me.

Note that it doesn't work either if pre-up wlanconfig ath0 destroy is removed.

---

### Post by chili555 on 2008-07-24
Does it work if you add a line at the beginning?```
auto ath0
```

---

### Post by AVT- on 2008-07-25
Yes, it works. Thankyou! I can't believe the solution was so simple..

---

