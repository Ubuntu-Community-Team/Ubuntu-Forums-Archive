---
title: "Trouble with Atheros AR5005EG Wi-Fi chipset"
date: 2007-10-19
forum: Networking &amp; Wireless
---

### Post by souta95 on 2007-10-19
First off, I apologize if I am just overlooking something obvious, I do not know much when it comes to Linux drivers.

I downloaded and installed Ubuntu 7.10 today and I am trying to get it to work on my Acer 5050 series laptop (5050-3371).  I have gotten all the hardware working except the Wi-Fi.

After some searching I found that the chipset is an exception when it comes to supported Atheros cards, it is the AR5006EG.

I did some reading and I decided to try to use NDISwrapper for the drivers.  I ended up getting stuck with that when, even thought I blacklisted the ath_pci driver it kept showing up as an alternate driver (yes, I did restart after editing the /etc/modbrobe.d/blacklist file).  On top of that the card wouldn't show up as an interface, but the graphical NDIS wrapper configuration thing showed that the hardware was present for the driver I loaded.

I did some more research and decided to try using the madwifi drivers (after uninstalling the NDISwrapper driver and associated packages).

I found this post: [http://ubuntuforums.org/showthread.php?t=212600&page=2](http://ubuntuforums.org/showthread.php?t=212600&page=2)

It has a walkthrough for setting up the madwifi driver.  I got as far as the sudo ifconfig ath0 up command, where it reports that the interface does not exist (same or similar problem as with NDISwrapper).

iwconfig gives the following results:

lo        no wireless extensions.

eth0      no wireless extensions.

The restricted device manager detects the device and offers to install drivers (ath_pci) for it, but they do not work.  I think I read somewhere where you have to uninstall the restricted drivers manager for this to work, the problem is is that I am using it for my video driver, too (I have an ATI Mobility Radeon X1100).

Am I on the right track?  Could somebody help me get this working?  I would really appreciate it, thanks.

---

### Post by dmizer on 2007-10-19
first of all, when you look at ndiswrapper and it says that ath_pci is an alternate driver because it's just being friendly and trying to tell you that you have another option other than ndiswrapper to get your card working.  it's not telling you that ath_pci is installed.

okay ... let's go back to ndiswrapper.  but we'll use the command line because it tells us (and/or me) more.

blacklist these three modules by adding them to /etc/modprobe.d/blacklist (as root):
```
blacklist ath_pci
blacklist ath_rate_sample
blacklist new_ath_pci
```
then, go to: system > administration > restricted drivers
and uncheck the atheros driver.

reboot.

now i need some information about ndiswrapper.  please post the output of the following (while the card is installed):
```
ndiswrapper -l
lsmod | grep ndiswrapper
```

also, what drivers did you use for the card?

---

### Post by leovA on 2007-10-19
ive got a simelair problem, ive also got a atheros chip in my acer 5610z laptop, so i installed ndiswrapper black listed ath_pci and used the correct drivers.

now ndiswrapper says hardware present: yes

but when i click on configure network, only my wired network is there... :confused:

btw when i use ndiswrapper -l

it returns:

```
net5211 : driver installed
device (168c:001C) present (alternate driver: ath_pci)
```

lsmod | grep ndiswrapper doesnt do anything

---

### Post by leovA on 2007-10-19
anyone? i really need this to work :P

---

### Post by dmizer on 2007-10-19
> **leovA said:**
> 
lsmod | grep ndiswrapper doesnt do anything

try this command:
```
lsmod | grep ath
```

---

### Post by leovA on 2007-10-19
Thank You for the reply,

lsmod | grep ath also returns nothing

my wifi chip is detected by ubuntu hardware info, and ndis says the driver is correct and working, but it doesnt show in the network manager, that only shows my modem and my wired broadcom chip :confused:

---

### Post by souta95 on 2007-10-19
Ok, I will go back to ndiswrapper, I will post the results when I get to that point.

I am using windoes XP drivers from Acer, but my laptop shipped with Vista on it (I am dual-booting, also)

---

### Post by souta95 on 2007-10-19
ndiswrapper -l gives the following:

> net5211 : driver installed
        device (168C:001C) present (alternate driver: ath)pci)

lsmod | grep ndiswrapper, and lsmod | grep ath return nothing

Following a tutorial I found for ndiswrapper I did a sudo depmod -a and a sudo modprobe ndiswrapper.

now lsmod | grep ndiswrapper returns:
> ndiswrapper   185240   0
usbcore   138632  4 ndiswrapper,ehci_hcd,ohci_hcd

lsmod | grep ath still returns nothing

---

### Post by souta95 on 2007-10-19
following on in the tutorial it says to do a ifconfig and a iwconfig

these return the following:

ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 00:16:36:FC:87:9E  
          inet addr:192.168.11.105  Bcast:192.168.11.255  Mask:255.255.255.0
          inet6 addr: fe80::216:36ff:fefc:879e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:720 errors:0 dropped:0 overruns:0 frame:0
          TX packets:543 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:910614 (889.2 KB)  TX bytes:53923 (52.6 KB)
          Interrupt:20 Base address:0xec00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

iwconfig:
```
lo        no wireless extensions.

eth0      no wireless extensions.

```

It says that if the device does not appear as in interface the driver isn't working.

