---
title: "Wifi icon not visible in 18.04"
date: 2018-07-27
forum: Networking &amp; Wireless
---

### Post by ronikgandhi on 2018-07-27
Recently I installed ubuntu 18.04 on my lenovo ideapad.
I can connect to the internet through usb tethering but there's no option available for wifi. Inside the Wi-Fi tab in settings it is written that "No Wi-Fi adapter found. Make sure wifi adapter is plugged and turned on.".

---

### Post by kc1di on 2018-07-29
Do you know which wifi card that machine has? if not install inxi ```
sudo apt install inxi
``` then in a terminal enter this command and post the output here:
```
inxi -Fxz
```
Thanks.

---

