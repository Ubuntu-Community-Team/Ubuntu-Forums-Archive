---
title: "Lucent Wavelan 2 Mbps ISA Card Not Detected By Kernel"
date: 2008-10-25
forum: Networking &amp; Wireless
---

### Post by digiPixel on 2008-10-25
After looking at the system logs through "System Log" the Lucent Wavelan 2 Mbps ISA wireless card is not picked up. Has support for this device been removed with the recent Linux Kernels (in 2.6 series)? Currently the machine is running Ubuntu 8.04 LTS.

Are there any drivers (modules) that work with the card listed above for the 2.6.24-16-generic Kernel?

---

### Post by ddrichardson on 2008-10-26
I haven't poked around or recompiled a kernel in a while but assuming ISA support has been removed from the stock kernel, you could recompile one.

---

