---
title: "Wireless connection issues with Lenovo Thinkpad T530 and rtl8188ce wireless card"
date: 2013-11-07
forum: Networking &amp; Wireless
---

### Post by nissim.lavy1 on 2013-11-07
Hey guys,

I recently got a Lenovo T530 laptop and everything works well besides for the wireless connectivity. I can't connect wirelessly to a network but connecting with a cable is no problem. What happens is that when trying to connect wirelessly, it ends up being stuck in the authenticating stage of the connection process and either times out (with Wicd) or keeps going in an infinite loop trying to authenticate(with Network Manager). Just like every other thead/post about this suggested, I updated the drivers for the card but that didn't seem to help the issue and I still can't connect and I still end up stuck in the authenticating stage. How can I go about fixing this issue? Thanks!

lspci -k
```

00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)
    Subsystem: Lenovo Device 21f6
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
    Subsystem: Lenovo Device 21f6
    Kernel driver in use: i915
    Kernel modules: i915
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
    Subsystem: Lenovo Device 21f6
    Kernel driver in use: xhci_hcd
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
    Subsystem: Lenovo Device 21f6
    Kernel driver in use: mei
    Kernel modules: mei
00:19.0 Ethernet controller: Intel Corporation 82579LM Gigabit Network Connection (rev 04)
    Subsystem: Lenovo Device 21f3
    Kernel driver in use: e1000e
    Kernel modules: e1000e
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
    Subsystem: Lenovo Device 21f6
    Kernel driver in use: ehci_hcd
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
    Subsystem: Lenovo Device 21f6
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.2 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 3 (rev c4)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
    Subsystem: Lenovo Device 21f6
    Kernel driver in use: ehci_hcd
00:1f.0 ISA bridge: Intel Corporation QM77 Express Chipset LPC Controller (rev 04)
    Subsystem: Lenovo Device 21f6
    Kernel modules: lpc_ich
00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
    Subsystem: Lenovo Device 21f6
    Kernel driver in use: ahci
    Kernel modules: ahci
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
    Subsystem: Lenovo Device 21f6
    Kernel modules: i2c-i801
02:00.0 System peripheral: Ricoh Co Ltd PCIe SDXC/MMC Host Controller (rev 07)
    Subsystem: Lenovo Device 21f6
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci
03:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)
    Subsystem: Realtek Semiconductor Co., Ltd. Device 8195
    Kernel driver in use: rtl8192ce
    Kernel modules: rtl8192ce

```

lshw -C network
```

*-network               
       description: Ethernet interface
       product: 82579LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 04
       serial: 3c:97:0e:cc:62:29
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=2.0.0-k duplex=full firmware=0.13-3 ip=192.168.1.13 latency=0 multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:42 memory:f2500000-f251ffff memory:f253b000-f253bfff ioport:6080(size=32)
  *-network
       description: Wireless interface
       product: RTL8188CE 802.11b/g/n WiFi Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: b8:76:3f:d4:04:5c
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192ce driverversion=3.5.0-42-generic firmware=N/A latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 ioport:4000(size=256) memory:f1c00000-f1c03fff

```

---

