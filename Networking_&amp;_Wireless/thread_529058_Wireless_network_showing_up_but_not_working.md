---
title: "Wireless network showing up but not working"
date: 2007-08-18
forum: Networking &amp; Wireless
---

### Post by SlaughterDog on 2007-08-18
I tried to set up my wireless, followed [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper) and got the NDISwrapper and driver installed. I can configure the wireless through the GUI and it shows my network, however it usually shows 0% signal (Windows shows more signal and works well with it) and it seems I can only connect when I'm using roaming mode. Moreover, nothing works when I do that; it's as if I wasn't connected.

---

### Post by Jamie Jackson on 2007-08-19
What's the output of;

lshw -C network
and
ndiswrapper -l
and
dmesg | egrep -i "(ndis|pci|irq)"

---

### Post by SlaughterDog on 2007-08-25
> **Jamie Jackson said:**
> What's the output of;

lshw -C network
and
ndiswrapper -l
and
dmesg | egrep -i "(ndis|pci|irq)"
```

todd@computer:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@03:00.0
       logical name: eth0
       version: 01
       serial: 00:17:31:65:e5:5a
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK ip=192.168.1.101 latency=0 multicast=yes
       resources: ioport:b800-b8ff iomemory:ff8ff000-ff8fffff irq:17
  *-network UNCLAIMED
       description: Ethernet controller
       product: 88w8335 [Libertas] 802.11b/g Wireless
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@05:00.0
       version: 03
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list
       configuration: latency=64
       resources: iomemory:ff9f0000-ff9fffff iomemory:ff9e0000-ff9effff irq:11




todd@computer:~$ ndiswrapper -l
mrv8000c : driver installed
        device (11AB:1FAA) present
todd@computer:~$ 



todd@computer:~$ dmesg | egrep -i "(ndis|pci|irq)"
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:7ee00000)
[   16.427431] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   16.875280] ENABLING IO-APIC IRQs
[    0.059771] ACPI: bus type pci registered
[    0.059871] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=5
[    0.059873] PCI: Using configuration type 1
[    0.059874] Setting up standard PCI resources
[    0.072368] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.072373] PCI: Probing PCI hardware (bus 00)
[    0.073023] PCI quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
[    0.073026] PCI quirk: region 0480-04bf claimed by ICH6 GPIO
[    0.073741] PCI: Transparent bridge - 0000:00:1e.0
[    0.073790] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.090875] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P2._PRT]
[    0.091101] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.094953] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[    0.095476] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P7._PRT]
[    0.095701] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P8._PRT]
[    0.098292] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.098499] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.098705] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11 12 14 *15)
[    0.098912] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.099116] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.099324] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.099530] ACPI: PCI Interrupt Link [LNKG] (IRQs *3 4 5 6 7 10 11 12 14 15)
[    0.099736] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 11 12 *14 15)
[    0.103384] PCI: Using ACPI for IRQ routing
[    0.103386] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    0.114281] PCI: Bridge: 0000:00:01.0
[    0.114290] PCI: Bridge: 0000:00:1c.0
[    0.114301] PCI: Bridge: 0000:00:1c.3
[    0.114313] PCI: Bridge: 0000:00:1c.4
[    0.114324] PCI: Bridge: 0000:00:1e.0
[    0.114342] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[    0.114345] PCI: Setting latency timer of device 0000:00:01.0 to 64
[    0.114358] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
[    0.114362] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    0.114375] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 17
[    0.114379] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[    0.114392] ACPI: PCI Interrupt 0000:00:1c.4[A] -> GSI 16 (level, low) -> IRQ 16
[    0.114395] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[    0.114403] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    8.615703] PCI: Setting latency timer of device 0000:00:01.0 to 64
[    8.615730] Allocate Port Service[0000:00:01.0:pcie00]
[    8.615789] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    8.615822] Allocate Port Service[0000:00:1c.0:pcie00]
[    8.615843] Allocate Port Service[0000:00:1c.0:pcie02]
[    8.615911] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[    8.615945] Allocate Port Service[0000:00:1c.3:pcie00]
[    8.615967] Allocate Port Service[0000:00:1c.3:pcie02]
[    8.616035] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[    8.616069] Allocate Port Service[0000:00:1c.4:pcie00]
[    8.616092] Allocate Port Service[0000:00:1c.4:pcie02]
[    8.982756] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    8.982857] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    8.983255] 00:06: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    8.984083] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    8.984085] PNP: PS/2 controller doesn't have AUX irq; using default 12
[    8.986289] serio: i8042 KBD port at 0x60,0x64 irq 1
[    8.986292] serio: i8042 AUX port at 0x60,0x64 irq 12
[    9.016430] Starting balanced_irq
[   10.423291] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 16 (level, low) -> IRQ 16
[   10.423299] PCI: Setting latency timer of device 0000:00:1a.0 to 64
[   10.423399] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000dc00
[   10.528773] ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 17 (level, low) -> IRQ 18
[   10.528782] PCI: Setting latency timer of device 0000:00:1a.1 to 64
[   10.528826] uhci_hcd 0000:00:1a.1: irq 18, io base 0x0000e000
[   10.636584] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 19
[   10.636592] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   10.636635] uhci_hcd 0000:00:1d.0: irq 19, io base 0x0000d480
[   10.744407] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 17
[   10.744412] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   10.744454] uhci_hcd 0000:00:1d.1: irq 17, io base 0x0000d800
[   10.852235] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 20
[   10.852241] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   10.852284] uhci_hcd 0000:00:1d.2: irq 20, io base 0x0000d880
[   10.960144] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 18 (level, low) -> IRQ 20
[   10.960152] PCI: Setting latency timer of device 0000:00:1a.7 to 64
[   10.960197] PCI: cache line size of 32 is not supported by device 0000:00:1a.7
[   10.960201] ehci_hcd 0000:00:1a.7: irq 20, io mem 0xffaffc00
[   11.071938] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 19
[   11.071947] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   11.071996] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   11.072000] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xffaff800
[   11.183903] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 19 (level, low) -> IRQ 17
[   11.183923] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   11.184085] eth0: RTL8168b/8111b at 0xf8832000, 00:17:31:65:e5:5a, IRQ 17
[   11.190909] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   12.194258] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   12.194334] ata1: SATA max UDMA/133 cmd 0xf88b0100 ctl 0x00000000 bmdma 0x00000000 irq 16
[   12.194379] ata2: SATA max UDMA/133 cmd 0xf88b0180 ctl 0x00000000 bmdma 0x00000000 irq 16
[   12.822728] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 17
[   12.822741] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   12.822760] ata3: SATA max UDMA/133 cmd 0x0001ec00 ctl 0x0001e882 bmdma 0x0001e400 irq 17
[   12.822776] ata4: SATA max UDMA/133 cmd 0x0001e800 ctl 0x0001e482 bmdma 0x0001e408 irq 17
[   13.176425] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 19 (level, low) -> IRQ 17
[   13.176438] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   13.176456] ata5: SATA max UDMA/133 cmd 0x0001d400 ctl 0x0001d082 bmdma 0x0001c880 irq 17
[   13.176472] ata6: SATA max UDMA/133 cmd 0x0001d000 ctl 0x0001cc02 bmdma 0x0001c888 irq 17
[   13.512327] PCI: Enabling device 0000:02:00.1 (0000 -> 0001)
[   13.512332] ACPI: PCI Interrupt 0000:02:00.1[B] -> GSI 17 (level, low) -> IRQ 18
[   13.512347] PCI: Setting latency timer of device 0000:02:00.1 to 64
[   13.512367] ata7: PATA max UDMA/100 cmd 0x0001ac00 ctl 0x0001a882 bmdma 0x0001a400 irq 18
[   13.512391] ata8: PATA max UDMA/100 cmd 0x0001a800 ctl 0x0001a482 bmdma 0x0001a408 irq 18
[   21.940198] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   21.942486] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   22.271077] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   22.761818] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 21
[   22.761831] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   35.068040] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16

```

