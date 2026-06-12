---
title: "Huawei E160g USB modem resume without reboot"
date: 2008-09-13
forum: Networking &amp; Wireless
---

### Post by Jeztastic on 2008-09-13
Hi,

Have managed to get this working with gnome-ppp, though no luck with network manager 0.7 as yet. 

However, when I disconnect and reconnect the modem from my PC, it will not then recognise it until I reboot with the modem connected. 

I have done a search, and have not yet found anything similar or applicable.

Thanks,

Jez

---

### Post by GeorgeVita on 2008-09-20
Hi Jez,
did you find any solution for your problem? A friend also has a similar problem with an E170. Did you try to **lsusb** and **ls /dev/ttyUSB*** after boot (without modem) inserting it first time and then try again after removing and reinserting. What number of ttyUSBx assigns the system? Keeps the same ex. ttyUSB0 & ttyUSB1 or gives new like ttyUSB2 & ttyUSB3?
Regards,
George

---

