---
title: "OPTi internet card driver"
date: 2008-06-14
forum: Networking &amp; Wireless
---

### Post by ForksHolder on 2008-06-14
Hello,

I have an OPTi internet card (Model: CCC-650).

My question is simple, how do i get the card's driver?

Thanks,
ForksHolder.

NOTE: I have a Compaq nc6220 laptop with Ubuntu Hardy 8.04

---

### Post by ForksHolder on 2008-06-14
Anybody?.. Please?..

I have to get this internet working.

---

### Post by ForksHolder on 2008-06-15
Bump?.....

---

### Post by chili555 on 2008-06-15
I have searched for this card and found nothing. It's imperative to know more details before we can associate a driver with it.

Do you have the Windows driver disc that came with the card in case ndiswrapper becomes the last alternative?

Is this a PCMCIA card? If so, please, from a terminal, let us see:```
 lspcmcia -v
```If it's a USB device, please show us:```
lsusb -v
```In any case, also let us see:```
sudo lshw -C network
```Thanks.

---

