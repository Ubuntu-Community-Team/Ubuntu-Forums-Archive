---
title: "How to install drivers in Ubuntu"
date: 2010-12-07
forum: New to Ubuntu
---

### Post by allbread on 2010-12-07
My current hardware (ignore my sig):

Tyan Thunder K8WE-S2915 / Ubuntu 10.04
2 x Opteron 856 / 4GB PC-3200
2 x EVGA GeForce 8800 PCIe
2 x 500GB SATA (RAID 0)

While I'm familiar with the interface for installing proprietary GPU drivers in Ubuntu 10.04 I was wondering how I should go about installing older/legacy chipset and/or RAID drivers. Specifically, I am retiring my old XP media center built around a Tyan Thunder K8WE S2895 motherboard and would like to upgrade the OS to the latest LTS release of Ubuntu.

According to Tyan the following drivers are available:

[ftp://ftp.tyan.com/drivers_linux/nVidia_chipset/](ftp://ftp.tyan.com/drivers_linux/nVidia_chipset/)

and

[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

Assuming that these drivers are not included by default in the 10.04 installation (or 2.6.32 kernel) how do I go about "installing" them once I've downloaded each relevant package - also, are these drivers kernel specific and, if so, how do I go about determining what the current kernel supports?

Thanks!

---

### Post by cariboo on 2010-12-07
I've been using nvidia based motherboards for years, I've never had to install any extra drivers for anything, The system I'm using right now uses the MPC61 chipsets.. On-board raid is a bit flaky, so I would suggest software raid, if you really need it.

---

### Post by allbread on 2010-12-08
> **cariboo907 said:**
> I've been using nvidia based motherboards for years, I've never had to install any extra drivers for anything, The system I'm using right now uses the MPC61 chipsets.. On-board raid is a bit flaky, so I would suggest software raid, if you really need it.

Thanks for the info. 

This board uses the Nvidia nForce 2200+2050 chipset.

In general, how does one go about determining which specific hardware drivers/chipsets are supported in a particular Ubuntu/Linux release... other than looking for random anecdotal "I've tried it and it works" responses on the web?

Is there documentation anywhere listing what chipsets are supported "out of the box"?

If a vendor provides Linux drivers how does one go about installing these in a particular Linux distribution - or determining if they are even compatible with a particular kernel?

---