I almost forgot, sorry, the tutorial is here:  [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by dr_cerebro on 2007-10-20
Exactly the same problem here, with an Acer Aspire 5050-4872 using Ubuntu 7.10 x86_64

iwconfig:

```

arturo@Frankenstein:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.


```

ifconfig:

```

arturo@Frankenstein:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1B:24:4C:9B:19  
          inet addr:192.168.1.64  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:24ff:fe4c:9b19/64 Scope:Link
          UP DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Metric:1
          RX packets:2755 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2069 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:2137393 (2.0 MB)  TX bytes:340992 (333.0 KB)
          Interrupt:20 Base address:0x8c00 

lo        Link encap:Bucle local  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK CORRIENDO  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


```

lspci:

```

arturo@Frankenstein:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:07.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 IDE interface: ATI Technologies Inc 4379 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP]
02:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)
08:01.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
08:01.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
08:01.2 Generic system peripheral [0805]: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
08:01.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc: (rev 01)
08:01.4 FLASH memory: ENE Technology Inc SD/MMC Card Reader Controller (rev 01)
08:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

```

dmesg:

```

[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] Entering add_active_range(0, 0, 157) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 114320) 1 entries of 3200 used
[    0.000000] end_pfn_map = 1048576
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP signature @ 0xFFFF8100000F8A30 checksum 0
[    0.000000] ACPI: RSDP 000F8A30, 0014 (r0 PTLTD )
[    0.000000] ACPI: RSDT 1BE92D4C, 0038 (r1 PTLTD    RSDT    6040000  LTP        0)
[    0.000000] ACPI: FACP 1BE99DAC, 0074 (r1 ATI    Bowfin    6040000 ATI     F4240)
[    0.000000] ACPI: DSDT 1BE92D84, 7028 (r1    ATI    SB460  6040000 MSFT  2000002)
[    0.000000] ACPI: FACS 1BE9AFC0, 0040
[    0.000000] ACPI: SSDT 1BE99E20, 0136 (r1 PTLTD  POWERNOW  6040000  LTP        1)
[    0.000000] ACPI: APIC 1BE99F56, 0046 (r1 PTLTD       APIC    6040000  LTP        0)
[    0.000000] ACPI: MCFG 1BE99F9C, 003C (r1 PTLTD    MCFG    6040000  LTP        0)
[    0.000000] ACPI: BOOT 1BE99FD8, 0028 (r1 PTLTD  $SBFTBL$  6040000  LTP        1)
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000001be90000
[    0.000000] Entering add_active_range(0, 0, 157) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 114320) 1 entries of 3200 used
[    0.000000] Bootmem setup node 0 0000000000000000-000000001be90000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA32        4096 ->  1048576
[    0.000000]   Normal    1048576 ->  1048576
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0:        0 ->      157
[    0.000000]     0:      256 ->   114320
[    0.000000] On node 0 totalpages: 114221
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 1125 pages reserved
[    0.000000]   DMA zone: 2816 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 1506 pages used for memmap
[    0.000000]   DMA32 zone: 108718 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000] ATI board detected. Disabling timer routing over 8254.
[    0.000000] ACPI: PM-Timer IO Port: 0x8008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Setting APIC routing to flat
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] swsusp: Registered nosave memory region: 000000000009d000 - 000000000009e000
[    0.000000] swsusp: Registered nosave memory region: 000000000009e000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000d0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000d0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:c0000000)
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] PERCPU: Allocating 34696 bytes of per cpu data
[    0.000000] Built 1 zonelists.  Total pages: 111534
[    0.000000] Kernel command line: root=UUID=95b447b0-347a-4d5f-af2b-838339274254 ro quiet splash locale=es_ES
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 16384 bytes)
[   11.943346] time.c: Detected 2200.080 MHz processor.
[   11.944201] Console: colour VGA+ 80x25
[   11.944217] Checking aperture...
[   11.944220] CPU 0: aperture @ 1998000000 size 32 MB
[   11.944222] Aperture too small (32 MB)
[   11.955792] No AGP bridge found
[   11.961014] Memory: 438280k/457280k available (2274k kernel code, 18604k reserved, 1181k data, 296k init)
[   11.961064] SLUB: Genslabs=23, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   12.037256] Calibrating delay using timer specific routine.. 4404.48 BogoMIPS (lpj=8808965)
[   12.037288] Security Framework v1.0.0 initialized
[   12.037296] SELinux:  Disabled at boot.
[   12.037347] Dentry cache hash table entries: 65536 (order: 7, 524288 bytes)
[   12.037717] Inode-cache hash table entries: 32768 (order: 6, 262144 bytes)
[   12.037907] Mount-cache hash table entries: 256
[   12.038042] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   12.038044] CPU: L2 Cache: 512K (64 bytes/line)
[   12.038047] CPU 0/0 -> Node 0
[   12.038067] SMP alternatives: switching to UP code
[   12.038235] Freeing SMP alternatives: 24k freed
[   12.038618] Early unpacking initramfs... done
[   12.320125] ACPI: Core revision 20070126
[   12.320192] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   12.833990] Using local APIC timer interrupts.
[   12.879403] result 12500457
[   12.879405] Detected 12.500 MHz APIC timer.
[   12.880510] Brought up 1 CPUs
[   12.880705] NET: Registered protocol family 16
[   12.880783] ACPI: bus type pci registered
[   12.880794] PCI: Using configuration type 1
[   12.881523] ACPI: EC: Look up EC in DSDT
[   12.882429] ACPI: EC: GPE=0x14, ports=0x66, 0x62
[   12.906337] ACPI Error (psargs-0355): [\_SB_.PHSR] Namespace lookup failure, AE_NOT_FOUND
[   12.906343] ACPI Error (psparse-0551): Method parse/execution failed [\_SB_.PCI0.LPC0.EC0_._REG] (Node ffff81001a3159e0), AE_NOT_FOUND
[   12.907705] ACPI: System BIOS is requesting _OSI(Linux)
[   12.907707] ACPI: Please test with "acpi_osi=!Linux"
[   12.907708] Please send dmidecode to linux-acpi@vger.kernel.org
[   12.907963] ACPI: Interpreter enabled
[   12.907967] ACPI: (supports S0 S3 S4 S5)
[   12.907979] ACPI: Using IOAPIC for interrupt routing
[   12.911653] ACPI: EC: GPE=0x14, ports=0x66, 0x62
[   12.911698] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   12.911704] PCI: Probing PCI hardware (bus 00)
[   12.913377] PCI: Transparent bridge - 0000:00:14.4
[   12.913481] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   12.913632] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB4_._PRT]
[   12.913730] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB5_._PRT]
[   12.913827] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB6_._PRT]
[   12.913925] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB7_._PRT]
[   12.914039] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[   12.914149] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[   12.916692] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 11) *0, disabled.
[   12.916799] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 11) *0, disabled.
[   12.916903] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 11) *0, disabled.
[   12.917007] ACPI: PCI Interrupt Link [LNKD] (IRQs 10 11) *0, disabled.
[   12.917111] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 11) *0, disabled.
[   12.917218] ACPI: PCI Interrupt Link [LNKF] (IRQs 10 11) *0, disabled.
[   12.917322] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11) *0, disabled.
[   12.917426] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 11) *0, disabled.
[   12.917530] ACPI: PCI Interrupt Link [LNKU] (IRQs 3 4 5 7) *0, disabled.
[   12.917597] Linux Plug and Play Support v0.97 (c) Adam Belay
[   12.917609] pnp: PnP ACPI init
[   12.917617] ACPI: bus type pnp registered
[   12.919361] pnp: PnP ACPI: found 10 devices
[   12.919363] ACPI: ACPI bus type pnp unregistered
[   12.919418] PCI: Using ACPI for IRQ routing
[   12.919420] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   12.919427] PCI: Cannot allocate resource region 7 of bridge 0000:00:05.0
[   12.919471] PCI: Cannot allocate resource region 8 of bridge 0000:00:05.0
[   12.919509] PCI: Cannot allocate resource region 7 of bridge 0000:00:06.0
[   12.919546] PCI: Cannot allocate resource region 8 of bridge 0000:00:06.0
[   12.919584] PCI: Cannot allocate resource region 7 of bridge 0000:00:07.0
[   12.919622] PCI: Cannot allocate resource region 8 of bridge 0000:00:07.0
[   12.919764] NET: Registered protocol family 8
[   12.919766] NET: Registered protocol family 20
[   12.919871] pnp: 00:01: iomem range 0xe0000000-0xefffffff could not be reserved
[   12.919874] pnp: 00:01: iomem range 0xfec00000-0xfec00fff could not be reserved
[   12.919877] pnp: 00:01: iomem range 0xfee00000-0xfee00fff could not be reserved
[   12.919884] pnp: 00:08: ioport range 0x1080-0x1080 has been reserved
[   12.919887] pnp: 00:08: ioport range 0x220-0x22f has been reserved
[   12.919891] pnp: 00:09: iomem range 0xe0000-0xfffff could not be reserved
[   12.919894] pnp: 00:09: iomem range 0xfff00000-0xffffffff could not be reserved
[   12.919896] pnp: 00:09: iomem range 0x0-0xfff could not be reserved
[   12.920138] PCI: Bridge: 0000:00:01.0
[   12.920140]   IO window: 9000-9fff
[   12.920144]   MEM window: d0100000-d01fffff
[   12.920146]   PREFETCH window: d4000000-d7ffffff
[   12.920149] PCI: Bridge: 0000:00:04.0
[   12.920150]   IO window: disabled.
[   12.920153]   MEM window: d0200000-d02fffff
[   12.920155]   PREFETCH window: disabled.
[   12.920157] PCI: Bridge: 0000:00:05.0
[   12.920158]   IO window: disabled.
[   12.920160]   MEM window: disabled.
[   12.920162]   PREFETCH window: disabled.
[   12.920164] PCI: Bridge: 0000:00:06.0
[   12.920165]   IO window: disabled.
[   12.920167]   MEM window: disabled.
[   12.920169]   PREFETCH window: disabled.
[   12.920171] PCI: Bridge: 0000:00:07.0
[   12.920172]   IO window: disabled.
[   12.920174]   MEM window: disabled.
[   12.920176]   PREFETCH window: disabled.
[   12.920187] PCI: Bus 9, cardbus bridge: 0000:08:01.0
[   12.920189]   IO window: 0000a400-0000a4ff
[   12.920195]   IO window: 0000a800-0000a8ff
[   12.920201]   PREFETCH window: 30000000-33ffffff
[   12.920207]   MEM window: 38000000-3bffffff
[   12.920212] PCI: Bridge: 0000:00:14.4
[   12.920215]   IO window: a000-afff
[   12.920221]   MEM window: d0300000-d03fffff
[   12.920226]   PREFETCH window: 30000000-33ffffff
[   12.920241] PCI: Enabling device 0000:00:04.0 (0000 -> 0002)
[   12.920245] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   12.920251] PCI: Setting latency timer of device 0000:00:05.0 to 64
[   12.920257] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   12.920263] PCI: Setting latency timer of device 0000:00:07.0 to 64
[   12.920285] PCI: Enabling device 0000:08:01.0 (0000 -> 0003)
[   12.920294] ACPI: PCI Interrupt 0000:08:01.0[A] -> GSI 23 (level, low) -> IRQ 23
[   12.920349] NET: Registered protocol family 2
[   12.920432] Time: tsc clocksource has been installed.
[   12.948454] IP route cache hash table entries: 4096 (order: 3, 32768 bytes)
[   12.948519] TCP established hash table entries: 16384 (order: 6, 393216 bytes)
[   12.948736] TCP bind hash table entries: 16384 (order: 6, 262144 bytes)
[   12.948904] TCP: Hash tables configured (established 16384 bind 16384)
[   12.948906] TCP reno registered
[   12.960510] checking if image is initramfs... it is
[   13.504301] Freeing initrd memory: 7749k freed
[   13.509581] Simple Boot Flag at 0x36 set to 0x1
[   13.509931] audit: initializing netlink socket (disabled)
[   13.509942] audit(1192851761.060:1): initialized
[   13.511573] VFS: Disk quotas dquot_6.5.1
[   13.511617] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   13.511701] io scheduler noop registered
[   13.511702] io scheduler anticipatory registered
[   13.511704] io scheduler deadline registered
[   13.511782] io scheduler cfq registered (default)
[   13.511788] PCI: MSI quirk detected. MSI deactivated.
[   13.512321] Boot video device is 0000:01:05.0
[   13.512460] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   13.512477] assign_interrupt_mode Found MSI capability
[   13.512481] Allocate Port Service[0000:00:04.0:pcie00]
[   13.512514] Allocate Port Service[0000:00:04.0:pcie02]
[   13.512562] PCI: Setting latency timer of device 0000:00:05.0 to 64
[   13.512579] assign_interrupt_mode Found MSI capability
[   13.512581] Allocate Port Service[0000:00:05.0:pcie00]
[   13.512627] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   13.512644] assign_interrupt_mode Found MSI capability
[   13.512646] Allocate Port Service[0000:00:06.0:pcie00]
[   13.512691] PCI: Setting latency timer of device 0000:00:07.0 to 64
[   13.512708] assign_interrupt_mode Found MSI capability
[   13.512710] Allocate Port Service[0000:00:07.0:pcie00]
[   13.532185] Real Time Clock Driver v1.12ac
[   13.532264] Linux agpgart interface v0.102 (c) Dave Jones
[   13.532267] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   13.533165] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   13.533330] input: Macintosh mouse button emulation as /class/input/input0
[   13.533386] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[   13.536622] i8042.c: Detected active multiplexing controller, rev 1.1.
[   13.538611] serio: i8042 KBD port at 0x60,0x64 irq 1
[   13.538616] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   13.538618] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   13.538620] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   13.538623] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   13.538869] mice: PS/2 mouse device common for all mice
[   13.538979] TCP cubic registered
[   13.539043] NET: Registered protocol family 1
[   13.539250] /build/buildd/linux-source-2.6.22-2.6.22/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   13.539257] Freeing unused kernel memory: 296k freed
[   13.603866] input: AT Translated Set 2 keyboard as /class/input/input1
[   14.700223] AppArmor: AppArmor initialized<5>audit(1192851762.252:2):  type=1505 info="AppArmor initialized" pid=1227
[   14.717007] fuse init (API version 7.8)
[   14.817484] Failure registering capabilities with primary security module.
[   15.020898] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   15.521958] ACPI: EC: acpi_ec_wait timeout, status = 255, expect_event = 2
[   15.521962] ACPI: EC: input buffer is not empty, aborting transaction
[   15.521967] ACPI Exception (evregion-0420): AE_TIME, Returned by Handler for [EmbeddedControl] [20070126]
[   15.521973] ACPI Exception (dswexec-0462): AE_TIME, While resolving operands for [OpcodeName unavailable] [20070126]
[   15.521979] ACPI Error (psparse-0551): Method parse/execution failed [\_TZ_.THRM._TMP] (Node ffff81001a316340), AE_TIME
[   26.293978] SCSI subsystem initialized
[   26.298336] libata version 2.21 loaded.
[   26.301009] sata_sil 0000:00:12.0: version 2.2
[   26.301049] PCI: Enabling device 0000:00:12.0 (0005 -> 0007)
[   26.301058] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 22 (level, low) -> IRQ 22
[   26.301287] scsi0 : sata_sil
[   26.301332] scsi1 : sata_sil
[   26.301589] ata1: SATA max UDMA/100 cmd 0xffffc20000190080 ctl 0xffffc2000019008a bmdma 0xffffc20000190000 irq 22
[   26.301595] ata2: SATA max UDMA/100 cmd 0xffffc200001900c0 ctl 0xffffc200001900ca bmdma 0xffffc20000190008 irq 22
[   26.309133] usbcore: registered new interface driver usbfs
[   26.309155] usbcore: registered new interface driver hub
[   26.309174] usbcore: registered new device driver usb
[   26.309804] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   26.434932] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   26.434938] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   26.716124] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   26.771231] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[   26.779847] ata1.00: ATA-7: Hitachi HTS541612J9SA00, SBDOC70P, max UDMA/100
[   26.779850] ata1.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   26.799822] ata1.00: configured for UDMA/100
[   27.114886] ata2: SATA link down (SStatus 0 SControl 310)
[   27.118872] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54161 SBDO PQ: 0 ANSI: 5
[   27.119046] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> IRQ 19
[   27.119169] ohci_hcd 0000:00:13.0: OHCI Host Controller
[   27.119327] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[   27.119356] ohci_hcd 0000:00:13.0: irq 19, io mem 0xd0005000
[   27.178931] usb usb1: configuration #1 chosen from 1 choice
[   27.178955] hub 1-0:1.0: USB hub found
[   27.178970] hub 1-0:1.0: 4 ports detected
[   27.282833] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 19 (level, low) -> IRQ 19
[   27.282953] ohci_hcd 0000:00:13.1: OHCI Host Controller
[   27.283012] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
[   27.283033] ohci_hcd 0000:00:13.1: irq 19, io mem 0xd0006000
[   27.310717] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[   27.311034] sd 0:0:0:0: [sda] Write Protect is off
[   27.311037] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   27.315012] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   27.319019] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[   27.322681] sd 0:0:0:0: [sda] Write Protect is off
[   27.322685] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   27.326667] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   27.326672]  sda:<6>usb usb2: configuration #1 chosen from 1 choice
[   27.342800] hub 2-0:1.0: USB hub found
[   27.342813] hub 2-0:1.0: 4 ports detected
[   27.446771] ACPI: PCI Interrupt 0000:00:13.2[A] -> GSI 19 (level, low) -> IRQ 19
[   27.446902] ehci_hcd 0000:00:13.2: EHCI Host Controller
[   27.446954] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
[   27.447009] ehci_hcd 0000:00:13.2: irq 19, io mem 0xd0007000
[   27.586425] usb 1-1: new low speed USB device using ohci_hcd and address 2
[   27.586446] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   27.586570] usb usb3: configuration #1 chosen from 1 choice
[   27.586594] hub 3-0:1.0: USB hub found
[   27.586600] hub 3-0:1.0: 8 ports detected
[   27.690512] ATIIXP: IDE controller at PCI slot 0000:00:14.1
[   27.690534] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 16
[   27.690545] ATIIXP: chipset revision 128
[   27.690547] ATIIXP: not 100% native mode: will probe irqs later
[   27.690556]     ide0: BM-DMA at 0x8420-0x8427, BIOS settings: hda:DMA, hdb:pio
[   27.690570] ATIIXP: simplex device: DMA disabled
[   27.690571] ide1: ATIIXP Bus-Master DMA disabled (BIOS)
[   27.690575] Probing IDE interface ide0...
[   27.747522]  sda1 sda2 < sda5 >
[   27.777199] sd 0:0:0:0: [sda] Attached SCSI disk
[   27.779988] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   28.329710] usb 3-3: new high speed USB device using ehci_hcd and address 3
[   28.430035] hda: Optiarc DVD RW AD-7560A, ATAPI CD/DVD-ROM drive
[   28.719540] usb 3-3: configuration #1 chosen from 1 choice
[   28.810037] Attempting manual resume
[   28.810041] swsusp: Resume From Partition 8:5
[   28.810042] PM: Checking swsusp image.
[   28.909151] PM: Resume from disk failed.
[   29.033041] usb 1-1: new low speed USB device using ohci_hcd and address 3
[   29.104982] hda: selected mode 0x42
[   29.105440] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   29.106175] Probing IDE interface ide1...
[   29.231883] usb 1-1: configuration #1 chosen from 1 choice
[   29.242923] usbcore: registered new interface driver hiddev
[   29.247121] input: PS/2+USB Mouse as /class/input/input2
[   29.247252] input: USB HID v1.11 Mouse [PS/2+USB Mouse] on usb-0000:00:13.0-1
[   29.247265] usbcore: registered new interface driver usbhid
[   29.247268] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   29.669370] 8139cp 0000:08:02.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[   29.669376] 8139cp 0000:08:02.0: Try the "8139too" driver instead.
[   29.670758] 8139too Fast Ethernet driver 0.9.28
[   29.670815] ACPI: PCI Interrupt 0000:08:02.0[A] -> GSI 20 (level, low) -> IRQ 20
[   29.671580] eth0: RealTek RTL8139 at 0xffffc20000198c00, 00:1b:24:4c:9b:19, IRQ 20
[   29.671584] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[   29.680589] hda: ATAPI 24X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(33)
[   29.680598] Uniform CD-ROM driver Revision: 3.20
[   30.164002] kjournald starting.  Commit interval 5 seconds
[   30.164013] EXT3-fs: mounted filesystem with ordered data mode.
[  119.304328] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[  119.308629] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[  119.653100] ath_hal: module license 'Proprietary' taints kernel.
[  119.653706] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[  119.847700] wlan: 0.8.4.2 (0.9.3.2)
[  119.897329] ath_pci: 0.9.4.5 (0.9.3.2)
[  119.897383] PCI: Enabling device 0000:02:00.0 (0000 -> 0002)
[  119.897389] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[  119.897402] PCI: Setting latency timer of device 0000:02:00.0 to 64
[  119.921725] wifi%d: unable to attach hardware: 'Hardware revision not supported' (HAL status 13)
[  119.921735] ACPI: PCI interrupt for device 0000:02:00.0 disabled
[  120.498995] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
[  120.742988] Linux video capture interface: v2.00
[  120.983807] Yenta: CardBus bridge found at 0000:08:01.0 [1025:010f]
[  120.983837] Yenta: Using CSCINT to route CSC interrupts to PCI
[  120.983839] Yenta: Routing CardBus interrupts to PCI
[  120.983845] Yenta TI: socket 0000:08:01.0, mfunc 0x00001202, devctl 0x44
[  120.992354] uvcvideo: Found UVC 1.00 device USB2.0 Camera (5986:0100)
[  121.179666] usbcore: registered new interface driver uvcvideo
[  121.179671] USB Video Class driver (v0.1.0)
[  121.217682] Yenta: ISA IRQ mask 0x0cf8, PCI irq 23
[  121.217687] Socket status: 30000006
[  121.217690] Yenta: Raising subordinate bus# of parent bus (#08) from #09 to #0c
[  121.217696] pcmcia: parent PCI bridge I/O window: 0xa000 - 0xafff
[  121.217699] pcmcia: parent PCI bridge Memory window: 0xd0300000 - 0xd03fffff
[  121.217702] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x33ffffff
[  121.270385] sdhci: Secure Digital Host Controller Interface driver
[  121.270389] sdhci: Copyright(c) Pierre Ossman
[  121.270433] sdhci: SDHCI controller found at 0000:08:01.2 [1524:0550] (rev 1)
[  121.270458] ACPI: PCI Interrupt 0000:08:01.2[B] -> GSI 22 (level, low) -> IRQ 22
[  121.270904] mmc0: SDHCI at 0xd0301400 irq 22 DMA
[  121.275967] sdhci: SDHCI controller found at 0000:08:01.4 [1524:0551] (rev 1)
[  121.275987] PCI: Enabling device 0000:08:01.4 (0000 -> 0002)
[  121.275994] ACPI: PCI Interrupt 0000:08:01.4[B] -> GSI 22 (level, low) -> IRQ 22
[  121.276173] mmc1: SDHCI at 0xd0301100 irq 22 PIO
[  121.543661] input: PC Speaker as /class/input/input3
[  121.928910] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x1280b1, caps: 0xa04713/0x204000
[  121.972648] input: SynPS/2 Synaptics TouchPad as /class/input/input4
[  122.178786] ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ 16
[  124.142415] lp: driver loaded but no devices found
[  124.742677] Adding 1301224k swap on /dev/sda5.  Priority:-1 extents:1 across:1301224k
[  126.475197] EXT3 FS on sda1, internal journal
[  132.297430] ACPI: Battery Slot [BAT1] (battery absent)
[  134.050690] No dock devices found.
[  134.719790] input: Power Button (FF) as /class/input/input5
[  134.723504] ACPI: Power Button (FF) [PWRF]
[  134.744123] input: Power Button (CM) as /class/input/input6
[  134.747808] ACPI: Power Button (CM) [PWRB]
[  134.768502] input: Lid Switch as /class/input/input7
[  134.772192] ACPI: Lid Switch [LID]
[  134.792664] input: Sleep Button (CM) as /class/input/input8
[  134.796347] ACPI: Sleep Button (CM) [SLPB]
[  135.615120] ACPI: EC: acpi_ec_wait timeout, status = 255, expect_event = 2
[  135.615124] ACPI: EC: input buffer is not empty, aborting transaction
[  135.615129] ACPI Exception (evregion-0420): AE_TIME, Returned by Handler for [EmbeddedControl] [20070126]
[  135.615135] ACPI Exception (dswexec-0462): AE_TIME, While resolving operands for [OpcodeName unavailable] [20070126]
[  135.615140] ACPI Error (psparse-0551): Method parse/execution failed [\_SB_.ACAD._PSR] (Node ffff81001a318fc0), AE_TIME
[  135.615176] ACPI Exception (ac-0095): AE_TIME, Error reading AC Adapter state [20070126]
[  137.798957] powernow-k8: Found 1 AMD Turion(tm) 64 Mobile Technology MK-38 processors (version 2.00.00)
[  137.798997] powernow-k8:    0 : fid 0xe (2200 MHz), vid 0xb
[  137.799000] powernow-k8:    1 : fid 0xc (2000 MHz), vid 0xd
[  137.799002] powernow-k8:    2 : fid 0xa (1800 MHz), vid 0xf
[  137.799004] powernow-k8:    3 : fid 0x8 (1600 MHz), vid 0x11
[  137.799006] powernow-k8:    4 : fid 0x0 (800 MHz), vid 0x18
[  145.968994] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[  146.210093] ppdev: user-space parallel port driver
[  147.676406] audit(1192851896.375:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5136 profile="/usr/sbin/cupsd"
[  149.520499] Failure registering capabilities with primary security module.
[  151.580487] Bluetooth: Core ver 2.11
[  151.580586] NET: Registered protocol family 31
[  151.580589] Bluetooth: HCI device and connection manager initialized
[  151.580592] Bluetooth: HCI socket layer initialized
[  151.621214] Bluetooth: L2CAP ver 2.8
[  151.621218] Bluetooth: L2CAP socket layer initialized
[  151.625846] Bluetooth: RFCOMM socket layer initialized
[  151.625921] Bluetooth: RFCOMM TTY layer initialized
[  151.625923] Bluetooth: RFCOMM ver 1.8
[  154.934765] NET: Registered protocol family 17
[  159.203443] NET: Registered protocol family 10
[  159.203585] lo: Disabled Privacy Extensions
[  162.846229] Marking TSC unstable due to cpufreq changes
[  162.847042] Time: acpi_pm clocksource has been installed.
[  163.170167] [fglrx] Maximum main memory to use for locked dma buffers: 369 MBytes.
[  163.170395] [fglrx] module loaded - fglrx 8.37.6 [May 25 2007] on minor 0
[  163.205922] ACPI: PCI Interrupt 0000:01:05.0[A] -> GSI 17 (level, low) -> IRQ 17
[  165.204536] [fglrx] total      GART = 130023424
[  165.204542] [fglrx] free       GART = 114032640
[  165.204545] [fglrx] max single GART = 114032640
[  165.204547] [fglrx] total      LFB  = 67108864
[  165.204549] [fglrx] free       LFB  = 52719616
[  165.204551] [fglrx] max single LFB  = 52719616
[  165.204552] [fglrx] total      Inv  = 0
[  165.204553] [fglrx] free       Inv  = 0
[  165.204555] [fglrx] max single Inv  = 0
[  165.204556] [fglrx] total      TIM  = 0
[  167.134833] eth0: no IPv6 routers present
[  168.505387] hda-intel: Invalid position buffer, using LPIB read method instead.

```

lsmod | grep ath:

```

arturo@Frankenstein:~$ lsmod | grep ath
ath_pci               105392  0 
wlan                  225736  1 ath_pci
ath_hal               219888  1 ath_pci

```

Additional information: This is an AMD Turion 64 laptop, but with Ubuntu 7.04, the version x86_86 was never able to initialize the kernel.  I had to install the version i386.  In order to make wlan0 "visible" I had to install acer_acpi 0.8.2, and then installed the driver with ndiswrapper and wifi worked fine.

Does anyone know how to fix this?

---

### Post by dr_cerebro on 2007-10-20
I checked bug launchpad and this is not reported.

---

### Post by souta95 on 2007-10-20
> **dr_cerebro said:**
> ...
In order to make wlan0 "visible" I had to install acer_acpi 0.8.2, and then installed the driver with ndiswrapper and wifi worked fine.
...

You may be on to something, I'm trying to install acer_acpi now, but I am having trouble.

I found this tutorial: [http://ubuntuforums.org/showthread.php?t=224350](http://ubuntuforums.org/showthread.php?t=224350)

I get as far as the ```
su
modprobe acer_acpi
chmod 777 /proc/acpi/acer/wireless
echo "enabled: 1">/proc/acpi/acer/wireless
exit
```

or, more specifically the echo "enabled: 1">/proc/acpi/acer/wireless part.  (I did set a password for root with sudo passwd root)

If I try to edit the file with gedit it keeps saying it has changed before I can save it.  I also tried echo 'enabled: 1' | tee -a /proc/acpi/acer/wireless, but I don't think I structured the command correctly.

I found that the current version of it is now in a repository at its new homepage here:  [http://code.google.com/p/aceracpi/](http://code.google.com/p/aceracpi/), so I just used Synaptic to install it.

Any thought on how to get acer_acpi working?

BTW, I forgot to say, I am using 32-bit Linux (because of Firefox related stuff), but I have a 64-bit processor (Turion 64)

---

### Post by dmizer on 2007-10-20
@souta95:

okay ... add 'ndiswrapper' to the end of /etc/modules like so:
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

ndiswrapper
```

also, disable ipv6 using the following method:
[https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4?](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4?)

reboot your computer and see if your wireless card appears in system > adminstration > networking.

---

### Post by leovA on 2007-10-20
thank you for all the reply's i already tought that it could be something with acer_acpi, i have the lastest version installed but when i typed ```
echo "enabled: 1">/proc/acpi/acer/wireless
``` in the terminal it said that there was an error with enabled like an invalid option, icant remember exactly, ill check it when i come home from work

edit:

```
echo "enabled: 1">/proc/acpi/acer/wireless
```

returns:

```
-bash: echo: write error: Invalid argument enabled: 1
```

---

### Post by dr_cerebro on 2007-10-20
Well, I asked in many forums, until they gave me the answer, but in the published threads it is not corrected.

I followed the steps in [this]("http://ubuntuforums.org/showthread.php?t=224349&highlight=acer_acpi") howto and made several changes in order to make it work.

I had to install acer_acpi-0.8.2 because, in other versions, something just do not work... a path to something (I can't remember what), but, here is the step by step of acer_acpi, but first, I want to make a statement: I WILL NEVER BUY AN ACER LAPTOP AGAIN. *"Terribilis est machina ista"*.  At least in Linux.

I'm just a newbie, so, do not expect me to explain each step, and by the way, I do not speak English very well, so...

Let's start:

First, I deactivated Atheros from Restricted Modules.

Then, restarted and open a terminal

```
sudo aptitude update
```

Then:

```
sudo aptitude install build-essential linux-headers-$(uname -r)
```

You make a directory named download for example:

```
mkdir ~/download
```

You enter to that directory:

```
cd ~/download
```

Download the acer_acpi tar file:

```
wget http://aceracpi.googlecode.com/files/acer_acpi-0.8.2.tar.bz2
```

Decompress:

```
tar jxvf acer_acpi-0.8.2.tar.bz2
```

Enter to the created directory:

```
cd acer_acpi-0.8.2
```

Then:

```
make
```

Then:

```
sudo make install
```

Then:

```
cd ../..
```

Then:

```
sudo modprobe acer_acpi
```

Then:

```
sudo chmod 777 /proc/acpi/acer/wireless
```

Then:

```
sudo echo 1 > /proc/acpi/acer/wireless
```

Then:

```
dmesg | grep acer_acpi
```

Then:

```
sudo gedit /etc/init.d/acer_acpi_wireless_enable
```

Then, just copy and paste the next script, save and close gedit:

```

#!/bin/sh

case "$1" in

        start|"")

                modprobe acer_acpi

                chmod 777 /proc/acpi/acer/wireless

                echo 1 > /proc/acpi/acer/wireless

                ;;

        stop)

                echo 0 > /proc/acpi/acer/wireless

                modprobe -r acer_acpi

                ;;

esac

```

Then:

```
sudo chmod 755 /etc/init.d/acer_acpi_wireless_enable
```

Then:

```
sudo update-rc.d acer_acpi_wireless_enable start 39 S . start 34 0 6 .
```

Then, just verify it it worked:

```
ls /etc/rcS.d/S39acer_acpi_wireless_enable
```

```
ls /etc/rc0.d/S34acer_acpi_wireless_enable
```

```
ls /etc/rc6.d/S34acer_acpi_wireless_enable
```

You can find the original post here: [http://ubuntuforums.org/showthread.php?t=224349&highlight=acer_acpi](http://ubuntuforums.org/showthread.php?t=224349&highlight=acer_acpi)

Restart the computer and follow the EXACT step by step described in this howto: [http://ubuntuforums.org/showthread.php?t=512828](http://ubuntuforums.org/showthread.php?t=512828)
But, the sad thing, is than it downloads a driver for a i386 architecture, it just do not work with AMD 64.

But, as I previously said.  I could make it work as many times as possible in Ubuntu i386, but it just do not work in version x86_64.  That is why I am using this ugly yellow wire to connect my laptop to the internet, while writing this post.

---

### Post by souta95 on 2007-10-20
I have followed it and acer_acpi appears to be installed now, but it still isn't showing up in networking.

what bout this part?:
> ...
the version x86_86 was never able to initialize the kernel. I had to install the version i386
...

How would I go about doing that, or should I even try?  I think my kernel is "x86/x86_64"

Thanks you very much for the help so far, I really appreciate it!!

Update:  I installed the linux-386 kernel meta package, but still no wireless :-(

---

### Post by dr_cerebro on 2007-10-20
> **souta95 said:**
> I have followed it and acer_acpi appears to be installed now, but it still isn't showing up in networking.

what bout this part?:


How would I go about doing that, or should I even try?  I think my kernel is "x86/x86_64"

Thanks you very much for the help so far, I really appreciate it!!

Update:  I installed the linux-386 kernel meta package, but still no wireless :-(

Well, the same happened to me, if I installed version i386 everything works following the previous steps.  In Gutsy version x86_64, i installed acer_acpi and if you run dmesg you will see, acer_acpi is installed, but if you type iwconfig, you will see nothing has happened, still there is not wlan0, while in i386, after installing acer_acpi, wlan0 appears, and then you can follow the steps to install ndiswrapper and the Windows driver, and Wifi start working PERFECT.

---

### Post by souta95 on 2007-10-20
well, I am using the i386 kernel, and have reinstalled the acer_acpi for this kernel, but I still don't see an interface for the card...

I already had ndiswrapper installed.  I think I am going to try to reinstall it to see of that will do anything.

otherwise I think I am going to investigate on using my PCMCIA (PC Card) Wi-Fi adapter, it has a Marvell chipset.

---

### Post by dr_cerebro on 2007-10-20
> **souta95 said:**
> well, I am using the i386 kernel, and have reinstalled the acer_acpi for this kernel, but I still don't see an interface for the card...

I already had ndiswrapper installed.  I think I am going to try to reinstall it to see of that will do anything.

otherwise I think I am going to investigate on using my PCMCIA (PC Card) Wi-Fi adapter, it has a Marvell chipset.

That's weird, I just tried Gutsy i386 and make wireless work (I did all that in Feisty too).

---

### Post by leovA on 2007-10-20
yeey i got it working too :D

thanks for the help everybody!

---

### Post by souta95 on 2007-10-20
I went ahead and tried setting my PC card adapter up, and I got it working in about 15 minuets with ndiswrapper, so I will just use that until Linux has better support for Acer laptops and the Atheros chipset that I have.

I can't thank you people enough for the support I got, though.  Thank you.

---

### Post by dr_cerebro on 2007-10-20
Congratulations to all of you.
Mine still do not work.

---

### Post by dr_cerebro on 2007-10-21
FINALLY SOLVED... I'M WRITING THIS POST, CONNECTED WIRELESS.

This is how I did it...

I followed the steps listed in the instructions I posted in page 2 of this thread, but if I installed the driver in this post: [http://ubuntuforums.org/showthread.php?t=512828](http://ubuntuforums.org/showthread.php?t=512828) then wireless did not work because the driver in the installer IS A 32 BIT DRIVER, and I installed Gutsy in 64 BITS (x86_64), so, i made a fresh install, disable restricted drivers, installed acer_acpi, next I downloaded the XP driver from here: 

[ftp://ftp.work.acer-euro.com/notebook/aspire_5050/driver//Atheros_WLAN_XB63_Driver_5.1.1.9_XP.zip](ftp://ftp.work.acer-euro.com/notebook/aspire_5050/driver//Atheros_WLAN_XB63_Driver_5.1.1.9_XP.zip) 

extracted the directory (just double click on it and extract in your user name directory).  It would create a folder named ZR3_Atheros_XB63_5.1.1.9_XP_WHQL

Follow the instructions in this thread: [http://ubuntuforums.org/showthread.php?t=512828](http://ubuntuforums.org/showthread.php?t=512828) but stop after installing ndiswrapper

Open a terminal and type:

```

cp ~/ZR3_Atheros_XB63_5.1.1.9_XP_WHQL/XP_5.1.1.9_LED_Negative_Pole/WHQL_5-1-1-9_X64 ~/atheros-ar5007eg-installer-0.1c

```

Then, continue with the instructions, but instead of:

```
pushd atheros-ar5007eg-installer-0.1c/ar5007eg/
```

Type:

```
pushd atheros-ar5007eg-installer-0.1c/WHQL_5-1-1-9_X64/
```

And continue with the instructions.

That will install the 64 bit driver.

I hope this will be useful to someone.

---

### Post by Subbu.exe on 2007-10-22
Working Perfectly on my Acer 4710z! (Atheros AR5006EG Chipset)

I used the same .inf files used in Windows XP for ndiswrapper though.

Thanks! :)

---

### Post by gummo on 2007-10-24
Thanx to all who participated in this thread.

My atheros 5006EG is now perfectly working on my Acer 7520G.
I am using ndiswrapper, acer_acpi and the XP64 drivers on Gutsy AMD_64, for anyone who still has probs ;)

Now only the sound remains to be fixed :p

---

### Post by dr_cerebro on 2007-10-24
> **gummo said:**
> Thanx to all who participated in this thread.

My atheros 5006EG is now perfectly working on my Acer 7520G.
I am using ndiswrapper, acer_acpi and the XP64 drivers on Gutsy AMD_64, for anyone who still has probs ;)

Now only the sound remains to be fixed :p

I can help you with the sound, but I have to run now, I have to go to work... later I will post how to make sound work, maybe just surround is muted, if not, I will tell you how to make it work.

I will check this thread tonight to see if you still have problems with the sound.

---

### Post by gummo on 2007-10-25
> **dr_cerebro said:**
> I can help you with the sound, but I have to run now, I have to go to work... later I will post how to make sound work, maybe just surround is muted, if not, I will tell you how to make it work.

I will check this thread tonight to see if you still have problems with the sound.

Hi and thanx for the reply.

Following several threads on this forums i managed to install the realtek drivers, however I think the problem is I am using the 64 bit distro. The drivers seem to install fine but when I go to the volume control it still tells me "No volume control GStreamer plugin and/or devices found".

---

### Post by dr_cerebro on 2007-10-25
Maybe it would be better if you install the ALSA drivers.
Remember, once installed, you will have to set preferences to show Surround, which is unmuted by default, and you will have sound.

These are the steps:

```
sudo apt-get update
```

```
sudo apt-get install module-assistant build-essential fakeroot dh-make debhelper debconf libstdc++5 linux-headers-generic
```

```
sudo apt-get install libncurses5-dev
```

Then, go to ALSA official page: [http://www.alsa-project.org/](http://www.alsa-project.org/), and download: 

Package

* Driver * 1.0.14
* Library * 1.0.14a
* Utilities * 1.0.14
* OSS Compat. Library * 1.0.14

then:

```
mkdir ~/alsa
```

Copy these files you just downloaded to the alsa directory you just created:

```
cp ~alsa*.* ~/alsa
```

Then, it is easy, just follow the steps:

```
sudo /etc/init.d/alsa-utils stop
```

```
cd ~/alsa
```

```
tar xvf alsa-driver-1.0.14.tar.bz2
```

```
tar xvf alsa-lib-1.0.14a.tar.bz2
```

```
tar xvf alsa-utils-1.0.14.tar.bz2
```

```
tar xvf alsa-oss-1.0.14.tar.bz2
```

```
cd alsa-driver-1.0.14 
```

```
sudo ./configure --with-kernel=/usr/src/linux-headers-$(uname -r) --with-oss=yes
```

```
sudo make
```

```
sudo make install
```

```
cd ..
```

```
cd alsa-lib-1.0.14a
```

```

sudo ./configure
sudo make
sudo make install
cd ..
```

```
cd alsa-utils-1.0.14
```

```

sudo ./configure
sudo make
sudo make install
cd ..
```

```
cd alsa-oss-1.0.14
```

```

sudo ./configure
sudo make
sudo make install
cd ..
```

That's it.

If marks error, does not matter, just installing alsa-driver works perfect.

Open the volume icon on the right top of the Desktop, and in Edit--->Preferences select surround and mark it, unmute it... and enjoy your sound

Let me know if it works for you

---

### Post by muncrief on 2007-10-26
Well, after two weeks of trying I've had no success at getting my sons Acer Aspire 5100 wireless connection to work on either Ubuntu Feisty or Gutsy AMD64. It's very embarrassing, and a personal hardship since I promised if I couldn't install Ubuntu AMD64 on his laptop, with a Windows XP virtual machine for Rhapsody, in one day he could have my beautiful 17" monitor until I did.

So I've been living with his old 15" CRT monitor since then, and won't get my monitor back until some version of Linux with an XP VM is installed on his laptop (and yes, I have his tiny  laptop to work on until then).

Hey, at least I keep my word.

I've tried many proposed solutions from the plethora of Ubuntu wireless problem posts, and came upon this thread last week and have tried multiple iterations of it's instructions, keeping up with and adjusting to and trying the latest code as well as the oldest code and instructions proposed (I'm a hardware/firmware/software engineer with over two decades of experience under my belt, mostly in embedded systems, so I'm usually very proficient at debugging).

However, I've only been able to establish a wireless connection  a few times, and it was always only after initially configuring some ndis driver, but after that I could never connect again. And yes, I rebooted my router, did a clean install of Ubuntu (Feisty and Gutsy) numerous times, etc. And I've used all versions of acer_acpi from 0.8.2 to 0.10_rc3 (and curiously those before 0.9.0 always  reported a MAC address of 00:00:00:00:00:00 for his wireless device), and ndiswrapper 1.48 to 1.49rc4. I'm using 128 bit WEP, but turning it off or on doesn't seem to change anything.

And the problem is clear when I look at my routers (BEFW11S4 V3) wireless MAC address list, my sons wireless MAC is recorded as 00:00:00:00:00:00 even when using acer_acpi after 0.9.0. (acer_acpi after 0.9.0 detect the correct MAC address in System->Preferences->Hardware Information, but the router sees 00~).  I can actually shut down all of our computers, shut down the cable modem and router, power up the modem and router, and then only my sons laptop, and see 00:00:00:00:00:00 recorded in the routers wireless MAC list when I try to connect from the laptop. As I said before the only exception is occasionally connecting after initially changing the ndiswrapper driver, but even that is not reliably reproducible.

To go through everything I've tried would take many pages of description, but rest assured from disabling ipv6 to blacklisting every module having to do with Atheros, to every other randomly (but plausible) solution, nothing has worked. However, when I dual boot into Windows XP (using one of the drivers I've tried numerous times with ndiswrapper) his wireless works flawlessly.

So I'm just going to post my sons chipset ID and hope someone might have a solution. I'm actually going to have to try some other distros in the meantime (hey, I need my monitor back!), but I'm hoping someone here will have some suggestions or even a solution. I truly love Ubuntu, and want to show my son that Linux is a superior alternative to Windows.

His chipset is reported as an AR5006EG under Linux and XP, and its ID is 168C:001C (rev 01)

---

### Post by dr_cerebro on 2007-10-26
> **muncrief said:**
> Well, after two weeks of trying I've had no success at getting my sons Acer Aspire 5100 wireless connection to work on either Ubuntu Feisty or Gutsy AMD64. It's very embarrassing, and a personal hardship since I promised if I couldn't install Ubuntu AMD64 on his laptop, with a Windows XP virtual machine for Rhapsody, in one day he could have my beautiful 17" monitor until I did.

So I've been living with his old 15" CRT monitor since then, and won't get my monitor back until some version of Linux with an XP VM is installed on his laptop (and yes, I have his tiny  laptop to work on until then).

Hey, at least I keep my word.

I've tried many proposed solutions from the plethora of Ubuntu wireless problem posts, and came upon this thread last week and have tried multiple iterations of it's instructions, keeping up with and adjusting to and trying the latest code as well as the oldest code and instructions proposed (I'm a hardware/firmware/software engineer with over two decades of experience under my belt, mostly in embedded systems, so I'm usually very proficient at debugging).

However, I've only been able to establish a wireless connection  a few times, and it was always only after initially configuring some ndis driver, but after that I could never connect again. And yes, I rebooted my router, did a clean install of Ubuntu (Feisty and Gutsy) numerous times, etc. And I've used all versions of acer_acpi from 0.8.2 to 0.10_rc3 (and curiously those before 0.9.0 always  reported a MAC address of 00:00:00:00:00:00 for his wireless device), and ndiswrapper 1.48 to 1.49rc4. I'm using 128 bit WEP, but turning it off or on doesn't seem to change anything.

And the problem is clear when I look at my routers (BEFW11S4 V3) wireless MAC address list, my sons wireless MAC is recorded as 00:00:00:00:00:00 even when using acer_acpi after 0.9.0. (acer_acpi after 0.9.0 detect the correct MAC address in System->Preferences->Hardware Information, but the router sees 00~).  I can actually shut down all of our computers, shut down the cable modem and router, power up the modem and router, and then only my sons laptop, and see 00:00:00:00:00:00 recorded in the routers wireless MAC list when I try to connect from the laptop. As I said before the only exception is occasionally connecting after initially changing the ndiswrapper driver, but even that is not reliably reproducible.

To go through everything I've tried would take many pages of description, but rest assured from disabling ipv6 to blacklisting every module having to do with Atheros, to every other randomly (but plausible) solution, nothing has worked. However, when I dual boot into Windows XP (using one of the drivers I've tried numerous times with ndiswrapper) his wireless works flawlessly.

So I'm just going to post my sons chipset ID and hope someone might have a solution. I'm actually going to have to try some other distros in the meantime (hey, I need my monitor back!), but I'm hoping someone here will have some suggestions or even a solution. I truly love Ubuntu, and want to show my son that Linux is a superior alternative to Windows.

His chipset is reported as an AR5006EG under Linux and XP, and its ID is 168C:001C (rev 01)

My friend... In my machine, happens something similar the first times after installation.... just connects wireless sometimes, freezes a lot after boot, but suddenly it starts working, it happens always before a fresh instalation and folliwing these steps.  The important thing is, if after installing acer_acpi, ndiswrapper and the suitable driver for your system... if you type iwconfig and it returns a wlan0... then there is no problem, it will work fine later.

---

### Post by muncrief on 2007-10-26
OK good doctor, I'll give it one more try. And for anyone else who may be considering switching to other Linux distributions to avoid this problem, both Fedora 7 and Suse 10.3 have the same problem, so I guess this is a core Linux issue.

So if I understand what your saying doctor, I should do a clean install, install the extras as instructed here, and if I see wlan0 just wait for awhile? I have waited for many, many hours while working on the problem over the last few weeks, but never after a clean install, and of course I've always been changing things, not just waiting.

So I'm just going to install and wait, and hopefully wireless will start working. I'll let everyone know how it went in four or five hours. And even if it doesn't work, I certainly appreciate all on this forum, and of course you doctor, for helping out on this issue. It seems that even if I can't get mine working you all have helped a lot of others.

---

### Post by dr_cerebro on 2007-10-26
> **muncrief said:**
> OK good doctor, I'll give it one more try. And for anyone else who may be considering switching to other Linux distributions to avoid this problem, both Fedora 7 and Suse 10.3 have the same problem, so I guess this is a core Linux issue.

So if I understand what your saying doctor, I should do a clean install, install the extras as instructed here, and if I see wlan0 just wait for awhile? I have waited for many, many hours while working on the problem over the last few weeks, but never after a clean install, and of course I've always been changing things, not just waiting.

So I'm just going to install and wait, and hopefully wireless will start working. I'll let everyone know how it went in four or five hours. And even if it doesn't work, I certainly appreciate all on this forum, and of course you doctor, for helping out on this issue. It seems that even if I can't get mine working you all have helped a lot of others.

After a clean install, do the steps installing acer_acpi, then follow the steps to install ndiswrapper and the suitable driver, restart the computer and type iwconfig, if a wlan0 appears... you will be wireless soon, maybe it would freeze a couple of times, like in my machine (the most of the people following these steps do not have this problem, but I do).

Good luck, let me know how it works for you.

---

### Post by muncrief on 2007-10-27
Well, unfortunately after a day and night mostly waiting, I've had no success.

After waiting awhile I did indeed connect wirelessly a few times, but as always before whenever I rebooted my wireless was lost. Once after rebooting and losing my connection it did come back after 70 minutes, but then when I rebooted it was lost again. And by the way, I waited two hours without touching the computer or router between each try. During the last try, which stuck exactly to the original instructions with the exception of installing ndiswrapper-1.49rc3, I waited overnight for nine hours.

In any case, I discovered that there is a known bug in ndiswrapper and that's why I have to use version 1.49rc3, which at this time only implements a work around for it  (remember when I use 1.48 my wireless MAC address is reported as 00-00-00-00-00-00). Since this bug has to do with the modems address not being read correctly, I can only assume that the bug has to do with my problem. Here's what the release notes for ndiswrapper 1.49rc3 say:

"If a driver returns invalid MAC address (00:00:00:00:00) when
queried with OID_802_3_CURRENT_ADDRESS (probably because
NdisReadNetworkAddress returns NDIS_STATUS_FAILURE?), use
OID_802_3_PERMANENT_ADDRESS to get the correct address. This is required for
some atheros devices (e.g., AR5007EG)"

As you can see, the ndiswrapper developers themselves don't know why the modem returns a MAC address of 0, couldn't get the regular method to work, and are instead using a different method to obtain the wlan devices MAC address. Evidently this works for them on the local computer, but not always on the wireless router. Except for rare occasions, my wireless router is continuously being told that my wlan devices MAC address is 0, and that's why I can't connect.

And it's not a start up problem, because I have spent many days rebooting the router to clear any previous wired or wireless DHCP or other MAC information, turning the radio on and off in various ways with various drivers by hand, and observing that almost always I get a "ADDRCONF(NETDEV: wlan0: link is not ready" message in /var/log/messages, which parallels the mysterious NDIS_STATUS_FAILURE problem that the developers suspect is at the heart of the ndiswrapper problem.

And by the way for those following this thread who may have a 5005 or 5006 device, they all basically use the 5007 driver, although I have tried other drivers, including the official XP driver for the computer.

So I must say I'm quite frustrated, and will have to give up by Sunday evening and buy myself a new monitor if I haven't figured out the problem by then, and just expand my sons XP partition and remove Ubuntu.

I have over two decades of hardware/firmware/software development under my belt though, and now that I know this is a real problem plaguing the Linux community, I'm going to do my best to see if I can figure out what is wrong. However, the fact that the developers can't figure out what's wrong doesn't bode well for me. But you never know, sooner or later someone has to figure it out ...

---

### Post by gummo on 2007-10-27
Nice how to dr_cerebro

Sadly it did not work for me. Again everything installs flawlessly but when i go to "Volume Control" i still get the "No volume control GStreamer plugins and/or devices found" error. My guess is, this is due to the Realtek drivers i installed earlier wich are prolly screwing things up now.
I have bookmarked this thread and i will try this on a fresh install one of these days when i got a couple of hours to spare.

---

### Post by dr_cerebro on 2007-10-27
So sad to hear those bad news.

I hope you both can solve this soon.

Muncrief: Check this thread with Madwifi: [http://ubuntuforums.org/showthread.php?t=38972](http://ubuntuforums.org/showthread.php?t=38972) maybe you will have to make some modifications, let me know if it works, I didn't try that one.

gummo: Did you select Alsa Mixer in File--->Change device ?

---

### Post by khairulamir on 2007-10-29
hi
huh.....my wireless still cant work......i have followed the step given and everything look like ok...no error message...but when i choose the network from the network icon it does not connect to the network...so plzzz......i net to use it.....what the easiest way to overcome this problem....i use laptop acer aspire 4520 and ubuntu 7.10 64

---

### Post by dr_cerebro on 2007-10-29
> **khairulamir said:**
> hi
huh.....my wireless still cant work......i have followed the step given and everything look like ok...no error message...but when i choose the network from the network icon it does not connect to the network...so plzzz......i net to use it.....what the easiest way to overcome this problem....i use laptop acer aspire 4520 and ubuntu 7.10 64

Try this: [http://ubuntuforums.org/showthread.php?t=512828](http://ubuntuforums.org/showthread.php?t=512828)

---

### Post by khairulamir on 2007-10-30
thanx dr_cerebro,
for ur information...i have followed all the step given from the url ....and my wireless detected...but the problem is it don't connected to the network.....the icon show like connection was established but i still cant conect to the internet...

so i try check the ip address and  the IP address  is 0,

---

### Post by dr_cerebro on 2007-11-02
I moved to another distro, and I had the same problem.
Just restarted the wireless router and then it worked perfectlly.
Maybe that would help.

---

### Post by Marco Polo on 2007-11-11
Hello everyone, congratulations to all of you who managed to make wireless work, as for me, i'm still "wired" :) Here's the problem:
I have Acer Aspire 5315-2153 notebook, which has AR5006EG wireless chipset. I have installed acer_acpi with Synaptec package manager from their repository and this is what i get when typing **"dmesg |grep acer_acpi"**:

[B][   18.200000] acer_acpi: Acer Laptop ACPI Extras version 0.9.1
[   18.200000] acer_acpi: No or unsupported WMI interface, unable to load.
[  118.000000] acer_acpi: Acer Laptop ACPI Extras version 0.9.1
[  118.000000] acer_acpi: No or unsupported WMI interface, unable to load.
[  414.944000] acer_acpi: Acer Laptop ACPI Extras version 0.9.1
[  414.944000] acer_acpi: No or unsupported WMI interface, unable to load.[/B]

It seems that something is wrong. I was following instructions given by dr_cerebro [here]("http://ubuntuforums.org/showpost.php?p=3580373&postcount=15") on second page of this thread. But typing command **"sudo modprobe acer_acpi"** returns:

**FATAL: Error inserting acer_acpi (/lib/modules/2.6.22-14-generic/extra/acer_acpi.ko): No such device**

though if i view "/lib/modules/2.6.22-14-generic/extra/" directory there is a file "acer_acpi.ko" present there. Can anyone help me please? Because of this i just can't move forward with wifi. I'm a new guy to linux so maybe i miss some obvious necessary steps, so please, tell me what to do.

---

### Post by Marco Polo on 2007-11-12
Oh my god, it worked!
Ok, forget about my previuos post, i did manage to enable this ******* wireless :))) Well, i don't know, why "sudo modprobe acer_acpi" didn't work yesterday, but today it did work and thatks to [this]("http://ubuntuforums.org/showthread.php?t=512828&highlight=5006eg") HowTo which was already mentioned, i finally got to enable my wifi.
Thanks to everyone!

---

### Post by Marco Polo on 2007-11-12
OMG...
Sorry everyone, i didn't mean to flood, but i'm having troubles with wifi again... Well, now the problem is that my Atheros adapter dissapeared from  "Device manager"  and  "lshw"  listing, while i'm absolutely sure it was there before. It seems that all this occured after performing software update, this was the only thing i did after wifi worked. And right after reboot wifi is not working and adapter just dissapeared. 
Does anyone know how to bring it back? I'm sure i can do that by re-installing whole Ubuntu from CD, but is it necessary? Any help/links are greatly appreciated.

---

### Post by Blind-Summit on 2007-11-13
I have a samsung R60 laptop so the Acer solution doesn't seem to do anything for me. 

I tried loading the .inf file with ndiswrapper. It says the hardware is present but I cannot see the wifi card in the system->administration->networking.

I had no problems with this with the Broadcom chipset / belkin wifi card on my desktop PC.

People have also mentioned this madwifi driver thing - I have tried and failed.

Could someone please help me on my way to getting this setup?

Thanks in advance

---

### Post by dkuhlman on 2007-11-20
I'm bumping this because I have the same problem.  And, I'm trying to add a little information.

I have an Atheros AR5006EG also.

I'm running Gutsy Gibbon x86_64.

What I've done:

1. Used retricted-manager to disable the Atheros Hardware Access Layer.

2. Used ndisgtk to install the following driver:

      GIGABYTE-super-wireless-V.5.2.0.117.07/Driver/VistaX64

3. Added the following to /etc/modprobe.d/blacklist:

        blacklist ath_pci
        blacklist ath_rate_sample
        blacklist new_ath_pci

4. Reboot.

Still, "Wireless" does not show up in Network Manager.

Also, when I when I try to restart networking, I get errors:

```
/etc [14] sudo init.d/networking restart
 * Reconfiguring network interfaces...
wlan0: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.wlan0.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.
   ...done.

```

And, if I use wconfig, I see "no wireless extensions."

Has anyone gotten wireless to work on Gutsy Gibbon amd64/x86_64 with the Atheros AR5006?  Maybe I'm just spending a lot of time trying to do something that can't be done.

Or, is there one more step that I'm missing?

Dave

---

### Post by Digger78 on 2007-11-20
Try an XP driver, i dont think ndiswrapper supports vista drivers

---

### Post by dkuhlman on 2007-11-20
> **dkuhlman said:**
> I'm bumping this because I have the same problem.  And, I'm trying to add a little information.

I have an Atheros AR5006EG also.

I'm running Gutsy Gibbon x86_64.

What I've done:

1. Used retricted-manager to disable the Atheros Hardware Access Layer.

2. Used ndisgtk to install the following driver:

      GIGABYTE-super-wireless-V.5.2.0.117.07/Driver/VistaX64

3. Added the following to /etc/modprobe.d/blacklist:

        blacklist ath_pci
        blacklist ath_rate_sample
        blacklist new_ath_pci

4. Reboot.

Still, "Wireless" does not show up in Network Manager.


Some progress made.  Now, "Wireless connection" shows up in Network Manager.

The Gigabyte driver did not work for me, so I tried another driver.

I believe what made the difference was that I switched to this driver:

[ftp://ftp.work.acer-euro.com/notebook/aspire_5050/driver//Atheros_WLAN_XB63_Driver_5.1.1.9_XP.zip]("ftp://ftp.work.acer-euro.com/notebook/aspire_5050/driver//Atheros_WLAN_XB63_Driver_5.1.1.9_XP.zip")

And, after unrolling that, I used this subdirectory:

```
ZR3_Atheros_XB63_5.1.1.9_XP_WHQL/XP_5.1.1.9_LED_Negative_Pole/WHQL_5-1-1-9_X64
```

I used ndisgtk to install the .inf file in that directory.

This is described by dr_cerebro in a previous message in this thread.

So, now in Network Manager, I'm trying to configure my Wireless connection. 

But, no matter how I configure in, when I use Wireless Assistant to try to connect, Wireless Assistant tells me: "Connection failed".

I guess I need to do more reading.

Dave

---

### Post by dkuhlman on 2007-11-21
> **dkuhlman said:**
> 
(snip)

So, now in Network Manager, I'm trying to configure my Wireless connection. 

But, no matter how I configure in, when I use Wireless Assistant to try to connect, Wireless Assistant tells me: "Connection failed".

I guess I need to do more reading.

Dave

Success!  After several rebootings and being more careful about configuring my "Wireless connection" the way my router is configured, I have been able to successfully access the outside world via wireless.  Let's hope that I can do it again, the next time I re-boot.

And, under Ubuntu linux, my wireless device, as noted in an earlier message, seems to be mis-identifying itself.  Under Linux, "sudo lshw -C network" shows that it is Arheros AR5006EG.  Whereas, when I boot this same machine into MS Windows Vista, it identifies as Atheros AR5007EG.  My machine is a Toshiba Satellite A215-S4697.  And, I'm on Ubuntu GNU/Linux x86_64.

Dave

---

### Post by dr_cerebro on 2007-11-22
Well, I need to say, the same happened to me too... after several rebootings it worked flawlessly, but the first times it doesn't.

---

### Post by gusanto on 2008-01-04
> **dr_cerebro said:**
> Well, I asked in many forums, until they gave me the answer, but in the published threads it is not corrected.

I followed the steps in [this]("http://ubuntuforums.org/showthread.php?t=224349&highlight=acer_acpi") howto and made several changes in order to make it work.

I had to install acer_acpi-0.8.2 because, in other versions, something just do not work... a path to something (I can't remember what), but, here is the step by step of acer_acpi, but first, I want to make a statement: I WILL NEVER BUY AN ACER LAPTOP AGAIN. *"Terribilis est machina ista"*.  At least in Linux.

I'm just a newbie, so, do not expect me to explain each step, and by the way, I do not speak English very well, so...

Let's start:

First, I deactivated Atheros from Restricted Modules.

Then, restarted and open a terminal

```
sudo aptitude update
```

Then:

```
sudo aptitude install build-essential linux-headers-$(uname -r)
```

You make a directory named download for example:

```
mkdir ~/download
```

You enter to that directory:

```
cd ~/download
```

Download the acer_acpi tar file:

```
wget http://aceracpi.googlecode.com/files/acer_acpi-0.8.2.tar.bz2
```

Decompress:

```
tar jxvf acer_acpi-0.8.2.tar.bz2
```

Enter to the created directory:

```
cd acer_acpi-0.8.2
```

Then:

```
make
```

Then:

```
sudo make install
```

Then:

```
cd ../..
```

Then:

```
sudo modprobe acer_acpi
```

Then:

```
sudo chmod 777 /proc/acpi/acer/wireless
```

Then:

```
sudo echo 1 > /proc/acpi/acer/wireless
```

Then:

```
dmesg | grep acer_acpi
```

Then:

```
sudo gedit /etc/init.d/acer_acpi_wireless_enable
```

Then, just copy and paste the next script, save and close gedit:

```

#!/bin/sh

case "$1" in

        start|"")

                modprobe acer_acpi

                chmod 777 /proc/acpi/acer/wireless

                echo 1 > /proc/acpi/acer/wireless

                ;;

        stop)

                echo 0 > /proc/acpi/acer/wireless

                modprobe -r acer_acpi

                ;;

