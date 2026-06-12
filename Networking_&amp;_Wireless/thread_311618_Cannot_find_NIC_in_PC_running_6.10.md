---
title: "Cannot find NIC in PC running 6.10"
date: 2006-12-03
forum: Networking &amp; Wireless
---

### Post by AndrewS on 2006-12-03
I just installed Edgy on my core-2-duo PC.  Installation went fine (unbelievably quick) but no internet connection.  The NIC seems to be an Attansic L1, which from some threads seems to be problematic.  I ran lspci and the last line referred to an ethernet controller, unknown device.  I tried to install LINUX_LAN (from DriverGuide.com) but it wouldn't install (lots of error messages about too many parameters).

Any suggestions?  Might be easier to install a NIC card, they're not expensive?

TIA

Andrew

---

### Post by sitedesign on 2006-12-03
You could either install the windows drivers using ndiswrapper or buy a different NIC.

Are you using a desktop system or laptop. For a desktop a basic PCI card will be easy and very cheap, or a laptop using a mini PCI card is also cheap. Go for simple Intel cards for mini PCI or any of the ones listed in the hardware compatibility list.
Look at the follwing for more detail. There are hardware lists for know to work cards both cabled and WIFI.
[https://help.ubuntu.com/community/NetworkDevices](https://help.ubuntu.com/community/NetworkDevices)

Hope that helps.

---

### Post by AndrewS on 2006-12-04
Peter

Thanks, I agree a new NIC seems the way to go.  I'm fairly new to Linux and don't know much about ndiswrapper.  I'm not sure whether is is a part of 6.10 by default, but anyway I suspect that not having an internet connection (which is why I might want to use ndiswrapper!) might be a handicap.  Maybe something to look into later.

Andrew

---

### Post by AndrewS on 2006-12-05
Peter

Installed a basic 10/100 NIC card last night, all works fine (well, the internet connection does - still some other bits to sort out but that's Linux!).  Thanks for your advice.

Andrew

> **sitedesign said:**
> You could either install the windows drivers using ndiswrapper or buy a different NIC.

Are you using a desktop system or laptop. For a desktop a basic PCI card will be easy and very cheap, or a laptop using a mini PCI card is also cheap. Go for simple Intel cards for mini PCI or any of the ones listed in the hardware compatibility list.
Look at the follwing for more detail. There are hardware lists for know to work cards both cabled and WIFI.
[https://help.ubuntu.com/community/NetworkDevices](https://help.ubuntu.com/community/NetworkDevices)

Hope that helps.

---

