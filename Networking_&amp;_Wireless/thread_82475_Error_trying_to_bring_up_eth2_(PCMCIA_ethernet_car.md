---
title: "Error trying to bring up eth2 (PCMCIA ethernet card)"
date: 2005-10-26
forum: Networking &amp; Wireless
---

### Post by daller on 2005-10-26
Hi There,

I've tried to bring up my PCMCIA ethernet card up:

daniel@dallap:~$ sudo ifup eth2
There is already a pid file /var/run/dhclient.eth2.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
SIOCSIFADDR: No such device
eth2: ERROR while getting interface flags: No such device
eth2: ERROR while getting interface flags: No such device
sit0: unknown hardware address type 776
Bind socket to interface: No such device
Failed to bring up eth2.

I haven't tried PCMCIA before (Does it even work on my laptop: Dell Inspiron 8600)

dmesg:

[4311426.260000] PCI: Enabling device 0000:03:00.0 (0000 -> 0003)
[4311426.260000] ACPI: PCI Interrupt 0000:03:00.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[4311426.260000] PCI: Setting latency timer of device 0000:03:00.0 to 64
[4311426.263000] eth2: RealTek RTL8139 at 0x4000, 00:50:fc:b8:5a:32, IRQ 11
[4311426.263000] eth2:  Identified 8139 chip type 'RTL-8139C'
[4311453.441000] eth2: link down
[4311463.630000] eth2: no IPv6 routers present
[4311711.408000] eth2: link up, 100Mbps, full-duplex, lpa 0x45E0
[4311784.867000] ACPI: PCI interrupt for device 0000:03:00.0 disabled
[4311791.714000] 8139too: pci dev 0000:03:00.0 (id 10ec:8139 rev ff) is an enhanced 8139C+ chip
[4311791.714000] 8139too: Use the "8139cp" driver for improved performance and stability.
[4311791.714000] ACPI: PCI Interrupt 0000:03:00.0[?] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[4311791.714000] 8139too: 0000:03:00.0: region #0 not a PIO resource, aborting
[4311791.714000] 8139cp: pci dev 0000:03:00.0 (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[4311791.714000] 8139cp: Try the "8139too" driver instead.
[4311845.987000] 8139too: pci dev 0000:03:00.0 (id 10ec:8139 rev ff) is an enhanced 8139C+ chip
[4311845.987000] 8139too: Use the "8139cp" driver for improved performance and stability.
[4311845.987000] ACPI: PCI Interrupt 0000:03:00.0[?] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[4311845.987000] 8139too: 0000:03:00.0: region #0 not a PIO resource, aborting
[4311845.987000] ACPI: PCI Interrupt 0000:03:00.0[?] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[4311845.987000] PCI: cache line size of 32 is not supported by device 0000:03:00.0
[4311845.987000] ACPI: PCI interrupt for device 0000:03:00.0 disabled
[4311845.987000] 8139cp: probe of 0000:03:00.0 failed with error -22

---

### Post by daller on 2005-11-23
Well, the card had a defect!

---

