---
title: "Wireless 4965 Toshiba laptop help"
date: 2008-06-29
forum: Networking &amp; Wireless
---

### Post by gigaferz on 2008-06-29
Hello!

 Im setting up a laptop and I can not make the wireless to work!

It doesnt show up  on network manager.

  Here is my information

laptop:~$ sudo lshw -C network
[sudo] password gg: 
  *-network               
       description: Ethernet interface
       product: 88E8039 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 14
       serial: 00:a0:d1:76:6c:35
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.20 duplex=full firmware=N/A ip=192.168.0.100 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Network controller
       product: PRO/Wireless 4965 AG or AGN Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 61
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=iwl4965 latency=0 module=iwl4965
joshdogg@joshdogg-laptop:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.


And here is Dmesg section:

3.102514] mmc0: SDHCI at 0xf0905800 irq 18 DMA
[   33.153707] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   33.153724] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   33.153763] sky2 0000:02:00.0: v1.20 addr 0xf0600000 irq 16 Yukon-FE (0xb7) rev 3
[   33.162795] sky2 eth0: addr 00:a0:d1:76:6c:35
[   33.549070] iwl4965: Intel(R) Wireless WiFi Link 4965AGN driver for Linux, 1.2.0
[   33.549075] iwl4965: Copyright(c) 2003-2007 Intel Corporation
[   33.549232] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   33.549265] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   33.549297] iwl4965: Detected Intel Wireless WiFi Link 4965AGN
[   33.721422] Linux video capture interface: v2.00
[   33.777478] uvcvideo: Found UVC 1.00 device Chicony USB 2.0 Camera (04f2:b008)

I just updated the system, I was expecting to work out of the box , Should I use ndiswrapper?

I can see I have no logical name for the wireless chip,

Thank you

---

### Post by Wobblybob on 2008-06-29
Hi,

try [system], [Admin..], [Hardware drivers] to see if you need the restricted drivers enabled, if they are listed and need enabling you will need to connect the laptop via a cable to your internet connection to allow it to download and install them. A reboot will then be required and you should check back in hardware drivers again to make sure they are enabled and in use.

---

### Post by gigaferz on 2008-06-29
Hello, thank you for the reply.

I looked in there and the only restricted driver is for nvidia cards. There are no more devices listed.

---

### Post by gigaferz on 2008-06-29
ndiswrapper doesnt detect any devices either.

How do i activate or assign a logical name to this card?

---

