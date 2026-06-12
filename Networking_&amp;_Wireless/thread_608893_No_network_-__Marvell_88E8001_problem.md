---
title: "No network -  Marvell 88E8001 problem"
date: 2007-11-10
forum: Networking &amp; Wireless
---

### Post by kickus on 2007-11-10
Hello

I just installed a fresh Gutsy on a desktop machine with Asus P5B-V motherboard. I´m not able to get any network interface for the internal Marvell 88E8001 controller. The same nic works when booting to windows.

"lshw -C network" listed the controller, but I have no working driver.

*-network unclaimed
Description: Ethernet controller...

I started with the Generic kernel from the gutsy install cd (linux 2.6.22), but downloaded and compiled (using oldconfig + adding the sk98lin, and make-kpkg) a new kernel (2.6.23.1) and the problem persisted.

The module skge loads automatically, but no interface appears. 

"ifconfig eth0 up" says no such device

Thanks for any advice,
Kristian

---

### Post by kickus on 2007-11-11
Ok, I made some more testing.

The problem seems to be either Ubuntu-specific or a bug introduced in some newer kernel.. I downloaded the latest knoppix (5.1) which uses kernel 2.6.19, and the network works.

lshw -C network
  *-network
       description: Ethernet interface
       product: 88E8001 Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 4
       bus info: pci@0000:04:04.0
       logical name: eth1
       version: 14
       serial: 00:1b:fc:9e:14:c3
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=skge driverversion=1.9 duplex=full firmware=N/A ip=192.168.0.67 latency=32 link=yes maxlatency=31 mingnt=23 module=skge multicast=yes port=twisted pair speed=100MB/s

lspci gives:
04:04.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 14)
        Subsystem: ASUSTeK Computer Inc. Marvell 88E8001 Gigabit Ethernet Controller (Asus)
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
        Memory at ff9f8000 (32-bit, non-prefetchable) [size=16K]
        I/O ports at b800 [size=256]
        Expansion ROM at 80000000 [disabled] [size=128K]
        Capabilities: [48] Power Management version 2
        Capabilities: [50] Vital Product Data


The knoppix kernel uses successfully the skge module.

How should I tackle the Ubuntu problem? Compile a custom old kernel?

Thanks for any advice.
Kristian

---

