---
title: "Nee beginner-level help with LinkSys WUSB54GC Setup"
date: 2008-06-23
forum: Networking &amp; Wireless
---

### Post by DaddyUnit on 2008-06-23
This is a WAY beginner question and I'm not even a SMART beginner, so be forewarned.

I've given up, for the moment, trying to get the new laptop's built-in wireless to work. Apparently there are no drivers and ndiswrapper doesn't work for AMD64 (or at least my AMD64).

No problem. I went to the list of known good functional operational USB wireless devices, compared it with the list of available devices at my local retailer and decided on a LinkSys WUSB54GC ([https://help.ubuntu.com/community/WifiDocs/Device/LinksysWUSB54GC](https://help.ubuntu.com/community/WifiDocs/Device/LinksysWUSB54GC)), excited by the comments that it should work "out of the box".

It didn't.

I've re-read the page linked above and it talks about the device being easily set up in "NetworkManager". I researched NetworkManager and tried to install it using the Synaptic Package Manager. Unfortunately the Package Manager will only let me uninstall it. I guess it must be installed already, but I don't know where or how to find it.

Is NetworkManager the thing that comes up when you go to System > Administration > Network?

Any help would be greatly appreciated. I'm like 3 days into this and it's getting very frustrating. Thanks in advance.

Here is more information on my laptop:
Here are more details on my machine:

Acer Aspire 4520
AMD Athlon X2 Dual Core Processor 1K-53(1.7GHz, 2x 256KB L2 Cache)
There's a sticker on the case that says I've got nvidia GeForce 7000M

lspci
jeff@jeff-laptop:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.3 Co-processor: nVidia Corporation MCP67 Co-processor (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2)
00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0e.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation GeForce 7000M (rev a2) (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
01:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
01:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
01:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
01:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
07:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)


iwconfig
jeff@jeff-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

iwlist scan
jeff@jeff-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

---

### Post by DaddyUnit on 2008-06-25
Fixed the problem by doing an ndiswrapper on the driver on the CD that came with the adapter.

Copied the *Drivers > Vista* directory to the desktop.

Used the terminal to get into the *Vista* directory then ran *sudo ndiswrapper -i netr73.inf*.

Restarted, removed/reinserted the adapter.

Configured the adapter *System > Administration > Network*.

---

