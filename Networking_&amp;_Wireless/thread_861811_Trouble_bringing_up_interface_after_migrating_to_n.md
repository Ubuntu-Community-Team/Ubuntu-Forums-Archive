---
title: "Trouble bringing up interface after migrating to new hardware"
date: 2008-07-16
forum: Networking &amp; Wireless
---

### Post by fortipaul on 2008-07-16
Various events have conspired and the result is that I've had to move the hard disk on which Ubuntu is installed to another machine. After the move, my network interface won't come up.

When I run ifup eth0, I get the following:

```

SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
SIOCSIFNETMASK: No such device
SIOCSIFBRDADDR: No such device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
Failed to bring up eth0.

```

As far as I can tell, the appropriate drivers are loaded and working. lsmod show the sis900 8139too and 8139cp drivers are loaded.

Here is the output from lspci:

```

00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
	Subsystem: ASUSTeK Computer Inc. Unknown device 80ff
	Flags: bus master, medium devsel, latency 32, IRQ 209
	I/O ports at 8800 [size=256]
	Memory at e5800000 (32-bit, non-prefetchable) [size=4K]
	Expansion ROM at effe0000 [disabled] [size=128K]
	Capabilities: [40] Power Management version 2

00:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
	Subsystem: AOPEN Inc. Unknown device 0027
	Flags: bus master, medium devsel, latency 32, IRQ 201
	I/O ports at 8400 [size=256]
	Memory at e5000000 (32-bit, non-prefetchable) [size=256]
	Capabilities: [50] Power Management version 2

```

I'm only using one of these, the ASUSTek card. It is eth0 and configured accordingly in /etc/network/interfaces

The odd thing is, using the following steps, I can make the interface come up manually. Yet the steps don't make sense to me, and I'm hosed again on reboot. Also, I can't make it happen every time.

1) Create the file /etc/modprobe.conf with one line:

```
alias eth0 sis900
```

2) Using modprobe unload all network drivers
3) Using modprobe reload the 8139too driver
4) Do ifup eth0

After the interface comes up, lsmod shows not only 8193too loaded, but also sis900. This makes no sense to me because (a) 8139too isn't the right driver and (b) I thought the files in /etc/modprobe.d/ were used rather than /etc/modeprobe.conf.

The reason I tried that was because of what I saw using dmesg:

```

[42952351.510000] 8139too Fast Ethernet driver 0.9.27
[42952351.510000] ACPI: PCI Interrupt 0000:00:09.0[A] -> GSI 17 (level, low) -> IRQ 201
[42952351.510000] eth0: RealTek RTL8139 at 0xde88a000, 00:40:f4:a5:af:19, IRQ 201
[42952351.510000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[42952357.200000] sis900.c: v1.08.09 Sep. 19 2005
[42952357.200000] ACPI: PCI Interrupt 0000:00:04.0[A] -> GSI 19 (level, low) -> IRQ 209
[42952357.200000] 0000:00:04.0: VIA 6103 PHY transceiver found at address 1.
[42952357.210000] 0000:00:04.0: Using transceiver found at address 1 as default
[42952357.210000] eth0: SiS 900 PCI Fast Ethernet at 0x8800, IRQ 209, 00:0e:a6:cc:98:e6.
[42952360.210000] eth0: Media Link On 100mbps full-duplex 

```

eth0 is identified as both sis900 and an 8139 chipset, at different times.

Any suggestions would be much appreciated.

---

### Post by oxoxbyx on 2011-01-14
bump

---

