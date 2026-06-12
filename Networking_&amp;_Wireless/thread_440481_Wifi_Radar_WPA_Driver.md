---
title: "Wifi Radar WPA Driver?"
date: 2007-05-11
forum: Networking &amp; Wireless
---

### Post by victory2007 on 2007-05-11
I installed wifi radar and i am in an open network enviroment but if I ever go into a wpa area how do I get it to work.  What is the WPA driver, is that how I get it to work.  Thanks

---

### Post by spd106 on 2007-05-12
This is the driver on the list of those compatible with wpa_supplicant. You can see the list on the man page or at this website [http://hostap.epitest.fi/wpa_supplicant/](http://hostap.epitest.fi/wpa_supplicant/)

I would say nine times out of ten you should use wext, particularly on releases after Dapper.

---

### Post by magdulewicz on 2008-03-20
Open terminal, type ```
wpa_supplicant
```. There sholud be something like ```
drivers:
  hostap = Host AP driver (Intersil Prism2/2.5/3)
  madwifi = MADWIFI 802.11 support (Atheros, etc.)
  atmel = ATMEL AT76C5XXx (USB, PCMCIA)
  wext = Linux wireless extensions (generic)
  ndiswrapper = Linux ndiswrapper
  ipw = Intel ipw2100/2200 driver
  wired = wpa_supplicant wired Ethernet driver
  test = wpa_supplicant test driver

```
If not, probably you need to open Synaptic and install wpasupplicant package.
Then, find the driver that fits or try them one by one :)

---

