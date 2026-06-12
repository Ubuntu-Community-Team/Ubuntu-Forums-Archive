---
title: "Wifi extremely slow as compared to Windows on the same machine"
date: 2019-06-16
forum: Networking &amp; Wireless
---

### Post by mikemurz on 2019-06-16
My desktop has both Windows and Ubuntu 18.04. I was able to get wifi working on Ubuntu but the speed test results are very slow compared to the speeds I get when running in Windows. The particular driver I am using is Realtek [COLOR=#000000]RTL8822BE. [/COLOR]Here is the results of the wireless-info script: [https://paste.ubuntu.com/p/vMXwfWDsKr/](https://paste.ubuntu.com/p/vMXwfWDsKr/)

Can anyone help me determine why I am seeing slow speeds on Ubuntu?

---

### Post by praseodym on 2019-06-17
Change the encryption mode to WPA2-AES (CCMP) and to channel 1, no mixed mode WPA/WPA2

---

