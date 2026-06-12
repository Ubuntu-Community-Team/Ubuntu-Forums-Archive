---
title: "Ubuntu 17.10 QCA6174 Unstable WiFi"
date: 2018-04-19
forum: Networking &amp; Wireless
---

### Post by rravp on 2018-04-19
I have experienced an unstable wifi connection on my ubuntu 17.10 laptop (rto every 15-30 minutes), and it led me to this thread: [https://askubuntu.com/questions/967355/wifi-unstable-after-17-10-update?rq=1](https://askubuntu.com/questions/967355/wifi-unstable-after-17-10-update?rq=1)

i have tried the following fixes but nothing worked for me:

- updated linux-firmware via apt-get to 1.169.3
- updated QCA6174 firmware manually to firmware-6.bin_WLAN.RM.4.4.1-00051-QCARMSWP-1 / firmware-6.bin_WLAN.RM.4.4.1-00065-QCARMSWP-1 / and even firmware-6.bin_WLAN.RM.4.4.1-00102-QCARMSWP-1
- changed my kernel from 4.13.0-x to 4.15.17
- set wifi.scan-rand-mac-address=no and wifi.powersave = 2

here's the log:
[http://paste.ubuntu.com/p/6gdG8xTxjv/](http://paste.ubuntu.com/p/6gdG8xTxjv/)

any help would be appreciated. thanks!

---

### Post by praseodym on 2018-04-21
Change the encryption mode in your router to WPA2-AES (CCMP), no mixed mode with TKIP

---

### Post by rravp on 2018-05-11
> **praseodym said:**
> Change the encryption mode in your router to WPA2-AES (CCMP), no mixed mode with TKIP

sorry for the late reply, so far so good. thanks for the help!

---

