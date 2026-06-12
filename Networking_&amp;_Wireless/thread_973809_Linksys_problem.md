---
title: "Linksys problem"
date: 2008-11-07
forum: Networking &amp; Wireless
---

### Post by makaveli0129 on 2008-11-07
Ok I have a dell inspiron 5100 laptop with a linksys wpc600n which should be the broadcom BCM4328 chipset now when i installed the ubuntu 8.10 it shows under System>Administration>HardwareDrivers 2 drivers for my wireless the Broadcom B43 wireless driver and than the wl driver i activated both and wireless card still doesn't work no lights or anything like that tried activating each seperately still nothing.

After doing all that i even tried installing ndiswrapper and using the bcmwl5.inf file and trying it that way but still can't get it to work i am at my wits end here and would apprieciate any help that i could get when i type ndiswrapper -l i get:

bcmwl5 : driver installed
	device (14E4:4328) present (alternate driver: wl)

the lspci command shows this:


03:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 01)

---

