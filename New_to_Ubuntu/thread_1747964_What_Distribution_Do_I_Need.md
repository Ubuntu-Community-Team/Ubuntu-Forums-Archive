---
title: "What Distribution Do I Need"
date: 2011-05-03
forum: New to Ubuntu
---

### Post by Mannimarco on 2011-05-03
I want to install proprietary video driver for ATI Radeon X1600. But I have read that this card is no longer supported by ATI ([http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide))

Do I need to install Ubuntu 8.04 or just install 10.10/11.04 and use open source driver? (I want games to run faster)

And, by the way, what is the difference between proprietary and open source drivers? I heard open source drivers were slower, but how much slower? For example if I have 100 fps using proprietary driver, how many I will have using open source?

Just in case, my PC configuration:
Pentium 4 3GHz, Motherboard ASUS P5LD2 SE, Radeon X1600 256 MB, 1GB RAM, 200GB HDD.

---

### Post by seawolf167 on 2011-05-03
I always like to use the LTS versions of Ubuntu, put it is personal preference. You should be fine using any version.

A quick search for your drivers from ATI shows that the proprietary drivers are available for [download here]("http://support.amd.com/us/gpudownload/linux/legacy/Pages/radeon_linux.aspx?type=2.4.2&product=2.4.2.3.10&lang=us&rev=9.3&ostype=Linux%20x86"). They will almost certainly be available via the System -> Administration -> Hardware Drivers search as well since they are older legacy drivers.

I like the proprietary drivers because I they have a little more features, but the open source drivers, especially for older cards will have a hardly noticeable difference.

---

### Post by clhsharky on 2011-05-03
> The Linux ATI Catalyst&#8482; driver will only be supported in Linux distributions prior to February 2009 for the legacy products listed above.
Cat 9.3 will only work on Ubuntu 8.04 8.10 releases and is no longer a supported release.


Sharky

---

### Post by clhsharky on 2011-05-03
Mannimarco

I have a ATI Radeon X1650 card and Natty has the fastest Open Source Stack radeon driver for 3D.


Sharky

---

### Post by pme 72 on 2011-05-04
You might find some answers about relative performance in articles from Phoronix.com like this one from today:

May 2011: Gallium3D vs. Classic Mesa vs. Catalyst
[http://www.phoronix.com/scan.php?page=article&item=amd_mesa_mai2011&num=1](http://www.phoronix.com/scan.php?page=article&item=amd_mesa_mai2011&num=1)

---

### Post by Mannimarco on 2011-05-06
Thank everyone for the answers, I will install either 10.10 or 11.04. Windows will be for games only. I need to learn a lot before I'll be able to understand Wine error messages.

Solved

---

