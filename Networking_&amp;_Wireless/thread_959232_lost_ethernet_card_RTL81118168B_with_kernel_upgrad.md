---
title: "lost ethernet card RTL8111/8168B with kernel upgrade"
date: 2008-10-26
forum: Networking &amp; Wireless
---

### Post by maestrobwh1 on 2008-10-26
Ubuntu Hardy Upgraded kernel to 2.6.24-21 from 2.6.24-16.  

Internal Ethernet didn't work anymore.  

I never used the LAN in my EEE-pc, and just put the sd card in my EEE-box (very cool by the way).  When I had upgraded, I only got "lo" from "ifconfig"  

It took me a while to figure out what happened to my ZyDas USB 802.11b/g device.  It shows up as wlan0/master0 rather than eth1 as it did with the -16 kernel but at any rate, once I figured this out, it works well.

LAN Device with "lspci" lists as
**04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)**


_~$ sudo ifconfig eth0 up_
eth0: ERROR while getting interface flags: No such device
~$sudo ifconfig eth1 up 
ra0: ERROR while getting interface flags: No such device
~$

_~$ lshw -C Network_
WARNING: you should run this program as super-user.
  *-network DISABLED
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth2
       version: 02
       serial: 00:22:15:64:9b:0c
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK latency=0 module=r8169 multicast=yes

_~$ dmesg | grep -e eth_
[   53.244780] eth0: RTL8168c/8111c at 0xf883a000, 00:22:15:64:9b:0c, XID 3c4000c0 IRQ 220
[I][   54.577621] Driver 'sd' needs updating - please use bus_type methods
[   61.862634] Driver 'sr' needs updating - please use bus_type methods[/I]
**[   79.853502] udev: renamed network interface eth0 to eth2**

_~$ sudo ifconfig eth2 up_
~$ 

So it works, but at any rate, i**s the stuff in italics something to worry about?**  I assume that running in the EEE-pc has eth0 configured, and for some reason eth1 is still assigned to (a) the USB adapter, but the new kernel configures it differently so it shows eth1 not present anymore, as well.

No matter as long as it works I guess, but I posted this in part to learn what happened, and also, if someone else has a similar situation, it might help them.

---

