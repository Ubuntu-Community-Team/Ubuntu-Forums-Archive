---
title: "Problem with Broadcom wireless card"
date: 2007-09-11
forum: Networking &amp; Wireless
---

### Post by neonl on 2007-09-11
I have an Acer laptop equipped with a Broadcom wireless card. I installed Ubuntu and it recognized the card, though I cannot connect to the network. I went to the manual settings, disabled the roaming mode, specified the IP addresses, the DNS address. The computer has a button for the wireless card but it doesn't work even if I press it...

Any thing I must do?

---

### Post by kevdog on 2007-09-11
Did you install any drivers?  Broadcom chipsets are not natively supported in linux.  They require either the user space utilities of the bcm43xx driver be installed or to use ndiswrapper with the winxp drivers.

Let me know if you need help

---

### Post by noob12 on 2007-09-11
You typically need to load or enable either acerhk or acer_acpi in order to enable the wireless radio.  What series of Acer laptop do you have and which version of Ubuntu do you have installed?  The instructions depend on at least that info.

---

### Post by neonl on 2007-09-20
> **noob12 said:**
> You typically need to load or enable either acerhk or acer_acpi in order to enable the wireless radio.  What series of Acer laptop do you have and which version of Ubuntu do you have installed?  The instructions depend on at least that info.

The acer laptop is an Aspire 5051. I'm using Ubuntu Festy

Thanks

---

