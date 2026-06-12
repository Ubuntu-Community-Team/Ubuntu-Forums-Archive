---
title: "Network problem"
date: 2010-10-24
forum: New to Ubuntu
---

### Post by ALF102 on 2010-10-24
Hi, I've just made a switch from Ubuntu to Kubuntu using this how-to:

[http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)

Then I try to connect to my wireless but it kept asking for the network passphrase repeatedly despite having provided the KDE wallet pass. Below is my hardware info:


00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 09)
        Subsystem: Acer Incorporated [ALI] Device 0214
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>
        Kernel driver in use: agpgart-intel
        Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09) (prog-if 00 [VGA controller])
        Subsystem: Acer Incorporated [ALI] Device 0214
        Flags: bus master, fast devsel, latency 0, IRQ 42
        Memory at f0000000 (64-bit, non-prefetchable) [size=4M]
        Memory at d0000000 (64-bit, prefetchable) [size=256M]
        I/O ports at 1800 [size=8]
        Expansion ROM at <unassigned> [disabled]
        Capabilities: <access denied>
        Kernel driver in use: i915
        Kernel modules: i915

00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09)
        Subsystem: Acer Incorporated [ALI] Device 0214
        Flags: bus master, fast devsel, latency 0
        Memory at f0400000 (64-bit, non-prefetchable) [size=1M]
        Capabilities: <access denied>

00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Acer Incorporated [ALI] Device 0214
        Flags: bus master, medium devsel, latency 0, IRQ 20
        I/O ports at 1820 [size=32]
        Capabilities: <access denied>
        Kernel driver in use: uhci_hcd

00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Acer Incorporated [ALI] Device 0214


But I still can connect to the internet using wired connection.

---

### Post by tajiknomi on 2010-10-24
[SIZE=2]*paste the out-put if this...*[/SIZE]

[SIZE=2]**sudo lshw -C network**[/SIZE]

---

### Post by ALF102 on 2010-10-24
*-network               
       description: Ethernet interface
       product: AR8121/AR8113/AR8114 Gigabit or Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: b0
       serial: 00:1f:16:a2:a1:de
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=ATL1E driverversion=1.0.0.7-NAPI duplex=full firmware=L1e ip=10.1.1.4 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:43 memory:f0500000-f053ffff ioport:2000(size=128)
  *-network
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 00:25:56:32:52:ef
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=2.6.35-22-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:f0600000-f060ffff

---

### Post by ALF102 on 2010-10-24
Need anymore info?

---

### Post by ALF102 on 2010-10-24
Ok, I've tried to followed this step but no luck. [http://ubuntuforums.org/showthread.php?t=1379448&highlight=AR5001+Kubuntu](http://ubuntuforums.org/showthread.php?t=1379448&highlight=AR5001+Kubuntu)

When I run ndiswrapper -l, it says "invalid driver"

---

