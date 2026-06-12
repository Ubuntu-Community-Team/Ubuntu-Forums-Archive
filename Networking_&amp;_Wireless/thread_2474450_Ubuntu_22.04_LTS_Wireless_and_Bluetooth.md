---
title: "Ubuntu 22.04 LTS Wireless and Bluetooth"
date: 2022-04-29
forum: Networking &amp; Wireless
---

### Post by harvman2 on 2022-04-29
Hi,

I'm using a Dell Venue 11 Pro 7130 MS tablet.
It uses a Dell Wireless 1537 802.11 WiFi + Bluetooth 4.0.
Previously run Windows 10 and able to connect to wireless Internet and to Bluetooth mouse.
However, now that I've installed Ubuntu 22.04 LTS I am unable to find or use wireless or Bluetooth.
Can you please help?
Thanks!

---

### Post by jeremy31 on 2022-04-30
Please post results from terminal for ```
lspci -nnk | grep -iA3 net; lsusb; sudo dmesg | egrep -i 'blue|firm'
```

---

