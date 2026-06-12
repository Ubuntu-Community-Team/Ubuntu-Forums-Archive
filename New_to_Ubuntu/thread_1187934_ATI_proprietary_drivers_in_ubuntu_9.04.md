---
title: "ATI proprietary drivers in ubuntu 9.04"
date: 2009-06-15
forum: New to Ubuntu
---

### Post by akkad on 2009-06-15
i used to use the ATI proprietary drivers in the older ubuntu versions, where it used to appear in the proprietary drivers list with an option to activate it, now in ubuntu 9.04 it is not listed, and when i install the driver package (xorg-driver-fglrx) ubuntu hangs after the boot with unsuccessful reach to the login screen, so i removed this package and rolled back to the default one, so is there any possibility to install this driver?

the reason why i want this driver is, it used to give better graphics where currently with the default driver i have some broken graphics and flickered rendering.

---

### Post by Brinstar on 2009-06-15
> **akkad said:**
> i used to use the ATI proprietary drivers in the older ubuntu versions, where it used to appear in the proprietary drivers list with an option to activate it, now in ubuntu 9.04 it is not listed, and when i install the driver package (xorg-driver-fglrx) ubuntu hangs after the boot with unsuccessful reach to the login screen, so i removed this package and rolled back to the default one, so is there any possibility to install this driver?

the reason why i want this driver is, it used to give better graphics where currently with the default driver i have some broken graphics and flickered rendering.

downgrade to ubuntu 8.10, or 8.04

support for older drivers was removed from 9.04.

---

### Post by BlueFiberOptics on 2009-06-15
Isn't there a new open source driver people with older ATI cards can use?

---

### Post by Brinstar on 2009-06-15
> **BlueFiberOptics said:**
> Isn't there a new open source driver people with older ATI cards can use?

yes but the performance is a lot worse than the official ATI drivers. like 30% worse.

---

### Post by akkad on 2009-06-15
> **Brinstar said:**
> yes but the performance is a lot worse than the official ATI drivers. like 30% worse.

but what about the original drivers cant we use them?

---

### Post by BlueFiberOptics on 2009-06-15
The original drivers that support Ubuntu 9.04 no longer support the older chipsets found in older ATI cards.

---

### Post by ugm6hr on 2009-06-15
ATI dropped support for a variety of legacy chipsets (including some less than 2 years old).

[http://support.amd.com/us/gpudownload/linux/legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.7&lang=English](http://support.amd.com/us/gpudownload/linux/legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.7&lang=English)

Bottom line:

> The Linux ATI Catalyst™ driver will only be supported in Linux distributions prior to February 2009 for the legacy products listed above.

I found the RadeonHD driver worth trying.

---

### Post by porchrat on 2009-06-15
That really irritated me. My X1250 no longer has support. How can it be legacy already I bought the thing less than a year ago?!

Oh well, I wish nvidia would hurry it up with the awesome laptop chips already because if this is the way ATI behave I my next laptop will definitely contain an nvidia GPU

---

