---
title: "MT6711 Gateway Laptop"
date: 2007-09-04
forum: Networking &amp; Wireless
---

### Post by Siph0n on 2007-09-04
The wireless on my laptop works fine, but I was curious why iwconfig shows wmaster0 and wlan0. In the /etc/network/interfaces file I only have lo and wlan0 defined.... Should I also have a wmaster0 defined there? What is the difference between wlan0 and wmaster0?

Shawn

---

### Post by Siph0n on 2007-09-05
bump.... anyone know?

---

### Post by jamesattard on 2008-05-16
wmaster0 is the master device
wlan0 is the interface.

Users should only deal with wlan0 :) udev rules create the wmaster0 device name afaik

---

### Post by Kaulbach on 2008-07-08
The Realtek 8187 which comes on this model is USB based, and so the wmaster0 is the host adapter name of this. The wlan0 is the actual device which is attached to the USB.

---

