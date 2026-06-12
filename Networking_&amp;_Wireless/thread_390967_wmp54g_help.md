---
title: "wmp54g help"
date: 2007-03-22
forum: Networking &amp; Wireless
---

### Post by eddyj on 2007-03-22
Okay, so I used ndiswrapper and the gui to install the driver for my card (wmp54g v4.1) and typed in the network in the settings but it doesn't seem to connect.

Also, when I do sudo iwlist scan or sudo iwlist wlan0 scan it will sometimes come up the the networks, but most of the time it displays "no scan results".

I'm kind of stuck here at the moment and need some help.

---

### Post by MeeMaw on 2007-03-22
Linksys used lots of different chipsets and drivers in their cards..... (I use a WMP54g card myself)
So when you do
sudo iwlist scan      or      sudo iwlist wlan scan
what do you get (when you get something.....)
and what did you get when you did
sudo lspci
And are you using Dapper or Edgy?
(a little more info, please)
Thanks

---

