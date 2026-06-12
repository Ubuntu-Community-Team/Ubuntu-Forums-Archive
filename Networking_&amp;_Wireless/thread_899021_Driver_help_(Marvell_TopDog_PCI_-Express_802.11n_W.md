---
title: "Driver help (Marvell TopDog PCI -Express 802.11n Wireless (EC85)"
date: 2008-08-23
forum: Networking &amp; Wireless
---

### Post by BurnedKirby on 2008-08-23
I've tried installing the driver files but could not.. These old topics were somewhat useful...
[http://ubuntuforums.org/showthread.php?t=575785&highlight=TOPDOG+PCI+802.11n&page=3](http://ubuntuforums.org/showthread.php?t=575785&highlight=TOPDOG+PCI+802.11n&page=3)

[http://ubuntuforums.org/showthread.php?t=843398&page=2](http://ubuntuforums.org/showthread.php?t=843398&page=2)

But did not fix my problem. I followed the instructions on the first link, and using "sudo ndiswrapper -l" only gets me an error.
```

02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. Unknown device [11ab:2a08] (rev 03)

```

```

  *-network UNCLAIMED
       description: Ethernet controller
       product: Marvell Technology Group Ltd.
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0

```

```

stephen@Solstice:~/Desktop/netmw14x$ sudo ndiswrapper -a 11ab:2a08 netmw14x
WARNING: Driver 'netmw14x' will be used for '11AB:2A08'
This is safe _only_ if driver netmw14x is meant for chip in device 11AB:2A08
stephen@Solstice:~/Desktop/netmw14x$ sudo ndiswrapper -m
adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper ...

************************************************************************
*
* The update-modules command is deprecated and should not be used!
*
************************************************************************

stephen@Solstice:~/Desktop/netmw14x$ sudo ndiswrapper -m
module configuration already contains alias directive

stephen@Solstice:~/Desktop/netmw14x$ sudo depmod -a
stephen@Solstice:~/Desktop/netmw14x$ sudo modprobe ndiswrapper
stephen@Solstice:~/Desktop/netmw14x$ ndiswrapper -l
netmw14x : invalid driver!

```

Using M series Gateway Laptop with latest stable version of ubuntu (8.04.1?)

the netmw14x folder has a netmw143.sys, netmw145.sys, netmw146.sys (this file is a copy of netmw145.sys), and NetMW14x.inf.

I'm at a loss at what I should do... Any help?

---

### Post by BurnedKirby on 2008-08-24
bump.


(Sorry for double posting)

---

### Post by BurnedKirby on 2008-08-25
Sorry for triple posting, but is there seriously no one going to help? I guess I registered to this forum for nothing...

---

### Post by falcon61102 on 2008-08-31
It looks like you're getting the error because of the drivers that you used aren't for the chipset that you have.  Did you get the drivers from one of the old topics or did you download them yourself?

---

