---
title: "Broadcom issues with kernel 2.6.24-16-generic"
date: 2008-05-08
forum: Networking &amp; Wireless
---

### Post by sjwest on 2008-05-08
The kernel 2.6.24-14-generic works fine.  In the 16-generic kernel that 8.04 has there is no wlan0 interface.  Seems this is the problem, not the with the networking per see.

[INDENT]lshw -C network

     *-network
       description: Wireless interface
       product: BCM4312 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:10:00.0
       logical name: wlan0
       version: 02
       serial: REMOVED
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.45+Broadcom,10/12/2006, 4.100. ip=HIDDEN latency=0 link=yes module=ndiswrapper multicast=yes wireless=IEEE 802.11g
[/INDENT]

This is an upgrade from version 7.

---

### Post by Ayuthia on 2008-05-08
> **sjwest said:**
> The kernel 2.6.24-14-generic works fine.  In the 16-generic kernel that 8.04 has there is no wlan0 interface.  Seems this is the problem, not the with the networking per see.

[INDENT]lshw -C network

     *-network
       description: Wireless interface
       product: BCM4312 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:10:00.0
       logical name: wlan0
       version: 02
       serial: REMOVED
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.45+Broadcom,10/12/2006, 4.100. ip=HIDDEN latency=0 link=yes module=ndiswrapper multicast=yes wireless=IEEE 802.11g
[/INDENT]

This is an upgrade from version 7.

The issue appears to be the version of NDISwrapper (Yours is showing 1.45).  2.6.24 needs to have an NDISwrapper version greater than 1.50.  I would use either the one from the repositories or go with 1.52 from the NDISwrapper site.

---

### Post by sjwest on 2008-05-08
Can we not blame the ndis driver that worked in 7.10 ?

---

### Post by Ayuthia on 2008-05-08
I am not trying to blame anything.  All I know is that 2.6.24 introduced the new Broadcom modules b43, b44, and ssb.  Because of this, NDISwrapper ran into problems.  The developers for NDISwrapper ended up having to make new versions to all NDISwrapper to work.  This came in version 1.50.  As far as I know, the best version that seems to be working is 1.52.

The only thing that Ubuntu can be blamed for is using the 2.6.24 kernel.  But at some point they are going to have to upgrade to a new kernel and they will still run into this.

Out of curiosity, did you install NDISwrapper from the repositories?

---

### Post by sjwest on 2008-05-08
> **Ayuthia said:**
> I am not trying to blame anything. Out of curiosity, did you install NDISwrapper from the repositories?

Ndiswrapper is fresh from the 8.04 upgrade.  I had the debian backports repo in 7.10 but thats still disabled in 8.04 and is not over used 

I will at some point download the newer wrapper and compile it from sourceforge.

---

### Post by Ayuthia on 2008-05-08
> **sjwest said:**
> Ndiswrapper is fresh from the 8.04 upgrade.  I had the debian backports repo in 7.10 but thats still disabled in 8.04 and is not over used 

I will at some point download the newer wrapper and compile it from sourceforge.

You might try to reload the driver (ndiswrapper -e/ndiswrapper -i).  I am thinking that the driver might not be able to be upgraded by Hardy.

---

