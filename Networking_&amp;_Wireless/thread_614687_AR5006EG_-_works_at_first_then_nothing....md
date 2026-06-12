---
title: "AR5006EG - works at first then nothing..."
date: 2007-11-16
forum: Networking &amp; Wireless
---

### Post by nivnac on 2007-11-16
Hope someone can help with this one, it's been driving be up the wall.

I have a new Samsung R60 with AR5006EG Wireless. I doesn't work out of the box but after installing the ndiswrapper all was working well. I had a nice long list of wireless networks under nm-applet and was able to connect to mine easily.

However as soon as I rebooted I can no longer see any wireless networks, no matter what I try.

What's going on?
Anyone have any tricks to try here?

---

### Post by Digger78 on 2007-11-17
is ndiswrapper loading at boot?

If not, add ndiswrapper to  /etc/modules

---

### Post by inversis on 2007-11-17
same problem here.

with commands showed here.
[http://www.uluga.ubuntuforums.org/showthread.php?p=3786519&posted=1#post3786519](http://www.uluga.ubuntuforums.org/showthread.php?p=3786519&posted=1#post3786519)

I have "ndiswrapper" on /etc/modules

Btw, i notice something strange:

sudo lshw -C network
```
  *-network               
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 01
       serial: 00:19:db:ef:4f:cb
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=half latency=0 link=no module=r8169 multicast=yes port=twisted pair
[COLOR="Red"]  *-network DISABLED
       description: Wireless interface[/COLOR]
       product: AR5006EG 802.11 b/g Wireless PCI Express Adapter
       vendor: Atheros Communications, Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 00:15:af:4f:07:6f
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net5211 driverversion=1.49+,11/15/2006,5.1.1.9 latency=0 link=no module=ndiswrapper multicast=yes wireless=IEEE 802.11g
```


could this be the problem?
"  *-network DISABLED
       description: Wireless interface"

---

### Post by Digger78 on 2007-11-17
> **inversis said:**
> same problem here.

with commands showed here.
[http://www.uluga.ubuntuforums.org/showthread.php?p=3786519&posted=1#post3786519](http://www.uluga.ubuntuforums.org/showthread.php?p=3786519&posted=1#post3786519)

I have "ndiswrapper" on /etc/modules

Btw, i notice something strange:

sudo lshw -C network
```
  *-network               
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 01
       serial: 00:19:db:ef:4f:cb
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=half latency=0 link=no module=r8169 multicast=yes port=twisted pair
[COLOR="Red"]  *-network DISABLED
       description: Wireless interface[/COLOR]
       product: AR5006EG 802.11 b/g Wireless PCI Express Adapter
       vendor: Atheros Communications, Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 00:15:af:4f:07:6f
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net5211 driverversion=1.49+,11/15/2006,5.1.1.9 latency=0 link=no module=ndiswrapper multicast=yes wireless=IEEE 802.11g
```


could this be the problem?
"  *-network DISABLED
       description: Wireless interface"

I see from your other post that you have not blacklisted the "alternate" driver

> net5211 : driver installed
        device (168C:001C) present ([COLOR="Red"]alternate driver: ath_pci[/COLOR])


add **ath_pci** to **/etc/modprobe.d/blacklist** then [B]reboot
[/B]
 ndiswrapper -l should now show

net5211 : driver installed
        device (168C:001C) present

if **sudo lshw -C network** still shows "network disabled" try **ifconfig wlan0 up**

let me know how it goes. i had some trouble getting "associated" with my router, but it working now ;)

---

