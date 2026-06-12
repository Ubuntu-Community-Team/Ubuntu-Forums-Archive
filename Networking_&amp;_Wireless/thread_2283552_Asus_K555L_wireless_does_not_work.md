---
title: "Asus K555L wireless does not work"
date: 2015-06-22
forum: Networking &amp; Wireless
---

### Post by katz2 on 2015-06-22
Hi,

I have an Asus K555L as well, and I still couldn't manage to get the WLAN working.
My first attempt was with a Xubuntu-14.04.2, but I just tried with Ubuntu-15.04 as well.

```
lshw -c net; lspci -nnk | grep -iA2 net; rfkill list all
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: -------------
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168g-3_0.0.1 04/23/13 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:47 ioport:e000(size=256) memory:f7904000-f7904fff memory:f7900000-f7903fff
  *-network
       description: Network controller
       product: BCM43142 802.11b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=bcma-pci-bridge latency=0
       resources: irq:19 memory:f7800000-f7807fff
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
    Subsystem: ASUSTeK Computer Inc. Device [1043:200f]
    Kernel driver in use: r8169
03:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
    Subsystem: Lite-On Communications Inc Device [11ad:6675]
    Kernel driver in use: bcma-pci-bridge
1: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: asus-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no

```

I also tried installing the 4 packages from here: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.0.5-wily/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.0.5-wily/)
But nothing seemed to change, no enable wireless option at all.

I managed to buy myself a quite unique piece of hardware, because I couldn't get the WLAN working on Win7 either. The driver I got for it only works on Win8.1 and nothing else...

Any help is appriciated!

---

### Post by wildmanne39 on 2015-06-22
*Thread moved to **Networking & Wireless**.*

Hi, please click on the wireless script in my signature and follow the directions for running the script and posting the results here. 
Thanks

---

### Post by Pilot6 on 2015-06-23
You do wrong things. Instead of installing unsupported kernel, just install wireless drivers.

You need to remove that kernel image and headers, connect to internet by wire and run

sudo apt-get install bcmwl-kernel-source

Or go to System Settings -> Software & Updates -> Additional Drivers.

And there are hundreds of replies like that in the net.

---

### Post by katz2 on 2015-06-23
> sudo apt-get install bcmwl-kernel-source

Thanks, this alone solved the problem.
Sorry for the thread, I never had problems with the wlan on my devices so far, so I assumed it isn't a general problem and only tried searching for device specific stuff.

---

