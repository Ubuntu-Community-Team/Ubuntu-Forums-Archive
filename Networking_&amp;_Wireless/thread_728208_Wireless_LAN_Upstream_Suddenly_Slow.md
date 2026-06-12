---
title: "Wireless LAN Upstream Suddenly Slow"
date: 2008-03-18
forum: Networking &amp; Wireless
---

### Post by jelly on 2008-03-18
I posted this in the wrong forum (Hardware & Laptops) a little while ago and didn't get any response, so I've reposted it here with some more information about my setup.

In short: Data transfers TO my machine are slow (~60KB/s), data transfers FROM my machine are as expected (~1.1MB/s).  This has only recently started happening - and I've not installed anything but updates to existing software.  Other machines on the network are fine.

In long: I've had an Ubuntu 7.10 install on my desktop machine since its release that's had no problems at all. Just over a month ago I changed to a new wireless router (in a new place) which, again, has been working perfectly.

For some reason, however, the other day my wireless LAN upstream has suddenly dropped dramatically. I have three machines on my wireless LAN - A, B and U - U is the Ubuntu desktop with the problem. Here are the things I've tested..

A -> U: 1.1MB/s
U -> A: 60KB/s
A -> B: 1.1MB/s
B -> A: 1.1MB/s
B -> U: 1.1MB/s
U -> B: 60KB/s

What on EARTH is going on!?! I've reset everything, of course, tried turning off machines so there are only two on the wireless network at any one time, etc.

I don't have the exact details of my desktop (U) wireless card, drivers, etc. handy but I'll post them later. At this stage I was just wondering if anyone had any thoughts on where to look to determine the source of the problem.

As it's something that's only just started happening, I'm wondering if maybe there was a recent update that's triggered this happening.

Below are some details I've got about my setup.  I'm not sure how else to get any info about it.. so any information along those lines would also be useful.

Thanks in advance,

- Jelly.

Output from hwinfo:
```

PCI 0b.0: 0280 Network controller
  [Created at pci.296]
  UDI: /org/freedesktop/Hal/devices/pci_1814_301
  Unique ID: 2nea.eNpRIUbLOTC
  SysFS ID: /devices/pci0000:00/0000:00:0b.0
  SysFS BusID: 0000:00:0b.0
  Hardware Class: network
  Model: "RaLink RT2561/RT61 802.11g PCI"
  Vendor: pci 0x1814 "RaLink"
  Device: pci 0x0301 "RT2561/RT61 802.11g PCI"
  SubVendor: pci 0x1814 "RaLink"
  SubDevice: pci 0x2561 
  Driver: "rt61pci"
  Driver Modules: "rt61pci"
  Device File: wmaster0
  Device Files: wmaster0, wlan0
  Memory Range: 0xfb000000-0xfb007fff (rw,non-prefetchable)
  IRQ: 19 (62153 events)
  HW Address: 00:0e:2e:d1:aa:b2
  Link detected: yes
  Module Alias: "pci:v00001814d00000301sv00001814sd00002561bc02sc80i00"
  Driver Info #0:
    Driver Status: rt61pci is active
    Driver Activation Cmd: "modprobe rt61pci"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

```

---

