---
title: "Dell Inspiron 1521"
date: 2008-10-16
forum: Networking &amp; Wireless
---

### Post by Riaku on 2008-10-16
Hey I have a Dell Inspiron 1521 I want to install Ubuntu on I checked and I don't know if my wireless card is supported :_____: It's a Dell 1395 wireless. Does anyone know if it is supported? if it is how can I get it usable?

---

### Post by superprash2003 on 2008-10-16
yes.. this link should help you [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

---

### Post by Ayuthia on 2008-10-16
If I recall correctly, it is a Broadcom 4312 (14e4:4315).  If that is the case, it should work in Ubuntu.  It should just be a matter of going into System->Administration->Hardware Drivers and activating the Broadcom STA wireless.

If you have a wired connection and plan to use Hardy, you might want to run the updates first to get to the most recent kernel version because there are some improvements made to the wireless driver.

---