esac

```

Then:

```
sudo chmod 755 /etc/init.d/acer_acpi_wireless_enable
```

Then:

```
sudo update-rc.d acer_acpi_wireless_enable start 39 S . start 34 0 6 .
```

Then, just verify it it worked:

```
ls /etc/rcS.d/S39acer_acpi_wireless_enable
```

```
ls /etc/rc0.d/S34acer_acpi_wireless_enable
```

```
ls /etc/rc6.d/S34acer_acpi_wireless_enable
```

You can find the original post here: [http://ubuntuforums.org/showthread.php?t=224349&highlight=acer_acpi](http://ubuntuforums.org/showthread.php?t=224349&highlight=acer_acpi)

Restart the computer and follow the EXACT step by step described in this howto: [http://ubuntuforums.org/showthread.php?t=512828](http://ubuntuforums.org/showthread.php?t=512828)
But, the sad thing, is than it downloads a driver for a i386 architecture, it just do not work with AMD 64.

But, as I previously said.  I could make it work as many times as possible in Ubuntu i386, but it just do not work in version x86_64.  That is why I am using this ugly yellow wire to connect my laptop to the internet, while writing this post.
I have the same problem "not detected Atheros AR5006EG on my Sony Vaio VGN-NR120E.  I am a newbie, know nothing and have followed some guides to install madwifi then nidswrapper but have no luck. 
Please help me.
Many thanks.

---

### Post by buccaneere on 2008-01-05
> **gusanto said:**
> I have the same problem "not detected Atheros AR5006EG on my Sony Vaio VGN-NR120E.  I am a newbie, know nothing and have followed some guides to install madwifi then nidswrapper but have no luck. 
Please help me.
Many thanks.

Hi gusanto... 

I just got two Atheros-equipped boxes properly configured, with help from weiman01(wirelessknowledgebase).

This is the thread with all necessary info:  [http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834)
 The OP'er gets into the thread to help out frequently.

In the meantime, I'll try to help. Post return for

[HTML]~$  iwconfig [/HTML]

and also for

[HTML] ~$ sudo iwlist scan[/HTML]

from your command line...

---

### Post by buccaneere on 2008-01-05
> **dr_cerebro said:**
> Well, I need to say, the same happened to me too... after several rebootings it worked flawlessly, but the first times it doesn't.

Atheros driver has a bug.

Either restart networking after boot-up

[HTML]~$ sudo /etc/init.d/networking restart[/HTML]

or see code fix here (thanks to weiman) [http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834)  post #2, I think...

---

### Post by gusanto on 2008-01-05
OK,
Output from iwconfig:
> lo        no wireless extensions.

eth0      no wireless extensions.

and from sudo iwlist scan:
> lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

---

### Post by Digger78 on 2008-01-05
> **gusanto said:**
> OK,
Output from iwconfig:


and from sudo iwlist scan:

you said that you have ndiswrapper installed?

remove madwifi, it doesnt work

what is the output from

```
ndiswrapper -l
```

---

### Post by buccaneere on 2008-01-05
> **Digger78 said:**
> you said that you have ndiswrapper installed?

remove madwifi, it doesnt work


You sure about that digger? I got madwifi drivin' both of my atheros-equipped boxes...

AND, incidently, the wireless interface for both of them is called ATH0, not eth0... Only my broadcom-equipped machine has interface 'ethx' (eth1).

gusanto, run iwconfig again, and see if one of the interfaces is called 'ath0'... 

If not, enter [HTML]lspci[/HTML] , or [HTML]lsusb[/HTML] , and look for 'xx : xx.x Ethernet controller: Atheros communications, Inc. AR5006EG802.11abg NIC (rev01)' or something with Atheros...

---

### Post by Digger78 on 2008-01-05
Madwifi didnt work for me.

My card was detected as Atheros AR5006EG but it is actually an Atheros AR5007EG

I suspect this is the same for gusanto.

---

### Post by buccaneere on 2008-01-05
> **Digger78 said:**
> Madwifi didnt work for me.

My card was detected as Atheros AR5006EG but it is actually an Atheros AR5007EG

I suspect this is the same for gusanto.

That explains it then - mine are both 5005G's.

Still, his wireless interface should still show as ath(x)...

---

### Post by gusanto on 2008-01-06
> **buccaneere said:**
> That explains it then - mine are both 5005G's.

Still, his wireless interface should still show as ath(x)...


I already installed madwifi throuhg synaptic (please correct me if I did it wrong).
Outpput from ndiswrapper -l is
> net5211 : driver installed
        device (168C:001C) present (alternate driver: ath_pci)

Output from lspci
> 06:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)

Output from iwconfig
> lo        no wireless extensions.

eth0      no wireless extensions.



From System>Adminitration>Windows Wireless Drivers, it says:
> net5211
Hardware present: Yes

I also already disable Atheros HAL from Restricted Driver Manager.

---

### Post by gusanto on 2008-01-06
Correction of previous post:
I meant is unsintalled madwifi throuhg synaptic (please correct me if I did it wrong).

---

### Post by Digger78 on 2008-01-06
Did you **blacklist ath_pci** ?

add **blacklist ath_pci** to **/etc/modprobe.d/blacklist**

```
sudo -s   [COLOR="Red"](this line will change you to a root terminal)[/COLOR]

