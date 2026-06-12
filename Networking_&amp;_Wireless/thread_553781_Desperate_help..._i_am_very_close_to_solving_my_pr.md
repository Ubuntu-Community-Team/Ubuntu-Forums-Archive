---
title: "Desperate help... i am very close to solving my problem"
date: 2007-09-18
forum: Networking &amp; Wireless
---

### Post by liorz1984 on 2007-09-18
Hey, 
I have an  Intel PRO/Wireless 3945ABG card,
I have a serious problem with connecting to wifi networks.
I was managed to install the ipw3945 driver on my fiesty fawn , but i can't really make it run or load.
when i run the load script i get this error: ERROR: Could not find Intel PRO/Wireless 3945ABG Network Connection.
 

More information regarding my system
lshw -C network gives me this output:

 *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 3
       bus info: pci@04:03.0
       logical name: eth0
       version: 10
       serial: 00:16:17:54:5e:de
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.2.102 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: ioport:d800-d8ff iomemory:fe9ffc00-fe9ffcff irq:19
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:19:db:09:a5:falo        no wireless extensions.


iwconfig gives me this output :

eth0      no wireless extensions.

wmaster0  IEEE 802.11g  Frequency:2.437 GHz  
          RTS thr:off   Fragment thr=2346 B   
          
wlan0     IEEE 802.11g  ESSID:"blabla"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0E:2E:BA:A2:AE   
          RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g



