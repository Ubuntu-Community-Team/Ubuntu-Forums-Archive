---
title: "how to get firmware non free installed?"
date: 2016-07-14
forum: Networking &amp; Wireless
---

### Post by DrScum on 2016-07-14
Installed new Desktop Version 16.04
Wlan card not supported firmware non free
downloaded firmware non free package, not installable with software install
downloaded gdebi package not installable with software install
can you guys imagine how thrilled I am?

How do I get my Wlan card working in order to be able to connect to the internet to get things done?

---

### Post by howefield on 2016-07-14
Thread moved to the "*Networking & Wireless*" forum.

---

### Post by DrScum on 2016-07-14
solution to the first:

navigate to directory which has the downloaded package and enter sudo dpkg -i nameofpackage.deb

but it gets better: the previous attempt to install a .deb package with ubuntu software install leaves unmet dependencies so that you can't install anything using aptitude. 
To fix that you have to enter sudo apt-get install -f
How are people merging to Ubuntu going to feel when they meet these obstacles right in the first hour after their install?

---

### Post by wildmanne39 on 2016-07-14
Hi, please click on the wireless script in my signature and follow the directions for running the script and posting the results here. 
Thanks

---

