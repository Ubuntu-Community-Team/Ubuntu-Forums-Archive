---
title: "Realtek wifi driver install gone wrong"
date: 2018-03-18
forum: Networking &amp; Wireless
---

### Post by joecy on 2018-03-18
I am new to Ubuntu and have just installed Ubuntu 16 on my laptop. My wifi, was showing I had access but didn’t work. Then stopped showing. I search the Ubuntu help and tried installing drivers, my driver is 8723be. But I must have mistyped along the way and when I put in sudo modprobe -r rtl8723be I am getting an error message; 
Libkmod-config.c:635 kmod_config_parse: /etc/modprobe.d/rtl8723be.conf line1: ignoring bad line starting “options’

Any help with this would be great so I don’t have to go back to windows til I figure it out, bad timing on. Y part, have a uni assignment due.

---

### Post by ank2 on 2018-03-18
Sure the 8723be is the right driver? What is lspci saying, assuming it is on the PCI bus? Google for results about the driver name.

Since you didn't make the driver load permanent I'd reboot the machine and then go through the setup again. Try not to modprobe anything, unless your hardware a very new and Ubuntu might not recognize it yet.

---

### Post by jeremy31 on 2018-03-18
*Thread moved to **Networking & Wireless**.*
Please post results for ```
cat  /etc/modprobe.d/rtl8723be.conf
```

---

