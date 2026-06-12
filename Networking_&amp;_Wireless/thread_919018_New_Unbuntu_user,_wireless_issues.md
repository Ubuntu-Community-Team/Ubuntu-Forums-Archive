---
title: "New Unbuntu user, wireless issues"
date: 2008-09-13
forum: Networking &amp; Wireless
---

### Post by flame0086 on 2008-09-13
I just got Ubuntu installed this last week and have been enjoying it so far. The one main issue I have been struggling with is my wireless. My laptop is apparently using a Broadcom B34. I can see Wireless networks, but I can never connect to them. I went though the basic troubleshooting with the unbuntu help button, but nothing changed. I found the sticky at the top and started to go though the listed steps, but I got stuck at creating a blacklist. When I try to save the document, it tells me that I don't have permission to save the file :confused: Any help pointing me in the right direction is appreciated. Thanks in advanced.

---

### Post by icheyne on 2008-09-13
Get the windows driver (using Google) and follow these instructions.

[https://help.ubuntu.com/8.04/internet/C/ndiswrapper.html](https://help.ubuntu.com/8.04/internet/C/ndiswrapper.html)

---

### Post by uberlube on 2008-09-13
Use the howto in my sig and it will direct you to get it to work

---

### Post by flame0086 on 2008-09-13
never mind, figured it out thanks for the help

---

### Post by flame0086 on 2008-09-13
> **uberlube said:**
> Use the howto in my sig and it will direct you to get it to work

so everything goes smoothly until 'modprobe ndiswrapper'. It gives me
 
WARNING: /etc/modprobe.conf line 1: ignoring bad line starting with 'alias'
WARNING: /etc/modprobe.d/blacklist line 43: ignoring bad line starting with 'blasklist'

Not sure if that is suppose to happen, but when I reboot, I can no longer even see the wireless connections. I tried using both "wlan0" and "eth1".

---

