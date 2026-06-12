---
title: "Dual wifi adapter problem"
date: 2016-11-25
forum: Networking &amp; Wireless
---

### Post by raynor123 on 2016-11-25
Hi,
I have bought a new wifi adapter (using chipset ATH9K) when i installed new drivers (backports) my old drivers (rtlwifi) stopped to works.

I usually install with  make defconfig-rtlwifi (or defconfig-ath9k) then make install.

How can i make them works together? (wlan0 & wlan1)

---

### Post by jeremy31 on 2016-11-25
What version ubuntu are you using?
Usually using the following command will support most wireless cards ```
make defconfig-wifi
```

---

