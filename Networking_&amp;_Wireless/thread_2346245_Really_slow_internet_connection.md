---
title: "Really slow internet connection"
date: 2016-12-12
forum: Networking &amp; Wireless
---

### Post by ijack2020 on 2016-12-12
Can someone help me I'm on an MSI GT780R, running Ubuntu 16.04. The internet is incredibly slow, it seems this problem only happens on Linux. When I use Windows, the internet works just fine. Usually when I download anything, the entire internet sort of freezes until the download is complete. For example, I could download Eclipse, and the internet won't work (or will work incredibly slow) until Eclipse finishes. From there, it'll work okay, sometimes not work at all.

I ran this command: sudo lshw -C network

And the results were.

```
 *-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: enp2s0
       version: 06
       serial: 6c:62:6d:30:83:6c
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8168e-2.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:36 ioport:d000(size=256) memory:ec104000-ec104fff memory:ec100000-ec103fff
  *-network
       description: Wireless interface
       product: Centrino Wireless-N 130
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlp3s0
       version: 34
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=4.4.0-53-generic firmware=18.168.6.1 ip=10.0.0.190 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:39 memory:f6200000-f6201fff
  *-network
       description: Ethernet interface
       physical id: 6
       bus info: usb@1:1.5
       logical name: enp0s26u1u5c4i2
       capabilities: ethernet physical
       configuration: broadcast=yes driver=ipheth link=no multicast=yes

```

I'm really not sure what to do, I tried looking for the drivers, and ran into it on Intel's official page. But apparently I already have it in /lib/firmware ? Really confused, any help would be appreciated.

---

### Post by kpatz on 2016-12-12
Are you connected wired or wireless?

Looks like your problem is here:```
speed=10Mbit/s
capacity: 1Gbit/s
```Your NIC is gigabit capable but it's only connecting at 10baseT speed.

Maybe a bad cable, or switch/router port?

What's the output of this command:```
sudo mii-tool -v enp2s0
```

---

### Post by ijack2020 on 2016-12-12
I'm connected wireless, sorry for not mentioning that. When I run the command I get this

```
enp2s0: no link
  product info: vendor 00:07:32, model 17 rev 4
  basic mode:   autonegotiation enabled
  basic status: no link
  capabilities: 1000baseT-HD 1000baseT-FD 100baseTx-FD 100baseTx-HD 10baseT-FD 10baseT-HD
  advertising:  100baseTx-FD 100baseTx-HD 10baseT-FD 10baseT-HD flow-control
```

---

### Post by wildmanne39 on 2016-12-12
Hi, please click on the wireless script in my signature and follow the directions for running the script and posting the results here. 
Thanks

---