---

### Post by steam_engenius on 2007-08-25
I'm having a similar problem. Just upgraded to the 2.6.22-10 kernel and my wireless adapter can detect my network but the internet isn't working.

I entered 'lshw -C network' and get the following for my wireless adapter
> 
*-network
[INDENT]description: Wireless Interface[/INDENT]
[INDENT]physical id: 1[/INDENT]
[INDENT]logical name: rausb0[/INDENT]
[INDENT]serial: 00:18:39:0d:d6:d8[/INDENT]
[INDENT]capabilities: ethernet physical wireless[/INDENT]
[INDENT]configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g[/INDENT]

Any help/advice would be much appreciated. Thanks.

---

### Post by steam_engenius on 2007-08-26
Bump

---

### Post by kevdog on 2007-08-26
steam_engenius

You are obviously using a USB wireless dongle.  Do you know what brand?  Im trying to find the chipset inside your device.  You might need to google your device and discover the chipset type for me.

---

### Post by steam_engenius on 2007-08-26
Why yes I am lol. Its a Linksys WUSB54G, which is said in the Ubuntu WifiDocs to work straight out of the box, which it did until I installed the new kernel. Thanks for the reply.

---

### Post by steam_engenius on 2007-08-26
Also I tried booting back into the 2.6.20-16 (I think that was it) kernel (which didnt really work out too well because I had already reinstalled my nvidia driver to work with the new kernel) , and then when I went to boot back into the new kernel its stalling at "Configuring network interfaces"

