---
title: "No WWAN adapter found in Ubuntu 24.04 LTS -- WAN hardware not detected"
date: 2024-11-15
forum: Networking &amp; Wireless
---

### Post by olavurmortensen on 2024-11-15
I'm trying to connect to mobile broadband in Ubuntu 24.04 LTS installed on a ThinkPad T14s. The "Mobile Network" settings page just says:[INDENT]
No WWAN Adapter Found
Make sure you have a Wireless WAN / Cellular device[/INDENT]


I cannot even find the hardware device. The only device I find via `lshw` which is related to network is the one below, which is the wifi. I don't believe that device has anything to do with the mobile broadband device.

```

*-network
             description: Wireless interface
             product: Raptor Lake PCH CNVi WiFi
             vendor: Intel Corporation
             physical id: 14.3
             bus info: pci@0000:00:14.3
             logical name: wlp0s20f3
             version: 01
             serial: e8:c8:29:8f:dc:57
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical wireless
             configuration: broadcast=yes driver=iwlwifi driverversion=6.8.0-47-generic firmware=86.fb5c9aeb.0 so-a0-gf-a0-86.uc ip=192.168.237.155 latency=0 link=yes multicast=yes wireless=IEEE 802.11


```Below is the lspci output, which also indicates there is no mobile broadband on the bus. 

```

00:00.0 Host bridge: Intel Corporation Raptor Lake-P/U 2p+8e cores Host Bridge/DRAM Controller (rev 01)
00:02.0 VGA compatible controller: Intel Corporation Raptor Lake-P [Iris Xe Graphics] (rev 04)
00:04.0 Signal processing controller: Intel Corporation Raptor Lake Dynamic Platform and Thermal Framework Processor Participant (rev 01)
00:06.0 PCI bridge: Intel Corporation Raptor Lake PCIe 4.0 Graphics Port (rev 01)
00:07.0 PCI bridge: Intel Corporation Raptor Lake-P Thunderbolt 4 PCI Express Root Port #0 (rev 01)
00:07.2 PCI bridge: Intel Corporation Raptor Lake-P Thunderbolt 4 PCI Express Root Port #2 (rev 01)
00:08.0 System peripheral: Intel Corporation GNA Scoring Accelerator module (rev 01)
00:0d.0 USB controller: Intel Corporation Raptor Lake-P Thunderbolt 4 USB Controller (rev 01)
00:0d.2 USB controller: Intel Corporation Raptor Lake-P Thunderbolt 4 NHI #0 (rev 01)
00:0d.3 USB controller: Intel Corporation Raptor Lake-P Thunderbolt 4 NHI #1 (rev 01)
00:14.0 USB controller: Intel Corporation Alder Lake PCH USB 3.2 xHCI Host Controller (rev 01)
00:14.2 RAM memory: Intel Corporation Alder Lake PCH Shared SRAM (rev 01)
00:14.3 Network controller: Intel Corporation Raptor Lake PCH CNVi WiFi (rev 01)
00:15.0 Serial bus controller: Intel Corporation Alder Lake PCH Serial IO I2C Controller #0 (rev 01)
00:16.0 Communication controller: Intel Corporation Alder Lake PCH HECI Controller (rev 01)
00:1f.0 ISA bridge: Intel Corporation Raptor Lake LPC/eSPI Controller (rev 01)
00:1f.3 Audio device: Intel Corporation Raptor Lake-P/U/H cAVS (rev 01)
00:1f.4 SMBus: Intel Corporation Alder Lake PCH-P SMBus Host Controller (rev 01)
00:1f.5 Serial bus controller: Intel Corporation Alder Lake-P PCH SPI Controller (rev 01)
04:00.0 Non-Volatile memory controller: Sandisk Corp WD Black SN770 / PC SN740 256GB / PC SN560 (DRAM-less) NVMe SSD (rev 01)


```

For all I know the mobile broadband device could be on the USB bus, but there is no indication of that.

```

$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 003 Device 003: ID 27c6:6594 Shenzhen Goodix Technology Co.,Ltd. Goodix USB2.0 MISC
Bus 003 Device 004: ID 30c9:00ad Luxvisions Innotech Limited Integrated Camera
Bus 003 Device 005: ID 2ce3:9563 Generic EMV Smartcard Reader
Bus 003 Device 006: ID 8087:0033 Intel Corp. AX211 Bluetooth
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub


```

NetworkManager indicates WWAN is enabled but there hardware is missing. WAN is enabled in the BIOS.

```

$ nmcli general
STATE      CONNECTIVITY  WIFI-HW  WIFI     WWAN-HW  WWAN    
connected  full          enabled  enabled  missing  enabled 

```

There is a guide inon how to enable WWAN in a Lenovo ThinkEdge SE30 on Ubuntu. But it seems very specific to that machine.
[URL="https://support.lenovo.com/no/nb/solutions/ht513558-how-to-enable-wwan-in-stock-ubuntu-thinkedge-se30"]https://support.lenovo.com/no/nb/solutions/ht513558-how-to-enable-wwan-in-stock-ubuntu-thinkedge-se30

[/URL]I'm at a loss. What do I do when the system doesn't even seem to know the hardware exists?

---

### Post by him610 on 2024-11-15
It could be your Lenovo T12 does not have the capability to connect to a mobile network (Is that WWAN?)
Please refer to this website [https://support.lenovo.com/us/en/solutions/pd014511-wireless-devices-reference-guide]("https://support.lenovo.com/us/en/solutions/pd014511-wireless-devices-reference-guide") 
If you search for T12, it is not found.

You could go to online seller Az, search for *wwan card for laptop*; A good variety will be displayed; however, you might want to check if your T12 has a socket for a wwan card.

---

