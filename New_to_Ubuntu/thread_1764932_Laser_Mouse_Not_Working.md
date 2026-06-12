---
title: "Laser Mouse Not Working"
date: 2011-05-22
forum: New to Ubuntu
---

### Post by a.kleiner on 2011-05-22
I have a Targus Bluetooth Laser Mouse. My laptop, running Ubuntu 11.04, seems to recognize it (screenshot attached), but it won't actually work. Ideas?

---

### Post by LowSky on 2011-05-27
go to preferences on the bluetooth menu.

delete the mouse form the saved devices. re-add the mouse.  hopefully it works this time. FYI: if you pair the mouse to another device this could happen again and again.

---

### Post by khelben1979 on 2011-05-28
From what I can see on [their official webpage]("http://www.targus.com/uk/product_details.asp?sku=AMB08EU"), your mouse is only supported with MacOS X 10.4 and beyond, but... I guess they haven't bothered to note other operating systems.

The bluetooth mouse haveto get recognized by the bluetooth software stack in Ubuntu called [bluez]("http://www.bluez.org/"), the support varies depending on what version of the Linux kernel you're using, 2.6.38 is supported by Ubuntu 11.04.

If you don't get it working as LowSky suggested, you'll haveto consider getting a USB mouse instead or accept using the track pad only.

---