echo blacklist ath_pci >> /etc/modprobe.d/blacklist  [COLOR="Red"](this line will blacklist ath_pci)[/COLOR]

exit     [COLOR="Red"](this line will return you to the user terminal)[/COLOR]
```

you can check it with

```
cat /etc/modprobe.d/blacklist
```

**reboot** then try setting up your connection

---

### Post by gusanto on 2008-01-06
Yes I blacklisted ath_pci on /etc/modprobe.d/blacklist
Even on the line above it ath_pci was already blacklisted like below:
 
>  # causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801
blacklist ath_pci

blacklist ath_pci
 

Does it matter if ath_pci is blacklisted twice?  I also tried to delete one from /etc/modprobe.d/blacklist file to avoid the redundancy (sory if this is basic).  The problem is still the same though.

---

### Post by Digger78 on 2008-01-06
The double entry shouldnt make any difference but you can remove one if you want.

```
gdesu gedit /etc/modprobe.d/blacklist
```

what version of ndiswrapper are you using?

```
ndiswrapper -v
```

Does your Vaio have a key combo to enable/disable wireless but it doesnt work?

---

### Post by gusanto on 2008-01-06
> **Digger78 said:**
> The double entry shouldnt make any difference but you can remove one if you want.

```
gdesu gedit /etc/modprobe.d/blacklist
```

what version of ndiswrapper are you using?

```
ndiswrapper -v
```
> utils version: 1.9
driver filename:       /lib/modules/2.6.22-14-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko
version:        1.45
vermagic:       2.6.22-14-generic SMP mod_unload 586 


Does your Vaio have a key combo to enable/disable wireless but it doesnt work?
There is an on/off button for the wireless.  It is swithed on, but no light indicator lights on.  The wireless card is also not detected on Network Settings.

Do you need to see the dmseg output? (which part, I have no idea about it, please give me the command, I think grep something).

---

### Post by Digger78 on 2008-01-06
as far as i can tell you have ndiswrapper + driver setup properly, I think the problem is that your card is not enabled. 

[QUOTE=gustano]There is an on/off button for the wireless. It is swithed on, but no light indicator lights on
[/QUOTE]

you seem to be missing the driver that receives that signal and enables/disables the card.

try

```
sudo modprobe sonypi
```

then try enabling/disabling the card with the on/off button

check dmesg for any errors

---

### Post by gusanto on 2008-01-06
dmesg |grep sonypi
> [   21.588000] sonypi: Sony Programmable I/O Controller Driver v1.26.
[   21.588000] sonypi: please try the sony-laptop module instead and report failures, see also [http://www.linux.it/~malattia/wiki/index.php/Sony_drivers](http://www.linux.it/~malattia/wiki/index.php/Sony_drivers)
[   21.588000] sonypi: detected type2 model, verbose = 0, fnkeyinit = off, camera = off, compat = off, mask = 0xffffffff, useinput = on, acpi = on
[   21.588000] sonypi: enabled at irq=11, port1=0x1080, port2=0x1084
[   21.588000] sonypi: device allocated minor is 62
[   21.640000] sonypi command failed at /build/buildd/linux-source-2.6.22-2.6.22/drivers/char/sonypi.c : sonypi_call1 (line 652)
[   21.684000] sonypi command failed at /build/buildd/linux-source-2.6.22-2.6.22/drivers/char/sonypi.c : sonypi_call2 (line 663)
[   21.724000] sonypi command failed at /build/buildd/linux-source-2.6.22-2.6.22/drivers/char/sonypi.c : sonypi_call2 (line 665)
[   21.768000] sonypi command failed at /build/buildd/linux-source-2.6.22-2.6.22/drivers/char/sonypi.c : sonypi_call1 (line 652)

dmesg |grep ndiswrapper
> [   16.468000] ndiswrapper version 1.45 loaded (smp=yes)
[   16.588000] ndiswrapper: driver net5211 (,05/02/2007,5.3.0.45) loaded
[   16.588000] ndiswrapper (ZwClose:2247): closing handle 0xdfe1e628 not implemented
[   16.588000] ndiswrapper (NdisWriteErrorLogEntry:192): log: C0001389, count: 4, return_address: f8d66064
[   16.588000] ndiswrapper (NdisWriteErrorLogEntry:195): code: 0xf7e68600
[   16.588000] ndiswrapper (NdisWriteErrorLogEntry:195): code: 0x28
[   16.588000] ndiswrapper (NdisWriteErrorLogEntry:195): code: 0xf8bf6000
[   16.588000] ndiswrapper (NdisWriteErrorLogEntry:195): code: 0xf8bf6000
[   16.588000] ndiswrapper (mp_init:263): couldn't initialize device: C000009A
[   16.588000] ndiswrapper (pnp_start_device:440): Windows driver couldn't initialize the device (C0000001)
[   16.588000] ndiswrapper (mp_halt:305): device dfd11500 is not initialized - not halting
[   16.588000] ndiswrapper: device eth%d removed
[   16.588000] ndiswrapper: probe of 0000:06:00.0 failed with error -22
[   16.592000] usbcore: registered new interface driver ndiswrapper

dmesg |grep error
> [   15.780288] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   16.588000] ndiswrapper: probe of 0000:06:00.0 failed with error -22

Switching on or off the switch button for the wireless card did not make any different, it still can't detect the wireless card.

---

### Post by buccaneere on 2008-01-07
](*,)

I don't know what other words to use, to say what I've said 3 times...

Your atheros chipset is not showing up in your return for iwconfig. This command reports the status of wireless interfaces. It should show up as 'ath0'.

Even with the wrong drivers loaded, the interface can show up in the list of wireless interfaces. Yours isn't even showing up, except as a piece of hardware with a pci address. You are not yet at the point of loading drivers.

Sorry I don't know more - but I know the destination is north, and you're headed south. (or east or west)

---

### Post by buccaneere on 2008-01-07
Are you sure the wireless device is physically turned on? Usually 'Fn' key + another key, maybe with the wireless symbol on it...

---

### Post by gusanto on 2008-01-07
So I lost too too far.
My laptop has switch (on/off button) for the wireless LAN.  It is turned on for sure.

---

### Post by buccaneere on 2008-01-08


You need to communicate this problem with either 'xeth delta', or 'wieman01'. They know wireless as good as anybody, who I've seen post in this forum.

If you can get up with either of them, copy and paste what I said in my previous post - I'm certain that is the starting diagnostic clue that they will need...

---

### Post by wieman01 on 2008-01-09
> **gusanto said:**
> So I lost too too far.
My laptop has switch (on/off button) for the wireless LAN.  It is turned on for sure.
Hello, 

Please post this for me:
> sudo iwlist scan
> sudo ndiswrapper -l
> sudo cat /etc/network/interfaces
> sudo lshw -C network
> dmesg
Let's see what's going on.

---

### Post by gusanto on 2008-01-09
Here is the outputs from the commads:

sudo iwlist scan
> lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

sudo ndiswrapper -l
> net5211 : driver installed
        device (168C:001C) present (alternate driver: ath_pci)

sudo cat /etc/network/interfaces
> auto lo
iface lo inet loopback

sudo lshw -C network
>   *-network               
       description: Ethernet interface
       product: 88E8039 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 14
       serial: 00:1a:80:1f:8b:1a
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.18 duplex=full firmware=N/A ip=192.168.1.102 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR5006EG 802.11 b/g Wireless PCI Express Adapter
       vendor: Atheros Communications, Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0

When I tried to include the output from dmseg on this post as you ask, I got the following message:
> The following errors occurred when this message was submitted:
You have included 10 images in your message. You are limited to using 8 images so please go back and correct the problem and then continue again.

Is it because too many lines I attached (more than 700 lines).  Probably you need to give me specific command of dmseg.

---

### Post by wieman01 on 2008-01-10
> *-network **[COLOR="Red"]UNCLAIMED[/COLOR]**
I think your wireless device is turned off. Is there any button that lets you turn it on?

_**EDIT:**_
I came across this post: [http://ubuntuforums.org/showpost.php?p=3868406&postcount=48]("http://ubuntuforums.org/showpost.php?p=3868406&postcount=48")

---

### Post by buccaneere on 2008-01-10
> **buccaneere said:**
> Are you sure the wireless device is physically turned on? Usually 'Fn' key + another key, maybe with the wireless symbol on it...

I asked him that too there wieman, just a few posts ago. He said it is turned on.

Gusanto - do you have a little LED on the box somewhere that shows wireless power 'ON'?

Is this a desktop with a wireless card?

---

### Post by gusanto on 2008-01-10
Hi Wieman01 and Buccaneere,
My computer is Sony Vaio VGN-NR120E laptop.  That's right, it has wireless LAN on/off button and LED light.  When I'm running Windows, the LED is on when the switch is turned on but not on when I'm running Gutsy even though the switch is turned on.

---

### Post by buccaneere on 2008-01-11
> **gusanto said:**
> Hi Wieman01 and Buccaneere,
My computer is Sony Vaio VGN-NR120E laptop.  That's right, it has wireless LAN on/off button and LED light.  When I'm running Windows, the LED is on when the switch is turned on but not on when I'm running Gutsy even though the switch is turned on.

Software for switch function, not other wise 'auto-enabled'...

[http://rfswitch.sourceforge.net/](http://rfswitch.sourceforge.net/)

---

### Post by wieman01 on 2008-01-11
> **buccaneere said:**
> I asked him that too there wieman, just a few posts ago. He said it is turned on.

Gusanto - do you have a little LED on the box somewhere that shows wireless power 'ON'?

Is this a desktop with a wireless card?
And you were right... the device is definitely turned off. Now let's focus on how to turn it on... :-)

---

### Post by fossn8 on 2008-01-12
I have the same issue with the MAC address of the Atheros AR5006EG card reported as 00:00:00:00:00:00.  This is a problem for me because I block by MAC address at my firewall.  Has there been any progress with this issue on any front?

BTW, I found the site ivangarcia.org to be very key to helping me setup Wifi,

---

### Post by gusanto on 2008-01-18
Hi all,
I'm still wacthing this thread and hoping a solution of this problem.
Any new idea?

---

### Post by EckoAK on 2008-01-26
*bump*

I'm right here with you Gusanto, only I'm on an ASUS F3KA-A1 and my light does come on when I press the button. However, my card is also not being recognized because I get the same results for those four commands. My light must be wired to the button combination or something, and not actually reading my card.

Someone, help us? Please?

---

### Post by wieman01 on 2008-01-27
What PC have you got? No button at all? I still don't get what could be going on...

---

### Post by EckoAK on 2008-01-27
an asus f3ka-a1
[http://www.newegg.com/product/product.asp?item=N82E16834220202]("http://www.newegg.com/product/product.asp?item=N82E16834220202")
there is a button and a light for wireless on/off. the problem was the card wasnt being recognized at all, i was getting no "ath0" device under "ifconfig"
i couldnt spend any more time on this, so i reinstalled vista. thanks for the help. im just going to wait until madwifi does something about this, it looks like they should have something done by version 1.0.0.0 >.<

---

