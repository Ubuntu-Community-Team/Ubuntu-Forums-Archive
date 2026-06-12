---
title: "configuring interfaces /etc/network/interfaces"
date: 2007-12-30
forum: Networking &amp; Wireless
---

### Post by mariusmeyer on 2007-12-30
I have a D-Link DWL-510 rev. C wireless network card, that I finally got to work with serialmonkey's rt61 drivers. I've tried to make the network work across reboots, but havn't been able to so far. Here is how my /etc/network/interfaces looks like:

```
auto lo
iface lo inet loopback
auto wlan0
iface wlan0 inet dhcp
	pre-up sudo ifconfig wlan0 up
	post-up sudo iwconfig wlan0 essid marius-maria
	post-up sudo iwpriv wlan0 set AuthMode=WPAPSK
	post-up sudo iwpriv wlan0 set EncrypType=TKIP
	post-up sudo iwpriv wlan0 set WPAPSK=superstableamosplus
	post-up sudo iwpriv wlan0 set SSID=marius-maria
	post-up sudo iwpriv wlan0 set NetworkType=Infra
	post-up sudo dhclient wlan0
```

Is there anything in here that's not correct/would prevent it from working? If I type all this manually, it works after a few tries (seems like dhclient needs a few goes before it works).

Thanks all, and happy new year!

---

