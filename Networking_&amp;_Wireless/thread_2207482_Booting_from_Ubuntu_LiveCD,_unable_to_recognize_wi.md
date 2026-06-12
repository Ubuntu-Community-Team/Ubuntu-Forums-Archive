---
title: "Booting from Ubuntu LiveCD, unable to recognize wireless USB adapter"
date: 2014-02-23
forum: Networking &amp; Wireless
---

### Post by gill2 on 2014-02-23
I am trying to run Ubuntu through a LiveCD. It loads without issue, but I am unable to connect to the internet. Ubuntu does not seem to recognize the existence of my wireless USB adapter (it's an ASUS USB-AC56 Dual-band Wireless-AC1200 Adapter).

Does anyone know how I can get it working, or is the only solution to set up a wired connection?

---

### Post by tripp98 on 2014-02-23
the easiest is to wire it then go to system settings 
software and updates
additional drivers
your card may have a propitiatory driver that may work without any work.

---

### Post by Vladlenin5000 on 2014-02-23
Although the previous post is correct and definitely you should try it provided you have also Ethernet available, in order to start troubleshooting knowing what hardware is really there is of the utmost importance. The hardware we need to know is the WiFi chipset itself and no, it's not Asus. Asus is just the assembler/brand (or rebrand). Inside there's a chipset made by Ralink, Realtek, Intel, Broadcom/Atheros and not many more.

Please do in a terminal ```
sudo lsusb
``` and post the results.

---

