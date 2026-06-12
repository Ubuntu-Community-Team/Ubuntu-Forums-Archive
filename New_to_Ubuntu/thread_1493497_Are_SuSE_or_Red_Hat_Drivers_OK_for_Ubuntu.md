---
title: "Are SuSE or Red Hat Drivers OK for Ubuntu?"
date: 2010-05-25
forum: New to Ubuntu
---

### Post by slalomchip on 2010-05-25
I have Ubuntu 10.4 on a Dell Inspiron 1420 laptop with a PCI Express port.  I also have an IOGear 2-port eSATA PCI Express SATA 300 controller card.  I'd like to use the eSATA controller card in the laptop, but IOGear does not support Linux drivers.

However, IOGear Tech Support said that their chipset is the si3132 from Silicon Image and pointed me to the SI support page, where SI provides driver downloads for SuSE 9.0 (Linux kernel 2.6.5-7.191) and Red Hat 4.0 (Linux kernel 2.6.9-34) distributions.  There were no Ubuntu distributions listed.

Before attempting to load one of these drivers (and screwing up my laptop), I thought I'd ask if anyone has recommendations of what I should do.  Should I proceed loading the drivers for either SuSE or RH, is one preferred over the other, or should I just walk away from the whole thing (and maybe look fir a different hardware vendor that supports a Ubuntu driver or a generic Linux driver?

Thanks in advance.

---

### Post by sylvester_0 on 2010-05-25
Those kernels you listed are pretty old (we're up to 2.6.34 now.) Are you sure the hardware doesn't "just work?" I'm guessing the driver for your device is in mainline and you won't need to do any additional work except plug it in.

---

### Post by -humanaut- on 2010-05-25
> **sylvester_0 said:**
> Those kernels you listed are pretty old (we're up to 2.6.34 now.) Are you sure the hardware doesn't "just work?" I'm guessing the driver for your device is in mainline and you won't need to do any additional work except plug it in.

+1

I'd be difficult to install those drivers (I'm assuming no source code is available) you'd have to try and convert the binaries with Alien or some other method to a .deb file both Suse and Red hat use .rpm. But I'm assuming as sylvester suggested they should "just work" now.

---

### Post by Yanno on 2010-05-26
try to update ur source list and make an upgrade.

---