Im going to try booting into recovery mode now

---

### Post by steam_engenius on 2007-08-26
For now I'm just switching back to the old kernel (which works fine), if anyone has any wisdom as to why the new kernel would mess up my internet, it would be greatly appreciated. Thanks a bunch <3

---

### Post by babysteps on 2007-08-26
[QUOTE=SlaughterDog;3249276][code]
todd@computer:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@03:00.0
       logical name: eth0
       version: 01
       serial: 00:17:31:65:e5:5a
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK ip=192.168.1.101 latency=0 multicast=yes
       resources: ioport:b800-b8ff iomemory:ff8ff000-ff8fffff irq:17
  *-network UNCLAIMED
       description: Ethernet controller
       product: 88w8335 [Libertas] 802.11b/g Wireless
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@05:00.0
       version: 03
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list
       configuration: latency=64
       resources: iomemory:ff9f0000-ff9fffff iomemory:ff9e0000-ff9effff irq:11




todd@computer:~$ ndiswrapper -l
mrv8000c : driver installed
        device (11AB:1FAA) present


I have the exact same chipset as yours. I was using it on the LTS version of 6.06 Dapper Drake, but I had problem with getting connected to the web.  I installed the kubuntu version of 6.06 and was able to use the Wireless Assistant that came with the Kubuntu to actually get on line.
(*Edit: just wanted to say that after an update my wireless didn't work due to the new kernel. At the time i had no option but to reinstall the old kernel and then reinstalling the ndiswrapper and wireless drivers.  This time instead of the pci card coming on with the boot up the light on the wireless card stays off until I boot up and go to the terminal to issue : sudo modprobe ndiswrapper ....after which time I will then click on the wireless assistant to get my connection to the internet. )

First of all, you might want to see what you get if you type: sudo lshw -C network 
instead of just lshw -C network. (since the warning message says: WARNING: you should run this program as super-user.)  If it still says "UNCLAIMED" and or if it doesn't list :
1)a logical name (mine is wlan0) 
2) ndiswrapper + mrv8000c as driver 
then you can looked into it some more. 
Mine looks like this: (after issueing sudo lshw -C network)
*-network
       description: 88W8300 802.11b Cardbus PC Card
       product: 83
       vendor: Marvell Semiconductor
       physical id: 0
       version: 01
       slot: Socket 1
       resources: irq:11
  *-network
       description: Wireless interface
       product: 88w8335 [Libertas] 802.11b/g Wireless
       vendor: Marvell Technology Group Ltd.
       physical id: 3
       bus info: pci@06:00.0
       logical name: wlan0
       version: 03
       serial: 00:18:4d:ee:d4:65
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+mrv8000c driverversion=1.47+Marvell,02/22/2005,3.1.1.7 ip=192.168.1.45 link=yes multicast=yes wireless=IEEE 802.11g
       resources: iomemory:26000000-2600ffff iomemory:26010000-2601ffff irq:11

---

### Post by kevdog on 2007-08-26
Since you are working in the old kernel, can you post
lshw -C network

Whats happening is that in the old kernel there is a built in driver that works, but in the newer kernel you likely need to upgrade the old version of the driver to make it work.  I could be wrong but Im betting you have either a rt2500 or rt73 driver you are using.  The info you post above will tell the story.

---

### Post by SlaughterDog on 2007-08-28
```
todd@computer:~$ sudo lshw -C network
Password:
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@03:00.0
       logical name: eth0
       version: 01
       serial: 00:17:31:65:e5:5a
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=192.168.1.101 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: ioport:b800-b8ff iomemory:ff8ff000-ff8fffff irq:17
  *-network UNCLAIMED
       description: Ethernet controller
       product: 88w8335 [Libertas] 802.11b/g Wireless
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@05:00.0
       version: 03
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list
       configuration: latency=64
       resources: iomemory:ff9f0000-ff9fffff iomemory:ff9e0000-ff9effff irq:11

```

---

