---
title: "I am Forced to Re-add Drivers after an Upgrade | 18.04"
date: 2020-12-10
forum: Networking &amp; Wireless
---

### Post by jt3222 on 2020-12-10
Team,

I bought a USB Wifi adapter for my Xubuntu 18.04 laptop. I followed the manufacture's directions by going to the driver directory and typing "make" and then "make install". Everything works fine until I update my laptop (apt upgrade), I am forced to go through the make and make install all over again, what am I doing wrong?

Regards,

John...

---

### Post by wildmanne39 on 2020-12-10
Hi, please click on the wireless script in my signature, follow the directions to run it and post the results back here using the pastebin link created so we can see what driver you are using, depending on the driver someone may be able to help you install it using DKMS, that is what is needed to have your driver rebuild for the new kernel when it is upgraded otherwise you will have to keep installing it again after each time the kernel is upgraded.

---

