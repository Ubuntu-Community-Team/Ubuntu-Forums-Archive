---
title: "Help! Wireless has vanished..."
date: 2007-07-13
forum: Networking &amp; Wireless
---

### Post by Torajima on 2007-07-13
Wireless has always worked fine for me. After (accidentally) running a system update, it has disappeared from Network Manager. When I right-click on it, "Enable Wireless" isn't there anymore. It doesn't show up under network settings, either.

I've tried a bunch of different things, including reinstalling gnome-network-manager, now that doesn't work either.

My computer is a Macbook. My Network controller is listed as Atheros Communications, Inc. Unknown device.

iwconfig shows "no wireless extensions"

Please help... my laptop isn't much use to me without wireless!

---

### Post by scrooge_74 on 2007-07-13
This has worked for me on Intel Laptops, go to /etc/network/interfaces

To the references to your wireless cards put the settings like this

auto eth0
iface eth0 inet dhcp

replace eth0 for your (probably ath0)
hope that helps

---

### Post by Torajima on 2007-07-13
All I have under /etc/networks/interfaces is:

> auto lo
iface lo inet loopback

iface eth0 inet dhcp

auto eth0

---

### Post by kevdog on 2007-07-13
Whats the output of:

iwconfig -C network

---

### Post by Torajima on 2007-07-13
Output is:

> Error : unrecognised wireless request "network"

---

### Post by kevdog on 2007-07-13
Sorry, 

how about
lshw -C network

---

### Post by Torajima on 2007-07-13
*-network
       description: Ethernet interface
       product: 88E8053 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@01:00.0
       logical name: eth0
       version: 22
       serial: 00:1b:63:1b:d1:44
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.13 firmware=N/A ip=192.168.111.29 latency=0 multicast=yes
       resources: iomemory:90200000-90203fff ioport:1000-10ff irq:16
  *-network UNCLAIMED
       description: Network controller
       product: Atheros Communications, Inc.
       vendor: Atheros Communications, Inc.
       physical id: 0
       bus info: pci@02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: iomemory:90100000-9010ffff irq:11

---

### Post by kevdog on 2007-07-13
Ok the reason it is coming back unclaimed is that you have no driver associated with your card. When you originally installed the card did you install any drivers for the card -- ie like madwifi or ndiswrapper???  Many atheros cards do work out of the box and this may have been your case -- meaning you didnt have to install a driver.  

Do you have any more info on your card --
If pci based card
lspci
lspci -n

If usb device
lsusb

Somehow the udpate either deleted or removed or unloaded the driver you probably used to use.

---

### Post by Torajima on 2007-07-13
I didn't install drivers, wifi worked out of the box.

Here's the relevant info from lspci...

> 01:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit
 Ethernet Controller (rev 22)
02:00.0 Network controller: Atheros Communications, Inc. Unknown device 0024 (re
v 01)

---

### Post by kevdog on 2007-07-13
Can you also post the following -- the madwifi Atheros drivers (although restricted) are in many cases installed by default with feisty -- thats probably the drivers you used.  Can you list for me the following:

lsmod -l | grep mad

Here is my output
kevin@Homer:~$ modprobe -l | grep mad
/lib/modules/2.6.20-16-generic/madwifi/ath_pci.ko
/lib/modules/2.6.20-16-generic/madwifi/ath_rate_sample.ko
/lib/modules/2.6.20-16-generic/madwifi/ath_rate_amrr.ko
/lib/modules/2.6.20-16-generic/madwifi/wlan_xauth.ko
/lib/modules/2.6.20-16-generic/madwifi/wlan_wep.ko
/lib/modules/2.6.20-16-generic/madwifi/wlan_tkip.ko
/lib/modules/2.6.20-16-generic/madwifi/ath_rate_onoe.ko
/lib/modules/2.6.20-16-generic/madwifi/wlan_scan_ap.ko
/lib/modules/2.6.20-16-generic/madwifi/wlan_ccmp.ko
/lib/modules/2.6.20-16-generic/madwifi/wlan_scan_sta.ko
/lib/modules/2.6.20-16-generic/madwifi/wlan.ko
/lib/modules/2.6.20-16-generic/madwifi/wlan_acl.ko
/lib/modules/2.6.20-16-generic/kernel/drivers/net/tokenring/madgemc.ko
/lib/modules/2.6.20-16-generic/kernel/drivers/infiniband/core/ib_umad.ko
/lib/modules/2.6.20-16-generic/kernel/drivers/infiniband/core/ib_mad.ko

