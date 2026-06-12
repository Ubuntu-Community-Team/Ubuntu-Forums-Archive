---
title: "Problem with connecting WPA Dell Wireless 1395"
date: 2008-07-16
forum: Networking &amp; Wireless
---

### Post by alien0101 on 2008-07-16
hi

I am having Dell Vostro 1500 notebook . My wireless card is Dell Wireless 1395.

I have installed latest Ububtu 8.04 and also upgraded.

Now I am using restricted wireless driver "wl"

I can see all the wireless networks but I am not able to connect to my wireless network which is configured with WPA encryption.

I am able to connect to unsecured network.

Any suggestions?

Earlier I tried with ndiswrapper and got same results..

I am not sure what else information I can provide.

---

### Post by alien0101 on 2008-07-16
Hey Guys,

I am here stuck with issue . Can anyone help?

Is there some problem with WPA connection in Ubuntu?

---

### Post by stavka on 2008-07-16
I am having the same problem with my vostro 1500. I am able to connect to WPA2 networks though. Check out my post [http://ubuntuforums.org/showthread.php?t=860820](http://ubuntuforums.org/showthread.php?t=860820) , no responses the yet..

---

### Post by mikewhatever on 2008-07-16
> **alien0101 said:**
> Hey Guys,

I am here stuck with issue . Can anyone help?

Is there some problem with WPA connection in Ubuntu?

Nope, no problem whatsoever with both WPA and WPA2. The problem might be with that wireless card, another Broadcom crappy product.

---

### Post by stavka on 2008-07-16
well, it is crappy, but it works in windows
where should we search for solution ?
I would hate to go back to windows just because of this

---

### Post by alien0101 on 2008-07-16
I think most of users facing this issue . 
Cannot we escalate this to ububtu team?

---

### Post by mikewhatever on 2008-07-16
> **stavka said:**
> well, it is crappy, but it works in windows
where should we search for solution ?
I would hate to go back to windows just because of this

Why does it matter if it works in Windows or not? Would it make you feel better if it didn't? Have you tried searching the forums?

---

### Post by moore.bryan on 2008-07-16
starting incredibly basic, do you have wpa_supplicant installed?

---

### Post by alien0101 on 2008-07-16
Following is the output of some of commands

uname -r
2.6.24-19-generic


lspci:

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
0c:00.0 Network controller: Broadcom Corporation BCM4310 USB Controller (rev 01)


lsmod | grep wl
wl                   1062164  0
ieee80211_crypt         7040  2 ieee80211_crypt_tkip,wl

dmesg
[   78.186390] PCI: Setting latency timer of device 0000:0c:00.0 to 64
[   78.212320] ieee80211_crypt: registered algorithm 'TKIP'
[   78.212602] eth1: Broadcom BCM4315 802.11 Wireless Controller 5.10.18.0
[   78.256391] ACPI: PCI interrupt for device 0000:0c:00.0 disabled
[   78.256621] ACPI: PCI Interrupt 0000:0c:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   78.256644] PCI: Setting latency timer of device 0000:0c:00.0 to 64
[   78.271317] eth1: Broadcom BCM4315 802.11 Wireless Controller 5.10.18.0
[   80.909581] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[   88.337606] eth1: no IPv6 routers present
[  101.063601] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[  103.549191] eth1: no IPv6 routers present
[  120.997215] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[  128.997664] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[  130.457999] eth1: no IPv6 routers present
[  136.279672] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[  138.370379] eth1: no IPv6 routers present
[  147.983095] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[  153.907683] eth1: no IPv6 routers present
[  161.665872] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[  165.134747] eth1: no IPv6 routers present
[  254.729462] CPU0 attaching NULL sched-domain.
[  254.729477] CPU1 attaching NULL sched-domain.
[  254.759926] CPU0 attaching sched-domain:
[  254.759939]  domain 0: span 03
[  254.759947]   groups: 01 02
[  254.759954]   domain 1: span 03
[  254.759962]    groups: 03
[  254.759967] CPU1 attaching sched-domain:
[  254.759974]  domain 0: span 03
[  254.759978]   groups: 02 01
[  254.759987]   domain 1: span 03
[  254.759991]    groups: 03
[  259.229089] b44: eth0: Link is up at 100 Mbps, full duplex.
[  259.229098] b44: eth0: Flow control is off for TX and off for RX.
[  259.234121] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  269.486251] eth0: no IPv6 routers present
[  374.511007] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[  376.699411] eth1: no IPv6 routers present

sudo lshw -C network

*-network              
       description: Wireless interface
       product: BCM4310 USB Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 01
       serial: 00:16:44:c0:e2:b3
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl latency=0 module=wl multicast=yes wireless=IEEE 802.11bg
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:1d:09:da:93:4e
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.0.101 latency=64 link=yes module=ssb multicast=yes port=twisted pair speed=100MB/s

---

### Post by alien0101 on 2008-07-16
Yes I am having wpa_supplicant installed.

---

### Post by moore.bryan on 2008-07-16
could you try to connect to one of your protected networks and then report the relevant messages in dmesg?

also, what does ```
dmesg | grep wifi
``` give you?

---

### Post by alien0101 on 2008-07-17
dmesg | grep wifi 
gives nothing

