---
title: "DWA-125 rev.A wireless dongle not working"
date: 2018-07-11
forum: Networking &amp; Wireless
---

### Post by loord on 2018-07-11
I'm currently dual-booting windows 8.1 and Ubuntu 16.04-i386 and my wireless usb doesnt seems to be working. I'm completely new to linux.

---

### Post by chili555 on 2018-07-11
Let's start by identifying your exact device. Please insert the USB wireless and open a terminal (Ctrl+Alt+t) and run:```
lsusb
```Post the result in your reply.

---

### Post by loord on 2018-07-11
> **chili555 said:**
> Let's start by identifying your exact device. Please insert the USB wireless and open a terminal (Ctrl+Alt+t) and run:```
lsusb
```Post the result in your reply.

thanks for replying. I was able to make it work by blacklisting integrated wireless card (rt2800pci). So, i guess the problem is fixed?

---