Please help me :( I've posted here several times and no one even bothered :(

---

### Post by arist0tle on 2007-09-18
Did you load the kernel module for the driver? If not, do a: sudo modprobe drivername
I am assuming that you have a thinkpad since those cards are very popular with that laptop. My thinkpad has an atheros card and it worked right out of the box. Also, what wireless client are you using to monitor wifi connections? I am using NetworkManager. Make sure you have the driver properly installed as well as the firmware for the card, then load the kernel module. You should get results with that. That card is pretty well supported by Linux.

---

### Post by liorz1984 on 2007-09-18
Hey
Thank you for replying to my post.
First, i did load the kernel module for the driver ( sudo modprobe ipw3945 ).
Second, i have an LG laptop.. i guess it is quite common in those laptops as well.
I'm using NetworkManager as well.

The main problem is that i can't see the name of my wireless card anywhere in system records,,,
not in the Hardware Information screen under the Administration tab and not in ifconfig... so i think that Fiesty **does not recognize my device\driver**...

---

### Post by arist0tle on 2007-09-18
I know that feisty supports that card. Does the card work properly with windows? (assuming you have a dual boot) Is the card itself seeded correctly? You may laugh, but when i got my thinkpad, they forgot to put a wireless card in it. I was baffled for a couple of hours b/c linux couldn't find the device

---

### Post by arist0tle on 2007-09-18
seated...whatever the word is....installed(lol!)

---

### Post by liorz1984 on 2007-09-18
Hey
The card is working perfectly in Windows, so it is probably installed, plus, NetworkManager recognizes my wifi, but can never connect to it.
also dhclient, cant connect to it...

I have been struggling with this problem for 2 weeks...

---

### Post by arist0tle on 2007-09-18
Sorry... I have never run into many problems with wifi so i don't really have any other suggestions. Try running the install disk in live mode and see if recognizes anything or allows you to connect. If it works, you know that it was something you messed with after installation. Good luck

---

### Post by noob12 on 2007-09-18
liorz1984:  Start by posting the output of  **lspci -nn**, so we can see the device ids of the cards you have.

---

### Post by liorz1984 on 2007-09-18
hey, thanks for your help!
here is the output:

00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub [8086:27a0] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 [8086:27d4] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
00:1f.2 IDE interface [0101]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller [8086:27c4] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801G (ICH7 Family) SMBus Controller [8086:27da] (rev 02)
04:03.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
04:04.0 CardBus bridge [0607]: O2 Micro, Inc. OZ711MP1/MS1 MemoryCardBus Controller [1217:7134] (rev 21)
04:04.2 Generic system peripheral [0805]: O2 Micro, Inc. Integrated MMC/SD Controller [1217:7120] (rev 01)
04:04.3 Bridge [0680]: O2 Micro, Inc. Integrated MS/xD Controller [1217:7130] (rev 01)
04:04.4 FireWire (IEEE 1394) [0c00]: O2 Micro, Inc. Firewire (IEEE 1394) [1217:00f7] (rev 02)

no entry about my wireless card

---

### Post by noob12 on 2007-09-18
Are you sure you have a PCI wireless card?  If so, the fact that it isn't showing in the lspci output indicates you have PCI routing issues during boot.   You aren't going to get anywhere until the card shows up.

If you are sure you have a PCI-based wireless card then post your full **dmesg**.  You should also try booting with the **pci=noacpi** boot flag and see if the card shows up then.

If you have a USB card, it should show up with **lsusb**.  In all cases you'll need to know the device id to proceed.

---

### Post by liorz1984 on 2007-09-18
Hey,
My card is built-in on the motherboard (at least that's what the tech support told me... )
It's not a usb card...
The main problem is that i can't see my card's name anywhere..

Iv'e also loaded ubuntu from the live CD and also, could not connect or view the card's name anywhere... :(

---

### Post by noob12 on 2007-09-18
Try booting with the flag **pci=noacpi** and seeing if that makes the device show up.  The device has to be on some bus even if it is onboard.

Also, post the output of **dmesg**.  Are you sure you have a wireless device onboard?

---

### Post by liorz1984 on 2007-09-19
Hey,
I tried booting with your sugguested option, but it didn't make my device appear..
here is the output of dmesg:

[    0.000000] Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Fri Aug 31 00:55:27 UTC 2007 (Ubuntu 2.6.20-16.31-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009fc00 end: 000000000009fc00 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009fc00 size: 0000000000000400 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000e0000 size: 0000000000020000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000007f6d0000 end: 000000007f7d0000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000007f7d0000 size: 000000000000e000 end: 000000007f7de000 type: 3
[    0.000000] copy_e820_map() start: 000000007f7de000 size: 0000000000022000 end: 000000007f800000 type: 4
[    0.000000] copy_e820_map() start: 00000000fee00000 size: 0000000000001000 end: 00000000fee01000 type: 2
[    0.000000] copy_e820_map() start: 00000000fff80000 size: 0000000000080000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007f7d0000 (usable)
[    0.000000]  BIOS-e820: 000000007f7d0000 - 000000007f7de000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007f7de000 - 000000007f800000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] 1143MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000ff780
[    0.000000] Entering add_active_range(0, 0, 522192) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   522192
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   522192
[    0.000000] On node 0 totalpages: 522192
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2287 pages used for memmap
[    0.000000]   HighMem zone: 290529 pages, LIFO batch:31
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP (v000 LGE                                   ) @ 0x000f87b0
[    0.000000] ACPI: RSDT (v001 LGE    LGPC     0x01252007 MSFT 0x00000097) @ 0x7f7d0000
[    0.000000] ACPI: FADT (v002 LGE    LGPC     0x01252007 MSFT 0x00000097) @ 0x7f7d0200
[    0.000000] ACPI: MADT (v001 LGE    OEMAPIC  0x01252007 MSFT 0x00000097) @ 0x7f7d0390
[    0.000000] ACPI: MCFG (v001 LGE    OEMMCFG  0x01252007 MSFT 0x00000097) @ 0x7f7d03f0
[    0.000000] ACPI: SLIC (v001 LGE    LGPC     0x01252007 MSFT 0x00000097) @ 0x7f7d0430
[    0.000000] ACPI: OEMB (v001 LGE    AMI_OEM  0x01252007 MSFT 0x00000097) @ 0x7f7de040
[    0.000000] ACPI: DSDT (v001 LGE      LGPC   0x01252007 INTL 0x02002026) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:15 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] Processor #1 6:15 APIC version 20
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 7f800000:7f600000)
[    0.000000] Detected 1666.814 MHz processor.
[   18.114425] Built 1 zonelists.  Total pages: 518113
[   18.114429] Kernel command line: root=UUID=5eb2a1ce-6912-473c-985c-fae6013b2784 pci=assign-busses ro quiet splash
[   18.114584] mapped APIC to ffffd000 (fee00000)
[   18.114587] mapped IOAPIC to ffffc000 (fec00000)
[   18.114589] Enabling fast FPU save and restore... done.
[   18.114592] Enabling unmasked SIMD FPU exception support... done.
[   18.114599] Initializing CPU#0
[   18.114670] PID hash table entries: 4096 (order: 12, 16384 bytes)
[   18.116531] Console: colour VGA+ 80x25
[   18.116794] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   18.117092] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   18.193422] Memory: 2059832k/2088768k available (1993k kernel code, 27636k reserved, 900k data, 328k init, 1171264k highmem)
[   18.193432] virtual kernel memory layout:
[   18.193433]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   18.193434]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   18.193435]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   18.193436]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   18.193437]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
[   18.193438]       .data : 0xc02f2434 - 0xc03d36d4   ( 900 kB)
[   18.193439]       .text : 0xc0100000 - 0xc02f2434   (1993 kB)
[   18.193442] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   18.270598] Calibrating delay using timer specific routine.. 3337.54 BogoMIPS (lpj=6675080)
[   18.270639] Security Framework v1.0.0 initialized
[   18.270645] SELinux:  Disabled at boot.
[   18.270662] Mount-cache hash table entries: 512
[   18.270801] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e39d 00000000 00000001
[   18.270809] monitor/mwait feature present.
[   18.270811] using mwait in idle threads.
[   18.270815] CPU: L1 I cache: 32K, L1 D cache: 32K
[   18.270818] CPU: L2 cache: 2048K
[   18.270820] CPU: Physical Processor ID: 0
[   18.270822] CPU: Processor Core ID: 0
[   18.270824] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e39d 00000000 00000001
[   18.270834] Compat vDSO mapped to ffffe000.
[   18.270838] Remapping vsyscall page to ffffe000
[   18.270850] Checking 'hlt' instruction... OK.
[   18.286693] SMP alternatives: switching to UP code
[   18.287053] Early unpacking initramfs... done
[   18.604913] ACPI: Core revision 20060707
[   18.605188] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   18.619498] CPU0: Intel(R) Core(TM)2 CPU         T5500  @ 1.66GHz stepping 06
[   18.619517] SMP alternatives: switching to SMP code
[   18.619593] Booting processor 1/1 eip 3000
[   18.629998] Initializing CPU#1
[   18.710365] Calibrating delay using timer specific routine.. 3333.83 BogoMIPS (lpj=6667668)
[   18.710371] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e39d 00000000 00000001
[   18.710376] monitor/mwait feature present.
[   18.710379] CPU: L1 I cache: 32K, L1 D cache: 32K
[   18.710381] CPU: L2 cache: 2048K
[   18.710383] CPU: Physical Processor ID: 0
[   18.710384] CPU: Processor Core ID: 1
[   18.710386] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e39d 00000000 00000001
[   18.710904] CPU1: Intel(R) Core(TM)2 CPU         T5500  @ 1.66GHz stepping 06
[   18.710926] Total of 2 processors activated (6671.37 BogoMIPS).
[   18.711123] ENABLING IO-APIC IRQs
[   18.711322] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   18.858303] checking TSC synchronization across 2 CPUs: passed.
[    0.003999] Brought up 2 CPUs
[    0.067673] migration_cost=40
[    0.067937] Booting paravirtualized kernel on bare hardware
[    0.068044] Time:  8:35:59  Date: 08/19/107
[    0.068071] NET: Registered protocol family 16
[    0.068151] EISA bus registered
[    0.068156] ACPI: bus type pci registered
[    0.068336] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=5
[    0.068338] PCI: Using configuration type 1
[    0.068340] Setting up standard PCI resources
[    0.081644] ACPI: Interpreter enabled
[    0.081646] ACPI: Using IOAPIC for interrupt routing
[    0.082171] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.082177] PCI: Probing PCI hardware (bus 00)
[    0.082445] Boot video device is 0000:00:02.0
[    0.083081] PCI quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
[    0.083085] PCI quirk: region 0480-04bf claimed by ICH6 GPIO
[    0.083944] PCI: Transparent bridge - 0000:00:1e.0
[    0.084032] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.099645] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[    0.100397] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.101220] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P2._PRT]
[    0.102407] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.102643] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.102878] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.103119] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 5 6 7 10 11 12 14 15)
[    0.103355] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.103590] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 *7 10 11 12 14 15)
[    0.103825] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.104068] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.104272] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.104281] pnp: PnP ACPI init
[    0.106021] pnp: PnP ACPI: found 12 devices
[    0.106026] PnPBIOS: Disabled by ACPI PNP
[    0.106069] PCI: Using ACPI for IRQ routing
[    0.106072] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    0.126996] NET: Registered protocol family 8
[    0.126998] NET: Registered protocol family 20
[    0.127885] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
[    0.127892] PCI: Bridge: 0000:00:1c.0
[    0.127895]   IO window: b000-bfff
[    0.127901]   MEM window: fd900000-fe0fffff
[    0.127911]   PREFETCH window: bbf00000-bdefffff
[    0.127917] PCI: Bridge: 0000:00:1c.2
[    0.127918]   IO window: disabled.
[    0.127926]   MEM window: disabled.
[    0.127930]   PREFETCH window: disabled.
[    0.127943] PCI: Bus 4, cardbus bridge: 0000:03:04.0
[    0.127945]   IO window: 0000c000-0000c0ff
[    0.127950]   IO window: 0000c400-0000c4ff
[    0.127956]   PREFETCH window: 84000000-87ffffff
[    0.127961]   MEM window: 88000000-8bffffff
[    0.127966] PCI: Bridge: 0000:00:1e.0
[    0.127970]   IO window: c000-dfff
[    0.127976]   MEM window: fe100000-fe9fffff
[    0.127981]   PREFETCH window: bdf00000-bfefffff
[    0.128011] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
[    0.128018] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    0.128042] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 17
[    0.128048] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[    0.128063] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    0.128080] ACPI: PCI Interrupt 0000:03:04.0[A] -> GSI 16 (level, low) -> IRQ 16
[    0.128111] NET: Registered protocol family 2
[    0.167945] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.168051] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.168529] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.168771] TCP: Hash tables configured (established 131072 bind 65536)
[    0.168773] TCP reno registered
[    0.180013] checking if image is initramfs... it is
[    0.807364] Freeing initrd memory: 6762k freed
[    0.807996] audit: initializing netlink socket (disabled)
[    0.808013] audit(1190190959.624:1): initialized
[    0.808112] highmem bounce pool size: 64 pages
[    0.808199] VFS: Disk quotas dquot_6.5.1
[    0.808221] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.808272] io scheduler noop registered
[    0.808275] io scheduler anticipatory registered
[    0.808277] io scheduler deadline registered
[    0.808288] io scheduler cfq registered (default)
[    0.808529] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    0.808587] assign_interrupt_mode Found MSI capability
[    0.808590] Allocate Port Service[0000:00:1c.0:pcie00]
[    0.808719] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[    0.808776] assign_interrupt_mode Found MSI capability
[    0.808778] Allocate Port Service[0000:00:1c.2:pcie00]
[    0.808961] isapnp: Scanning for PnP cards...
[    1.162650] isapnp: No Plug & Play device found
[    1.183413] Real Time Clock Driver v1.12ac
[    1.183467] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    1.184070] mice: PS/2 mouse device common for all mice
[    1.184620] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    1.184838] input: Macintosh mouse button emulation as /class/input/input0
[    1.184872] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    1.184876] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    1.185160] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    1.185599] i8042.c: Detected active multiplexing controller, rev 1.1.
[    1.185674] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.185677] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.185680] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.185682] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.185684] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.185792] EISA: Probing bus 0 at eisa.0
[    1.185832] EISA: Detected 0 cards.
[    1.215993] TCP cubic registered
[    1.216002] NET: Registered protocol family 1
[    1.216024] Starting balanced_irq
[    1.216031] Using IPI No-Shortcut mode
[    1.216145] input: AT Translated Set 2 keyboard as /class/input/input1
[    1.216148] ACPI: (supports S0 S1 S3 S4 S5)
[    1.216196]   Magic number: 7:322:574
[    1.216235]   hash matches device ptyb6
[    1.216448] Freeing unused kernel memory: 328k freed
[    1.219342] Time: tsc clocksource has been installed.
[    2.432945] Capability LSM initialized
[    2.469737] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [   AMI] OemTableId [  CPU1PM] [20060707]
[    2.469890] ACPI: CPU0 (power states: C1[C1] C2[C2])
[    2.470117] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [   AMI] OemTableId [  CPU2PM] [20060707]
[    2.470246] ACPI: CPU1 (power states: C1[C1] C2[C2])
[    3.104000] ACPI: Thermal Zone [THRM] (63 C)
[    3.112000] Time: acpi_pm clocksource has been installed.
[    3.500000] usbcore: registered new interface driver usbfs
[    3.500000] usbcore: registered new interface driver hub
[    3.500000] usbcore: registered new device driver usb
[    3.500000] USB Universal Host Controller Interface driver v3.0
[    3.500000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 18
[    3.500000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[    3.500000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.500000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    3.500000] uhci_hcd 0000:00:1d.0: irq 18, io base 0x0000e880
[    3.500000] usb usb1: configuration #1 chosen from 1 choice
[    3.500000] hub 1-0:1.0: USB hub found
[    3.500000] hub 1-0:1.0: 2 ports detected
[    3.532000] ieee1394: Initialized config rom entry `ip1394'
[    3.544000] SCSI subsystem initialized
[    3.572000] libata version 2.20 loaded.
[    3.572000] 8139too Fast Ethernet driver 0.9.28
[    3.608000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
[    3.608000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[    3.608000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.608000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[    3.608000] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000e800
[    3.608000] usb usb2: configuration #1 chosen from 1 choice
[    3.608000] hub 2-0:1.0: USB hub found
[    3.608000] hub 2-0:1.0: 2 ports detected
[    3.716000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 17
[    3.716000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[    3.716000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.716000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[    3.716000] uhci_hcd 0000:00:1d.2: irq 17, io base 0x0000e480
[    3.716000] usb usb3: configuration #1 chosen from 1 choice
[    3.716000] hub 3-0:1.0: USB hub found
[    3.716000] hub 3-0:1.0: 2 ports detected
[    3.824000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 16
[    3.824000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[    3.824000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    3.824000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[    3.824000] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000e400
[    3.824000] usb usb4: configuration #1 chosen from 1 choice
[    3.824000] hub 4-0:1.0: USB hub found
[    3.824000] hub 4-0:1.0: 2 ports detected
[    3.848000] usb 1-1: new low speed USB device using uhci_hcd and address 2
[    3.932000] ACPI: PCI Interrupt 0000:03:04.4[A] -> GSI 16 (level, low) -> IRQ 16
[    3.932000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 18
[    3.932000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    3.932000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.932000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[    3.932000] ehci_hcd 0000:00:1d.7: debug port 1
[    3.932000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[    3.932000] ehci_hcd 0000:00:1d.7: irq 18, io mem 0xfeb3bc00
[    3.936000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.936000] usb usb5: configuration #1 chosen from 1 choice
[    3.936000] hub 5-0:1.0: USB hub found
[    3.936000] hub 5-0:1.0: 8 ports detected
[    3.980000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[16]  MMIO=[fe9fd000-fe9fd7ff]  Max Packet=[2048]  IR/IT contexts=[8/8]
[    4.044000] ACPI: PCI Interrupt 0000:03:03.0[A] -> GSI 21 (level, low) -> IRQ 20
[    4.044000] eth0: RealTek RTL8139 at 0xf8872c00, 00:16:17:54:5e:de, IRQ 20
[    4.044000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[    4.044000] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    4.044000] ata_piix 0000:00:1f.2: version 2.10ac1
[    4.044000] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    4.200000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 19
[    4.200000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[    4.204000] ata1: SATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001ffa0 irq 14
[    4.204000] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001ffa8 irq 15
[    4.204000] scsi0 : ata_piix
[    4.376000] ata1.00: ata_hpa_resize 1: sectors = 234441648, hpa_sectors = 234441648
[    4.376000] ata1.00: ATA-7: FUJITSU MHV2120BH PL, 00000029, max UDMA/100
[    4.376000] ata1.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    4.388000] ata1.00: ata_hpa_resize 1: sectors = 234441648, hpa_sectors = 234441648
[    4.388000] ata1.00: configured for UDMA/100
[    4.388000] scsi1 : ata_piix
[    4.392000] usb 1-1: device not accepting address 2, error -71
[    4.548000] ATA: abnormal status 0x7F on port 0x00010177
[    4.564000] ATA: abnormal status 0x7F on port 0x00010177
[    4.736000] ata2.01: ATAPI, max UDMA/33
[    4.908000] ata2.01: configured for UDMA/33
[    4.908000] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHV2120B 0000 PQ: 0 ANSI: 5
[    4.912000] scsi 1:0:1:0: CD-ROM            HL-DT-ST DVDRAM GSA-T10N  PA02 PQ: 0 ANSI: 5
[    4.924000] SCSI device sda: 234441648 512-byte hdwr sectors (120034 MB)
[    4.924000] sda: Write Protect is off
[    4.924000] sda: Mode Sense: 00 3a 00 00
[    4.924000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.924000] SCSI device sda: 234441648 512-byte hdwr sectors (120034 MB)
[    4.924000] sda: Write Protect is off
[    4.924000] sda: Mode Sense: 00 3a 00 00
[    4.924000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.924000]  sda: sda1 sda2 sda3 sda4 < sda5 >
[    5.144000] sd 0:0:0:0: Attached scsi disk sda
[    5.148000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    5.148000] sr 1:0:1:0: Attached scsi generic sg1 type 5
[    5.164000] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    5.164000] Uniform CD-ROM driver Revision: 3.20
[    5.164000] sr 1:0:1:0: Attached scsi CD-ROM sr0
[    5.264000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00dc100036161901]
[    5.332000] usb 5-6: new high speed USB device using ehci_hcd and address 4
[    5.512000] Attempting manual resume
[    5.512000] swsusp: Resume From Partition 8:5
[    5.512000] PM: Checking swsusp image.
[    5.512000] PM: Resume from disk failed.
[    5.552000] kjournald starting.  Commit interval 5 seconds
[    5.552000] EXT3-fs: mounted filesystem with ordered data mode.
[    5.616000] usb 5-6: configuration #1 chosen from 1 choice
[    5.856000] usb 1-1: new low speed USB device using uhci_hcd and address 4
[    6.064000] usb 1-1: configuration #1 chosen from 1 choice
[    6.312000] usb 2-1: new full speed USB device using uhci_hcd and address 2
[    6.496000] usb 2-1: configuration #1 chosen from 1 choice
[    6.500000] hub 2-1:1.0: USB hub found
[    6.500000] hub 2-1:1.0: 4 ports detected
[   16.340000] iTCO_vendor_support: vendor-support=0
[   16.340000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[   16.340000] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x0860)
[   16.340000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   16.388000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   16.392000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   16.404000] intel_rng: FWH not detected
[   16.820000] Linux agpgart interface v0.102 (c) Dave Jones
[   16.828000] agpgart: Detected an Intel 945GM Chipset.
[   16.828000] agpgart: Detected 7932K stolen memory.
[   16.844000] agpgart: AGP aperture is 256M @ 0xd0000000
[   16.844000] input: PC Speaker as /class/input/input2
[   16.900000] Yenta: CardBus bridge found at 0000:03:04.0 [1462:3b7f]
[   16.900000] Yenta O2: res at 0x94/0xD4: 00/ea
[   16.900000] Yenta O2: enabling read prefetch/write burst
[   16.908000] sdhci: Secure Digital Host Controller Interface driver
[   16.908000] sdhci: Copyright(c) Pierre Ossman
[   17.032000] Yenta: ISA IRQ mask 0x0cb8, PCI irq 16
[   17.032000] Socket status: 30000006
[   17.032000] pcmcia: parent PCI bridge I/O window: 0xc000 - 0xdfff
[   17.032000] cs: IO port probe 0xc000-0xdfff: clean.
[   17.032000] pcmcia: parent PCI bridge Memory window: 0xfe100000 - 0xfe9fffff
[   17.032000] pcmcia: parent PCI bridge Memory window: 0xbdf00000 - 0xbfefffff
[   17.040000] sdhci: SDHCI controller found at 0000:03:04.2 [1217:7120] (rev 1)
[   17.040000] ACPI: PCI Interrupt 0000:03:04.2[A] -> GSI 16 (level, low) -> IRQ 16
[   17.040000] sdhci:slot0: Unknown controller version (16). You may experience problems.
[   17.040000] mmc0: SDHCI at 0xfe9ff800 irq 16 PIO
[   17.192000] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x12a0b1, caps: 0xa0471b/0x200000
[   17.224000] input: SynPS/2 Synaptics TouchPad as /class/input/input3
[   17.232000] usbcore: registered new interface driver hiddev
[   17.332000] Loading module: rt2x00lib - CVS (N/A) by [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com).
[   17.332000] Loading module: rt73usb - CVS (N/A) by [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com).
[   17.384000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 16
[   17.384000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   17.440000] input: HID 04d9:0499 as /class/input/input4
[   17.440000] input: USB HID v1.10 Mouse [HID 04d9:0499] on usb-0000:00:1d.0-1
[   17.440000] usbcore: registered new interface driver usbhid
[   17.440000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   17.488000] cs: IO port probe 0x100-0x3af: clean.
[   17.488000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   17.488000] cs: IO port probe 0x820-0x8ff: clean.
[   17.492000] cs: IO port probe 0xc00-0xcf7: clean.
[   17.492000] cs: IO port probe 0xa00-0xaff: clean.
[   17.664000] usbcore: registered new interface driver rt73usb
[   17.892000] wmaster0: Selected rate control algorithm 'simple'
[   18.372000] si3054: cannot initialize. EXT MID = 0000
[   18.544000] fuse init (API version 7.8)
[   18.624000] lp: driver loaded but no devices found
[   18.684000] Adding 2192832k swap on /dev/disk/by-uuid/9d70f204-72a7-451e-87bf-da2423632d6d.  Priority:-1 extents:1 across:2192832k
[  136.324000] EXT3 FS on sda3, internal journal
[  137.652000] NET: Registered protocol family 17
[  140.292000] ACPI: Battery Slot [BAT1] (battery present)
[  140.352000] Using specific hotkey driver
[  140.384000] ACPI: AC Adapter [ADP1] (on-line)
[  140.404000] input: Power Button (FF) as /class/input/input5
[  140.404000] ACPI: Power Button (FF) [PWRF]
[  140.404000] input: Power Button (CM) as /class/input/input6
[  140.404000] ACPI: Power Button (CM) [PWRB]
[  140.404000] input: Sleep Button (CM) as /class/input/input7
[  140.404000] ACPI: Sleep Button (CM) [SLPB]
[  140.404000] input: Lid Switch as /class/input/input8
[  140.404000] ACPI: Lid Switch [LID0]
[  140.476000] ibm_acpi: ec object not found
[  140.596000] No dock devices found.
[  140.612000] ACPI: Video Device [JVGA] (multi-head: yes  rom: no  post: no)
[  140.668000] pcc_acpi: loading...
[  144.344000] wlan0: starting scan
[  144.392000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  145.032000] ppdev: user-space parallel port driver
[  145.200000] [drm] Initialized drm 1.1.0 20060810
[  145.208000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[  145.208000] [drm] Initialized i915 1.6.0 20060119 on minor 0
[  145.252000] wlan0: scan completed
[  148.004000] NET: Registered protocol family 10
[  148.004000] lo: Disabled Privacy Extensions
[  148.148000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[  148.148000] apm: disabled - APM is not SMP safe.
[  158.708000] wlan0: no IPv6 routers present
[  158.856000] eth0: no IPv6 routers present
[  165.356000] wlan0: starting scan
[  166.248000] wlan0: scan completed
[  186.256000] wlan0: starting scan
[  187.148000] wlan0: scan completed
[  207.244000] wlan0: starting scan
[  208.112000] wlan0: scan completed
[  210.856000] Bluetooth: Core ver 2.11
[  210.856000] NET: Registered protocol family 31
[  210.856000] Bluetooth: HCI device and connection manager initialized
[  210.856000] Bluetooth: HCI socket layer initialized
[  210.872000] Bluetooth: L2CAP ver 2.8
[  210.872000] Bluetooth: L2CAP socket layer initialized
[  211.024000] Bluetooth: RFCOMM socket layer initialized
[  211.024000] Bluetooth: RFCOMM TTY layer initialized
[  211.024000] Bluetooth: RFCOMM ver 1.8
[  228.136000] wlan0: starting scan
[  229.060000] wlan0: scan completed
[  233.248000] eth0: no IPv6 routers present
[  249.172000] wlan0: starting scan
[  250.096000] wlan0: scan completed
[  270.204000] wlan0: starting scan
[  271.096000] wlan0: scan completed
[  391.164000] wlan0: starting scan
[  392.044000] wlan0: scan completed
[  512.120000] wlan0: starting scan
[  513.028000] wlan0: scan completed

Thank you very much for helping, you are a life saver! :)

---

### Post by liorz1984 on 2007-09-19
Now i checked in windows device manager, and the driver appears as 802.11g Mini Card Wireless Adapter, and on the details it's wrriten that the manufacturer is Ralink

---

### Post by noob12 on 2007-09-19
I had suggested **pci=noacpi**.  Here's the command line it says you actually used:
```

Kernel command line: root=UUID=5eb2a1ce-6912-473c-985c-fae6013b2784 pci=assign-busses ro quiet splash

```

There were some interesting things in the dmesg anyway.  Had you specified loading these explicitly?

```

[ 17.332000] Loading module: rt2x00lib - CVS (N/A) by http://rt2x00.serialmonkey.com.
[ 17.332000] Loading module: rt73usb - CVS (N/A) by http://rt2x00.serialmonkey.com.
... later ...
[ 17.664000] usbcore: registered new interface driver rt73usb
[ 17.892000] wmaster0: Selected rate control algorithm 'simple'
... and later, lots of log entries from wlan0 ...
[ 144.344000] wlan0: starting scan
[ 145.252000] wlan0: scan completed
[ 158.708000] wlan0: no IPv6 routers present
][ 165.356000] wlan0: starting scan
[ 166.248000] wlan0: scan completed
[ 186.256000] wlan0: starting scan
[ 187.148000] wlan0: scan completed
[ 207.244000] wlan0: starting scan
[ 208.112000] wlan0: scan completed
[ 228.136000] wlan0: starting scan
[ 229.060000] wlan0: scan completed
[ 249.172000] wlan0: starting scan
[ 250.096000] wlan0: scan completed
[ 270.204000] wlan0: starting scan
[ 271.096000] wlan0: scan completed
[ 391.164000] wlan0: starting scan
[ 392.044000] wlan0: scan completed
[ 512.120000] wlan0: starting scan
[ 513.028000] wlan0: scan completed

```

That looks like you do have a usb device, possibly an onboard device attached via an onboard usb, and you have some drivers loading for it but you may need to update them.  Let's get the specific device id to decide how to proceed.  Please post the output of
```

lsusb

```

---

### Post by liorz1984 on 2007-09-19
Hey,
Sorry for putting the wrong output, i've tried your suggestion, pci=noacpi and it didn't work, so i tried something else afterwards and put this output by mistake,
Anyway, I've checked in windows device manager (sorted it by connection..), and the wireless card didn't appear on the PCI bus section, or at any of the usb hubs it appears only on the regular view (forgot the name..)
Anyway, this is the output to lsusb, i have nothing connected to my usb hubs right now:

Bus 004 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 0db0:6877 Micro Star International 
Bus 001 Device 001: ID 0000:0000  


Hope it will help.. thx.
Lior

---

### Post by noob12 on 2007-09-19
Yes, so first of all you don't have an Intel 3945 device at all.  The **lsusb** shows you have an RALink RT73 usb-based onboard.

Ubuntu ships with a somewhat dated version of the rt73usb driver.  It does seem to have claimed the device and assigned it an interface named wlan0.  This shows up in your **sudo lshw -C network** and should show up if you run **ifconfig -a**.  It probably won't work.

I suggest that you follow this HOWTO thread:  [http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236) to install the latest rt73 drivers from serialmonkey and if you have questions during that process, post back to that thread.

---

### Post by liorz1984 on 2007-09-19
Hey, Looks like your'e right, iv'e followed the steps in the instructions, now the name of the card appears in Hardware information and in iwconfig.
But, i can't see any wireless networks in network manager, or connect to them.
(not even through dhclient)
here is the output of ifconfig -a
wlan1     Link encap:Ethernet  HWaddr 00:19:DB:09:A5:FA  
          inet6 addr: fe80::219:dbff:fe09:a5fa/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:806 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1175 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:64517 (63.0 KiB)  TX bytes:89494 (87.3 KiB)

and here is the output of iwconfig , showing the name of the device:
wlan1     RT73 WLAN  ESSID:""  
          Mode:Managed  Frequency=2.417 GHz  Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level:-22 dBm  Noise level:-115 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Im pretty lost here, iv'e followed every step of the instructions without errors, and i still can't connect or view available networks.
Good thing though, that the device is recognized right now...

Any more ideas in mind?.. thank you very much!

---

### Post by liorz1984 on 2007-09-19
Output of lshw -C network:

  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan1
       serial: 00:19:db:09:a5:fa
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=RT73 WLAN

---

### Post by noob12 on 2007-09-19
I would suggest that you post back on that thread, as some RT73 experts watch it.  I'm not very familiar with that chipset.

See if **sudo iwlist scan** works to show your access point.

---

### Post by liorz1984 on 2007-09-19
It shows my access point... 

wlan1     Scan completed :
          Cell 01 - Address: 00:0E:2E:AE:32:D8
                    ESSID:"ASHKENAZI"
                    Mode:Managed
                    Channel:2
                    Encryption key:off
                    Bit Rates:0 kb/s


But i can't connect... :(

---

### Post by noob12 on 2007-09-19
OK.  Well try the obvious things, like right-click on the Network Manager icon and Enable Wireless, then left-click on it and select your ESSID. 

Then I would ask the people on that thread.   I'm not familar with specifics of the rt73 chipset, and I think there are some tidbits there that 



Also make sure the ESSID broadcast is on in your AP.  It looks like you already have encryption off.  That's a reasonable way to get started.  You should add the security once you have connectivity working.

You can try to configure the wireless manually using iwconfig to point at your ESSID and see if you can associate.  This is directly from that thread(!) with wlan1 in your case because you seem to have gotten that device name assignment (check /etc/iftab if you want it to be named wlan0 instead).

```

sudo ifconfig wlan1 up
sudo iwconfig wlan1 essid ASHKENAZI
sudo iwconfig wlan1 key off
sudo dhclient wlan1

```

---

### Post by liorz1984 on 2007-09-20
Thank you, 
I've done that (from reading this tutorial) , didn't work...
Now that im getting this post to the top, i hope ralink experts will see it and comment...

---

### Post by liorz1984 on 2007-09-20
OK ! Got it! i've got wireless up and running.
The only thing now, is get it to work with network manager, because i was only able to connect manualy, using dhclient.
I reinstalled network-manager, but it didn't help...

What i did to solve the problem is just completly remove any trace of the previous ipw3945 installation , and reinstall the rt73 driver...

---

### Post by noob12 on 2007-09-20
Some chipsets/drivers are supported by NM.  Others aren't.  Based on [http://live.gnome.org/NetworkManagerHardware](http://live.gnome.org/NetworkManagerHardware), yours (rt73) is on the Unsupported list.

You might ask there (on the rt73 HOWTO thread)  or in a separate thread if people have been able to use wicd with recent rt73 serialmonkey drivers successfully.  If people say they are using wicd successfully, you might try that.

---

### Post by liorz1984 on 2007-09-20
Ok, thank you very very much! you have been superbly helpful, i've checked Wicd and it didn't work,, i guess i'll have to wait for newer versions to come out...

 Again, thank you for your patience!

---

### Post by noob12 on 2007-09-20
The last alternative that might work for you is wifi-radar.  You might search around for that.   I don't really have any experience with that myself.

---

### Post by noob12 on 2007-09-21
There is also this that might help.  A utility called rutilt:    [http://cbbk.free.fr/bonrom/](http://cbbk.free.fr/bonrom/)

---

