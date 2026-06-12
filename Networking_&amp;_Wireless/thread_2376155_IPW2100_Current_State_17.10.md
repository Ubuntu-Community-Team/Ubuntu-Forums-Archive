---
title: "IPW2100 Current State 17.10"
date: 2017-10-30
forum: Networking &amp; Wireless
---

### Post by databoy2k on 2017-10-30
Hi All:

Working on an ancient old Toshiba Tecra that my dad insists on using and that rightfully never saw beyond Windows XP. Time for some security.

I've set up Lubuntu although when I did the wireless switch was off. I turned it back on but cannot seem to get the wifi adapter to turn on.

dmesg comes up with:
```
ipw2100: eth%d: Error initializing Symbol
ipw2100: eth%d: Error loading microcode: -5
ipw2100: eth%d: Failed to power on the adapter.
ipw2100: eth%d: Failed to start the firmware.
ipw2100 000:02:05.0: Driver probe function unexpectedly returned 1
```

Obviously the latest kernels have the 1.3 firmware in them. Confirmed with ls /lib/firmware | grep ipw2100

--Edit-- As one more quick piece of info, the wifi was working during its past life on XP, so I don't think the card itself is dead.

Thousands of ancient threads wondering how to get this stupid card working. Is it still a no-go, or do we now have a good idea how to fix it?

Thanks!

--Databoy2k

---

### Post by praseodym on 2017-10-31
Which Lubuntu version is it?

---

### Post by databoy2k on 2017-10-31
17.10

---

### Post by jeremy31 on 2017-10-31
Have you tried 16.04?  This is one of the older Intel chipsets still supported but I don't know how well they are supported now as there are a lot fewer users to submit issues

---

### Post by chili555 on 2017-11-01
May we see:```
lshw -C network
lspci -nnk | grep 0280 -A3
```

---

### Post by chili555 on 2017-11-01
> **mörgæs said:**
> Sorry, then please ignore the post. I hoped they were closely related.No worries. Please note that after I saw my mistake, I edited my post. My goof.

---

### Post by databoy2k on 2017-11-02
```
*-network:0               
       description: Network controller
       product: PRO/Wireless LAN 2100 3B Mini PCI Adapter
       vendor: Intel Corporation
       physical id: 5
       bus info: pci@0000:02:05.0
       version: 04
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: driver=ipw2100 latency=64 maxlatency=34 mingnt=2
       resources: irq:11 memory:fceff000-fcefffff
  *-network:1
       description: Ethernet interface
       product: 82801DB PRO/100 VE (MOB) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: enp2s8
       version: 83
       serial: 00:08:0d:e3:27:fe
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full ip=10.10.1.140 latency=64 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100Mbit/s
       resources: irq:11 memory:fcefe000-fcefefff ioport:cf40(size=64)

02:05.0 Network controller [0280]: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter [8086:1043] (rev 04)
	Subsystem: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter [8086:2580]
	Kernel driver in use: ipw2100
	Kernel modules: ipw2100, wl
```

---

### Post by chili555 on 2017-11-02
> Kernel modules: ipw2100, wlInteresting. Let's remove the incorrect driver in case it conflicts:```
sudo apt purge bcmwl-kernel-source
```Your readings, so far, look pretty solid except for the dmesg in the original post. May we now see:```
rfkill list all
dmesg | grep 02:05
```

---

