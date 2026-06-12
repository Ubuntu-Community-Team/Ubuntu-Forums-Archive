---
title: "Wavlink ac1300 install issues"
date: 2017-06-17
forum: Networking &amp; Wireless
---

### Post by ron_robinson on 2017-06-17
I just picked up a wavlink ac1300 usb 3.0 wifi adapter.  When i go to install via additional drivers, it will not add the two needed.  It just keeps going back to....device not working.  I need help.  Thank you.

---

### Post by chili555 on 2017-06-17
'Additional Drivers' only offers drivers for certain Broadcom devices. Yours is evidently not one of them.

Let's try to identify your device. Please run and post the result of the terminal command:```
lsusb
```

---

### Post by ron_robinson on 2017-06-17
Bus 006 device 002: Id obda: 8812 realtek semiconductor Corp. Rtl8812au 802.11a/b/g/n/a.c. elan adapter

---

### Post by chili555 on 2017-06-17
Here you go!  [https://askubuntu.com/questions/838131/having-problems-seeing-my-wifi-ubuntu-gnome-16-04/838368#838368](https://askubuntu.com/questions/838131/having-problems-seeing-my-wifi-ubuntu-gnome-16-04/838368#838368)

---

### Post by SeijiSensei on 2017-06-18
That's the solution that worked for me, too.

There's also this package for Xenial and later:  [https://packages.ubuntu.com/xenial/kernel/rtl8812au-dkms](https://packages.ubuntu.com/xenial/kernel/rtl8812au-dkms)

I'm still on Trusty so I built the driver from source as described in the askubuntu article.

---

