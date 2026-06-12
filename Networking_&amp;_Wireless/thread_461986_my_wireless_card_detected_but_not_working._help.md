---
title: "my wireless card detected but not working. help"
date: 2007-06-02
forum: Networking &amp; Wireless
---

### Post by waterspider on 2007-06-02
pls i have a BCM4303 802.11b wireless card on my computer the wireless indicator is showing and our wireless access point is set to open but i cannot be able to connect.....please help

---

### Post by al_erola on 2007-06-02
> **waterspider said:**
> pls i have a BCM4303 802.11b wireless card on my computer the wireless indicator is showing and our wireless access point is set to open but i cannot be able to connect.....please help

What kind of security do you have on your access point, wep, wpa, none? 

Please run and post the results of running **sudo ifconfig** and **sudo iwconfig**  also run **sudo dhclient**.

Keep looking for topics on your Broadcom card.

Good luck.

---

### Post by handydan918 on 2007-06-02
You may also want to post the output from "lsmod" and "ndiswrapper -l". I have a broadcom 4318 chipset that I never have been able to get working with the native bcm43xx driver, but it works great with ndiswrapper!

---

