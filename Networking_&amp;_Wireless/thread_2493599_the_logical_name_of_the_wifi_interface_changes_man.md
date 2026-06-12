---
title: "the logical name of the wifi interface changes many times during booting"
date: 2023-12-19
forum: Networking &amp; Wireless
---

### Post by hbbco on 2023-12-19
I am using Ubuntu Jammy version 22.04.3 and frequently the logical name of the wifi interface is not the correct wlp2s0 but wlan0. I think there is an operating system crash at the time the machine starts working and establishes the wifi connection, is that correct? If there is a fault, how to correct it?

---

### Post by TheFu on 2023-12-19
Google found this: [https://askubuntu.com/questions/1303099/how-to-change-the-name-of-wireless-interface](https://askubuntu.com/questions/1303099/how-to-change-the-name-of-wireless-interface) ... they use the udev rule technique.
Does it not work?

---

