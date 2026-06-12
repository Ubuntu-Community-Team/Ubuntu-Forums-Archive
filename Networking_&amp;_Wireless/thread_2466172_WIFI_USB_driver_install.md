---
title: "WIFI USB driver install"
date: 2021-08-21
forum: Networking &amp; Wireless
---

### Post by chris-rounce1 on 2021-08-21
New to Linux and want to use my USB WiFi adaptor as PC not close to router, can someone point me to a source to get a script to install drivers from a folder on a USB stick that has drivers for Linux for either my TL-WN725N and RTL8192CU adaptors
many thanks
Chris

---

### Post by chili555 on 2021-08-21
I assume the folder contains the manufacturer supplied drivers which are notoriously out-dated, so let's start fresh. Please insert the device and run and post:

```
lsusb
```

---

### Post by morrownr on 2021-08-22
Chris,

I agree with where chili555 is headed with this so please do what he is asking but then do this also:

Plug both adapters in (yes, both can be plugged in at the same time).

Run and post the results of the following with a terminal (command line) - to get a terminal Press and Hold Crtl + Alt, then press T :

```
iw dev
```

---

