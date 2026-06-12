---
title: "How to install INAMAX 1200AC wireless driver for Ubuntu 20.04"
date: 2020-05-24
forum: Networking &amp; Wireless
---

### Post by carlosgarcia351 on 2020-05-24
Please Help!

I am new to Ubuntu. I just installed Ubuntu as my OS system and noticed that my USB Wireless Antenna "INAMAX 1200AC" is not recognized by ubuntu. Does anyone knows how to find a suitable driver for Ubuntu and how to install it?

The device is the one shown in the link below

[https://www.amazon.com/Inamax-1200Mbps-Wireless-802-11ac-Mac10-6-10-13/dp/B0773ZPKS2](https://www.amazon.com/Inamax-1200Mbps-Wireless-802-11ac-Mac10-6-10-13/dp/B0773ZPKS2)

I would greatly appreciate your help!

Thanks in advance!

---

### Post by chili555 on 2020-05-25
What the device looks like on the outside doesn't help us find the correct driver. We need details!

Please insert the device and run the terminal command:

```
lsusb
```

Next, post the result and we'll proceed to the next steps.

---

### Post by Yellow Pasque on 2020-05-25
Vendor explicitly claims "No Linux support", but it is based on a Realtek 8812BU chipset, so maybe there is hope?

---

### Post by chili555 on 2020-05-25
> **Yellow Pasque said:**
> Vendor explicitly claims "No Linux support", but it is based on a Realtek 8812BU chipset, so maybe there is hope?Perhaps.

```
chili@T440p:~/Desktop/Forum/rtl88x2bu-5.6.1_30362.20181109_COEX20180928-6a6a$ modinfo 88x2bu.ko
filename:       /home/chili/Desktop/Forum/rtl88x2bu-5.6.1_30362.20181109_COEX20180928-6a6a/88x2bu.ko
version:        v5.6.1_30362.20181109_COEX20180928-6a6a
author:         Realtek Semiconductor Corp.
description:    Realtek Wireless Lan Driver
license:        GPL
srcversion:     FFCFBC04AC474141B5021C4
alias:          usb:v0B05p184Cd*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v0B05p1841d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v7392pC822d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v7392pB822d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v2357p0115d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v2357p012Dd*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v2001p331Ed*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v2001p331Cd*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v13B1p0043d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v0BDApB812d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v0BDApB82Cd*dc*dsc*dp*icFFiscFFipFFin*



```Possibly here: [https://github.com/cilynx/rtl88x2bu](https://github.com/cilynx/rtl88x2bu)

---