### Post by steam_engenius on 2007-08-30
```

michael@michael-desktop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: 3c940 10/100/1000Base-T [Marvell]
       vendor: 3Com Corporation
       physical id: 5
       bus info: pci@02:05.0
       logical name: eth0
       version: 12
       serial: 00:0e:a6:99:60:1c
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=skge driverversion=1.9 firmware=N/A latency=64 maxlatency=31 mingnt=23 multicast=yes
       resources: iomemory:feaf8000-feafbfff ioport:d400-d4ff irq:16
  *-network:1
       description: Ethernet interface
       product: 3c905 100BaseTX [Boomerang]
       vendor: 3Com Corporation
       physical id: d
       bus info: pci@02:0d.0
       logical name: eth1
       version: 00
       serial: 00:60:97:63:e1:a3
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical
       configuration: broadcast=yes driver=3c59x latency=64 maxlatency=8 mingnt=3 multicast=yes
       resources: ioport:dd80-ddbf irq:20
  *-network
       description: Wireless interface
       physical id: 2
       logical name: rausb1
       serial: 00:18:39:0d:d6:d8
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=RT2500USBSTA driverversion=1.0.0 - BETA2 ip=192.168.1.14 multicast=yes wireless=RT2500USB WLAN

```

Ok so I do have the rt2500 driver ver 1.0.0. I had a look at the serialmonkey site and saw that there was a beta 1.1.0 release. Should I be using that driver instead? And if so, would it be functional on the kernel I'm using now (2.6.20-16-generic)? Im kind of hesitant to bother because I don't want to completely mess up the working wireless I have now.

---

### Post by kevdog on 2007-08-30
Can you help me understand what you posted.  There are two different output with two different wireless devices.  

This one:
network
       description: Wireless interface
       physical id: 2
       logical name: rausb1
       serial: 00:18:39:0d:d6:d8
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=RT2500USBSTA driverversion=1.0.0 - BETA2 ip=192.168

Requires installation of serial monkey drivers -- rt2500

This one:
  *-network UNCLAIMED
       description: Ethernet controller
       product: 88w8335 [Libertas] 802.11b/g Wireless
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@05:00.0
       version: 03
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list
       configuration: latency=64
       resources: iomemory:ff9f0000-ff9fffff iomemory:ff9e0000-ff9effff irq:11


requires ndiswrapper with winxp drivers.

---

### Post by steam_engenius on 2007-08-31
> 
*-network UNCLAIMED
description: Ethernet controller
product: 88w8335 [Libertas] 802.11b/g Wireless
vendor: Marvell Technology Group Ltd.
physical id: 0
bus info: pci@05:00.0
version: 03
width: 32 bits
clock: 66MHz
capabilities: bus_master cap_list
configuration: latency=64
resources: iomemory:ff9f0000-ff9fffff iomemory:ff9e0000-ff9effff irq:11


This is SlaughterDog's machine, mine is the first one you referenced. When I run lsmod I see this for my adapter (this is while running the newer kernel):

```

...
uhci_hcd     26640  0
**usbcore      137864  8  rt2500usb,rt2x00usb,usb_storage,usbhid,libusual,ehci_hcd,uhci_hcd**
thermal      14344   0
...

```

Does this mean its loading 2 different drivers? I tried blacklisting the rt2500 driver but it didn't really work. Any suggestions would be helpful and greatly appreciated.

---

### Post by Jay_Bee on 2007-09-04
I installed Gutsy Tribe 5 and Intel wireless in my laptop (with activated restricted driver) detects network but is unable to connect... I would like to see this fixed, because I need internet for my work... kernel is 2.6.22-10 :(
EDIT: It mysteriously works now, using Wifi-radar.

---

### Post by SlaughterDog on 2007-09-08
But I *do* have NDIS wrapper installed, with the XP driver.

---

### Post by SlaughterDog on 2007-09-08
Oh, here's a dumb mistake... I forgot I don't have my SSID broadcast, and tried to connect to a wireless network called 'home' last time. No wonder it didn't work; I don't think it's my network.
If I enable roaming mode and try to connect to custom network and put in my SSID, and put in my WPA password, it connects with 25% to 35% signal, which I think is fine. Problem is, I still can't do anything on it; Firefox acts like there's no connection and I can't access my other computer via network. Can't even get into my router config. 
Also, I seem to have to use roaming mode because it's the only way it will ask for a WPA password; if I try to disable roaming, the box there only asks for a WEP password.

And here's another annoyance; if I unplug my Ethernet cord to test this stuff, it seems to switch off that NIC as the light on it goes out and I can't get it to work again until I restart the computer. Is there an easy way to re-enable it?

---

