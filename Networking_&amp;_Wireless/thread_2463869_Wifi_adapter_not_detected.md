---
title: "Wifi adapter not detected"
date: 2021-06-20
forum: Networking &amp; Wireless
---

### Post by chakki1234 on 2021-06-20
Hey, i tried installing ubuntu on my new asus lap. I first ran ubuntu on live mode and the wifi adapter was not being recognized I also tried installing ubuntu but the wifi and Bluetooth were still not working.Could you help me out with this.

---

### Post by jeremy31 on 2021-06-20
Moved to networking
Post results from terminal for ```
lspci -nnk | grep -iA3 net; lsusb; dmesg | egrep -i 'blue|firm'
```

---

