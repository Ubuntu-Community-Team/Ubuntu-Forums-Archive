---
title: "WIFI Stick"
date: 2024-06-19
forum: Networking &amp; Wireless
---

### Post by vbueschken on 2024-06-19
Hi,

I have installed UBUNTU 24.04 on a HP T630. it is connected via LAN to my network.

Now I want to install a WIFI Stick to be more flexible with the location of my Hardware.

Can anyone recommend a WIFI Stick that works plug&play in my environment?

Thanks
Volker

---

### Post by him610 on 2024-06-20
RE: [https://support.hp.com/us-en/document/c05240287]("https://support.hp.com/us-en/document/c05240287")

The HP specs indicate you have wifi....
> Wi-Fi networking
Feature
Description
Wi-Fi adapter options:
Intel Dual Band Wireless-AC 3168 Wi-Fi/Bluetooth combo adapter
Intel Dual Band Wireless-AC 8260 Wi-Fi/Bluetooth combo adapter

Does yours not have either of the Intel wifi adapters? Please show results of....
```
 inxi -Nxxz 
```

You may consider reading this post about usb wifi adapters - [https://ubuntuforums.org/showthread.php?t=2397914]("https://ubuntuforums.org/showthread.php?t=2397914")

---

### Post by morrownr on 2024-06-21
[https://github.com/morrownr/USB-WiFi](https://github.com/morrownr/USB-WiFi)

Menu item 2 is the Plug and Play List. The above link is in the top sticky here.

---

