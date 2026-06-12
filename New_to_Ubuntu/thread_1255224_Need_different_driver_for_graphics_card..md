---
title: "Need different driver for graphics card."
date: 2009-09-01
forum: New to Ubuntu
---

### Post by arnicainthemembrane on 2009-09-01
I have an old IBM Thinkpad T40 running ubuntu v. 8.04.

Graphics Card: RV350 [Mobility Radeon 9600 M10]

I'd like to upgrade to 8.10 so I can use Firefox 3.5, etc.

My problem is, when I attempt to upgrade, I'm told there aren't any drivers available for my graphics card:

**"This computer is currently using the AMD 'fglrx' graphics driver. No version of this driver is available that works with your hardware in Ubuntu 8.10**"

I'm also told that my "ATI accelerated graphics driver" is proprietary and therefore can't be upgraded or supported by ubuntu.

Is there some means by which I can fix this problem? Can I download another graphics driver thereby opening up the system to a distro upgrade? Or will an upgrade only be possible with another graphics card and -because mine is permanently soldered to the systems board - therefore another computer?

---

### Post by alphacrucis2 on 2009-09-01
> **arnicainthemembrane said:**
> I have an old IBM Thinkpad T40 running ubuntu v. 8.04.

Graphics Card: RV350 [Mobility Radeon 9600 M10]

I'd like to upgrade to 8.10 so I can use Firefox 3.5, etc.

My problem is, when I attempt to upgrade, I'm told there aren't any drivers available for my graphics card:

**"This computer is currently using the AMD 'fglrx' graphics driver. No version of this driver is available that works with your hardware in Ubuntu 8.10**"

I'm also told that my "ATI accelerated graphics driver" is proprietary and therefore can't be upgraded or supported by ubuntu.

Is there some means by which I can fix this problem? Can I download another graphics driver thereby opening up the system to a distro upgrade? Or will an upgrade only be possible with another graphics card and -because mine is permanently soldered to the systems board - therefore another computer?

I think your card should be fine with the Catalyst 9.3 fglrx driver which should work with 8.10 (it won't work with 9.04 as you need Catalyst 9.4 or greater for that and your card isn't supported by those later versions of fglrx). Normally you just Select System - Administration - Hardware Drivers. If it doesn't offer the fglrx driver then you could allways download Catalyst 9.3 (linux version) from ATI's driver website. Make sure you strictly follow the instructions given on the site.:

[http://support.amd.com/us/gpudownload/Pages/index.aspx]("http://support.amd.com/us/gpudownload/Pages/index.aspx")

The other option you have is to use the Open Source radeon driver.

---

### Post by 3rdalbum on 2009-09-01
> **arnicainthemembrane said:**
> I have an old IBM Thinkpad T40 running ubuntu v. 8.04.

Graphics Card: RV350 [Mobility Radeon 9600 M10]

I'd like to upgrade to 8.10 so I can use Firefox 3.5, etc.

Firefox 3.5 isn't in 8.10, but you can download it from the Mozilla website and install it locally.

The "fglrx" driver isn't the only driver that's available for ATI cards. There's also an open-source driver that even supports 3D on some cards. Basically, get an 8.10 live CD and try it out, because the open-source ATI driver is the default.

ATI has been removing support for some of their older chipsets, so if your card isn't supported with the newer proprietary drivers, and the older proprietary drivers don't work with the new Ubuntu, then you can't do anything about it except use the open-source driver.

---

