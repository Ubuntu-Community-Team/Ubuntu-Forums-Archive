---
title: "Wpa2"
date: 2005-06-28
forum: Networking &amp; Wireless
---

### Post by hyapadi on 2005-06-28
Has anyone try wpa2 in ubuntu? How to do it?

Currently I'm using wpa2 psk in my router and my windows laptop. My Ubuntu box still running wpa connected to that wpa2 router. I does connect because of the backward compatibilty between wpa 2 and 1. But I want to set up my ubuntu box to connect using the wpa2 mode.

Thanks

---

### Post by luca_linux on 2005-07-27
You need to install wpa_supplicant.

---

### Post by PhilippWollermann on 2005-07-27
If you have wpa_supplicant installed (and I guess you do, if you're using WPA1 at the moment :)), it's very easy.. if I remember correctly, one just has to change WPA to WPA2 in the /etc/wpa_supplicant.conf. Have a look at the documentation or the example config which is supplied with the source of wpa_supplicant.

Philipp

---

