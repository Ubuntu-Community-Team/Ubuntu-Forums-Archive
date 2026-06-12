---
title: "b43 broadcom driver"
date: 2011-02-05
forum: New to Ubuntu
---

### Post by dc1386 on 2011-02-05
I have both drivers, but I have the b43 activated, and when I restart my system the wireless internet connections are not shown.  I can activate the STA driver and I get internet, then activate the b43 driver and it works fine.  I was wondering if there was a way to not have to do this every time I restart my comp.

---

### Post by cariboo on 2011-02-05
You should only need one driver, I have a bcm4312 chipset in my netbook, that works well with the STA/wl driver.

---

### Post by TBABill on 2011-02-05
Mine is the same as cariboo's. The reason it isn't working at startup is probably because you have gone back and forth between drivers. This is a bad idea and they conflict with each other. Depending on the card you have you only need one or the other, but never both. Alternating will hose your /etc/modprobe.d/blacklist.conf file and other things, making it not just startup normally on restart.

---

### Post by dc1386 on 2011-02-05
well when i use the sta driver, i cant download anything for some reason so i changed to the b43 and it works fine. so r u saying i should get rid of the sta driver and see if that works?

---

