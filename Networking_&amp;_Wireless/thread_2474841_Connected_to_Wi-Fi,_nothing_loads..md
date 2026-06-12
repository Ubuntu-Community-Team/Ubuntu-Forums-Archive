---
title: "Connected to Wi-Fi, nothing loads."
date: 2022-05-09
forum: Networking &amp; Wireless
---

### Post by magmon51 on 2022-05-09
The wife locked my system up by plugging a locked and unfamiliar iPhone into it while I was using Steam to map a controller for MineClone 2, creating an uninteractable window on top of everything else and forcing a hard reboot. Since, data transfer with anything internet related does not work.

It is not the network, all other devices connected still work. Further, zero data transfer happens if I connect to my phone’s hotspot.

Googling this is pointless, hopefully someone here has an answer because a reinstall is extremely annoying.

I’m on a late 2020 Razer Blade base with 22.04

Edit 1 - Booting from the 22.04 USB allows me to connect AND use the internet, so it is not hardware related.

---

### Post by chili555 on 2022-05-09
Please run and post:```
cat /etc/resolv.conf
ls -al /etc/resolv.conf
```Thanks.

---

