---
title: "how can I get info about drivers and versions"
date: 2006-09-22
forum: Networking &amp; Wireless
---

### Post by ryu kun on 2006-09-22
Hi everyone, I have some newbie questions. I hope this is the right place.

I use Ubuntu 6.06 and experience some problems with my Intel 3945 (ipw3945) wireless card with the NetworkManager 0.6.2. So I wanted to be sure if my card is recognised and uses the latest drivers. How can I check them, can you please tell me the commands? Also how can I learn my linux kernel version?

This is lspci's output:

```
0000:00:00.0 Host bridge: Intel Corporation Mobile Memory Controller Hub (rev 03)
0000:00:01.0 PCI bridge: Intel Corporation Mobile PCI Express Graphics Port (rev 03)
0000:00:1b.0 0403: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
0000:00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
0000:00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
0000:00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
0000:00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
0000:00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
0000:00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
0000:00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
0000:00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
0000:00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
0000:00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
0000:00:1f.2 0106: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controllers cc=AHCI (rev 01)
0000:00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
0000:01:00.0 VGA compatible controller: nVidia Corporation: Unknown device 01d8 (rev a1)
**0000:06:00.0 Network controller: Intel Corporation: Unknown device 4222 (rev 02)**
0000:08:06.0 CardBus bridge: Texas Instruments: Unknown device 8039
0000:08:06.1 FireWire (IEEE 1394): Texas Instruments: Unknown device 803a
0000:08:06.2 Mass storage controller: Texas Instruments: Unknown device 803b
0000:08:06.3 0805: Texas Instruments: Unknown device 803c
0000:08:08.0 Ethernet controller: Intel Corporation: Unknown device 1092 (rev 01)

```

It seems like it is not recognised, is it?

---

### Post by ryu kun on 2006-09-22
I guess I've found the commands:

lspci -v

```
0000:06:00.0 Network controller: Intel Corporation: Unknown device 4222 (rev 02)
        Subsystem: Hewlett-Packard Company: Unknown device 135c
        Flags: bus master, fast devsel, latency 0, IRQ 185
        Memory at 32000000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

```

dmesg

```
[17179569.184000] Linux version 2.6.15-27-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Sat Sep 16 01:51:59 UTC 2006
...
[17179604.772000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.0.5m
[17179604.772000] ipw3945: Copyright(c) 2003-2006 Intel Corporation
[17179604.772000] ACPI: PCI Interrupt 0000:06:00.0[A] -> GSI 18 (level, low) -> IRQ 185
[17179604.772000] PCI: Setting latency timer of device 0000:06:00.0 to 64
[17179604.772000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection
```

But I am still not sure if the card is properly recognised or not.

---