following is output of dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-19-generic (buildd@terranova) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Fri Jul 11 23:41:49 UTC 2008 (Ubuntu 2.6.24-19.36-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007f66d800 (usable)
[    0.000000]  BIOS-e820: 000000007f66d800 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000f8000000 - 00000000fc000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed18000 - 00000000fed1c000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000feda0000 - 00000000feda6000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] 1142MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 521837) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   521837
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   521837
[    0.000000] On node 0 totalpages: 521837
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2284 pages used for memmap
[    0.000000]   HighMem zone: 290177 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.4 present.
[    0.000000] ACPI: RSDP signature @ 0xC00FBBF0 checksum 0
[    0.000000] ACPI: RSDP 000FBBF0, 0024 (r2 DELL  )
[    0.000000] ACPI: XSDT 7F66F200, 005C (r1 DELL    M08     27D80203 ASL        61)
[    0.000000] ACPI: FACP 7F66F09C, 00F4 (r4 DELL    M08     27D80203 ASL        61)
[    0.000000] ACPI: DSDT 7F66F800, 5658 (r2 INT430 SYSFexxx     1001 INTL 20050624)
[    0.000000] ACPI: FACS 7F67E000, 0040
[    0.000000] ACPI: HPET 7F66F300, 0038 (r1 DELL    M08            1 ASL        61)
[    0.000000] ACPI: APIC 7F66F400, 0068 (r1 DELL    M08     27D80203 ASL        47)
[    0.000000] ACPI: MCFG 7F66F3C0, 003E (r16 DELL    M08     27D80203 ASL        61)
[    0.000000] ACPI: SLIC 7F66F49C, 0176 (r1 DELL    M08     27D80203 ASL        61)
[    0.000000] ACPI: BOOT 7F66EFC0, 0028 (r1 DELL    M08     27D80203 ASL        61)
[    0.000000] ACPI: SSDT 7F66D9FE, 04CC (r1  PmRef    CpuPm     3000 INTL 20050624)
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:15 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 6:15 APIC version 20
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:78000000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 517761
[    0.000000] Kernel command line: root=UUID=f6969c48-c6e3-47a8-a6b5-faf17b5d2f92 ro quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1396.536 MHz processor.
[    8.256861] Console: colour VGA+ 80x25
[    8.256866] console [tty0] enabled
[    8.257155] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    8.257491] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    8.369139] Memory: 2057520k/2087348k available (2177k kernel code, 28636k reserved, 1006k data, 368k init, 1169844k highmem)
[    8.369148] virtual kernel memory layout:
[    8.369149]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[    8.369150]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    8.369151]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[    8.369152]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    8.369154]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
[    8.369155]       .data : 0xc0320474 - 0xc041bdc4   (1006 kB)
[    8.369156]       .text : 0xc0100000 - 0xc0320474   (2177 kB)
[    8.369160] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[    8.369203] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[    8.369378] hpet clockevent registered
[    8.449357] Calibrating delay using timer specific routine.. 2796.54 BogoMIPS (lpj=5593085)
[    8.449380] Security Framework initialized
[    8.449387] SELinux:  Disabled at boot.
[    8.449402] AppArmor: AppArmor initialized
[    8.449406] Failure registering capabilities with primary security module.
[    8.449416] Mount-cache hash table entries: 512
[    8.449550] Initializing cgroup subsys ns
[    8.449556] Initializing cgroup subsys cpuacct
[    8.449567] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e39d 00000000 00000001 00000001
[    8.449576] monitor/mwait feature present.
[    8.449578] using mwait in idle threads.
[    8.449583] CPU: L1 I cache: 32K, L1 D cache: 32K
[    8.449585] CPU: L2 cache: 2048K
[    8.449588] CPU: Physical Processor ID: 0
[    8.449590] CPU: Processor Core ID: 0
[    8.449592] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e39d 00000000 00000001 00000001
[    8.449603] Compat vDSO mapped to ffffe000.
[    8.449617] Checking 'hlt' instruction... OK.
[    8.465796] SMP alternatives: switching to UP code
[    8.467698] Early unpacking initramfs... done
[    8.874496] ACPI: Core revision 20070126
[    8.874545] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[    8.878765] CPU0: Intel(R) Core(TM)2 Duo CPU     T5270  @ 1.40GHz stepping 0d
[    8.878781] SMP alternatives: switching to SMP code
[    8.879575] Booting processor 1/1 eip 3000
[    8.889830] Initializing CPU#1
[    8.969162] Calibrating delay using timer specific routine.. 2793.03 BogoMIPS (lpj=5586061)
[    8.969169] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e39d 00000000 00000001 00000001
[    8.969176] monitor/mwait feature present.
[    8.969179] CPU: L1 I cache: 32K, L1 D cache: 32K
[    8.969181] CPU: L2 cache: 2048K
[    8.969183] CPU: Physical Processor ID: 0
[    8.969185] CPU: Processor Core ID: 1
[    8.969187] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e39d 00000000 00000001 00000001
[    8.969816] CPU1: Intel(R) Core(TM)2 Duo CPU     T5270  @ 1.40GHz stepping 0d
[    8.969842] Total of 2 processors activated (5589.57 BogoMIPS).
[    8.970043] ENABLING IO-APIC IRQs
[    8.970238] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    9.117227] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    9.137237] Brought up 2 CPUs
[    9.137263] CPU0 attaching sched-domain:
[    9.137266]  domain 0: span 03
[    9.137268]   groups: 01 02
[    9.137272] CPU1 attaching sched-domain:
[    9.137273]  domain 0: span 03
[    9.137275]   groups: 02 01
[    9.137517] net_namespace: 64 bytes
[    9.137529] Booting paravirtualized kernel on bare hardware
[    9.138067] Time: 22:32:44  Date: 07/16/08
[    9.138096] NET: Registered protocol family 16
[    9.138308] EISA bus registered
[    9.138313] ACPI: bus type pci registered
[    9.148951] PCI: PCI BIOS revision 2.10 entry at 0xfad46, last bus=14
[    9.148954] PCI: Using configuration type 1
[    9.148973] Setting up standard PCI resources
[    9.158579] ACPI: EC: Look up EC in DSDT
[    9.212363] ACPI: Interpreter enabled
[    9.212368] ACPI: (supports S0 S3 S4 S5)
[    9.212384] ACPI: Using IOAPIC for interrupt routing
[    9.237133] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    9.238229] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    9.238234] PCI quirk: region 1080-10bf claimed by ICH6 GPIO
[    9.239682] PCI: Transparent bridge - 0000:00:1e.0
[    9.239732] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    9.240293] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
[    9.240491] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    9.240644] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    9.240792] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[    9.255030] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 *11)
[    9.255175] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *10
[    9.255316] ACPI: PCI Interrupt Link [LNKC] (IRQs 9 10 11) *4
[    9.255456] ACPI: PCI Interrupt Link [LNKD] (IRQs *5 7 9 10 11)
[    9.255596] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    9.255740] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[    9.255882] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 *7 9 10 11 12 14 15)
[    9.256012] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    9.256188] Linux Plug and Play Support v0.97 (c) Adam Belay
[    9.256224] pnp: PnP ACPI init
[    9.256232] ACPI: bus type pnp registered
[    9.304654] pnpacpi: exceeded the max number of mem resources: 12
[    9.304910] pnp: PnP ACPI: found 12 devices
[    9.304913] ACPI: ACPI bus type pnp unregistered
[    9.304917] PnPBIOS: Disabled by ACPI PNP
[    9.305165] PCI: Using ACPI for IRQ routing
[    9.305168] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    9.401016] NET: Registered protocol family 8
[    9.401019] NET: Registered protocol family 20
[    9.401056] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    9.401061] hpet0: 3 64-bit timers, 14318180 Hz
[    9.402099] AppArmor: AppArmor Filesystem Enabled
[    9.405008] Time: tsc clocksource has been installed.
[    9.405022] Switched to high resolution mode on CPU 0
[    9.405133] Switched to high resolution mode on CPU 1
[    9.420995] system 00:05: ioport range 0xc80-0xcff could not be reserved
[    9.421004] system 00:08: iomem range 0xfed00000-0xfed003ff has been reserved
[    9.421012] system 00:09: ioport range 0x900-0x97f has been reserved
[    9.421015] system 00:09: ioport range 0x4d0-0x4d1 has been reserved
[    9.421018] system 00:09: ioport range 0x1000-0x1005 has been reserved
[    9.421021] system 00:09: ioport range 0x1008-0x100f has been reserved
[    9.421028] system 00:0a: ioport range 0xf400-0xf4fe has been reserved
[    9.421031] system 00:0a: ioport range 0x1006-0x1007 has been reserved
[    9.421035] system 00:0a: ioport range 0x100a-0x1059 could not be reserved
[    9.421038] system 00:0a: ioport range 0x1060-0x107f has been reserved
[    9.421041] system 00:0a: ioport range 0x1080-0x10bf has been reserved
[    9.421044] system 00:0a: ioport range 0x10c0-0x10df has been reserved
[    9.421047] system 00:0a: ioport range 0x1010-0x102f has been reserved
[    9.421050] system 00:0a: ioport range 0x809-0x809 has been reserved
[    9.421058] system 00:0b: iomem range 0x0-0x9efff could not be reserved
[    9.421061] system 00:0b: iomem range 0x9f000-0x9ffff could not be reserved
[    9.421065] system 00:0b: iomem range 0xc0000-0xcffff could not be reserved
[    9.421068] system 00:0b: iomem range 0xe0000-0xfffff could not be reserved
[    9.421071] system 00:0b: iomem range 0x100000-0x7f66d7ff could not be reserved
[    9.421075] system 00:0b: iomem range 0x7f66d800-0x7f6fffff could not be reserved
[    9.421078] system 00:0b: iomem range 0x7f700000-0x7f7fffff could not be reserved
[    9.421082] system 00:0b: iomem range 0x7f700000-0x7fefffff could not be reserved
[    9.421085] system 00:0b: iomem range 0xfff00000-0xffffffff could not be reserved
[    9.421089] system 00:0b: iomem range 0xffa00000-0xffafffff has been reserved
[    9.421092] system 00:0b: iomem range 0xfec00000-0xfec0ffff could not be reserved
[    9.421096] system 00:0b: iomem range 0xfee00000-0xfee0ffff could not be reserved
[    9.451573] PCI: Bridge: 0000:00:1c.0
[    9.451576]   IO window: disabled.
[    9.451582]   MEM window: disabled.
[    9.451587]   PREFETCH window: disabled.
[    9.451594] PCI: Bridge: 0000:00:1c.1
[    9.451596]   IO window: disabled.
[    9.451602]   MEM window: fe800000-fe8fffff
[    9.451607]   PREFETCH window: disabled.
[    9.451614] PCI: Bridge: 0000:00:1c.3
[    9.451617]   IO window: d000-dfff
[    9.451624]   MEM window: fe600000-fe7fffff
[    9.451629]   PREFETCH window: f0000000-f01fffff
[    9.451636] PCI: Bridge: 0000:00:1e.0
[    9.451638]   IO window: disabled.
[    9.451644]   MEM window: fe500000-fe5fffff
[    9.451649]   PREFETCH window: disabled.
[    9.451684] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
[    9.451692] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    9.451721] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 17 (level, low) -> IRQ 17
[    9.451727] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[    9.451755] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 18
[    9.451762] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[    9.451778] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    9.451790] NET: Registered protocol family 2
[    9.488991] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    9.489247] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    9.489727] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    9.489951] TCP: Hash tables configured (established 131072 bind 65536)
[    9.489954] TCP reno registered
[    9.501072] checking if image is initramfs... it is
[   10.304841] Freeing initrd memory: 7317k freed
[   10.305000] Simple Boot Flag at 0x79 set to 0x1
[   10.305695] audit: initializing netlink socket (disabled)
[   10.305709] audit(1216247564.813:1): initialized
[   10.305932] highmem bounce pool size: 64 pages
[   10.308172] VFS: Disk quotas dquot_6.5.1
[   10.308258] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   10.308408] io scheduler noop registered
[   10.308411] io scheduler anticipatory registered
[   10.308413] io scheduler deadline registered
[   10.308426] io scheduler cfq registered (default)
[   10.308438] Boot video device is 0000:00:02.0
[   10.308701] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   10.308768] assign_interrupt_mode Found MSI capability
[   10.308824] Allocate Port Service[0000:00:1c.0:pcie00]
[   10.308862] Allocate Port Service[0000:00:1c.0:pcie02]
[   10.308975] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   10.309041] assign_interrupt_mode Found MSI capability
[   10.309094] Allocate Port Service[0000:00:1c.1:pcie00]
[   10.309129] Allocate Port Service[0000:00:1c.1:pcie02]
[   10.309243] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   10.309309] assign_interrupt_mode Found MSI capability
[   10.309362] Allocate Port Service[0000:00:1c.3:pcie00]
[   10.309397] Allocate Port Service[0000:00:1c.3:pcie02]
[   10.309692] isapnp: Scanning for PnP cards...
[   10.664113] isapnp: No Plug & Play device found
[   10.693230] Real Time Clock Driver v1.12ac
[   10.693388] hpet_resources: 0xfed00000 is busy
[   10.693451] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   10.694752] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   10.694826] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   10.694934] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   10.698131] serio: i8042 KBD port at 0x60,0x64 irq 1
[   10.698136] serio: i8042 AUX port at 0x60,0x64 irq 12
[   10.716710] mice: PS/2 mouse device common for all mice
[   10.716831] EISA: Probing bus 0 at eisa.0
[   10.716839] Cannot allocate resource for EISA slot 1
[   10.716875] EISA: Detected 0 cards.
[   10.716878] cpuidle: using governor ladder
[   10.716880] cpuidle: using governor menu
[   10.716969] NET: Registered protocol family 1
[   10.716999] Using IPI No-Shortcut mode
[   10.717028] registered taskstats version 1
[   10.717171]   Magic number: 0:22:553
[   10.717231]   hash matches device PNP0C0F:04
[   10.717241] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   10.717243] EDD information not available.
[   10.717442] Freeing unused kernel memory: 368k freed
[   10.719884] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   11.977834] fuse init (API version 7.9)
[   12.000939] ACPI: SSDT 7F66E534, 0244 (r1  PmRef  Cpu0Ist     3000 INTL 20050624)
[   12.001191] ACPI: SSDT 7F66DECA, 05E5 (r1  PmRef  Cpu0Cst     3001 INTL 20050624)
[   12.001821] Monitor-Mwait will be used to enter C-1 state
[   12.001824] Monitor-Mwait will be used to enter C-2 state
[   12.001827] Monitor-Mwait will be used to enter C-3 state
[   12.001962] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   12.001968] ACPI: Processor [CPU0] (supports 8 throttling states)
[   12.002226] ACPI: SSDT 7F66E778, 00C4 (r1  PmRef  Cpu1Ist     3000 INTL 20050624)
[   12.002457] ACPI: SSDT 7F66E4AF, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20050624)
[   12.003338] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[   12.003344] ACPI: Processor [CPU1] (supports 8 throttling states)
[   12.010672] ACPI: Thermal Zone [THM] (25 C)
[   12.400895] usbcore: registered new interface driver usbfs
[   12.400920] usbcore: registered new interface driver hub
[   12.400949] usbcore: registered new device driver usb
[   12.402244] USB Universal Host Controller Interface driver v3.0
[   12.402295] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 20 (level, low) -> IRQ 19
[   12.402307] PCI: Setting latency timer of device 0000:00:1a.0 to 64
[   12.402312] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[   12.402527] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[   12.402562] uhci_hcd 0000:00:1a.0: irq 19, io base 0x00006f20
[   12.402704] usb usb1: configuration #1 chosen from 1 choice
[   12.402732] hub 1-0:1.0: USB hub found
[   12.402737] hub 1-0:1.0: 2 ports detected
[   12.509259] ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 21 (level, low) -> IRQ 20
[   12.509272] PCI: Setting latency timer of device 0000:00:1a.1 to 64
[   12.509277] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[   12.509306] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
[   12.509341] uhci_hcd 0000:00:1a.1: irq 20, io base 0x00006f00
[   12.509472] usb usb2: configuration #1 chosen from 1 choice
[   12.509499] hub 2-0:1.0: USB hub found
[   12.509505] hub 2-0:1.0: 2 ports detected
[   12.528055] SCSI subsystem initialized
[   12.555796] libata version 3.00 loaded.
[   12.611887] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 20 (level, low) -> IRQ 19
[   12.611900] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   12.611905] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   12.611932] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 3
[   12.611963] uhci_hcd 0000:00:1d.0: irq 19, io base 0x00006f80
[   12.612091] usb usb3: configuration #1 chosen from 1 choice
[   12.612119] hub 3-0:1.0: USB hub found
[   12.612125] hub 3-0:1.0: 2 ports detected
[   12.715831] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 21 (level, low) -> IRQ 20
[   12.715844] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   12.715849] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   12.715876] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 4
[   12.715906] uhci_hcd 0000:00:1d.1: irq 20, io base 0x00006f60
[   12.716040] usb usb4: configuration #1 chosen from 1 choice
[   12.716067] hub 4-0:1.0: USB hub found
[   12.716074] hub 4-0:1.0: 2 ports detected
[   12.747719] usb 1-2: new full speed USB device using uhci_hcd and address 2
[   12.819792] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 22 (level, low) -> IRQ 21
[   12.819804] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   12.819809] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   12.819835] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 5
[   12.819869] uhci_hcd 0000:00:1d.2: irq 21, io base 0x00006f40
[   12.820008] usb usb5: configuration #1 chosen from 1 choice
[   12.820035] hub 5-0:1.0: USB hub found
[   12.820041] hub 5-0:1.0: 2 ports detected
[   12.915543] usb 1-2: configuration #1 chosen from 1 choice
[   12.917463] hub 1-2:1.0: USB hub found
[   12.919438] hub 1-2:1.0: 3 ports detected
[   12.923874] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 22 (level, low) -> IRQ 21
[   12.923890] PCI: Setting latency timer of device 0000:00:1a.7 to 64
[   12.923894] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[   12.923921] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 6
[   12.927833] ehci_hcd 0000:00:1a.7: debug port 1
[   12.927841] PCI: cache line size of 32 is not supported by device 0000:00:1a.7
[   12.927848] ehci_hcd 0000:00:1a.7: irq 21, io mem 0xfed1c400
[   12.943621] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   12.943740] usb usb6: configuration #1 chosen from 1 choice
[   12.943767] hub 6-0:1.0: USB hub found
[   12.943774] hub 6-0:1.0: 4 ports detected
[   13.047721] ata_piix 0000:00:1f.1: version 2.12
[   13.047742] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 16 (level, low) -> IRQ 16
[   13.047787] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   13.049388] scsi0 : ata_piix
[   13.049464] scsi1 : ata_piix
[   13.050236] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x6fa0 irq 14
[   13.050240] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x6fa8 irq 15
[   13.267529] usb 5-2: new full speed USB device using uhci_hcd and address 2
[   13.368006] ata1.00: ATAPI: HL-DT-ST DVD+/-RW GSA-T21N, A102, max UDMA/33
[   13.401010] usb 5-2: not running at top speed; connect to a high speed hub
[   13.417497] usb 5-2: configuration #1 chosen from 1 choice
[   13.491433] Clocksource tsc unstable (delta = -4966907639 ns)
[   13.495473] Time: hpet clocksource has been installed.
[   13.501128] ata1.00: configured for UDMA/33
[   13.501241] ata2: port disabled. ignoring.
[   13.503440] scsi 0:0:0:0: CD-ROM            HL-DT-ST DVD+-RW GSA-T21N A102 PQ: 0 ANSI: 5
[   13.503538] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[   13.506724] hub 1-2:1.0: activate --> -19
[   13.514647] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 17 (level, low) -> IRQ 17
[   13.514686] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   13.514802] scsi2 : ata_piix
[   13.514978] scsi3 : ata_piix
[   13.515758] ata3: SATA max UDMA/133 cmd 0x6eb0 ctl 0x6eb8 bmdma 0x6ee0 irq 17
[   13.515761] ata4: SATA max UDMA/133 cmd 0x6ec0 ctl 0x6ec8 bmdma 0x6ee8 irq 17
[   13.525060] usb 1-2: USB disconnect, address 2
[   13.543751] usb 1-2: new full speed USB device using uhci_hcd and address 3
[   13.551446] ata3.00: ATA-8: WDC WD1600BEVT-75ZCT0, 11.01A11, max UDMA/133
[   13.551452] ata3.00: 312581808 sectors, multi 8: LBA48 NCQ (depth 0/32)
[   13.553240] ata3.00: configured for UDMA/133
[   13.560999] usb 1-2: configuration #1 chosen from 1 choice
[   13.562660] hub 1-2:1.0: USB hub found
[   13.564618] hub 1-2:1.0: 3 ports detected
[   13.677441] usb 1-2.1: new full speed USB device using uhci_hcd and address 4
[   13.725733] usb 1-2.1: configuration #1 chosen from 1 choice
[   13.835776] usb 1-2.2: new full speed USB device using uhci_hcd and address 5
[   13.883386] scsi 2:0:0:0: Direct-Access     ATA      WDC WD1600BEVT-7 11.0 PQ: 0 ANSI: 5
[   13.883800] ACPI: PCI Interrupt 0000:03:01.0[A] -> GSI 19 (level, low) -> IRQ 18
[   13.885760] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 20 (level, low) -> IRQ 19
[   13.885772] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   13.885776] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   13.885807] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 7
[   13.889721] ehci_hcd 0000:00:1d.7: debug port 1
[   13.889728] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   13.889734] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xfed1c000
[   13.936579] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[18]  MMIO=[fe5fd800-fe5fdfff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[   13.940589] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   13.940725] usb usb7: configuration #1 chosen from 1 choice
[   13.940754] hub 7-0:1.0: USB hub found
[   13.940760] hub 7-0:1.0: 6 ports detected
[   13.941120] usb 1-2.2: configuration #1 chosen from 1 choice
[   13.991244] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   14.011818] ssb: Core 0 found: Fast Ethernet (cc 0x806, rev 0x07, vendor 0x4243)
[   14.011828] ssb: Core 1 found: V90 (cc 0x807, rev 0x03, vendor 0x4243)
[   14.011837] ssb: Core 2 found: PCI (cc 0x804, rev 0x0A, vendor 0x4243)
[   14.054069] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0
[   14.054111] b44.c:v2.0
[   14.057798] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:1d:09:da:93:4e
[   14.076670] Driver 'sd' needs updating - please use bus_type methods
[   14.076766] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   14.076780] sd 2:0:0:0: [sda] Write Protect is off
[   14.076783] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   14.076803] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   14.076859] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   14.076871] sd 2:0:0:0: [sda] Write Protect is off
[   14.076874] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   14.076893] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   14.076897]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   14.084541] usb 1-2.3: new full speed USB device using uhci_hcd and address 6
[   14.101094] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[   14.101100] Uniform CD-ROM driver Revision: 3.20
[   14.101173] sr 0:0:0:0: Attached scsi CD-ROM sr0
[   14.120841]  sda1 sda3 < sda5 sda6 sda7 sda8 >
[   14.186370] sd 2:0:0:0: [sda] Attached SCSI disk
[   14.192696] sr 0:0:0:0: Attached scsi generic sg0 type 5
[   14.192720] sd 2:0:0:0: Attached scsi generic sg1 type 0
[   14.221616] usb 1-2.3: configuration #1 chosen from 1 choice
[   14.225525] usb 5-2: USB disconnect, address 2
[   14.225754] usbcore: registered new interface driver hiddev
[   14.356769] input: Broadcom Corp as /devices/pci0000:00/0000:00:1a.0/usb1/1-2/1-2.2/1-2.2:1.0/input/input2
[   14.370130] input,hidraw0: USB HID v1.11 Keyboard [Broadcom Corp] on usb-0000:00:1a.0-2.2
[   14.597008] usb 7-6: new high speed USB device using ehci_hcd and address 2
[   14.721374] Attempting manual resume
[   14.721377] swsusp: Resume From Partition 8:8
[   14.721379] PM: Checking swsusp image.
[   14.721627] PM: Resume from disk failed.
[   14.730615] usb 7-6: configuration #1 chosen from 1 choice
[   14.737054] input: Broadcom Corp as /devices/pci0000:00/0000:00:1a.0/usb1/1-2/1-2.3/1-2.3:1.0/input/input3
[   14.737660] EXT3-fs: INFO: recovery required on readonly filesystem.
[   14.737664] EXT3-fs: write access will be enabled during recovery.
[   14.761034] input,hidraw1: USB HID v1.11 Mouse [Broadcom Corp] on usb-0000:00:1a.0-2.3
[   14.761066] usbcore: registered new interface driver usbhid
[   14.761070] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   15.141131] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[394fc00016ed99c1]
[   16.716411] kjournald starting.  Commit interval 5 seconds
[   16.716450] EXT3-fs: sda7: orphan cleanup on readonly fs
[   16.716457] ext3_orphan_cleanup: deleting unreferenced inode 697619
[   16.716490] ext3_orphan_cleanup: deleting unreferenced inode 697565
[   16.716500] ext3_orphan_cleanup: deleting unreferenced inode 368818
[   16.716520] ext3_orphan_cleanup: deleting unreferenced inode 1007630
[   16.716529] EXT3-fs: sda7: 4 orphan inodes deleted
[   16.716531] EXT3-fs: recovery complete.
[   16.743269] EXT3-fs: mounted filesystem with ordered data mode.
[   26.294322] input: PC Speaker as /devices/platform/pcspkr/input/input4
[   26.330615] iTCO_vendor_support: vendor-support=0
[   26.374045] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   26.487625] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   26.531851] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   26.631549] Linux agpgart interface v0.102
[   26.779305] agpgart: Detected an Intel 965GM Chipset.
[   26.780522] agpgart: Detected 7676K stolen memory.
[   26.793177] agpgart: AGP aperture is 256M @ 0xe0000000
[   26.867380] ACPI: Battery Slot [BAT0] (battery present)
[   26.879652] ACPI: AC Adapter [AC] (on-line)
[   26.904837] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1a0b1, caps: 0xa04791/0xb00000
[   26.904844] serio: Synaptics pass-through port at isa0060/serio1/input0
[   26.913196] input: Lid Switch as /devices/virtual/input/input5
[   26.941402] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input6
[   26.944952] ACPI: Lid Switch [LID]
[   26.945015] input: Power Button (CM) as /devices/virtual/input/input7
[   27.006434] iTCO_wdt: Found a ICH8M TCO device (Version=2, TCOBASE=0x1060)
[   27.006480] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   27.006525] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   27.056345] ACPI: Power Button (CM) [PBTN]
[   27.056414] input: Sleep Button (CM) as /devices/virtual/input/input8
[   27.112333] ACPI: Sleep Button (CM) [SBTN]
[   27.243797] ricoh-mmc: Ricoh MMC Controller disabling driver
[   27.243801] ricoh-mmc: Copyright(c) Philip Langdale
[   27.243847] ricoh-mmc: Ricoh MMC controller found at 0000:03:01.2 [1180:0843] (rev 12)
[   27.243864] ricoh-mmc: Controller is now disabled.
[   27.485634] ACPI: WMI-Acer: Mapper loaded
[   27.595968] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:2e/LNXVIDEO:00/input/input9
[   27.644159] sdhci: Secure Digital Host Controller Interface driver
[   27.644163] sdhci: Copyright(c) Pierre Ossman
[   27.644206] sdhci: SDHCI controller found at 0000:03:01.1 [1180:0822] (rev 22)
[   27.644231] ACPI: PCI Interrupt 0000:03:01.1[B] -> GSI 18 (level, low) -> IRQ 22
[   27.647309] mmc0: SDHCI at 0xfe5fd400 irq 22 DMA
[   27.652087] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   27.663131] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:01/input/input10
[   27.705649] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   27.716067] ACPI: Video Device [VID1] (multi-head: yes  rom: no  post: no)
[   27.716252] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:02/input/input11
[   27.780050] ACPI: Video Device [VID2] (multi-head: yes  rom: no  post: no)
[   28.160127] usbcore: registered new interface driver ndiswrapper
[   28.571706] Bluetooth: Core ver 2.11
[   28.578281] NET: Registered protocol family 31
[   28.578284] Bluetooth: HCI device and connection manager initialized
[   28.578288] Bluetooth: HCI socket layer initialized
[   28.655486] Bluetooth: HCI USB driver ver 2.9
[   28.657108] usbcore: registered new interface driver hci_usb
[   28.771620] Linux video capture interface: v2.00
[   28.889586] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 21 (level, low) -> IRQ 20
[   28.889611] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   28.893244] uvcvideo: Found UVC 1.00 device Laptop Integrated Webcam (05a9:2640)
[   28.893572] uvcvideo: Failed to query (135) UVC control 1 (unit 0) : -32 (exp. 26).
[   28.950724] usbcore: registered new interface driver uvcvideo
[   28.950730] USB Video Class driver (v0.1.0)
[   29.975293] lp: driver loaded but no devices found
[   30.101953] Adding 1935792k swap on /dev/sda8.  Priority:-1 extents:1 across:1935792k
[   30.650854] EXT3 FS on sda7, internal journal
[   31.765384] ip_tables: (C) 2000-2006 Netfilter Core Team
[   32.239080] NET: Registered protocol family 17
[   33.929640] No dock devices found.
[   34.977775] apm: BIOS not found.
[   35.092653] ppdev: user-space parallel port driver
[   35.230268] audit(1216272796.391:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5486 profile="/usr/sbin/cupsd" namespace="default"
[   35.591613] ACPI: PCI interrupt for device 0000:03:00.0 disabled
[   35.691831] usbcore: deregistering interface driver ndiswrapper
[   35.732755] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   35.736637] usbcore: registered new interface driver ndiswrapper
[   35.814464] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   35.831120] ssb: Core 0 found: Fast Ethernet (cc 0x806, rev 0x07, vendor 0x4243)
[   35.831137] ssb: Core 1 found: V90 (cc 0x807, rev 0x03, vendor 0x4243)
[   35.831155] ssb: Core 2 found: PCI (cc 0x804, rev 0x0A, vendor 0x4243)
[   35.844105] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0
[   35.844166] b44.c:v2.0
[   35.865474] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:1d:09:da:93:4e
[   37.148284] Bluetooth: L2CAP ver 2.9
[   37.148292] Bluetooth: L2CAP socket layer initialized
[   37.230713] Bluetooth: RFCOMM socket layer initialized
[   37.230734] Bluetooth: RFCOMM TTY layer initialized
[   37.230738] Bluetooth: RFCOMM ver 1.8
[   39.662216] [drm] Initialized drm 1.1.0 20060810
[   39.666352] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[   39.666369] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   39.666474] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   46.872920] NET: Registered protocol family 10
[   46.873366] lo: Disabled Privacy Extensions
[   46.875102] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   54.218160] CPU0 attaching NULL sched-domain.
[   54.218170] CPU1 attaching NULL sched-domain.
[   54.225804] CPU0 attaching sched-domain:
[   54.225814]  domain 0: span 03
[   54.225819]   groups: 01 02
[   54.225826] CPU1 attaching sched-domain:
[   54.225830]  domain 0: span 03
[   54.225833]   groups: 02 01
[   69.507510] ieee80211_crypt: registered algorithm 'NULL'
[   69.512555] ACPI: PCI Interrupt 0000:0c:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   69.512574] PCI: Setting latency timer of device 0000:0c:00.0 to 64
[   69.536225] ieee80211_crypt: registered algorithm 'TKIP'
[   69.536648] eth1: Broadcom BCM4315 802.11 Wireless Controller 5.10.18.0
[   69.581398] ACPI: PCI interrupt for device 0000:0c:00.0 disabled
[   69.581618] ACPI: PCI Interrupt 0000:0c:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   69.581639] PCI: Setting latency timer of device 0000:0c:00.0 to 64
[   69.597009] eth1: Broadcom BCM4315 802.11 Wireless Controller 5.10.18.0
[   74.107736] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[   76.853810] eth1: no IPv6 routers present
[   90.826211] eth1: no IPv6 routers present
[  114.989797] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[  116.766711] eth1: no IPv6 routers present
[  125.763802] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[  128.513259] eth1: no IPv6 routers present
[  135.141740] eth1: no IPv6 routers present

