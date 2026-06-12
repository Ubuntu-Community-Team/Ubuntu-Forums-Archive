---
title: "Network Manager WEP but no WPA"
date: 2006-09-07
forum: Networking &amp; Wireless
---

### Post by fubar on 2006-09-07
I've got an CNet CWP-854 wlan card. And I've just installed Ubuntu on a new computer. 

I've installed Network Manager, and commented out all of the lines in /etc/networking/interfaces except from the ones containing lo. And the Network manager allows me to connect to WEP enabled networks ( or at least i lists them.. Since i don't have the passwd I would'nt know )

The network card supports WPA in windows...

But anyways, have you got any tips of how to fix this? That would make me very happy. ( after struggling for a week with installing ubuntu because of my motherbord having a JMicron ide controller.. )

---

### Post by x64Jimbo on 2006-09-07
Well if you commented out everything except 'lo' that might be your problem. Your wifi interface is not 'lo'
Try uncommenting those lines.

---

### Post by Darrena on 2006-09-07
> **fubar said:**
> I've got an CNet CWP-854 wlan card. And I've just installed Ubuntu on a new computer. 

I've installed Network Manager, and commented out all of the lines in /etc/networking/interfaces except from the ones containing lo. And the Network manager allows me to connect to WEP enabled networks ( or at least i lists them.. Since i don't have the passwd I would'nt know )

The network card supports WPA in windows...

But anyways, have you got any tips of how to fix this? That would make me very happy. ( after struggling for a week with installing ubuntu because of my motherbord having a JMicron ide controller.. )

Unfortunately the linux drivers may not support wpa, what chipset is it?

---

### Post by fubar on 2006-09-08
It's an RT 2500 chipset.

---

### Post by Darrena on 2006-09-08
> **fubar said:**
> It's an RT 2500 chipset.

That chipset is under active development and while the driver that shipped with Dapper is old and only supports WEP with NetworkManager you can try some of the Beta's at:
[http://rt2x00.serialmonkey.com/wiki/index.php/Main_Page](http://rt2x00.serialmonkey.com/wiki/index.php/Main_Page)

---

### Post by fubar on 2006-09-08
Thanks a lot for putting me on the right track.. not I'll just need to try to get it working :)

---

