---
title: "My wireless adapter isn't cooperating..."
date: 2008-05-03
forum: Networking &amp; Wireless
---

### Post by itsallcrap on 2008-05-03
Hi folks

I just installed Ubuntu 8.04 after previously having 7.10 (did a clean install rather than an upgrade)

Under 7.10, my wireless adapter worked perfectly.  Now it seems somehow deactivated.

Here's the result of a ' lshw -C network'

```
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:0e:00.0
       logical name: eth0
       version: 01
       serial: 00:1b:38:16:90:30
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK ip=192.168.1.114 latency=0 module=r8169 multicast=yes
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:14:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0

```

Note that the wifi doesn't have a logical name.  Nor is any sort of wireless connection acknowledged in my network settings.  A driver for it is listed in my Hardware Drivers bit, though.  

Could this be because I had the adapter powered off when I installed the OS?  What can I do?

Thanks,

Tom.

---

### Post by luisromangz on 2008-05-03
Is the driver that shows in the restricted drivers manager enabled? If it isn't, enable it and it will install the required firmware (provided you connect it to internet using an ethernet cable or other means, of course).

---

### Post by itsallcrap on 2008-05-04
Yes, it was enabled and still not having it, but happily I managed to solve the issue with ndiswrapper and a Windows wireless driver.

To anybody else having this problem, I used this guide:

[http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html](http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html)

For an extremely step-by-step kind of guide, it seems curious that this neglects to mention where you're actually supposed to get the ndis tarball from.  Don't even bother trying to find it, folks - Synaptic can do it for you.

You can mark this one solved, admin types.

Thanks for your input luisromangz

---

