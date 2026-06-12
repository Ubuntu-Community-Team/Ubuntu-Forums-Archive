---
title: "Wireless not working after Ubuntu 10 install"
date: 2010-07-28
forum: New to Ubuntu
---

### Post by sugarwellington on 2010-07-28
I've installed ubuntu on my laptop and the wireless is not working.  I have an icon in the notification area with a grayed out wireless symbol and a red bang embedded in it.  When I left click it has grayed out "Wireless Network \n disconnected" and then "VPN Connections ->"... when I right click it has "Enable Networking" (checked), "Enable Notifications" (checked), Connection Information (grayed out), Edit Connections..., About

Isn't Ubuntu supposed to detect the wireless networks available and allow me to connect to one?  What am I doing wrong?  I've been looking in all the forums but I haven't found anything.

Thanks for any help.

Here is output for *sudo lshw -C network*
> 
  *-network               
       description: Network controller
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:f9ffc000-f9ffffff memory:f0000000-f00fffff(prefetchable)
  *-network
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:c9:05:31:0c
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.102 firmware=sb v3.04 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:30 memory:f9bf0000-f9bfffff


---

### Post by Megaptera on 2010-07-29
Hi,
You could try this simple fix. It's worked for me with Broadcom on my Dell with Ubuntu 9.10 & 10.04.
Don't forget to reboot afterwards:

[http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html](http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html)

Hope this helps?

---

### Post by sugarwellington on 2010-07-29
Dude, this totally works! You have my restored my rapidly fading faith in Ubuntu.  Thank you!

---

### Post by Megaptera on 2010-07-30
You're welcome! Very glad it worked.

---

### Post by Jazzy_Jeff on 2010-07-30
> **sugarwellington said:**
> Dude, this totally works! You have my restored my rapidly fading faith in Ubuntu.  Thank you!

There is usually a fix for most things in Linux. Just remember most things are made for Windows. I think Linux does an awesome job with most hardware.

---