---

### Post by alien0101 on 2008-07-17
Output of command 
sudo wpa_supplicant -w -Dwext -i eth1 -c/etc/wpa_supplicant.conf -dd 
is


Initializing interface 'eth1' conf '/etc/wpa_supplicant.conf' driver 'wext' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
Line: 2 - start of a new network block
ssid - hexdump_ascii(len=6):
     73 70 69 64 65 72                                 spider          
scan_ssid=1 (0x1)
proto: 0x3
key_mgmt: 0x2
pairwise: 0x18
group: 0x18
PSK - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid='spider'
Initializing interface (2) 'eth1'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
SIOCGIWRANGE: WE(compiled)=22 WE(source)=19 enc_capa=0xf
  capabilities: key_mgmt 0xf enc 0xf
WEXT: Operstate: linkmode=1, operstate=5
Own MAC address: 00:16:44:c0:e2:b3
wpa_driver_wext_set_wpa
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_countermeasures
wpa_driver_wext_set_drop_unencrypted
Setting scan request: 0 sec 100000 usec
Added interface eth1
RTM_NEWLINK: operstate=0 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added
RTM_NEWLINK: operstate=0 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added
State: DISCONNECTED -> SCANNING
Starting AP scan (specific SSID)
Scan SSID - hexdump_ascii(len=6):
     73 70 69 64 65 72                                 spider          
