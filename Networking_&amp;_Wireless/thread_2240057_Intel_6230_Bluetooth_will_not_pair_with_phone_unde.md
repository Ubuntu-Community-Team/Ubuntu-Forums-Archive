---
title: "Intel 6230: Bluetooth will not pair with phone under Ubuntu 14.04.1"
date: 2014-08-17
forum: Networking &amp; Wireless
---

### Post by MoebusNet on 2014-08-17
EDIT: Proper title should be 'Bluetooth will not connect with phone under Ubuntu 14.04.1'

Same phone (HTC Rezound with Android 4.0.3 OEM) connects with Lubuntu 14.04.1 using an Atheros 5212/5213 card on a different PC.

---

### Post by MoebusNet on 2014-08-18
OK, Bluetooth is able to transfer files & photos from phone to PC when I boot Lubuntu 14.04.1 (either 32-bit or 64-bit) from Live-USB using the same hardware. This would seem to rule out the  wireless card driver. I've filed a bug [Bug 1358134] against unity-control-center on Launchpad; we'll see how that goes.

---

### Post by MoebusNet on 2014-09-06
I've found a workaround that is working for me:

```
 sudo apt-get install lubuntu-desktop 
```

It didn't fix the original bluetooth  bug for Unity, but at least I can transfer photos from phone to PC via bluetooth now.

---

### Post by MoebusNet on 2014-09-25
Latest updates have completely broken Bluetooth on my system in 14.04 w/updates. :(

Phones & headset will pair but not connect on Ubuntu & Lubuntu DE's.

---

### Post by xc3RnbFO8P on 2014-09-25
Try to dissable Wifi > restart and connect bluetooth
afterwards you can enable Wifi

---

