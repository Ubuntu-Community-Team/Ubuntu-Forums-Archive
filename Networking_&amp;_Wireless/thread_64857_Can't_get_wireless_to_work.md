---
title: "Can't get wireless to work"
date: 2005-09-12
forum: Networking &amp; Wireless
---

### Post by Tiny Grasshopper on 2005-09-12
Hello, I have a question regarding my wireless controller. I can't get it to work in Ubuntu even though it shows up in the Device Manager. I have a Compaq Presario laptop 2104US and the wireless controller's a Broadcom chipset. It shows up with details in the HAL Device Manager, 

but "Wireless Connection" or "Wireless LAN Card" or anything similar doesn't show up in network-admin (System->Administration->Networking). 

What should I do?

---

### Post by numberexhaust on 2005-09-12
[QUOTE=Tiny Grasshopper]Hello, I have a question regarding my wireless controller. I can't get it to work in Ubuntu even though it shows up in the Device Manager. I have a Compaq Presario laptop 2104US and the wireless controller's a Broadcom chipset. It shows up with details in the HAL Device Manager, 

but "Wireless Connection" or "Wireless LAN Card" or anything similar doesn't show up in network-admin (System->Administration->Networking). 

What should I do?[/QUOTE]
 Your wireless card is not natively supported in linux.  There is a lot of stuff in these forums for that.  Try to find the .inf file for your driver on the website or whatever, then lookup how to use the program ndiswrapper to install that driver.  If you have any questions, post back here.

---

### Post by Tiny Grasshopper on 2005-10-03
I installed ndiswrapper 1.3rc1 and did a search for bcmwl5.sys and bcmwl5.inf, and used the search results for the Driver, I followed the instructions in the Wiki to install it, but it didn't work and ethernet didn't work with it. From looking at ndiswrapper's site I know that the PCI id is 14e4:4320 (rev 02) and I just need to figure how to get the drivers to use with it.

---

### Post by Tiny Grasshopper on 2005-10-05
Okay I've since gotten it to run, simply by using the older version 1.1, and following the previous instructions in wikis and such. thanks.

---