Trying to get current scan results first without requesting a new scan to speed up initial association
Scan results: -1
Failed to get scan results
Failed to get scan results - try scanning again
Setting scan request: 0 sec 0 usec
Starting AP scan (broadcast SSID)
Scan timeout - try to get results
Received 2874 bytes of scan results (14 BSSes)
Scan results: 14
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:1b:2f:03:ce:78 ssid='Sujnayak' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
1: 00:1c:f0:ea:20:6f ssid='spider' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   selected based on WPA IE
   selected WPA AP 00:1c:f0:ea:20:6f ssid='spider'
Try to find non-WPA AP
Trying to associate with 00:1c:f0:ea:20:6f (SSID='spider' freq=2462 MHz)
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
WPA: using IEEE 802.11i/D3.0
WPA: Selected cipher suites: group 8 pairwise 8 key_mgmt 2 proto 1
WPA: set AP WPA IE - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
WPA: clearing AP RSN IE
WPA: using GTK TKIP
WPA: using PTK TKIP
WPA: using KEY_MGMT WPA-PSK
WPA: Set own WPA IE default - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
No keys have been configured - skip key clearing
wpa_driver_wext_set_drop_unencrypted
State: SCANNING -> ASSOCIATING
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
wpa_driver_wext_associate
Association request to the driver failed
Setting authentication timeout: 5 sec 0 usec
EAPOL: External notification - EAP success=0
EAPOL: External notification - EAP fail=0
EAPOL: External notification - portControl=Auto
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK: operstate=0 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added
RTM_NEWLINK: operstate=0 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
Wireless event: cmd=0x8b04 len=12
RTM_NEWLINK: operstate=0 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
Wireless event: cmd=0x8b1a len=14
RTM_NEWLINK: operstate=0 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:00:00:00:00:00
Added BSSID 00:1c:f0:ea:20:6f into blacklist
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
State: ASSOCIATING -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
EAPOL: External notification - EAP success=0
RTM_NEWLINK: operstate=0 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
Wireless event: cmd=0x8c02 len=25
WEXT: Custom wireless event: 'Conn Deauth 00 07'
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:1c:00:00:20:6f
State: DISCONNECTED -> ASSOCIATED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
Associated to a new BSS: BSSID=00:1c:f0:ea:20:6f
No keys have been configured - skip key clearing
Associated with 00:1c:f0:ea:20:6f
WPA: Association event - clear replay counter
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
EAPOL: External notification - EAP success=0
EAPOL: External notification - portEnabled=1
EAPOL: SUPP_PAE entering state CONNECTING
EAPOL: SUPP_BE entering state IDLE
Setting authentication timeout: 10 sec 0 usec
Cancelling scan request
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8c03 len=20
RX EAPOL from 00:1c:f0:ea:20:6f
RX EAPOL - hexdump(len=99): 01 03 00 5f fe 00 89 00 20 00 00 00 00 00 00 00 01 13 cd d9 c9 fb 7d 3f 57 8b 59 b7 9b 4d a2 ed 05 23 89 00 56 06 89 e6 8b 54 b1 04 f7 16 9e 38 d8 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
Setting authentication timeout: 10 sec 0 usec
IEEE 802.1X RX: version=1 type=3 length=95
  EAPOL-Key type=254
  key_info 0x89 (ver=1 keyidx=0 rsvd=0 Pairwise Ack)
  key_length=32 key_data_length=0
  replay_counter - hexdump(len=8): 00 00 00 00 00 00 00 01
  key_nonce - hexdump(len=32): 13 cd d9 c9 fb 7d 3f 57 8b 59 b7 9b 4d a2 ed 05 23 89 00 56 06 89 e6 8b 54 b1 04 f7 16 9e 38 d8
  key_iv - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
