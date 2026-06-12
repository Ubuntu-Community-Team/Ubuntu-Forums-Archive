---
title: "wpa (tkip) hardware"
date: 2007-11-07
forum: Networking &amp; Wireless
---

### Post by xzero1 on 2007-11-07
I have an older 801.11b wifi card which does not support wpa in hardware. There was a program that I used in windows that did the wpa encryption in software. Does linux requre wpa hardware support for wpa operation? Is there any (non wine) software that will allow such a card to use wpa?

---

### Post by spd106 on 2007-11-07
In Ubuntu WPA is mostly handled by the wpa_supplicant, which does most of the processing in software. However I believe you still a driver that is capable of handling WPA for it to work. So you'll probably have to investigate whether your driver works with wpa_supplicant.

[http://hostap.epitest.fi/wpa_supplicant/](http://hostap.epitest.fi/wpa_supplicant/)

---

