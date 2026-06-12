---
title: "Crappy wifi signal"
date: 2008-02-16
forum: Networking &amp; Wireless
---

### Post by Ohioan on 2008-02-16
I have a Toshiba laptop with an atheros wifi card (a,b and g). on that laptop i have opensuse 10.3 and xubuntu 7.10.  My card wasn't supported out of the box with suse, so i had to download the madwifi driver.  Now, with suse, i get 100% signal.  but with xubuntu i get arond 50-55%.  i also get 100 with the Eee I'm on right now.  

anyone know if there is a madwifi driver that will work in ubuntu/xubuntu/kubuntu?

---

### Post by Sokertes on 2008-02-16
Give ndiswrapper a try. I had the same issue with my laptop running gentoo that had a

Broadcom Corporation BCM94311MCG wlan mini-PCI

At the time I used linuxant drivers which you had to pay for ($20.00 I beleive). It worked but only 75% of the time.

I looked into ndiswrapper and got it working with the windows drivers for the card and it was %110 better with signal strength and connections.

Sokertes

---

