---
title: "How to identifie wireless chipset"
date: 2007-07-16
forum: Networking &amp; Wireless
---

### Post by tsmiller on 2007-07-16
I just purchased a linksys wusb54gc wireless usb nic.  Is there a command that will tell me Specifically which wireless chipset is in this thing.  I am using Feisty 7.04.

I would like to know how to see the chipset information.  

The os is loading the ralink drivers.  How does the os identify the chipset?

Thanks,

Tom

---

### Post by t4thfavor on 2007-07-16
The OS (drivers) identify the chipset by its pciid. if you issue the command lspci -n you will see these ID's, alternatively to see the name of the device type lspci. 

I would imagine your machine would know what drivers to load, so you probably have ralink(is that realtek?) chips.

---

### Post by edwin.e.johnson on 2007-07-17
i have the same card wusb54gc ...... nothing but trouble its a usb wifi card so you have to
```
lsusb
```

i still havnt got this card to work with feisty if you have any lick let me know

---