WPA: RX EAPOL-Key - hexdump(len=99): 01 03 00 5f fe 00 89 00 20 00 00 00 00 00 00 00 01 13 cd d9 c9 fb 7d 3f 57 8b 59 b7 9b 4d a2 ed 05 23 89 00 56 06 89 e6 8b 54 b1 04 f7 16 9e 38 d8 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
State: ASSOCIATED -> 4WAY_HANDSHAKE
WPA: RX message 1 of 4-Way Handshake from 00:1c:f0:ea:20:6f (ver=1)
WPA: Renewed SNonce - hexdump(len=32): 06 9b e5 3e ff 03 03 16 32 71 01 7b 1a 72 71 ba f7 37 4c 95 4d d9 f1 62 3c 63 ce 5e 1c 12 6b c0
WPA: PMK - hexdump(len=32): [REMOVED]
WPA: PTK - hexdump(len=64): [REMOVED]
WPA: WPA IE for msg 2/4 - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
WPA: Sending EAPOL-Key 2/4
WPA: TX EAPOL-Key - hexdump(len=123): 01 03 00 77 fe 01 09 00 20 00 00 00 00 00 00 00 01 06 9b e5 3e ff 03 03 16 32 71 01 7b 1a 72 71 ba f7 37 4c 95 4d d9 f1 62 3c 63 ce 5e 1c 12 6b c0 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 1e a6 ad 23 ac 78 53 4f 24 4f d4 65 8e 15 0d 12 00 18 dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
RX EAPOL from 00:1c:f0:ea:20:6f
RX EAPOL - hexdump(len=123): 01 03 00 77 fe 01 c9 00 20 00 00 00 00 00 00 00 02 13 cd d9 c9 fb 7d 3f 57 8b 59 b7 9b 4d a2 ed 05 23 89 00 56 06 89 e6 8b 54 b1 04 f7 16 9e 38 d8 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 2e 53 c0 3a 65 03 3f 11 f6 68 d3 3b 33 b7 d3 4a 00 18 dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
IEEE 802.1X RX: version=1 type=3 length=119
  EAPOL-Key type=254
  key_info 0x1c9 (ver=1 keyidx=0 rsvd=0 Pairwise Install Ack MIC)
  key_length=32 key_data_length=24
  replay_counter - hexdump(len=: 00 00 00 00 00 00 00 02
  key_nonce - hexdump(len=32): 13 cd d9 c9 fb 7d 3f 57 8b 59 b7 9b 4d a2 ed 05 23 89 00 56 06 89 e6 8b 54 b1 04 f7 16 9e 38 d8
  key_iv - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  key_rsc - hexdump(len=: 00 00 00 00 00 00 00 00
  key_id (reserved) - hexdump(len=: 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): 2e 53 c0 3a 65 03 3f 11 f6 68 d3 3b 33 b7 d3 4a
WPA: RX EAPOL-Key - hexdump(len=123): 01 03 00 77 fe 01 c9 00 20 00 00 00 00 00 00 00 02 13 cd d9 c9 fb 7d 3f 57 8b 59 b7 9b 4d a2 ed 05 23 89 00 56 06 89 e6 8b 54 b1 04 f7 16 9e 38 d8 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 2e 53 c0 3a 65 03 3f 11 f6 68 d3 3b 33 b7 d3 4a 00 18 dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
WPA: Invalid EAPOL-Key MIC when using TPTK - ignoring TPTK
WPA: Could not verify EAPOL-Key MIC - dropping packet
RX EAPOL from 00:1c:f0:ea:20:6f
RX EAPOL - hexdump(len=131): 01 03 00 7f fe 03 91 00 20 00 00 00 00 00 00 00 03 74 fc 1b 63 d3 20 20 f5 7f a2 49 89 11 3d 9a 96 ad 62 91 84 5e 99 ff 1d 5b 5f 67 97 66 99 bc ba 7d 96 55 dc 89 17 10 9d e2 91 37 69 ee ea f3 f4 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 c7 88 53 ed ee 46 86 94 5c 31 64 5d 6a c0 c5 6d 00 20 78 bb 6f 29 1d 12 85 ea 02 81 94 94 42 09 03 b4 dd 1c 86 54 41 81 6f 03 ca d1 94 c0 f0 0e 33 97
IEEE 802.1X RX: version=1 type=3 length=127
  EAPOL-Key type=254
  key_info 0x391 (ver=1 keyidx=1 rsvd=0 Group Ack MIC Secure)
  key_length=32 key_data_length=32
  replay_counter - hexdump(len=: 00 00 00 00 00 00 00 03
  key_nonce - hexdump(len=32): 74 fc 1b 63 d3 20 20 f5 7f a2 49 89 11 3d 9a 96 ad 62 91 84 5e 99 ff 1d 5b 5f 67 97 66 99 bc ba
  key_iv - hexdump(len=16): 7d 96 55 dc 89 17 10 9d e2 91 37 69 ee ea f3 f4
  key_rsc - hexdump(len=: 00 00 00 00 00 00 00 00
  key_id (reserved) - hexdump(len=: 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): c7 88 53 ed ee 46 86 94 5c 31 64 5d 6a c0 c5 6d
WPA: RX EAPOL-Key - hexdump(len=131): 01 03 00 7f fe 03 91 00 20 00 00 00 00 00 00 00 03 74 fc 1b 63 d3 20 20 f5 7f a2 49 89 11 3d 9a 96 ad 62 91 84 5e 99 ff 1d 5b 5f 67 97 66 99 bc ba 7d 96 55 dc 89 17 10 9d e2 91 37 69 ee ea f3 f4 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 c7 88 53 ed ee 46 86 94 5c 31 64 5d 6a c0 c5 6d 00 20 78 bb 6f 29 1d 12 85 ea 02 81 94 94 42 09 03 b4 dd 1c 86 54 41 81 6f 03 ca d1 94 c0 f0 0e 33 97
WPA: Invalid EAPOL-Key MIC when using TPTK - ignoring TPTK
WPA: Could not verify EAPOL-Key MIC - dropping packet
RTM_NEWLINK: operstate=0 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added
EAPOL: startWhen --> 0
EAPOL: SUPP_PAE entering state CONNECTING
EAPOL: txStart
WPA: drop TX EAPOL in non-IEEE 802.1X mode (type=1 len=0)
Authentication with 00:1c:f0:ea:20:6f timed out.
BSSID 00:1c:f0:ea:20:6f blacklist count incremented to 2
wpa_driver_wext_disassociate
No keys have been configured - skip key clearing
State: 4WAY_HANDSHAKE -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
EAPOL: External notification - portEnabled=0
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: SUPP_BE entering state INITIALIZE
EAPOL: External notification - portValid=0
EAPOL: External notification - EAP success=0
Setting scan request: 0 sec 0 usec
State: DISCONNECTED -> SCANNING
Starting AP scan (specific SSID)
Scan SSID - hexdump_ascii(len=6):
     73 70 69 64 65 72                                 spider          
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8c02 len=27
WEXT: Custom wireless event: 'Conn Disassoc 00 08'
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:00:00:00:00:00
Added BSSID 00:00:00:00:00:00 into blacklist
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
State: SCANNING -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
EAPOL: External notification - EAP success=0
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added
RTM_NEWLINK: operstate=0 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added
Scan timeout - try to get results
Received 3444 bytes of scan results (17 BSSes)
Scan results: 17
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:1b:2f:03:ce:78 ssid='Sujnayak' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
1: 00:1c:f0:ea:20:6f ssid='spider' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - blacklisted
2: 00:1f:33:33:d8:3a ssid='GirlsNextDoor' wpa_ie_len=30 rsn_ie_len=26 caps=0x11
   skip - SSID mismatch
3: 00:1b:2f:e3:6c:84 ssid='GangWar' wpa_ie_len=30 rsn_ie_len=26 caps=0x11
   skip - SSID mismatch
4: 00:18:39:ba:b3:86 ssid='PRESTO' wpa_ie_len=0 rsn_ie_len=22 caps=0x11
   skip - SSID mismatch
5: 00:11:95:0b:33:0a ssid='garnersouth' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
6: 00:1c:10:93:99:0f ssid='parakh' wpa_ie_len=26 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
7: 00:1d:7e:16:09:f3 ssid='fortknox' wpa_ie_len=26 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
8: 00:1e:58:32:60:63 ssid='Lamborghini' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
9: 00:1e:e5:3a:25:5e ssid='california' wpa_ie_len=26 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
10: 00:16:b6:40:60:e8 ssid='mouseattle' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
11: 00:0f:b5:54:4b:e4 ssid='Quake' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
12: 00:14:6c:3b:7e:56 ssid='Subduction Zone' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
13: 00:0d:14:01:a1:53 ssid='redmondrockers' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
14: 00:1d:7e:20:1d:67 ssid='linksys' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
15: 00:13:10:86:a1:1c ssid='linksys' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - no WPA/RSN IE
16: 00:1c:df:c3:4e:57 ssid='Jayakumar Janakiraman' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - no WPA/RSN IE
Try to find non-WPA AP
0: 00:1b:2f:03:ce:78 ssid='Sujnayak' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
1: 00:1c:f0:ea:20:6f ssid='spider' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - blacklisted
2: 00:1f:33:33:d8:3a ssid='GirlsNextDoor' wpa_ie_len=30 rsn_ie_len=26 caps=0x11
   skip - SSID mismatch
3: 00:1b:2f:e3:6c:84 ssid='GangWar' wpa_ie_len=30 rsn_ie_len=26 caps=0x11
   skip - SSID mismatch
4: 00:18:39:ba:b3:86 ssid='PRESTO' wpa_ie_len=0 rsn_ie_len=22 caps=0x11
   skip - SSID mismatch
5: 00:11:95:0b:33:0a ssid='garnersouth' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
6: 00:1c:10:93:99:0f ssid='parakh' wpa_ie_len=26 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
7: 00:1d:7e:16:09:f3 ssid='fortknox' wpa_ie_len=26 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
8: 00:1e:58:32:60:63 ssid='Lamborghini' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
9: 00:1e:e5:3a:25:5e ssid='california' wpa_ie_len=26 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
10: 00:16:b6:40:60:e8 ssid='mouseattle' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
11: 00:0f:b5:54:4b:e4 ssid='Quake' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
12: 00:14:6c:3b:7e:56 ssid='Subduction Zone' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
13: 00:0d:14:01:a1:53 ssid='redmondrockers' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
14: 00:1d:7e:20:1d:67 ssid='linksys' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
15: 00:13:10:86:a1:1c ssid='linksys' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - SSID mismatch
16: 00:1c:df:c3:4e:57 ssid='Jayakumar Janakiraman' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - SSID mismatch
No APs found - clear blacklist and try again
Removed BSSID 00:00:00:00:00:00 from blacklist (clear)
Removed BSSID 00:1c:f0:ea:20:6f from blacklist (clear)
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:1b:2f:03:ce:78 ssid='Sujnayak' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
1: 00:1c:f0:ea:20:6f ssid='spider' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   selected based on WPA IE
   selected WPA AP 00:1c:f0:ea:20:6f ssid='spider'
Try to find non-WPA AP
Trying to associate with 00:1c:f0:ea:20:6f (SSID='spider' freq=2462 MHz)
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
WPA: using IEEE 802.11i/D3.0
WPA: Selected cipher suites: group 8 pairwise 8 key_mgmt 2 proto 1
WPA: set AP WPA IE - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
WPA: clearing AP RSN IE
WPA: using GTK TKIP
WPA: using PTK TKIP
WPA: using KEY_MGMT WPA-PSK
WPA: Set own WPA IE default - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
No keys have been configured - skip key clearing
wpa_driver_wext_set_drop_unencrypted
State: DISCONNECTED -> ASSOCIATING
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
wpa_driver_wext_associate
Association request to the driver failed
Setting authentication timeout: 5 sec 0 usec
EAPOL: External notification - EAP success=0
EAPOL: External notification - EAP fail=0
EAPOL: External notification - portControl=Auto
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8b04 len=12
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8b1a len=14
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:1c:00:00:20:6f
State: ASSOCIATING -> ASSOCIATED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
Associated to a new BSS: BSSID=00:1c:f0:ea:20:6f
No keys have been configured - skip key clearing
Associated with 00:1c:f0:ea:20:6f
WPA: Association event - clear replay counter
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
EAPOL: External notification - EAP success=0
EAPOL: External notification - portEnabled=1
EAPOL: SUPP_PAE entering state CONNECTING
EAPOL: SUPP_BE entering state IDLE
Setting authentication timeout: 10 sec 0 usec
Cancelling scan request
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8c03 len=20
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8c02 len=26
WEXT: Custom wireless event: 'Conn Success 00 00'
RX EAPOL from 00:1c:f0:ea:20:6f
RX EAPOL - hexdump(len=99): 01 03 00 5f fe 00 89 00 20 00 00 00 00 00 00 00 01 f6 47 aa dc a9 e3 e4 e4 11 4b 8e 18 0b a8 27 13 ab 12 d1 05 1e 1d 2a 1c 21 03 67 20 b0 b2 a9 db 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
Setting authentication timeout: 10 sec 0 usec
IEEE 802.1X RX: version=1 type=3 length=95
  EAPOL-Key type=254
  key_info 0x89 (ver=1 keyidx=0 rsvd=0 Pairwise Ack)
  key_length=32 key_data_length=0
  replay_counter - hexdump(len=: 00 00 00 00 00 00 00 01
  key_nonce - hexdump(len=32): f6 47 aa dc a9 e3 e4 e4 11 4b 8e 18 0b a8 27 13 ab 12 d1 05 1e 1d 2a 1c 21 03 67 20 b0 b2 a9 db
  key_iv - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  key_rsc - hexdump(len=: 00 00 00 00 00 00 00 00
  key_id (reserved) - hexdump(len=: 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
WPA: RX EAPOL-Key - hexdump(len=99): 01 03 00 5f fe 00 89 00 20 00 00 00 00 00 00 00 01 f6 47 aa dc a9 e3 e4 e4 11 4b 8e 18 0b a8 27 13 ab 12 d1 05 1e 1d 2a 1c 21 03 67 20 b0 b2 a9 db 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
State: ASSOCIATED -> 4WAY_HANDSHAKE
WPA: RX message 1 of 4-Way Handshake from 00:1c:f0:ea:20:6f (ver=1)
WPA: Renewed SNonce - hexdump(len=32): 6b cd e3 58 f0 a5 cc 70 00 4a c4 6b 42 00 ae 6c 11 30 a0 0e 78 43 2f f6 7e ce 5a 3a ca 75 bc da
WPA: PMK - hexdump(len=32): [REMOVED]
WPA: PTK - hexdump(len=64): [REMOVED]
WPA: WPA IE for msg 2/4 - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
WPA: Sending EAPOL-Key 2/4
WPA: TX EAPOL-Key - hexdump(len=123): 01 03 00 77 fe 01 09 00 20 00 00 00 00 00 00 00 01 6b cd e3 58 f0 a5 cc 70 00 4a c4 6b 42 00 ae 6c 11 30 a0 0e 78 43 2f f6 7e ce 5a 3a ca 75 bc da 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 10 58 2d 9b 4d 1e 21 17 71 f8 c4 a2 a9 fe 9c ea 00 18 dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
RX EAPOL from 00:1c:f0:ea:20:6f
RX EAPOL - hexdump(len=123): 01 03 00 77 fe 01 c9 00 20 00 00 00 00 00 00 00 02 f6 47 aa dc a9 e3 e4 e4 11 4b 8e 18 0b a8 27 13 ab 12 d1 05 1e 1d 2a 1c 21 03 67 20 b0 b2 a9 db 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 55 97 57 0d b3 04 91 fc f6 a8 24 09 d7 6e 12 59 00 18 dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
IEEE 802.1X RX: version=1 type=3 length=119
  EAPOL-Key type=254
  key_info 0x1c9 (ver=1 keyidx=0 rsvd=0 Pairwise Install Ack MIC)
  key_length=32 key_data_length=24
  replay_counter - hexdump(len=: 00 00 00 00 00 00 00 02
  key_nonce - hexdump(len=32): f6 47 aa dc a9 e3 e4 e4 11 4b 8e 18 0b a8 27 13 ab 12 d1 05 1e 1d 2a 1c 21 03 67 20 b0 b2 a9 db
  key_iv - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  key_rsc - hexdump(len=: 00 00 00 00 00 00 00 00
  key_id (reserved) - hexdump(len=: 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): 55 97 57 0d b3 04 91 fc f6 a8 24 09 d7 6e 12 59
WPA: RX EAPOL-Key - hexdump(len=123): 01 03 00 77 fe 01 c9 00 20 00 00 00 00 00 00 00 02 f6 47 aa dc a9 e3 e4 e4 11 4b 8e 18 0b a8 27 13 ab 12 d1 05 1e 1d 2a 1c 21 03 67 20 b0 b2 a9 db 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 55 97 57 0d b3 04 91 fc f6 a8 24 09 d7 6e 12 59 00 18 dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
WPA: Invalid EAPOL-Key MIC when using TPTK - ignoring TPTK
WPA: Could not verify EAPOL-Key MIC - dropping packet
RTM_NEWLINK: operstate=0 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added
RX EAPOL from 00:1c:f0:ea:20:6f
RX EAPOL - hexdump(len=131): 01 03 00 7f fe 03 91 00 20 00 00 00 00 00 00 00 03 74 fc 1b 63 d3 20 20 f5 7f a2 49 89 11 3d 9a 96 ad 62 91 84 5e 99 ff 1d 5b 5f 67 97 66 99 bc ba 7d 96 55 de 89 17 10 9d e2 91 37 69 ee ea f3 f4 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 80 c6 40 6b e8 79 e1 ce 10 20 08 d5 21 7e 5b e8 00 20 eb 4e fb 1b 40 92 88 5b d9 5b 1f 56 d5 6d cf f6 34 0f 89 e7 19 52 a9 8f b5 4e bc 50 65 8f 68 59
IEEE 802.1X RX: version=1 type=3 length=127
  EAPOL-Key type=254
  key_info 0x391 (ver=1 keyidx=1 rsvd=0 Group Ack MIC Secure)
  key_length=32 key_data_length=32
  replay_counter - hexdump(len=: 00 00 00 00 00 00 00 03
  key_nonce - hexdump(len=32): 74 fc 1b 63 d3 20 20 f5 7f a2 49 89 11 3d 9a 96 ad 62 91 84 5e 99 ff 1d 5b 5f 67 97 66 99 bc ba
  key_iv - hexdump(len=16): 7d 96 55 de 89 17 10 9d e2 91 37 69 ee ea f3 f4
  key_rsc - hexdump(len=: 00 00 00 00 00 00 00 00
  key_id (reserved) - hexdump(len=: 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): 80 c6 40 6b e8 79 e1 ce 10 20 08 d5 21 7e 5b e8
WPA: RX EAPOL-Key - hexdump(len=131): 01 03 00 7f fe 03 91 00 20 00 00 00 00 00 00 00 03 74 fc 1b 63 d3 20 20 f5 7f a2 49 89 11 3d 9a 96 ad 62 91 84 5e 99 ff 1d 5b 5f 67 97 66 99 bc ba 7d 96 55 de 89 17 10 9d e2 91 37 69 ee ea f3 f4 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 80 c6 40 6b e8 79 e1 ce 10 20 08 d5 21 7e 5b e8 00 20 eb 4e fb 1b 40 92 88 5b d9 5b 1f 56 d5 6d cf f6 34 0f 89 e7 19 52 a9 8f b5 4e bc 50 65 8f 68 59
WPA: Invalid EAPOL-Key MIC when using TPTK - ignoring TPTK
WPA: Could not verify EAPOL-Key MIC - dropping packet
EAPOL: startWhen --> 0
EAPOL: SUPP_PAE entering state CONNECTING
EAPOL: txStart
WPA: drop TX EAPOL in non-IEEE 802.1X mode (type=1 len=0)
Authentication with 00:1c:f0:ea:20:6f timed out.
Added BSSID 00:1c:f0:ea:20:6f into blacklist
wpa_driver_wext_disassociate
No keys have been configured - skip key clearing
State: 4WAY_HANDSHAKE -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
EAPOL: External notification - portEnabled=0
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: SUPP_BE entering state INITIALIZE
EAPOL: External notification - portValid=0
EAPOL: External notification - EAP success=0
Setting scan request: 0 sec 0 usec
State: DISCONNECTED -> SCANNING
Starting AP scan (broadcast SSID)
RTM_NEWLINK: operstate=0 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
Wireless event: cmd=0x8c02 len=27
WEXT: Custom wireless event: 'Conn Disassoc 00 08'
RTM_NEWLINK: operstate=0 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:00:00:00:00:00
Added BSSID 00:00:00:00:00:00 into blacklist
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
State: SCANNING -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
EAPOL: External notification - EAP success=0
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added
Scan timeout - try to get results
Received 2576 bytes of scan results (12 BSSes)
Scan results: 12
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:1b:2f:03:ce:78 ssid='Sujnayak' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
1: 00:1c:f0:ea:20:6f ssid='spider' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   selected based on WPA IE
   selected WPA AP 00:1c:f0:ea:20:6f ssid='spider'
Try to find non-WPA AP
Trying to associate with 00:1c:f0:ea:20:6f (SSID='spider' freq=2462 MHz)
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
WPA: using IEEE 802.11i/D3.0
WPA: Selected cipher suites: group 8 pairwise 8 key_mgmt 2 proto 1
WPA: set AP WPA IE - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
WPA: clearing AP RSN IE
WPA: using GTK TKIP
WPA: using PTK TKIP
WPA: using KEY_MGMT WPA-PSK
WPA: Set own WPA IE default - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
No keys have been configured - skip key clearing
wpa_driver_wext_set_drop_unencrypted
State: DISCONNECTED -> ASSOCIATING
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
wpa_driver_wext_associate
Association request to the driver failed
Setting authentication timeout: 5 sec 0 usec
EAPOL: External notification - EAP success=0
EAPOL: External notification - EAP fail=0
EAPOL: External notification - portControl=Auto
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8b04 len=12
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8b1a len=14
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:1c:00:00:20:6f
State: ASSOCIATING -> ASSOCIATED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
Associated to a new BSS: BSSID=00:1c:f0:ea:20:6f
No keys have been configured - skip key clearing
Associated with 00:1c:f0:ea:20:6f
WPA: Association event - clear replay counter
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
EAPOL: External notification - EAP success=0
EAPOL: External notification - portEnabled=1
EAPOL: SUPP_PAE entering state CONNECTING
EAPOL: SUPP_BE entering state IDLE
Setting authentication timeout: 10 sec 0 usec
Cancelling scan request
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8c03 len=20
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8c02 len=26
WEXT: Custom wireless event: 'Conn Success 00 00'
RX EAPOL from 00:1c:f0:ea:20:6f
RX EAPOL - hexdump(len=99): 01 03 00 5f fe 00 89 00 20 00 00 00 00 00 00 00 01 8c 57 b0 3e 6b 09 b6 d7 98 02 13 02 35 b7 f4 e9 eb 9c 23 31 dc 95 aa 83 27 65 82 d8 b9 f8 d0 33 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
Setting authentication timeout: 10 sec 0 usec
IEEE 802.1X RX: version=1 type=3 length=95
  EAPOL-Key type=254
  key_info 0x89 (ver=1 keyidx=0 rsvd=0 Pairwise Ack)
  key_length=32 key_data_length=0
  replay_counter - hexdump(len=: 00 00 00 00 00 00 00 01
  key_nonce - hexdump(len=32): 8c 57 b0 3e 6b 09 b6 d7 98 02 13 02 35 b7 f4 e9 eb 9c 23 31 dc 95 aa 83 27 65 82 d8 b9 f8 d0 33
  key_iv - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  key_rsc - hexdump(len=: 00 00 00 00 00 00 00 00
  key_id (reserved) - hexdump(len=: 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
WPA: RX EAPOL-Key - hexdump(len=99): 01 03 00 5f fe 00 89 00 20 00 00 00 00 00 00 00 01 8c 57 b0 3e 6b 09 b6 d7 98 02 13 02 35 b7 f4 e9 eb 9c 23 31 dc 95 aa 83 27 65 82 d8 b9 f8 d0 33 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
State: ASSOCIATED -> 4WAY_HANDSHAKE
WPA: RX message 1 of 4-Way Handshake from 00:1c:f0:ea:20:6f (ver=1)
WPA: Renewed SNonce - hexdump(len=32): 46 c1 55 2b 35 71 32 0b d3 c1 4d 6a 4e cb d0 9b fe 8a 05 2e 80 ab 8c 6e 5b 47 00 51 e3 89 f7 0d
WPA: PMK - hexdump(len=32): [REMOVED]
WPA: PTK - hexdump(len=64): [REMOVED]
WPA: WPA IE for msg 2/4 - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
WPA: Sending EAPOL-Key 2/4
WPA: TX EAPOL-Key - hexdump(len=123): 01 03 00 77 fe 01 09 00 20 00 00 00 00 00 00 00 01 46 c1 55 2b 35 71 32 0b d3 c1 4d 6a 4e cb d0 9b fe 8a 05 2e 80 ab 8c 6e 5b 47 00 51 e3 89 f7 0d 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 53 3b f1 51 17 7e 3e 06 8d 8f 7d 9a b7 12 0c b1 00 18 dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
RX EAPOL from 00:1c:f0:ea:20:6f
RX EAPOL - hexdump(len=123): 01 03 00 77 fe 01 c9 00 20 00 00 00 00 00 00 00 02 8c 57 b0 3e 6b 09 b6 d7 98 02 13 02 35 b7 f4 e9 eb 9c 23 31 dc 95 aa 83 27 65 82 d8 b9 f8 d0 33 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 f9 98 46 62 7b f9 a7 ee d7 d1 0b 33 8a 9b 65 4f 00 18 dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
IEEE 802.1X RX: version=1 type=3 length=119
  EAPOL-Key type=254
  key_info 0x1c9 (ver=1 keyidx=0 rsvd=0 Pairwise Install Ack MIC)
  key_length=32 key_data_length=24
  replay_counter - hexdump(len=: 00 00 00 00 00 00 00 02
  key_nonce - hexdump(len=32): 8c 57 b0 3e 6b 09 b6 d7 98 02 13 02 35 b7 f4 e9 eb 9c 23 31 dc 95 aa 83 27 65 82 d8 b9 f8 d0 33
  key_iv - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  key_rsc - hexdump(len=: 00 00 00 00 00 00 00 00
  key_id (reserved) - hexdump(len=: 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): f9 98 46 62 7b f9 a7 ee d7 d1 0b 33 8a 9b 65 4f
WPA: RX EAPOL-Key - hexdump(len=123): 01 03 00 77 fe 01 c9 00 20 00 00 00 00 00 00 00 02 8c 57 b0 3e 6b 09 b6 d7 98 02 13 02 35 b7 f4 e9 eb 9c 23 31 dc 95 aa 83 27 65 82 d8 b9 f8 d0 33 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 f9 98 46 62 7b f9 a7 ee d7 d1 0b 33 8a 9b 65 4f 00 18 dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
State: 4WAY_HANDSHAKE -> 4WAY_HANDSHAKE
WPA: RX message 3 of 4-Way Handshake from 00:1c:f0:ea:20:6f (ver=1)
WPA: IE KeyData - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
WPA: Sending EAPOL-Key 4/4
WPA: TX EAPOL-Key - hexdump(len=99): 01 03 00 5f fe 01 09 00 20 00 00 00 00 00 00 00 02 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 0e 5f 50 fa af 0d 8e 54 85 9c 17 04 bd 25 00 06 00 00
WPA: Installing PTK to the driver.
WPA: RSC - hexdump(len=6): 00 00 00 00 00 00
wpa_driver_wext_set_key: alg=2 key_idx=0 set_tx=1 seq_len=6 key_len=32
State: 4WAY_HANDSHAKE -> GROUP_HANDSHAKE
RX EAPOL from 00:1c:f0:ea:20:6f
RX EAPOL - hexdump(len=131): 01 03 00 7f fe 03 91 00 20 00 00 00 00 00 00 00 03 74 fc 1b 63 d3 20 20 f5 7f a2 49 89 11 3d 9a 96 ad 62 91 84 5e 99 ff 1d 5b 5f 67 97 66 99 bc ba 7d 96 55 e0 89 17 10 9d e2 91 37 69 ee ea f3 f4 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 04 aa 3f 00 dc fe fa 5c 2b 8e 4d d4 47 83 71 42 00 20 ac a4 39 22 26 87 b8 c4 eb 85 42 fb c8 e4 9d 8e e6 bb c9 8f 23 00 6a 2b b9 df ba c3 14 28 3b 54
IEEE 802.1X RX: version=1 type=3 length=127
  EAPOL-Key type=254
  key_info 0x391 (ver=1 keyidx=1 rsvd=0 Group Ack MIC Secure)
  key_length=32 key_data_length=32
  replay_counter - hexdump(len=: 00 00 00 00 00 00 00 03
  key_nonce - hexdump(len=32): 74 fc 1b 63 d3 20 20 f5 7f a2 49 89 11 3d 9a 96 ad 62 91 84 5e 99 ff 1d 5b 5f 67 97 66 99 bc ba
  key_iv - hexdump(len=16): 7d 96 55 e0 89 17 10 9d e2 91 37 69 ee ea f3 f4
  key_rsc - hexdump(len=: 00 00 00 00 00 00 00 00
  key_id (reserved) - hexdump(len=: 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): 04 aa 3f 00 dc fe fa 5c 2b 8e 4d d4 47 83 71 42
WPA: RX EAPOL-Key - hexdump(len=131): 01 03 00 7f fe 03 91 00 20 00 00 00 00 00 00 00 03 74 fc 1b 63 d3 20 20 f5 7f a2 49 89 11 3d 9a 96 ad 62 91 84 5e 99 ff 1d 5b 5f 67 97 66 99 bc ba 7d 96 55 e0 89 17 10 9d e2 91 37 69 ee ea f3 f4 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 04 aa 3f 00 dc fe fa 5c 2b 8e 4d d4 47 83 71 42 00 20 ac a4 39 22 26 87 b8 c4 eb 85 42 fb c8 e4 9d 8e e6 bb c9 8f 23 00 6a 2b b9 df ba c3 14 28 3b 54
WPA: RX message 1 of Group Key Handshake from 00:1c:f0:ea:20:6f (ver=1)
State: GROUP_HANDSHAKE -> GROUP_HANDSHAKE
WPA: Group Key - hexdump(len=32): [REMOVED]
WPA: Installing GTK to the driver (keyidx=1 tx=0).
WPA: RSC - hexdump(len=6): 00 00 00 00 00 00
wpa_driver_wext_set_key: alg=2 key_idx=1 set_tx=0 seq_len=6 key_len=32
WPA: Sending EAPOL-Key 2/2
WPA: TX EAPOL-Key - hexdump(len=99): 01 03 00 5f fe 03 11 00 20 00 00 00 00 00 00 00 03 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 5b 50 16 63 10 c4 da 2b 55 c3 34 b9 7f c6 9b c6 00 00
WPA: Key negotiation completed with 00:1c:f0:ea:20:6f [PTK=TKIP GTK=TKIP]
Cancelling authentication timeout
Removed BSSID 00:1c:f0:ea:20:6f from blacklist
State: GROUP_HANDSHAKE -> COMPLETED
CTRL-EVENT-CONNECTED - Connection to 00:1c:f0:ea:20:6f completed (auth) [id=0 id_str=]
wpa_driver_wext_set_operstate: operstate 0->1 (UP)
WEXT: Operstate: linkmode=-1, operstate=6
EAPOL: External notification - portValid=1
EAPOL: External notification - EAP success=1
EAPOL: SUPP_PAE entering state AUTHENTICATING
EAPOL: SUPP_BE entering state SUCCESS
EAP: EAP entering state DISABLED
EAPOL: SUPP_PAE entering state AUTHENTICATED
EAPOL: SUPP_BE entering state IDLE
RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added
EAPOL: startWhen --> 0
RTM_NEWLINK: operstate=1 ifi_flags=0x11003 ([UP][LOWER_UP])
WEXT: Operstate: linkmode=-1, operstate=6
Wireless event: cmd=0x8c02 len=27
WEXT: Custom wireless event: 'Conn Disassoc 00 08'
RTM_NEWLINK: operstate=1 ifi_flags=0x11003 ([UP][LOWER_UP])
WEXT: Operstate: linkmode=-1, operstate=6
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:00:00:00:00:00
Setting scan request: 0 sec 100000 usec
Added BSSID 00:1c:f0:ea:20:6f into blacklist
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
State: COMPLETED -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 1->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
EAPOL: External notification - portEnabled=0
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: SUPP_BE entering state INITIALIZE
EAPOL: External notification - portValid=0
EAPOL: External notification - EAP success=0
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added
RTM_NEWLINK: operstate=0 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added
State: DISCONNECTED -> SCANNING
Starting AP scan (specific SSID)
Scan SSID - hexdump_ascii(len=6):
     73 70 69 64 65 72                                 spider          
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8b04 len=12
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8b1a len=14
Scan timeout - try to get results
Scan results: -1
Failed to get scan results
Failed to get scan results - try scanning again
Setting scan request: 1 sec 0 usec
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:1c:00:00:20:6f
State: SCANNING -> ASSOCIATED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
Associated to a new BSS: BSSID=00:1c:f0:ea:20:6f
No keys have been configured - skip key clearing
Associated with 00:1c:f0:ea:20:6f
WPA: Association event - clear replay counter
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
EAPOL: External notification - EAP success=0
EAPOL: External notification - portEnabled=1
EAPOL: SUPP_PAE entering state CONNECTING
EAPOL: SUPP_BE entering state IDLE

---

### Post by alien0101 on 2008-07-17
I dont think this could be dirver issue as earlier I installed ndiswrapper and it was giving same problem.

Currently I am using wl driver.

Can someone guide me what could be the issue that its not able to connect to WPA access point but connect to unsecured network.

Give me atlease some pointers so that I may try to do something myself.

Is someone else facing the same issue?

---

### Post by moore.bryan on 2008-07-17
is this a usb wireless connection by any chance?

what is the output of ```
iwlist eth1 scan
```?

---

### Post by alien0101 on 2008-07-17
No this is not usb wireless...
It is in built wireless ..that came with Dell vostro 1500..

I dont think iwlist scan eth1 will give much info..
As per scanning is concerned I am getting list of all wireless networks ..and also able to connect to unsecured network..

Only problem comes when it tries to connect to WPA network

---

### Post by moore.bryan on 2008-07-17
okay, got it... sorry, i misunderstood. if you change the encryption method to something other than wpa, say wep, can you connect then?

---

### Post by alien0101 on 2008-07-17
I havnt tried that but I cannot change router settings to WEP.

Any suggestions for WPA connection

---

### Post by moore.bryan on 2008-07-17
can't change to wep? that may narrow things down, but... any way... i'm assuming you're using network-manager? have you tried [wicd]("http://wicd.sourceforge.net/")?

---

### Post by alien0101 on 2008-07-17
Yeah I followed most of the threads in forum.

I tried with WICD also , its the same problem..
It is able to get list of all networks and when I try to join WPA network, it tries for some time and after that join to unsecured network.


My other laptop which is having XP installed is able to join WPA network properly

---

### Post by moore.bryan on 2008-07-17
bear with me, as i'm relatively new to this thread and your issue...

have you read through [this]("http://ubuntuforums.org/showthread.php?t=734221") thread?

---

### Post by alien0101 on 2008-07-17
yeah I have gone to this thread earlier.

Its basically telling to remove ndiswrapper and use wl driver.

Currently I am using only wl driver.

---

### Post by moore.bryan on 2008-07-17
however, is the ndiswrapper module still loaded?
```
sudo lsmod
```

---

### Post by alien0101 on 2008-07-17
can ndiswrapper cause interferance with WPA?

---

### Post by moore.bryan on 2008-07-17
i've never heard of it, but some of the other threads loosely related to yours seem to think so. i've only had trouble/success with my madwifi stuff, so i never needed ndiswrapper... but i know what a "pita" wireless can be.

---

### Post by stavka on 2008-07-17
in my case,
wpasupplicant is installed
ndiswrapper is not
but when I run wpa_cli I get this:
```
wpa_cli v0.5.8
Copyright (c) 2004-2007, Jouni Malinen <j@w1.fi> and contributors

This program is free software. You can distribute it and/or modify it
under the terms of the GNU General Public License version 2.

Alternatively, this software may be distributed under the terms of the
BSD license. See README and COPYING for more details.


Could not connect to wpa_supplicant - re-trying

```

but I am able to connect to WPA2 networks and when I am trying to connect to WPA1 I get the following in daemon.log

```
Jul 15 23:14:27 victor-laptop NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD eth1^I^Iwext^I/var/run/wpa_supplicant0^I' 
Jul 15 23:14:27 victor-laptop NetworkManager: <info>  SUP: response was 'OK' 
Jul 15 23:14:27 victor-laptop NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
Jul 15 23:14:27 victor-laptop NetworkManager: <info>  SUP: response was 'OK' 
Jul 15 23:14:27 victor-laptop NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Jul 15 23:14:27 victor-laptop NetworkManager: <info>  SUP: response was '0' 
Jul 15 23:14:27 victor-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 616e646572736f6e' 
Jul 15 23:14:27 victor-laptop NetworkManager: <info>  SUP: response was 'OK' 
Jul 15 23:14:27 victor-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 proto WPA' 
Jul 15 23:14:27 victor-laptop NetworkManager: <info>  SUP: response was 'OK' 
Jul 15 23:14:27 victor-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt WPA-PSK' 
Jul 15 23:14:27 victor-laptop NetworkManager: <info>  SUP: response was 'OK' 
Jul 15 23:14:27 victor-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 psk <key>' 
Jul 15 23:14:27 victor-laptop NetworkManager: <info>  SUP: response was 'OK' 
Jul 15 23:14:27 victor-laptop NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Jul 15 23:14:27 victor-laptop NetworkManager: <info>  SUP: response was 'OK' 

```

---

### Post by moore.bryan on 2008-07-18
well, that first message tells us a lot... seems wpa_supplicant is having some issues. have you tried reinstalling it?
====
EDIT:
you may want to check [this]("http://ubuntuforums.org/showthread.php?t=766560") out too...

---

### Post by alien0101 on 2008-07-19
thanks everyone for replies..

Well I gave up with Ubuntu..
I installed OpenSuse 11.0 , installed ndiswrappwer..

and its working perfectly....

Ububtu guys need to do something....

---

### Post by moore.bryan on 2008-07-20
> **alien0101 said:**
> thanks everyone for replies..

Well I gave up with Ubuntu..
I installed OpenSuse 11.0 , installed ndiswrappwer..
sorry to hear the issue pushed you away, but use whatever works! ;-)
> Ububtu guys need to do something....
even more so is for hardware makers to help us linux folks out!

---

