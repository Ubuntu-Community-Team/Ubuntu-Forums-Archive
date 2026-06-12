---
title: "Wifi not working lenovo s21e"
date: 2017-03-05
forum: Networking &amp; Wireless
---

### Post by rensvanbreukelen on 2017-03-05
Hello,

I've just started using ubuntu, because it's not as space consuming as windows (quite helpfull on a 32g ssd). The problem is, is that I cannot get it to connect to wifi. The wifi icon is blank and it says "No network devices available". I've installed the bcmwl-kernel-source driver, but it's still not working. I'm using an broadcom corporation bcm43142 rev 01, according to lspci. I've already spend 3 hours browsing the net for fixes, downloaded this, downloaded that, did this, did that but its STILL NOT WORKING. I was hoping if one of you guys could help me out! Whatt do i have to do to fix this?

---

### Post by jeremy31 on 2017-03-05
Do you see an error about cannot insmod wl no required key if you
```
sudo modprobe -v wl
```

You will likely have to disable Secure Boot in BIOS

---

### Post by rensvanbreukelen on 2017-03-05
Thanks man! that did it!

---

