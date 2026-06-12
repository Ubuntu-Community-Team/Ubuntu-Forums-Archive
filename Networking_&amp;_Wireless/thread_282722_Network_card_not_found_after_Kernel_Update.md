---
title: "Network card not found after Kernel Update"
date: 2006-10-23
forum: Networking &amp; Wireless
---

### Post by ephie on 2006-10-23
Hello,

I installed Ubuntu Daper Drake and it right away connect to the internet through my network card to perform the automatic update!

Once the update was done, the computer restarted, but my network card is not recongnized anymore!

I realized that my kernel was updated... How come my network card is not recognized!

How can I get Ubuntu to recognize the network card driver with he new kernel?

(note:If I boot Ubuntu with the old Kernel the network card still works...)

Thanks for your help

---

### Post by spd106 on 2006-10-23
It sounds like the driver kernel modules haven't been updated or are not being loaded. What kind of network card is it? It might be useful to do a search for the driver and check that it is being loaded.

---

### Post by Suzan on 2006-10-23
Sure, you have the restricted-modules updated, too?

---

### Post by joergenlie on 2006-10-23
try reinstalling the wireless driver. I have compiled ndiswrapper and must reinstall it after kernel upgrade

Jørgen

---

### Post by jimmyk on 2006-10-23
If you are using Ndiswrapper with a Broadcom BCM4306 chip, there is a conflicting driver that comes with Dapper.  Can't remember what it's called, but you have to "rmmod" it.

---

### Post by ephie on 2006-10-30
I had a closer look ant the situation!

Ubuntu has the driver installed I think. I think it is more like a network connection problem!

I don't know how to add a network connection! I had a look in the help but the help is not uptodate and it still showes the old dialog box where the connections can be set up (it's the dialog box where you can set up you dialup internet connection over a normal modem). On the old dialog box there is a "add" button .... however on dapper drake the "add" button does not exist apparently!

how can I set it up trough a prompt?

eph!e

---

### Post by millhousecz on 2006-10-31
You must install linux-wlan-ng package.

sorry for my english

---

