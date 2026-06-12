---
title: "AMD compatible 9.04?"
date: 2009-08-12
forum: New to Ubuntu
---

### Post by dizzy1kenobi on 2009-08-12
Does anyone know if and when an AMD compatible version of 9.04 will be done?

---

### Post by zerhacke on 2009-08-12
AMD has always been well supported in the Linux community.

---

### Post by credobyte on 2009-08-12
Check my signature ( haven't had any troubles with Ubuntu on my AMD ) ..

---

### Post by philinux on 2009-08-12
> **credobyte said:**
> Check my signature ( haven't had any troubles with Ubuntu on my AMD ) ..

Snap.

---

### Post by dizzy1kenobi on 2009-08-12
Every time I go to upgrade I get a warning that says:

"Upgrading may reduce desktop effects, and performance in games and other graphically intensive programs.

This computer is currently using the AMD 'fglrx' graphics driver. No version of this driver is available that works with your hardware in Ubuntu 9.04."

Is there another driver?

---

### Post by jimsheep on 2009-08-12
unfortunately not.  you may want to stick with 8.04, as it's got the best support for ATI cards.  that said, i'm having almost no issues with the open source drivers in 8.10

---

### Post by WRDN on 2009-08-12
> **dizzy1kenobi said:**
> Every time I go to upgrade I get a warning that says:

"Upgrading may reduce desktop effects, and performance in games and other graphically intensive programs.

This computer is currently using the AMD 'fglrx' graphics driver. No version of this driver is available that works with your hardware in Ubuntu 9.04."

Is there another driver?

I installed the AMD video driver recently for my ATI 4870 1Gb GPU, and it worked fine- this was the closed source driver from AMDs website. Sadly, the same did not hold true for my recently Fedora 11 installation- the closed source fglrx driver does not work with kernels 2.6.29+ currently, without rebuilding and modifying the kernel image. I would personally wait till next Monday, as the Catalyst 9.8 will be released then- the driver is available at Quakecon 2009 (starting Thursday) so someone will likely post it on the internet.

As for other drivers, you could try the open source RadeonHD driver.

---