---

### Post by Torajima on 2007-07-13
"lsmod -l" doesn't work for me, but if I just use "lsmod | grep mad" it runs and returns nothing.

Thanks for helping me with this...

---

### Post by kevdog on 2007-07-13
Ok you dont have the modules installed

First find out your kernel module version:
uname -r

Then go into synaptic.  Once its up (takes forever), do a search for restricted drivers.

You are going to find a lot of entries for linux-restricted-modules-xxxxxx

You need to match the last part (xxxx) with your kernel version.  

Once you find the correct line:
Right click and select mark for installation.

Then hit apply at the top of the synaptic toolbar.

Hopefully that will do it for you.

Id recommend rebooting after the installation.

---

### Post by Torajima on 2007-07-13
According to synaptic, the restrictive drivers were already installed. I reinstalled them and re-booted, but the wifi still doesn't show up.

And "lsmod" is still not showing madwifi.

And while rebooting, I noticed this message:
> ath0 - error fetching interface information - device not found

---

### Post by kevdog on 2007-07-13
May have to include as a file attachment, but please post the entire output of:
dmesg

This is the boot log!

Please also post
sudo modprobe -l | grep mad

This will tell us truly if the modules are contained within the kernel

---

### Post by Torajima on 2007-07-13
Here you go...

> [    0.000000] Linux version 2.6.20-16-generic (root@king) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Thu Jun 7 19:00:28 UTC 2007 (Ubuntu 2.6.20-16.29-generic)
[    0.000000] Command line: root=UUID=cc7dd55b-7c80-4830-996c-aea8e8bb1760 ro quiet splash
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007e0f2000 (usable)
[    0.000000]  BIOS-e820: 000000007e0f2000 - 000000007e2f3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007e2f3000 - 000000007eebe000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007eebe000 - 000000007eeef000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007eeef000 - 000000007ef00000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007ef00000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed20000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffe00000 - 0000000100000000 (reserved)
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 516338) 1 entries of 3200 used
[    0.000000] end_pfn_map = 1048576
[    0.000000] DMI 2.4 present.
[    0.000000] ACPI: RSDP (v002 APPLE                                 ) @ 0x00000000000fe020
[    0.000000] ACPI: XSDT (v001 APPLE   Apple00 0x000000a5      0x01000013) @ 0x000000007eefd1c0
[    0.000000] ACPI: FADT (v003 APPLE   Apple00 0x000000a5 Loki 0x0000005f) @ 0x000000007eefb000
[    0.000000] ACPI: HPET (v001 APPLE   Apple00 0x00000001 Loki 0x0000005f) @ 0x000000007eefa000
[    0.000000] ACPI: MADT (v001 APPLE   Apple00 0x00000001 Loki 0x0000005f) @ 0x000000007eef9000
[    0.000000] ACPI: MCFG (v001 APPLE   Apple00 0x00000001 Loki 0x0000005f) @ 0x000000007eef8000
[    0.000000] ACPI: ASF! (v032 APPLE   Apple00 0x00000001 Loki 0x0000005f) @ 0x000000007eef7000
[    0.000000] ACPI: SBST (v001 APPLE   Apple00 0x00000001 Loki 0x0000005f) @ 0x000000007eef6000
[    0.000000] ACPI: ECDT (v001 APPLE   Apple00 0x00000001 Loki 0x0000005f) @ 0x000000007eef5000
[    0.000000] ACPI: SSDT (v001 APPLE     CpuPm 0x00003000 INTL 0x20050309) @ 0x000000007eeef000
[    0.000000] ACPI: SSDT (v001 SataRe  SataPri 0x00001000 INTL 0x20050309) @ 0x000000007eebd000
[    0.000000] ACPI: SSDT (v001 SataRe  SataSec 0x00001000 INTL 0x20050309) @ 0x000000007eebc000
[    0.000000] ACPI: DSDT (v001 APPLE   MacBook 0x00020001 INTL 0x20050309) @ 0x0000000000000000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000007e0f2000
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 516338) 1 entries of 3200 used
[    0.000000] Bootmem setup node 0 0000000000000000-000000007e0f2000
[    0.000000] No mptable found.
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA32        4096 ->  1048576
[    0.000000]   Normal    1048576 ->  1048576
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0:        0 ->      159
[    0.000000]     0:      256 ->   516338
[    0.000000] On node 0 totalpages: 516241
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 1085 pages reserved
[    0.000000]   DMA zone: 2858 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 7003 pages used for memmap
[    0.000000]   DMA32 zone: 505239 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Setting APIC routing to physical flat
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Nosave address range: 000000000009f000 - 00000000000a0000
[    0.000000] Nosave address range: 00000000000a0000 - 00000000000e0000
[    0.000000] Nosave address range: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:70000000)
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] PERCPU: Allocating 34048 bytes of per cpu data
[    0.000000] Built 1 zonelists.  Total pages: 508097
[    0.000000] Kernel command line: root=UUID=cc7dd55b-7c80-4830-996c-aea8e8bb1760 ro quiet splash
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[   27.119450] Console: colour VGA+ 80x25
[   27.120769] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[   27.121926] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   27.122108] Checking aperture...
[   27.122123] Calgary: detecting Calgary via BIOS EBDA area
[   27.122132] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[   27.148176] Memory: 2022292k/2065352k available (2217k kernel code, 42672k reserved, 1162k data, 304k init)
[   27.227736] Calibrating delay using timer specific routine.. 3995.99 BogoMIPS (lpj=7991983)
[   27.227798] Security Framework v1.0.0 initialized
[   27.227805] SELinux:  Disabled at boot.
[   27.227831] Mount-cache hash table entries: 256
[   27.228003] CPU: L1 I cache: 32K, L1 D cache: 32K
[   27.228006] CPU: L2 cache: 4096K
[   27.228009] CPU 0/0 -> Node 0
[   27.228011] using mwait in idle threads.
[   27.228013] CPU: Physical Processor ID: 0
[   27.228014] CPU: Processor Core ID: 0
[   27.228022] CPU0: Thermal monitoring enabled (TM2)
[   27.228035] SMP alternatives: switching to UP code
[   27.228329] Early unpacking initramfs... done
[   27.614779] ACPI: Core revision 20060707
[   27.615158] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   27.658094] Using local APIC timer interrupts.
[   27.708194] result 10390622
[   27.708196] Detected 10.390 MHz APIC timer.
[   27.711653] SMP alternatives: switching to SMP code
[   27.711809] Booting processor 1/2 APIC 0x1
[   27.723023] Initializing CPU#1
[   27.799417] Calibrating delay using timer specific routine.. 3990.09 BogoMIPS (lpj=7980188)
[   27.799424] CPU: L1 I cache: 32K, L1 D cache: 32K
[   27.799426] CPU: L2 cache: 4096K
[   27.799429] CPU 1/1 -> Node 0
[   27.799431] CPU: Physical Processor ID: 0
[   27.799432] CPU: Processor Core ID: 1
[   27.799439] CPU1: Thermal monitoring enabled (TM2)
[   27.800022] Intel(R) Core(TM)2 CPU         T7200  @ 2.00GHz stepping 06
[   27.803431] Brought up 2 CPUs
[   27.803485] time.c: Using 14.318180 MHz WALL HPET GTOD HPET/TSC timer.
[   27.803487] time.c: Detected 1995.002 MHz processor.
[   27.942385] migration_cost=23
[   27.942749] Time: 17:37:10  Date: 06/13/107
[   27.942787] NET: Registered protocol family 16
[   27.942868] ACPI: bus type pci registered
[   27.942876] PCI: Using configuration type 1
[   27.946623] ACPI: Interpreter enabled
[   27.946626] ACPI: Using IOAPIC for interrupt routing
[   27.947235] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   27.947241] PCI: Probing PCI hardware (bus 00)
[   27.948071] Boot video device is 0000:00:02.0
[   27.948729] PCI quirk: region 0400-047f claimed by ICH6 ACPI/GPIO/TCO
[   27.948734] PCI quirk: region 0500-053f claimed by ICH6 GPIO
[   27.949487] PCI: Transparent bridge - 0000:00:1e.0
[   27.949554] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   27.957452] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[   27.957733] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[   27.959362] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[   27.960315] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[   27.960563] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[   27.960811] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[   27.961056] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[   27.961298] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[   27.961541] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[   27.961786] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[   27.962029] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *11 12 14 15)
[   27.968868] Linux Plug and Play Support v0.97 (c) Adam Belay
[   27.968878] pnp: PnP ACPI init
[   27.973038] pnp: PnP ACPI: found 9 devices
[   27.973128] PCI: Using ACPI for IRQ routing
[   27.973131] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   27.973252] NET: Registered protocol family 8
[   27.973254] NET: Registered protocol family 20
[   27.973267] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   27.973271] hpet0: 3 64-bit timers, 14318180 Hz
[   27.974287] PCI-GART: No AMD northbridge found.
[   27.975015] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
[   27.975022] PCI: Bridge: 0000:00:1c.0
[   27.975025]   IO window: 1000-1fff
[   27.975031]   MEM window: 90200000-902fffff
[   27.975036]   PREFETCH window: 90500000-905fffff
[   27.975042] PCI: Bridge: 0000:00:1c.1
[   27.975044]   IO window: disabled.
[   27.975050]   MEM window: 90100000-901fffff
[   27.975054]   PREFETCH window: disabled.
[   27.975060] PCI: Bridge: 0000:00:1e.0
[   27.975062]   IO window: disabled.
[   27.975068]   MEM window: 90000000-900fffff
[   27.975072]   PREFETCH window: disabled.
[   27.975102] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 17
[   27.975108] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   27.975132] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 16 (level, low) -> IRQ 16
[   27.975138] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   27.975153] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   27.975191] NET: Registered protocol family 2
[   28.015350] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[   28.015611] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[   28.017588] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   28.018185] TCP: Hash tables configured (established 262144 bind 65536)
[   28.018188] TCP reno registered
[   28.031457] checking if image is initramfs... it is
[   28.786446] Freeing initrd memory: 6828k freed
[   28.792528] audit: initializing netlink socket (disabled)
[   28.792550] audit(1184348230.628:1): initialized
[   28.792756] VFS: Disk quotas dquot_6.5.1
[   28.792780] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   28.792840] io scheduler noop registered
[   28.792842] io scheduler anticipatory registered
[   28.792845] io scheduler deadline registered
[   28.792860] io scheduler cfq registered (default)
[   28.793249] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   28.793307] assign_interrupt_mode Found MSI capability
[   28.793311] Allocate Port Service[0000:00:1c.0:pcie00]
[   28.793352] Allocate Port Service[0000:00:1c.0:pcie02]
[   28.793482] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   28.793540] assign_interrupt_mode Found MSI capability
[   28.793542] Allocate Port Service[0000:00:1c.1:pcie00]
[   28.793578] Allocate Port Service[0000:00:1c.1:pcie02]
[   28.817798] Real Time Clock Driver v1.12ac
[   28.817858] Linux agpgart interface v0.102 (c) Dave Jones
[   28.817862] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   28.818444] mice: PS/2 mouse device common for all mice
[   28.819085] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   28.819253] input: Macintosh mouse button emulation as /class/input/input0
[   28.819294] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   28.819299] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   28.819653] PNP: No PS/2 controller found. Probing ports directly.
[   28.820504] i8042.c: No controller found.
[   28.820591] TCP cubic registered
[   28.820603] NET: Registered protocol family 1
[   28.820700] ACPI: (supports S0 S3 S4 S5)
[   28.820747]   Magic number: 15:366:643
[   28.820834] drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   28.820919] Freeing unused kernel memory: 304k freed
[   30.003920] Capability LSM initialized
[   30.037519] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [APPLE ] OemTableId [ Cpu0Ist] [20060707]
[   30.037730] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [APPLE ] OemTableId [ Cpu0Cst] [20060707]
[   30.038018] Monitor-Mwait will be used to enter C-1 state
[   30.038022] Monitor-Mwait will be used to enter C-2 state
[   30.038025] Monitor-Mwait will be used to enter C-3 state
[   30.038031] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   30.038036] ACPI: Processor [CPU0] (supports 8 throttling states)
[   30.038569] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [APPLE ] OemTableId [ Cpu1Ist] [20060707]
[   30.038761] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [APPLE ] OemTableId [ Cpu1Cst] [20060707]
[   30.039103] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[   30.039108] ACPI: Processor [CPU1] (supports 8 throttling states)
[   30.402490] usbcore: registered new interface driver usbfs
[   30.402512] usbcore: registered new interface driver hub
[   30.407081] SCSI subsystem initialized
[   30.411427] libata version 2.20 loaded.
[   30.423703] usbcore: registered new device driver usb
[   30.426745] ieee1394: Initialized config rom entry `ip1394'
[   30.427838] ACPI: PCI Interrupt 0000:03:03.0[A] -> GSI 19 (level, low) -> IRQ 19
[   30.480076] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[19]  MMIO=[90000000-900007ff]  Max Packet=[2048]  IR/IT contexts=[8/8]
[   30.490188] USB Universal Host Controller Interface driver v3.0
[   30.496088] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 21 (level, low) -> IRQ 21
[   30.496100] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   30.496104] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   30.496343] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   30.496375] uhci_hcd 0000:00:1d.0: irq 21, io base 0x00002080
[   30.496841] usb usb1: configuration #1 chosen from 1 choice
[   30.496996] hub 1-0:1.0: USB hub found
[   30.497003] hub 1-0:1.0: 2 ports detected
[   30.513662] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
[   30.513673] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   30.513677] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   30.513802] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   30.513831] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00002060
[   30.514262] usb usb2: configuration #1 chosen from 1 choice
[   30.514412] hub 2-0:1.0: USB hub found
[   30.514418] hub 2-0:1.0: 2 ports detected
[   30.538114] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   30.538122] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   30.538126] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   30.538254] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   30.538285] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00002040
[   30.538710] usb usb3: configuration #1 chosen from 1 choice
[   30.538860] hub 3-0:1.0: USB hub found
[   30.538866] hub 3-0:1.0: 2 ports detected
[   30.555562] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 16
[   30.555570] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   30.555574] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   30.555706] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   30.555738] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00002020
[   30.556163] usb usb4: configuration #1 chosen from 1 choice
[   30.556331] hub 4-0:1.0: USB hub found
[   30.556337] hub 4-0:1.0: 2 ports detected
[   30.574093] usb 1-2: new full speed USB device using uhci_hcd and address 2
[   30.583334] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 21 (level, low) -> IRQ 21
[   30.583367] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   30.583371] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   30.583396] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   30.583433] ehci_hcd 0000:00:1d.7: debug port 1
[   30.583440] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   30.583446] ehci_hcd 0000:00:1d.7: irq 21, io mem 0x90445400
[   30.587344] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   30.587415] usb usb5: configuration #1 chosen from 1 choice
[   30.587441] hub 5-0:1.0: USB hub found
[   30.587447] hub 5-0:1.0: 8 ports detected
[   30.616030] ata_piix 0000:00:1f.1: version 2.10ac1
[   30.616049] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[   30.616069] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   30.616138] ata1: PATA max UDMA/133 cmd 0x00000000000101f0 ctl 0x00000000000103f6 bmdma 0x00000000000120b0 irq 14
[   30.616169] ata2: PATA max UDMA/133 cmd 0x0000000000010170 ctl 0x0000000000010376 bmdma 0x00000000000120b8 irq 15
[   30.616191] scsi0 : ata_piix
[   30.674102] ata1.00: ATAPI, max UDMA/66
[   30.682794] usb 1-2: device not accepting address 2, error -71
[   30.711159] ata1.00: configured for UDMA/66
[   30.711183] scsi1 : ata_piix
[   30.749655] ATA: abnormal status 0x7F on port 0x0000000000010177
[   30.751317] scsi 0:0:0:0: CD-ROM            MATSHITA DVD-R   UJ-857D  KBVB PQ: 0 ANSI: 5
[   30.752083] ata_piix 0000:00:1f.2: MAP [ P0 P2 XX XX ]
[   30.752088] ata_piix 0000:00:1f.2: invalid MAP value 0
[   30.767420] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0019e3fffe9d9b20]
[   30.779077] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 19
[   30.779106] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   30.779149] ata3: SATA max UDMA/133 cmd 0x00000000000120c8 ctl 0x00000000000120ee bmdma 0x00000000000120a0 irq 19
[   30.779190] ata4: SATA max UDMA/133 cmd 0x00000000000120c0 ctl 0x00000000000120ea bmdma 0x00000000000120a8 irq 19
[   30.779205] scsi2 : ata_piix
[   30.825076] ATA: abnormal status 0x7F on port 0x00000000000120cf
[   30.836198] ATA: abnormal status 0x7F on port 0x00000000000120cf
[   30.837224] ata3.01: ata_hpa_resize 1: sectors = 390721968, hpa_sectors = 390721968
[   30.837232] ata3.01: ATA-7: TOSHIBA MK2035GSS, DK021B, max UDMA/100
[   30.837238] ata3.01: 390721968 sectors, multi 16: LBA48 NCQ (depth 0/4)
[   30.838526] ata3.01: ata_hpa_resize 1: sectors = 390721968, hpa_sectors = 390721968
[   30.838533] ata3.01: configured for UDMA/100
[   30.838559] scsi3 : ata_piix
[   30.880821] ATA: abnormal status 0x7F on port 0x00000000000120c7
[   30.880896] scsi 2:0:1:0: Direct-Access     ATA      TOSHIBA MK2035GS DK02 PQ: 0 ANSI: 5
[   30.888942] SCSI device sda: 390721968 512-byte hdwr sectors (200050 MB)
[   30.888954] sda: Write Protect is off
[   30.888956] sda: Mode Sense: 00 3a 00 00
[   30.888971] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   30.889016] SCSI device sda: 390721968 512-byte hdwr sectors (200050 MB)
[   30.889025] sda: Write Protect is off
[   30.889027] sda: Mode Sense: 00 3a 00 00
[   30.889042] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   30.889046]  sda:sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[   30.896558] Uniform CD-ROM driver Revision: 3.20
[   30.896614] sr 0:0:0:0: Attached scsi CD-ROM sr0
[   30.921657] usb 5-4: new high speed USB device using ehci_hcd and address 3
[   30.940652]  sda1 sda2 sda3 sda4 sda5
[   30.940842] sd 2:0:1:0: Attached scsi disk sda
[   30.944057] sr 0:0:0:0: Attached scsi generic sg0 type 5
[   30.944075] sd 2:0:1:0: Attached scsi generic sg1 type 0
[   31.054031] usb 5-4: configuration #1 chosen from 1 choice
[   31.251639] Attempting manual resume
[   31.251643] swsusp: Resume From Partition 8:5
[   31.251645] PM: Checking swsusp image.
[   31.251908] PM: Resume from disk failed.
[   31.262037] EXT3-fs: INFO: recovery required on readonly filesystem.
[   31.262043] EXT3-fs: write access will be enabled during recovery.
[   31.661245] usb 1-2: new full speed USB device using uhci_hcd and address 4
[   31.853719] usb 1-2: configuration #1 chosen from 1 choice
[   32.101014] usb 3-2: new full speed USB device using uhci_hcd and address 2
[   32.266033] usb 3-2: configuration #1 chosen from 1 choice
[   32.488282] usb 4-1: new full speed USB device using uhci_hcd and address 2
[   32.654867] usb 4-1: configuration #1 chosen from 1 choice
[   32.657980] usbcore: registered new interface driver hiddev
[   32.661503] input: Apple Computer Apple Internal Keyboard / Trackpad as /class/input/input1
[   32.661517] input: USB HID v1.11 Keyboard [Apple Computer Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.0-2
[   32.665413] input: Apple Computer Apple Internal Keyboard / Trackpad as /class/input/input2
[   32.665421] input: USB HID v1.11 Device [Apple Computer Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.0-2
[   32.681887] input: HID 05ac:1000 as /class/input/input3
[   32.681899] input: USB HID v1.11 Keyboard [HID 05ac:1000] on usb-0000:00:1d.3-1
[   32.699847] input: HID 05ac:1000 as /class/input/input4
[   32.699881] input: USB HID v1.11 Mouse [HID 05ac:1000] on usb-0000:00:1d.3-1
[   32.699896] usbcore: registered new interface driver usbhid
[   32.699901] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   32.963412] kjournald starting.  Commit interval 5 seconds
[   32.963448] EXT3-fs: recovery complete.
[   32.967548] EXT3-fs: mounted filesystem with ordered data mode.
[   44.444958] agpgart: Detected an Intel 945GM Chipset.
[   44.446056] agpgart: Detected 16124K stolen memory.
[   44.461412] agpgart: AGP aperture is 256M @ 0x80000000
[   44.461983] intel_rng: FWH not detected
[   44.533133] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   44.536280] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   44.613128] iTCO_vendor_support: vendor-support=0
[   44.615634] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[   44.615734] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x0460)
[   44.615780] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   44.641898] applesmc: Apple MacBook detected:
[   44.641902] applesmc:  - Model with accelerometer
[   44.641904] applesmc:  - Model without light sensors and backlight
[   44.641906] applesmc:  - Model with 7 temperature sensors
[   44.698457] applesmc: device successfully initialized (0xe0, 0x00).
[   44.698462] applesmc: device successfully initialized.
[   44.698662] applesmc: 1 fans found.
[   44.699485] input: applesmc as /class/input/input5
[   44.699507] applesmc: driver successfully loaded.
[   44.791165] usbcore: registered new interface driver xpad
[   44.791172] drivers/usb/input/xpad.c: driver for Xbox controllers v0.1.6
[   44.879212] appletouch Geyser 3 inited.
[   44.879532] input: appletouch as /class/input/input6
[   44.879978] usbcore: registered new interface driver appletouch
[   44.884556] input: Apple Mac mini infrared remote control driver as /class/input/input7
[   44.884728] usbcore: registered new interface driver appleir
[   44.884731] ubuntu/mactel/appleir.c: v1.1:USB Apple MacMini IR Receiver driver
[   44.900163] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   44.900178] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   44.900210] sky2 0000:01:00.0: v1.13 addr 0x90200000 irq 16 Yukon-EC (0xb6) rev 2
[   44.900473] sky2 eth0: addr 00:1b:63:1b:d1:44
[   44.948217] sky2 eth0: enabling interface
[   44.950092] sky2 eth0: ram buffer 48K
[   45.175102] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
[   45.175128] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   45.193907] hda_codec: STAC922x, Apple subsys_id=106b2200
[   45.329665] NET: Registered protocol family 17
[   45.382290] hda_intel: azx_get_response timeout, switching to polling mode...
[   45.409404] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control rx
[   45.528192] fuse init (API version 7.8)
[   45.635538] lp: driver loaded but no devices found
[   45.807170] Adding 499992k swap on /dev/disk/by-uuid/56970465-d2eb-42b9-a55d-7d032d522b58.  Priority:-1 extents:1 across:499992k
[   46.007830] EXT3 FS on sda3, internal journal
[   46.157932] NTFS driver 2.1.28 [Flags: R/O MODULE].
[   46.248569] NTFS volume version 3.1.
[   49.178017] input: Power Button (FF) as /class/input/input8
[   49.178043] ACPI: Power Button (FF) [PWRF]
[   49.178086] input: Lid Switch as /class/input/input9
[   49.178106] ACPI: Lid Switch [LID0]
[   49.178140] input: Power Button (CM) as /class/input/input10
[   49.178162] ACPI: Power Button (CM) [PWRB]
[   49.178195] input: Sleep Button (CM) as /class/input/input11
[   49.178212] ACPI: Sleep Button (CM) [SLPB]
[   49.323483] ACPI: AC Adapter [ADP1] (on-line)
[   49.331802] No dock devices found.
[   49.342013] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   49.350998] ibm_acpi: ec object not found
[   49.421854] ACPI: Battery Slot [BAT0] (battery present)
[   49.431772] Using specific hotkey driver
[   49.470859] pcc_acpi: loading...
[   51.693393] NET: Registered protocol family 10
[   51.693478] lo: Disabled Privacy Extensions
[   54.326911] ppdev: user-space parallel port driver
[   56.394826] [drm] Initialized drm 1.1.0 20060810
[   56.397483] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[   56.397710] [drm] Initialized i915 1.6.0 20060119 on minor 0

---

### Post by Torajima on 2007-07-13
Oh, and here is the output from modprobe:
> 
/lib/modules/2.6.20-16-generic/kernel/drivers/infiniband/core/ib_mad.ko
/lib/modules/2.6.20-16-generic/kernel/drivers/infiniband/core/ib_umad.ko
/lib/modules/2.6.20-16-generic/madwifi/ath_rate_onoe.ko
/lib/modules/2.6.20-16-generic/madwifi/wlan_xauth.ko
/lib/modules/2.6.20-16-generic/madwifi/wlan_acl.ko
/lib/modules/2.6.20-16-generic/madwifi/wlan_tkip.ko
/lib/modules/2.6.20-16-generic/madwifi/wlan.ko
/lib/modules/2.6.20-16-generic/madwifi/ath_pci.ko
/lib/modules/2.6.20-16-generic/madwifi/ath_rate_amrr.ko
/lib/modules/2.6.20-16-generic/madwifi/wlan_wep.ko
/lib/modules/2.6.20-16-generic/madwifi/wlan_ccmp.ko
/lib/modules/2.6.20-16-generic/madwifi/wlan_scan_sta.ko
/lib/modules/2.6.20-16-generic/madwifi/ath_rate_sample.ko
/lib/modules/2.6.20-16-generic/madwifi/wlan_scan_ap.ko

---

### Post by kevdog on 2007-07-13
I dont see anything about your network controller in the output.  Is that the whole dmesg???? Are you sure some didnt get cut off??

What about
sudo modprobe -l | grep mad

---

### Post by Torajima on 2007-07-13
> **kevdog said:**
> I dont see anything about your network controller in the output.  Is that the whole dmesg???? Are you sure some didnt get cut off??

What about
sudo modprobe -l | grep mad

Please see previous post for output from modprobe.

And I'll check and see if dmesg got cut off...

---

### Post by Torajima on 2007-07-13
I checked, that was indeed my entire dmesg...

---

### Post by kevdog on 2007-07-13
I definitely cant help you on this one.  With no error message, its very difficult to debug.  There are other logs in the /var/log directory such as boot, syslog, debug.  I would peruse through them and see if you can find anything related to your network adapter.

---

### Post by Torajima on 2007-07-13
Thanks for trying to help. If nothing else, I guess I can reinstall Ubuntu... but I've spent an enormous amount of time tweaking the os, and would hate to lose everything I've done.

---

### Post by kevdog on 2007-07-13
If I had to reinstall everything I would cry.  Ive done so many things to the system and havent been responsible about keeping a journal.  I think I would cry:(

---

