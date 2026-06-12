---
title: "Cannot Detect Existing Wireless Network"
date: 2005-08-25
forum: Networking &amp; Wireless
---

### Post by ZBlach on 2005-08-25
I've set up ndiswrapper correctly, and have all my settings correctly, but when I try 'iwlist wlan0 scan', no networks turn up, including the existing wireless network used by my windows partition. 

What can I do to configure the network correctly?

---

### Post by ssck on 2005-08-25
[QUOTE=ZBlach]I've set up ndiswrapper correctly, and have all my settings correctly, but when I try 'iwlist wlan0 scan', no networks turn up, including the existing wireless network used by my windows partition. 

What can I do to configure the network correctly?[/QUOTE]

are you using wired network as well ? if so, try to ifdown the wired network device first.then try iwlist wlan0 scan

---

