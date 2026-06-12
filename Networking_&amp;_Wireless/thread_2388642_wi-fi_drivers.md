---
title: "wi-fi drivers"
date: 2018-04-05
forum: Networking &amp; Wireless
---

### Post by moto1860 on 2018-04-05
I've a question about the wi-fi network controller drivers as I'm getting frequent disconnections (had the same issue when I updgraded from win8 to win10 and then solved them updating drivers): I've run *lshw -C network *to check my drivers and I've this:
```
 configuration: broadcast=yes driver=wl0 driverversion=6.30.223.271 (r587334) ip=192.168.1.20 latency=0 multicast=yes wireless=IEEE 802.11


```

These are the latest drivers for my device on Dell's website: [https://www.dell.com/support/home/us/en/04/drivers/driversdetails?driverId=4FK7J](https://www.dell.com/support/home/us/en/04/drivers/driversdetails?driverId=4FK7J)
[FONT=arial][SIZE=2]
[COLOR=#000000]So as Dell's site driver version is 5.100.82.112, A00 is mine are up to date being 6.30.223.271?[/COLOR][/SIZE][/FONT]

---

### Post by jeremy31 on 2018-04-06
*Thread moved to **Networking & Wireless**.*
I wouldn't expect the Windows driver version to match the Linux version

---

### Post by praseodym on 2018-04-06
Please run the wireless script from the sticky thread and show the outputs

---

### Post by moto1860 on 2018-04-08
> **praseodym said:**
> Please run the wireless script from the sticky thread and show the outputs
Sorry for late reply: [https://pastebin.com/dsy1vcHg](https://pastebin.com/dsy1vcHg)

---

### Post by praseodym on 2018-04-08
271 is the correct driver version. Do not use WEP "encryption", waaay to unsecure. Change the mode to WPA2-AES (CCMP) in your router

---

### Post by moto1860 on 2018-04-08
> **praseodym said:**
> 271 is the correct driver version. Do not use WEP "encryption", waaay to unsecure. Change the mode to WPA2-AES (CCMP) in your router
Thanks! don't have access to admin and pass of the router I'm using but I'll try to recover them.

---

