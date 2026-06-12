---
title: "Wifi Drops every 2 minutes"
date: 2015-10-08
forum: Networking &amp; Wireless
---

### Post by matthewism on 2015-10-08
Ever since i have installed ubuntu (yesterday) i've been having this problem, when wifi drops i constantly have to reconnect its really annoying. 
LSHW -C network command result:
```
matthew@matthew-pc:~$ sudo lshw -C network
[sudo] password for matthew: 
PCI (sysfs)  


  *-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 11
       serial: 10:c3:7b:4e:23:d9
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168g-2_0.0.1 02/06/13 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:35 ioport:e000(size=256) memory:fea00000-fea00fff memory:f0000000-f0003fff
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@6:1
       logical name: wlan0
       serial: 80:1f:02:f1:ea:5b
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192cu driverversion=3.19.0-25-generic firmware=N/A ip=192.168.1.119 link=yes multicast=yes wireless=IEEE 802.11bgn
matthew@matthew-pc:~$ 
matthew@matthew-pc:~$ 
matthew@matthew-pc:~$
```

---

### Post by jeremy31 on 2015-10-08
Post the result of ```
lsusb
```
It might be one supported by Pvaret's driver on github

---

### Post by matthewism on 2015-10-08
> **jeremy31 said:**
> Post the result of ```
lsusb
```
It might be one supported by Pvaret's driver on github

Thanks! i'll try downloading Pvarets driver.

---

### Post by matthewism on 2015-10-08
Thank you very much for poviding me with that source now my internet is working fine on ubuntu thanks alot!

---

### Post by jeremy31 on 2015-10-08
For other people that may find this post

There is a list of supported devices at [https://github.com/pvaret/rtl8192cu-fixes/blob/master/os_dep/linux/usb_intf.c](https://github.com/pvaret/rtl8192cu-fixes/blob/master/os_dep/linux/usb_intf.c) starting at line 72

If your USB results show ID ????:8172 just search the file for 8172 and see if there is a match

If you do get a match, follow instructions under "Installation" from [https://github.com/pvaret/rtl8192cu-fixes](https://github.com/pvaret/rtl8192cu-fixes)

Mathewism, please use the thread tool dropdown at the top of the page to 'Mark as solved'

I think Pilot6's PPA [https://launchpad.net/~hanipouspilot/+archive/ubuntu/rtlwifi](https://launchpad.net/~hanipouspilot/+archive/ubuntu/rtlwifi) has the same code as a deb file under rtl8192cu-dkms

---

