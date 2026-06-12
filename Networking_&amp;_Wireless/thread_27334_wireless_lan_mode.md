---
title: "wireless lan mode"
date: 2005-04-15
forum: Networking &amp; Wireless
---

### Post by gerald.schnabel on 2005-04-15
How can I configure the wireless Lan Card permanently? I don't want to use iwconfig after boot. After every boot I have to change the wireless mode from managed to Ad-Hoc. 

thanks for your help

Gerald

---

### Post by accuser on 2005-04-15
Settings -> Administration -> Networking. Select wireless card, click properties and enter the wireless settings.

---

### Post by gerald.schnabel on 2005-04-16
I tried this already. But there is no point to change the wireless mode (default is managed) to Ad-Hoc.

I got it now. I had to change the /etc/network/interfaces file and add follow line at the wireless interface

wireless-mode Ad-Hoc

thanks
gerald

---

