---
title: "Netgear WNDA 3100v2 install on Ubuntu 17.10"
date: 2017-10-21
forum: Networking &amp; Wireless
---

### Post by keech69 on 2017-10-21
Hi All,  I have a Netgear WNDA 3100 V2 WiFi stick and downloaded drivers for it from another post, how do I install them please, I am new to Ubuntu as I fell out of favour with Windows 10 Creators update as it screwed my comp up :mad:  so any help will be appreciated.

Thanks in advance.

---

### Post by jeremy31 on 2017-10-21
*Thread moved to **Networking & Wireless**.*

---

### Post by praseodym on 2017-10-21
Hi,

this stick uses a Broadcom chipset which is not supported directly under Linux. However, Ndiswrapper can work with the Windows driver:
```

sudo apt-get install ndisgtk ndiswrapper-common build-essential dkms
```
Download the driver from here and unpack it:

[https://media-cdn.ubuntu-de.org/forum/attachments/37/11/2955302-Broadcom_bcm43xx_USB_32_64bit_v3.tar.gz](https://media-cdn.ubuntu-de.org/forum/attachments/37/11/2955302-Broadcom_bcm43xx_USB_32_64bit_v3.tar.gz)

Use the GUI to install the respective *.INF file for 32 or 64 bit, respectively.

---

### Post by kurt18947 on 2017-10-21
That chipset and linux have a long history but not a good one. If Praseodym's advice doesn't work, a USB wifi adapter known to work "out of the box" might be a good investment.

---

### Post by keech69 on 2017-10-21
Thanks for all the help, I tried all what was posted, but still didn't get it to work. In one of my many boxes of cables I found a usb to ethernet adapter and that works with a ethernet cable from the router, not pretty but it works :P
Thanks again .

---

### Post by kurt18947 on 2017-10-25
> **keech69 said:**
> Thanks for all the help, I tried all what was posted, but still didn't get it to work. In one of my many boxes of cables I found a usb to ethernet adapter and that works with a ethernet cable from the router, not pretty but it works :P
Thanks again .

Good for you. I use wifi only if there isn't a convenient ethernet port. I have Verizon FiOS which gives MoCa networking by default. Each coax outlet can become an ethernet port with the addition of an Ebay FiOS router and a couple changes in the router's firmware. Trouble free and speed is adequate for my purposes, plus I think wired is more secure.

---

