---
title: "PCI Network Adapter Problem"
date: 2022-11-07
forum: Networking &amp; Wireless
---

### Post by cst369 on 2022-11-07
Hey, i purchased the Archer T8E (EU) network card as i cant have ethernet in my new room, thing is i can't manage to set it up with ubuntu22.04.
I tried checking it from the Additional Drivers section, it did ask me to type secure boot password (which i never used after) i did reboot but nothings changed.
When i go to my network manger i have no choice for WiFi, neither can i see any sign of the device.Please help.Thanks!

---

### Post by chili555 on 2022-11-07
Let's start by identifying the exact device. Please open a terminal and run:

```
lspci -nnk | grep 0280 -A3
```
Post the result and we'll proceed.

---

### Post by cst369 on 2022-11-08
Well i am afk at the moment, but i remember running that and showed broadcom4360

---

### Post by chili555 on 2022-11-08
> **cst369 said:**
> Well i am afk at the moment, but i remember running that and showed broadcom4360Please check here: [https://ubuntuforums.org/showthread.php?t=2214110](https://ubuntuforums.org/showthread.php?t=2214110)

---

### Post by cst369 on 2022-11-08
Well i tried evey single step before posting so no luck.

---

### Post by cst369 on 2022-11-08
Ok i just keeped trying and then i enrolled MOK, all good thanks for your time.

---

