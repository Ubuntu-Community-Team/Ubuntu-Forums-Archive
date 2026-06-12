---
title: "Forcedeth problem?  Eth0 randomly dies."
date: 2006-09-30
forum: Networking &amp; Wireless
---

### Post by cjtenny on 2006-09-30
So I get a new laptop, Compaq V3000z.  It works fine, all drivers end up working, and ethernet is running great (this isn't a wireless issue; haven't even set up ndiswrapper yet).  eth0 randomly died during scping some junk from my desktop -- reboot didn't fix it.  Power down, then power on (as opposed to rebooting without it repowering) does fix this but it still randomly stops during some transfers and refuses to be fixed.  I've tried rmmod then modprobe forcedeth, a few other things.  I even compiled the 2.6.18 kernel with forcedeth 0.56 and it has the exact same problem.  How can I get eth0 to consistently work?


Oh and by the way, the orange light still blinks and the green light still remains constant -- eth0 is still shown, but dhclient keeps sending DHCPREQUESTs with no avail, and pinging the router yields nothing.  In the dmesg output I believe i unplugged it (before the segment of dmesg), then ran dhclient and plugged it in.

It's an MCP51 ethernet controller from nvidia.

Here's some dmesg output, and lspci:

dmesg:
```
[ 2032.696000] nv_stop_tx: TransmitterStatus remained busy<6>eth0: link down.
[ 2034.372000] eth0: link up.
[ 2182.312000] nv_stop_tx: TransmitterStatus remained busy<7>eth0: no IPv6 routers present
[ 2483.736000] eth0: link down.
[ 2484.828000] nv_stop_tx: TransmitterStatus remained busyeth0: no link during initialization.
[ 2484.916000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 2491.620000] nv_stop_tx: TransmitterStatus remained busy<6>eth0: link down.
[ 2497.820000] eth0: link up.
[ 2497.820000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 2508.720000] eth0: no IPv6 routers present
```

lspci:
```
0000:00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
0000:00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
0000:00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
0000:00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
0000:00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
0000:00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
0000:00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
0000:00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
0000:00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
0000:00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
0000:00:05.0 VGA compatible controller: nVidia Corporation C51 PCI Express Bridge (rev a2)
0000:00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
0000:00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
0000:00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
0000:00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
0000:00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
0000:00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
0000:00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
0000:00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
0000:00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
0000:00:10.1 0403: nVidia Corporation MCP51 High Definition Audio (rev a2)
0000:00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
0000:01:00.0 Network controller: Broadcom Corporation: Unknown device 4311 (rev 01)
0000:03:09.0 FireWire (IEEE 1394): Ricoh Co Ltd: Unknown device 0832
0000:03:09.1 0805: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
0000:03:09.2 System peripheral: Ricoh Co Ltd: Unknown device 0843 (rev 01)
0000:03:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
0000:03:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)

```

---

