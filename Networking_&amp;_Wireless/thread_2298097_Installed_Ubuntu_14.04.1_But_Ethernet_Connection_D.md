---
title: "Installed Ubuntu 14.04.1 But Ethernet Connection Detected"
date: 2015-10-09
forum: Networking &amp; Wireless
---

### Post by Forrest_Betton on 2015-10-09
I installed Ubuntu 14.04.1 a while ago (with internet connection, originally, but recent attempts to re-install the same version were without internet connection) on my Lenovo x201 by wiping the hard drive and overwriting the previous windows 7 OS.  Since installing 14.04.1, my laptop has displayed "Ethernet Network disconnected", both with Networking enabled and not enabled.  

I ran the following basic diagnostics (commands in bold, outputs in regular font), I hope this helps. 

***additionally, my wireless adapted has not functioned for several years, I have been using a NETGEAR WNAD3100v2 wireless adapter but have not been able to re-download the drivers since then (will likely post a separate thread if/when I correct the ethernet)

[FONT=arial]**lsusb**[/FONT]**[FONT=&quot][/FONT]**
[FONT=arial][/FONT][FONT=arial]Bus 002 Device 004:ID 8086:0187 Intel Corp.[/FONT][FONT=&quot][/FONT]
[FONT=arial][/FONT][FONT=arial]Bus 002 Device 003:ID 0781:5530 SanDisk Corp. Cruzer[/FONT][FONT=&quot][/FONT]
[FONT=arial][/FONT][FONT=arial]Bus 002 Device 002:ID 8087:0020 Intel Corp. Integrated Rate Matching Hub[/FONT][FONT=&quot][/FONT]
[FONT=arial][/FONT][FONT=arial]Bus 002 Device 001:ID 1d6b:0002 Linux Foundation 2.0 root hub[/FONT][FONT=&quot][/FONT]
[FONT=arial][/FONT][FONT=arial]Bus 001 Device 006:ID 17ef:4816 Lenovo[/FONT][FONT=&quot][/FONT]
[FONT=arial][/FONT][FONT=arial]Bus 001 Device 007:ID 046d:c52b Logitech, Inc. Unifying Receiver[/FONT][FONT=&quot][/FONT]
[FONT=arial][/FONT][FONT=arial]Bus 001 Device 005:ID 17ef:1005 Lenovo[/FONT][FONT=&quot][/FONT]
[FONT=arial][/FONT][FONT=arial]Bus 001 Device 004:ID 0a5c:217f Broadcom Corp. BCM2045B (BDC-2.1)[/FONT][FONT=&quot][/FONT]
[FONT=arial][/FONT][FONT=arial]Bus 001 Device 003:ID 0846:9011 NetGear, Inc. WNDA3100v2 802.11abgn [Broadcom BCM4323][/FONT][FONT=&quot][/FONT]
[FONT=arial][/FONT][FONT=arial]Bus 001 Device 002:ID 8087:0020 Intel Corp. Integrated Rate Matching Hub[/FONT][FONT=&quot][/FONT]
[FONT=arial][/FONT][FONT=arial]Bus 001 Device 001:ID 1d6b:0002 Linux Foundation 2.0 root hub[/FONT][FONT=&quot][/FONT]
[FONT=arial][/FONT][FONT=arial] [/FONT]
[FONT=arial][/FONT][FONT=arial]**ifconfig**[/FONT]**[FONT=&quot][/FONT]**
[FONT=arial][/FONT][FONT=arial]lo        Link encap:Local Loopback  [/FONT][FONT=&quot][/FONT]
[FONT=arial][/FONT][FONT=arial]          inet addr:127.0.0.1  Mask:255.0.0.0[/FONT][FONT=&quot][/FONT]
[FONT=arial][/FONT][FONT=arial]          inet6 addr: ::1/128 Scope:Host[/FONT][FONT=&quot][/FONT]
[FONT=arial][/FONT][FONT=arial]          UP LOOPBACK RUNNING  MTU:65536 Metric:1[/FONT][FONT=&quot][/FONT]
[FONT=arial][/FONT][FONT=arial]          RX packets:16 errors:0 dropped:0overruns:0 frame:0[/FONT][FONT=&quot][/FONT]
[FONT=arial][/FONT][FONT=arial]          TX packets:16 errors:0 dropped:0overruns:0 carrier:0[/FONT][FONT=&quot][/FONT]
[FONT=arial][/FONT][FONT=arial]          collisions:0 txqueuelen:0[/FONT][FONT=&quot][/FONT]
[FONT=arial][/FONT][FONT=arial]          RX bytes:1184 (1.1 KB)  TX bytes:1184 (1.1 KB)[/FONT][FONT=&quot][/FONT]
[FONT=arial][/FONT][FONT=arial] [/FONT]
[FONT=arial][/FONT][FONT=arial]wmx0      Link encap:Ethernet  HWaddr 00:1d:e1:39:c4:ec  [/FONT][FONT=&quot][/FONT]
[FONT=arial][/FONT][FONT=arial]          UP NOARP  MTU:1400 Metric:1[/FONT][FONT=&quot][/FONT]
[FONT=arial][/FONT][FONT=arial]          RX packets:0 errors:0 dropped:0overruns:0 frame:0[/FONT][FONT=&quot][/FONT]
[FONT=arial][/FONT][FONT=arial]          TX packets:0 errors:0 dropped:0overruns:0 carrier:0[/FONT][FONT=&quot][/FONT]
[FONT=arial][/FONT][FONT=arial]          collisions:0 txqueuelen:20[/FONT][FONT=&quot][/FONT]
[FONT=arial][/FONT][FONT=arial]          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)[/FONT][FONT=&quot][/FONT]
[FONT=arial][/FONT][FONT=arial] [/FONT]
[FONT=arial][/FONT][FONT=arial]**sudo lshw -Cnetwork**[/FONT]**[FONT=&quot][/FONT]**
[FONT=arial][/FONT][FONT=arial]  *-network UNCLAIMED     [/FONT][FONT=&quot][/FONT]
[FONT=arial][/FONT][FONT=arial]       description: Ethernet controller[/FONT][FONT=&quot][/FONT]
[FONT=arial][/FONT][FONT=arial]       product: 82577LC Gigabit NetworkConnection[/FONT][FONT=&quot][/FONT]
[FONT=arial][/FONT][FONT=arial]       vendor: Intel Corporation[/FONT][FONT=&quot][/FONT]
[FONT=arial][/FONT][FONT=arial]       physical id: 19[/FONT][FONT=&quot][/FONT]
[FONT=arial][/FONT][FONT=arial]       bus info: pci@0000:00:19.0[/FONT][FONT=&quot][/FONT]
[FONT=arial][/FONT][FONT=arial]       version: 06[/FONT][FONT=&quot][/FONT]
[FONT=arial][/FONT][FONT=arial]       width: 32 bits[/FONT][FONT=&quot][/FONT]
[FONT=arial][/FONT][FONT=arial]       clock: 33MHz[/FONT][FONT=&quot][/FONT]
[FONT=arial][/FONT][FONT=arial]       capabilities: pm msi cap_list[/FONT][FONT=&quot][/FONT]
[FONT=arial][/FONT][FONT=arial]       configuration: latency=0[/FONT][FONT=&quot][/FONT]
[FONT=arial][/FONT][FONT=arial]       resources: memory:f2400000-f241ffffmemory:f2425000-f2425fff ioport:1820(size=32)[/FONT][FONT=&quot][/FONT]
[FONT=arial][/FONT][FONT=arial]  *-network[/FONT][FONT=&quot][/FONT]
[FONT=arial][/FONT][FONT=arial]       description: Ethernet interface[/FONT][FONT=&quot][/FONT]
[FONT=arial][/FONT][FONT=arial]       physical id: 2[/FONT][FONT=&quot][/FONT]
[FONT=arial][/FONT][FONT=arial]       logical name: wmx0[/FONT][FONT=&quot][/FONT]
[FONT=arial][/FONT][FONT=arial]       serial: 00:1d:e1:39:c4:ec[/FONT][FONT=&quot][/FONT]
[FONT=arial][/FONT][FONT=arial]       capabilities: ethernet physical[/FONT][FONT=&quot][/FONT]
[FONT=arial][/FONT][FONT=arial]       configuration: driver=i2400m_usbfirmware=i6050-fw-usb-1.5.sbcf link=no[/FONT][FONT=&quot][/FONT]
[FONT=arial][/FONT][FONT=arial] [/FONT]
[FONT=arial][/FONT][FONT=arial]**route -n**[/FONT]**[FONT=&quot][/FONT]**
[FONT=arial][/FONT][FONT=arial]Kernel IP routingtable[/FONT][FONT=&quot][/FONT]
[FONT=arial][/FONT][FONT=arial]Destination     Gateway         Genmask         Flags Metric Ref    Use Iface[/FONT][FONT=&quot][/FONT]
[FONT=arial][/FONT][FONT=arial] [/FONT]
[FONT=arial][/FONT][FONT=arial]**lspci**[/FONT]**[FONT=&quot][/FONT]**
[FONT=arial][/FONT][FONT=arial]00:00.0 Host bridge:Intel Corporation Core Processor DRAM Controller (rev 02)[/FONT][FONT=&quot][/FONT]
[FONT=arial][/FONT][FONT=arial]00:02.0 VGAcompatible controller: Intel Corporation Core Processor Integrated GraphicsController (rev 02)[/FONT][FONT=&quot][/FONT]
[FONT=arial][/FONT][FONT=arial]00:16.0 Communicationcontroller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev06)[/FONT][FONT=&quot][/FONT]
[FONT=arial][/FONT][FONT=arial]00:19.0 Ethernetcontroller: Intel Corporation 82577LC Gigabit Network Connection (rev 06)[/FONT][FONT=&quot][/FONT]
[FONT=arial][/FONT][FONT=arial]00:1a.0 USBcontroller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced HostController (rev 06)[/FONT][FONT=&quot][/FONT]
[FONT=arial][/FONT][FONT=arial]00:1b.0 Audio device:Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)[/FONT][FONT=&quot][/FONT]
[FONT=arial][/FONT][FONT=arial]00:1c.0 PCI bridge:Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)[/FONT][FONT=&quot][/FONT]
[FONT=arial][/FONT][FONT=arial]00:1c.3 PCI bridge:Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 06)[/FONT][FONT=&quot][/FONT]
[FONT=arial][/FONT][FONT=arial]00:1c.4 PCI bridge:Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 06)[/FONT][FONT=&quot][/FONT]
[FONT=arial][/FONT][FONT=arial]00:1d.0 USBcontroller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced HostController (rev 06)[/FONT][FONT=&quot][/FONT]
[FONT=arial][/FONT][FONT=arial]00:1e.0 PCI bridge:Intel Corporation 82801 Mobile PCI Bridge (rev a6)[/FONT][FONT=&quot][/FONT]
[FONT=arial][/FONT][FONT=arial]00:1f.0 ISA bridge:Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)[/FONT][FONT=&quot][/FONT]
[FONT=arial][/FONT][FONT=arial]00:1f.2 SATAcontroller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCIController (rev 06)[/FONT][FONT=&quot][/FONT]
[FONT=arial][/FONT][FONT=arial]00:1f.3 SMBus: IntelCorporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)[/FONT][FONT=&quot][/FONT]
[FONT=arial][/FONT][FONT=arial]00:1f.6 Signalprocessing controller: Intel Corporation 5 Series/3400 Series Chipset ThermalSubsystem (rev 06)[/FONT][FONT=&quot][/FONT]
[FONT=arial][/FONT][FONT=arial]ff:00.0 Host bridge:Intel Corporation Core Processor QuickPath Architecture Generic Non-coreRegisters (rev 02)[/FONT][FONT=&quot][/FONT]
[FONT=arial][/FONT][FONT=arial]ff:00.1 Host bridge:Intel Corporation Core Processor QuickPath Architecture System Address Decoder(rev 02)[/FONT][FONT=&quot][/FONT]
[FONT=arial][/FONT][FONT=arial]ff:02.0 Host bridge:Intel Corporation Core Processor QPI Link 0 (rev 02)[/FONT][FONT=&quot][/FONT]
[FONT=arial][/FONT][FONT=arial]ff:02.1 Host bridge:Intel Corporation Core Processor QPI Physical 0 (rev 02)[/FONT][FONT=&quot][/FONT]
[FONT=arial][/FONT][FONT=arial]ff:02.2 Host bridge:Intel Corporation Core Processor Reserved (rev 02)[/FONT][FONT=&quot][/FONT]
[FONT=arial][/FONT][FONT=arial]ff:02.3 Host bridge:Intel Corporation Core Processor Reserved (rev 02)[/FONT]

---

