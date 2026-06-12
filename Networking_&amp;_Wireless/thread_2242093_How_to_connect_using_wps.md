---
title: "How to connect using wps?"
date: 2014-08-30
forum: Networking &amp; Wireless
---

### Post by bienio2 on 2014-08-30
Well i can't remember my wi fi password so im trying to find WPS in Lubuntu 14.04.
Is there a way to connect using wps ?
Sorry for my english.

---

### Post by Maverickor on 2014-08-30
Do you mean the Chinese office softwares, WPS? There is no WPS in Ubuntu in default. Alternatively, you can use the LibreOffice series.
Or, you may download from the official website ([http://linux.wps.cn/](http://linux.wps.cn/)) using another computer under available network and copy to the one offline computer.
Hope this help :)

:wq

---

### Post by bienio2 on 2014-08-31
Nop it didnt:)

---

### Post by praseodym on 2014-08-31
Please have a look into this file:
```

sudo cat /etc/NetworkManager/system-connections/*
```
You will find the key as "psk=......"

---

