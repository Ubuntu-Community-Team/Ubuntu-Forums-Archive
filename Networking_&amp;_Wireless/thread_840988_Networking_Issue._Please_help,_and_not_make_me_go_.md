---
title: "Networking Issue. Please help, and not make me go back to Microsoft Vista"
date: 2008-06-25
forum: Networking &amp; Wireless
---

### Post by jpizzale on 2008-06-25
I am trying to make the switch to Ubuntu. I have a Dell Inspiron 1525. I have installed hardy Heron, and mostly everything works fine so far.

I have one problem. I cannot connect to my wireless network. I have tried ndiswapper, but this did not work. I am able to see my network, and type my password in, but there really is no connection between my Seimens Speedstream 6520 (Bell Sympatico P.O.S.) and my laptop.

Does anyone have any ideas. I wish that I could get support from somebody, I was even desparate enough and tried asking dell for help. They said that I should talk to Best Buy, but Best Buy says talk to Dell.

I really don't want to go to Vista, but I will if this doesn't work for me.

---

### Post by Ayuthia on 2008-06-26
I looked at your other [post]("http://ubuntuforums.org/showthread.php?t=839909") and one of the reasons why your card is not working is because you are trying to use Vista drivers.  That is not yet supported in ndiswrapper.

The other thing is that the 4310 card is a little tricky because it is a new card.  Broadcom has released a special driver for your card and it can be found by installing linux-restricted-modules.  However, the only person that I have seen try to use it was unable to get any encryption to work on it.  If you want to try it, you will need to install that package and add ndiswrapper to the blacklist:
```
echo blacklist ndiswrapper|sudo tee -a /etc/modprobe.d/blacklist
```

However, if you want to try another option that might work and uses ndiswrapper, try this link:
[http://ubuntuforums.org/showthread.php?t=786397&highlight=4310+hacked](http://ubuntuforums.org/showthread.php?t=786397&highlight=4310+hacked)

It seems to work for some people with your card.

The other option is to see if you can find the XP driver (bcmwl5) for your card and install that driver instead of the Vista (bcmwl6) version

---

### Post by cdtech on 2008-06-26
Could you list your wireless card info:
lshw -C network

---

### Post by Monarch2007 on 2008-06-26
With my limited experience, I guess it has a lot to do with the authentication mechanisms used by the Access Point (AP) to which your Laptop gets connected. So, do you know what mechanism is used by the AP? If you are using the laptop at home with your own wireless router installed, you should be able to figure this out easily.
I am able to hook up to my home network but at office, since they use LEAP authentication, I am not able to connect. Looks like no one knows how to do this either - didnt get any response for my questions.
Also, here are some steps to figure out what could have gone wrong:
You may need to find out if the driver is properly installed and communicating with the hardware. Then we could see if there are authentication issues and subsequently networking issues such as DHCP.

output of lshw -C network   // See if the HW and driver are listed OK
output of dmesg             // See if any errors are reported when you  
                            // try to enable the wireless lan interface

---

### Post by jpizzale on 2008-06-26
Here is the output from the lshw -C network and the dmesg.

  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:1d:09:40:bf:c9
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.20 duplex=full firmware=N/A ip=192.168.2.11 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Wireless interface
       product: BCM4310 USB Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: eth1
       version: 01
       serial: 00:16:44:a9:70:b1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl latency=0 module=wl multicast=yes wireless=IEEE 802.11bg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-19-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Jun 18 14:43:41 UTC 2008 (Ubuntu 2.6.24-19.34-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bf66d800 (usable)
[    0.000000]  BIOS-e820: 00000000bf66d800 - 00000000c0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000f8000000 - 00000000fc000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed18000 - 00000000fed1c000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000feda0000 - 00000000feda6000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee10000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffe00000 - 0000000100000000 (reserved)
[    0.000000] 2166MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 783981) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   783981
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   783981
[    0.000000] On node 0 totalpages: 783981
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 4332 pages used for memmap
[    0.000000]   HighMem zone: 550273 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.4 present.
[    0.000000] ACPI: RSDP signature @ 0xC00FBCB0 checksum 0
[    0.000000] ACPI: RSDP 000FBCB0, 0024 (r2 DELL  )
[    0.000000] ACPI: XSDT BF66F200, 0064 (r1 DELL    M08     27D80204 ASL        61)
[    0.000000] ACPI: FACP BF66F09C, 00F4 (r4 DELL    M08     27D80204 ASL        61)
[    0.000000] ACPI: DSDT BF66F800, 53EC (r2 INT430 SYSFexxx     1001 INTL 20050624)
[    0.000000] ACPI: FACS BF67E000, 0040
[    0.000000] ACPI: HPET BF66F300, 0038 (r1 DELL    M08            1 ASL        61)
[    0.000000] ACPI: APIC BF66F400, 0068 (r1 DELL    M08     27D80204 ASL        47)
[    0.000000] ACPI: MCFG BF66F3C0, 003E (r16 DELL    M08     27D80204 ASL        61)
[    0.000000] ACPI: SLIC BF66F49C, 0176 (r1 DELL    M08     27D80204 ASL        61)
[    0.000000] ACPI: OSFR BF66EA00, 002C (r1 DELL    M08     27D80204 ASL        61)
[    0.000000] ACPI: BOOT BF66EFC0, 0028 (r1 DELL    M08     27D80204 ASL        61)
[    0.000000] ACPI: SSDT BF66DA44, 04CC (r1  PmRef    CpuPm     3000 INTL 20050624)
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
[    0.000000] Allocating PCI resources starting at c4000000 (gap: c0000000:38000000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 777857
[    0.000000] Kernel command line: root=UUID=8297143e-013f-47b3-bd36-c09a1173d356 ro quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1828.797 MHz processor.
[    8.119022] Console: colour VGA+ 80x25
[    8.119025] console [tty0] enabled
[    8.119327] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    8.119625] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    8.272713] Memory: 3097872k/3135924k available (2177k kernel code, 36864k reserved, 1006k data, 368k init, 2218420k highmem)
[    8.272719] virtual kernel memory layout:
[    8.272720]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[    8.272721]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    8.272722]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[    8.272723]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    8.272724]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
[    8.272725]       .data : 0xc0320434 - 0xc041bdc4   (1006 kB)
[    8.272726]       .text : 0xc0100000 - 0xc0320434   (2177 kB)
[    8.272729] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[    8.272769] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[    8.272911] hpet clockevent registered
[    8.352783] Calibrating delay using timer specific routine.. 3661.92 BogoMIPS (lpj=7323841)
[    8.352803] Security Framework initialized
[    8.352809] SELinux:  Disabled at boot.
[    8.352822] AppArmor: AppArmor initialized
[    8.352826] Failure registering capabilities with primary security module.
[    8.352833] Mount-cache hash table entries: 512
[    8.352951] Initializing cgroup subsys ns
[    8.352956] Initializing cgroup subsys cpuacct
[    8.352965] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e39d 00000000 00000001 00000000
[    8.352973] monitor/mwait feature present.
[    8.352974] using mwait in idle threads.
[    8.352978] CPU: L1 I cache: 32K, L1 D cache: 32K
[    8.352980] CPU: L2 cache: 2048K
[    8.352982] CPU: Physical Processor ID: 0
[    8.352984] CPU: Processor Core ID: 0
[    8.352985] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e39d 00000000 00000001 00000000
[    8.352994] Compat vDSO mapped to ffffe000.
[    8.353006] Checking 'hlt' instruction... OK.
[    8.369120] SMP alternatives: switching to UP code
[    8.370645] Early unpacking initramfs... done
[    8.684067] ACPI: Core revision 20070126
[    8.684106] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[    8.691403] CPU0: Intel(R) Core(TM)2 Duo CPU     T5550  @ 1.83GHz stepping 0d
[    8.691417] SMP alternatives: switching to SMP code
[    8.692071] Booting processor 1/1 eip 3000
[    8.702257] Initializing CPU#1
[    8.780051] Calibrating delay using timer specific routine.. 3657.42 BogoMIPS (lpj=7314857)
[    8.780057] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e39d 00000000 00000001 00000000
[    8.780062] monitor/mwait feature present.
[    8.780065] CPU: L1 I cache: 32K, L1 D cache: 32K
[    8.780066] CPU: L2 cache: 2048K
[    8.780068] CPU: Physical Processor ID: 0
[    8.780069] CPU: Processor Core ID: 1
[    8.780071] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e39d 00000000 00000001 00000000
[    8.780590] CPU1: Intel(R) Core(TM)2 Duo CPU     T5550  @ 1.83GHz stepping 0d
[    8.780611] Total of 2 processors activated (7319.34 BogoMIPS).
[    8.780814] ENABLING IO-APIC IRQs
[    8.781007] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    8.927903] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    8.947884] Brought up 2 CPUs
[    8.947906] CPU0 attaching sched-domain:
[    8.947908]  domain 0: span 03
[    8.947910]   groups: 01 02
[    8.947913] CPU1 attaching sched-domain:
[    8.947914]  domain 0: span 03
[    8.947916]   groups: 02 01
[    8.948112] net_namespace: 64 bytes
[    8.948122] Booting paravirtualized kernel on bare hardware
[    8.948548] Time: 11:11:46  Date: 06/26/08
[    8.948573] NET: Registered protocol family 16
[    8.948738] EISA bus registered
[    8.948742] ACPI: bus type pci registered
[    8.960327] PCI: PCI BIOS revision 2.10 entry at 0xfad96, last bus=13
[    8.960329] PCI: Using configuration type 1
[    8.960344] Setting up standard PCI resources
[    8.968127] ACPI: EC: Look up EC in DSDT
[    8.968254] ACPI: BIOS _OSI(Linux) query ignored
[    8.968256] ACPI: DMI System Vendor: Dell Inc.
[    8.968258] ACPI: DMI Product Name: Inspiron 1525                   
[    8.968259] ACPI: DMI Product Version: 
[    8.968260] ACPI: DMI Board Name: 0U990C
[    8.968262] ACPI: DMI BIOS Vendor: Dell Inc.
[    8.968263] ACPI: DMI BIOS Date: 02/04/2008
[    8.968265] ACPI: Please send DMI info above to [email]linux-acpi@vger.kernel.org[/email]
[    8.968266] ACPI: If "acpi_osi=Linux" works better, please notify [email]linux-acpi@vger.kernel.org[/email]
[    8.978673] ACPI: Interpreter enabled
[    8.978676] ACPI: (supports S0 S3 S4 S5)
[    8.978688] ACPI: Using IOAPIC for interrupt routing
[    8.998455] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    8.999507] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    8.999511] PCI quirk: region 1080-10bf claimed by ICH6 GPIO
[    9.000962] PCI: Transparent bridge - 0000:00:1e.0
[    9.001009] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    9.001448] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
[    9.001594] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    9.001709] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    9.001821] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP05._PRT]
[    9.012581] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 *11)
[    9.012690] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *10
[    9.012797] ACPI: PCI Interrupt Link [LNKC] (IRQs 9 10 11) *5
[    9.012894] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 9 10 11) *0, disabled.
[    9.013003] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    9.013112] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[    9.013220] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 *7 9 10 11 12 14 15)
[    9.013319] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    9.013454] Linux Plug and Play Support v0.97 (c) Adam Belay
[    9.013480] pnp: PnP ACPI init
[    9.013486] ACPI: bus type pnp registered
[    9.051959] pnpacpi: exceeded the max number of mem resources: 12
[    9.052152] pnp: PnP ACPI: found 13 devices
[    9.052154] ACPI: ACPI bus type pnp unregistered
[    9.052157] PnPBIOS: Disabled by ACPI PNP
[    9.052345] PCI: Using ACPI for IRQ routing
[    9.052348] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    9.143447] NET: Registered protocol family 8
[    9.143449] NET: Registered protocol family 20
[    9.143479] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    9.143483] hpet0: 3 64-bit timers, 14318180 Hz
[    9.144515] AppArmor: AppArmor Filesystem Enabled
[    9.147435] Time: tsc clocksource has been installed.
[    9.147442] Switched to high resolution mode on CPU 0
[    9.147541] Switched to high resolution mode on CPU 1
[    9.163395] system 00:01: iomem range 0xff800000-0xff8fffff has been reserved
[    9.163398] system 00:01: iomem range 0xffc00000-0xffcfffff has been reserved
[    9.163406] system 00:06: ioport range 0xc80-0xcff could not be reserved
[    9.163413] system 00:09: iomem range 0xfed00000-0xfed003ff has been reserved
[    9.163418] system 00:0a: ioport range 0x900-0x97f has been reserved
[    9.163421] system 00:0a: ioport range 0x4d0-0x4d1 has been reserved
[    9.163423] system 00:0a: ioport range 0x1000-0x1005 has been reserved
[    9.163425] system 00:0a: ioport range 0x1008-0x100f has been reserved
[    9.163431] system 00:0b: ioport range 0xf400-0xf4fe has been reserved
[    9.163433] system 00:0b: ioport range 0x1006-0x1007 has been reserved
[    9.163436] system 00:0b: ioport range 0x100a-0x1059 could not be reserved
[    9.163438] system 00:0b: ioport range 0x1060-0x107f has been reserved
[    9.163441] system 00:0b: ioport range 0x1080-0x10bf has been reserved
[    9.163443] system 00:0b: ioport range 0x10c0-0x10df has been reserved
[    9.163445] system 00:0b: ioport range 0x1010-0x102f has been reserved
[    9.163448] system 00:0b: ioport range 0x809-0x809 has been reserved
[    9.163453] system 00:0c: iomem range 0x0-0x9efff could not be reserved
[    9.163456] system 00:0c: iomem range 0x9f000-0x9ffff could not be reserved
[    9.163458] system 00:0c: iomem range 0xc0000-0xcffff could not be reserved
[    9.163461] system 00:0c: iomem range 0xe0000-0xfffff could not be reserved
[    9.163463] system 00:0c: iomem range 0x100000-0xbf66d7ff could not be reserved
[    9.163466] system 00:0c: iomem range 0xbf66d800-0xbf6fffff could not be reserved
[    9.163469] system 00:0c: iomem range 0xbf700000-0xbf7fffff could not be reserved
[    9.163471] system 00:0c: iomem range 0xbf700000-0xbfefffff could not be reserved
[    9.163474] system 00:0c: iomem range 0xffe00000-0xffffffff could not be reserved
[    9.163476] system 00:0c: iomem range 0xffa00000-0xffbfffff has been reserved
[    9.163479] system 00:0c: iomem range 0xfec00000-0xfec0ffff could not be reserved
[    9.163481] system 00:0c: iomem range 0xfee00000-0xfee0ffff could not be reserved
[    9.193813] PCI: Bridge: 0000:00:1c.0
[    9.193817]   IO window: d000-dfff
[    9.193823]   MEM window: fe800000-fe8fffff
[    9.193828]   PREFETCH window: disabled.
[    9.193834] PCI: Bridge: 0000:00:1c.1
[    9.193835]   IO window: disabled.
[    9.193841]   MEM window: fe700000-fe7fffff
[    9.193846]   PREFETCH window: disabled.
[    9.193852] PCI: Bridge: 0000:00:1c.4
[    9.193855]   IO window: c000-cfff
[    9.193861]   MEM window: fe400000-fe6fffff
[    9.193865]   PREFETCH window: f0000000-f01fffff
[    9.193872] PCI: Bridge: 0000:00:1e.0
[    9.193873]   IO window: disabled.
[    9.193879]   MEM window: fe300000-fe3fffff
[    9.193884]   PREFETCH window: disabled.
[    9.193916] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
[    9.193923] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    9.193949] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 17 (level, low) -> IRQ 17
[    9.193955] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[    9.193980] ACPI: PCI Interrupt 0000:00:1c.4[A] -> GSI 16 (level, low) -> IRQ 16
[    9.193986] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[    9.194001] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    9.194011] NET: Registered protocol family 2
[    9.231302] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    9.231503] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    9.231898] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    9.232105] TCP: Hash tables configured (established 131072 bind 65536)
[    9.232108] TCP reno registered
[    9.243353] checking if image is initramfs... it is
[    9.858699] Freeing initrd memory: 7328k freed
[    9.858834] Simple Boot Flag at 0x79 set to 0x1
[    9.859393] audit: initializing netlink socket (disabled)
[    9.859406] audit(1214478706.465:1): initialized
[    9.859624] highmem bounce pool size: 64 pages
[    9.861352] VFS: Disk quotas dquot_6.5.1
[    9.861420] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    9.861540] io scheduler noop registered
[    9.861542] io scheduler anticipatory registered
[    9.861543] io scheduler deadline registered
[    9.861553] io scheduler cfq registered (default)
[    9.861564] Boot video device is 0000:00:02.0
[    9.861795] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    9.861859] assign_interrupt_mode Found MSI capability
[    9.861913] Allocate Port Service[0000:00:1c.0:pcie00]
[    9.861946] Allocate Port Service[0000:00:1c.0:pcie02]
[    9.862054] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[    9.862117] assign_interrupt_mode Found MSI capability
[    9.862168] Allocate Port Service[0000:00:1c.1:pcie00]
[    9.862196] Allocate Port Service[0000:00:1c.1:pcie02]
[    9.862299] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[    9.862363] assign_interrupt_mode Found MSI capability
[    9.862413] Allocate Port Service[0000:00:1c.4:pcie00]
[    9.862441] Allocate Port Service[0000:00:1c.4:pcie02]
[    9.862677] isapnp: Scanning for PnP cards...
[   10.216625] isapnp: No Plug & Play device found
[   10.238783] Real Time Clock Driver v1.12ac
[   10.238919] hpet_resources: 0xfed00000 is busy
[   10.238973] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   10.240006] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   10.240066] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   10.240150] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   10.256113] i8042.c: Detected active multiplexing controller, rev 1.1.
[   10.268468] serio: i8042 KBD port at 0x60,0x64 irq 1
[   10.268472] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   10.268474] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   10.268477] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   10.268479] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   10.281526] mice: PS/2 mouse device common for all mice
[   10.281626] EISA: Probing bus 0 at eisa.0
[   10.281634] Cannot allocate resource for EISA slot 1
[   10.281666] EISA: Detected 0 cards.
[   10.281668] cpuidle: using governor ladder
[   10.281670] cpuidle: using governor menu
[   10.281743] NET: Registered protocol family 1
[   10.281768] Using IPI No-Shortcut mode
[   10.281793] registered taskstats version 1
[   10.281910]   Magic number: 12:734:176
[   10.281929]   hash matches device ttyr2
[   10.281970]   hash matches device device:39
[   10.281975]   hash matches device device:0c
[   10.281979] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   10.281981] EDD information not available.
[   10.282165] Freeing unused kernel memory: 368k freed
[   10.306261] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   11.483171] fuse init (API version 7.9)
[   11.502011] ACPI: SSDT BF66E57A, 0202 (r1  PmRef  Cpu0Ist     3000 INTL 20050624)
[   11.502205] ACPI: SSDT BF66DF10, 05E5 (r1  PmRef  Cpu0Cst     3001 INTL 20050624)
[   11.502714] Monitor-Mwait will be used to enter C-1 state
[   11.502716] Monitor-Mwait will be used to enter C-2 state
[   11.502719] Monitor-Mwait will be used to enter C-3 state
[   11.502832] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   11.502836] ACPI: Processor [CPU0] (supports 8 throttling states)
[   11.503032] ACPI: SSDT BF66E77C, 00C4 (r1  PmRef  Cpu1Ist     3000 INTL 20050624)
[   11.503208] ACPI: SSDT BF66E4F5, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20050624)
[   11.503941] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[   11.503947] ACPI: Processor [CPU1] (supports 8 throttling states)
[   11.505225] ACPI: Thermal Zone [THM] (33 C)
[   11.813836] usbcore: registered new interface driver usbfs
[   11.813856] usbcore: registered new interface driver hub
[   11.820311] usbcore: registered new device driver usb
[   11.825086] USB Universal Host Controller Interface driver v3.0
[   11.825136] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 20 (level, low) -> IRQ 18
[   11.825147] PCI: Setting latency timer of device 0000:00:1a.0 to 64
[   11.825151] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[   11.825375] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[   11.825409] uhci_hcd 0000:00:1a.0: irq 18, io base 0x00006f20
[   11.825530] usb usb1: configuration #1 chosen from 1 choice
[   11.825551] hub 1-0:1.0: USB hub found
[   11.825555] hub 1-0:1.0: 2 ports detected
[   11.890234] SCSI subsystem initialized
[   11.930734] ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 21 (level, low) -> IRQ 19
[   11.930747] PCI: Setting latency timer of device 0000:00:1a.1 to 64
[   11.930752] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[   11.930775] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
[   11.930808] uhci_hcd 0000:00:1a.1: irq 19, io base 0x00006f00
[   11.930914] usb usb2: configuration #1 chosen from 1 choice
[   11.930935] hub 2-0:1.0: USB hub found
[   11.930939] hub 2-0:1.0: 2 ports detected
[   11.947656] libata version 3.00 loaded.
[   12.034605] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 20 (level, low) -> IRQ 18
[   12.034618] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   12.034623] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   12.034645] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 3
[   12.034675] uhci_hcd 0000:00:1d.0: irq 18, io base 0x00006f80
[   12.034788] usb usb3: configuration #1 chosen from 1 choice
[   12.034809] hub 3-0:1.0: USB hub found
[   12.034814] hub 3-0:1.0: 2 ports detected
[   12.138387] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 21 (level, low) -> IRQ 19
[   12.138400] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   12.138404] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   12.138424] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 4
[   12.138453] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00006f60
[   12.138559] usb usb4: configuration #1 chosen from 1 choice
[   12.138580] hub 4-0:1.0: USB hub found
[   12.138585] hub 4-0:1.0: 2 ports detected
[   12.170239] usb 1-1: new full speed USB device using uhci_hcd and address 2
[   12.242190] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 22 (level, low) -> IRQ 20
[   12.242201] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   12.242205] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   12.242226] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 5
[   12.242257] uhci_hcd 0000:00:1d.2: irq 20, io base 0x00006f40
[   12.242364] usb usb5: configuration #1 chosen from 1 choice
[   12.242385] hub 5-0:1.0: USB hub found
[   12.242389] hub 5-0:1.0: 2 ports detected
[   12.346062] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 22 (level, low) -> IRQ 20
[   12.346079] PCI: Setting latency timer of device 0000:00:1a.7 to 64
[   12.346083] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[   12.346107] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 6
[   12.350019] ehci_hcd 0000:00:1a.7: debug port 1
[   12.350026] PCI: cache line size of 32 is not supported by device 0000:00:1a.7
[   12.350033] ehci_hcd 0000:00:1a.7: irq 20, io mem 0xfed1c400
[   12.362896] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   12.363012] usb usb6: configuration #1 chosen from 1 choice
[   12.363035] hub 6-0:1.0: USB hub found
[   12.363041] hub 6-0:1.0: 4 ports detected
[   12.365541] usb 1-1: unable to read config index 0 descriptor/all
[   12.365545] usb 1-1: can't read configurations, error -71
[   12.466851] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 20 (level, low) -> IRQ 18
[   12.466867] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   12.466871] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   12.466893] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 7
[   12.470807] ehci_hcd 0000:00:1d.7: debug port 1
[   12.470814] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   12.470819] ehci_hcd 0000:00:1d.7: irq 18, io mem 0xfed1c000
[   12.486715] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   12.486867] usb usb7: configuration #1 chosen from 1 choice
[   12.486903] hub 7-0:1.0: USB hub found
[   12.486911] hub 7-0:1.0: 6 ports detected
[   12.589831] ACPI: PCI Interrupt 0000:02:09.0[A] -> GSI 16 (level, low) -> IRQ 16
[   12.642540] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[16]  MMIO=[fe3ff800-fe3fffff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[   12.646636] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 16 (level, low) -> IRQ 16
[   12.646672] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   12.646686] ACPI: PCI interrupt for device 0000:00:1f.1 disabled
[   12.646827] ahci 0000:00:1f.2: version 3.0
[   12.646851] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 17 (level, low) -> IRQ 17
[   12.646898] ahci 0000:00:1f.2: nr_ports (3) and implemented port map (0x5) don't match, using nr_ports
[   12.646900] ahci 0000:00:1f.2: forcing PORTS_IMPL to 0x7
[   12.705339] usb 6-1: new high speed USB device using ehci_hcd and address 2
[   12.842400] usb 6-1: configuration #1 chosen from 1 choice
[   12.889009] Clocksource tsc unstable (delta = -3301364762 ns)
[   12.910567] Time: hpet clocksource has been installed.
[   13.028925] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x7 impl SATA mode
[   13.028931] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part 
[   13.028940] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   13.029222] scsi0 : ahci
[   13.029420] scsi1 : ahci
[   13.029555] scsi2 : ahci
[   13.029807] ata1: SATA max UDMA/133 abar m2048@0xfe9fb800 port 0xfe9fb900 irq 220
[   13.029811] ata2: SATA max UDMA/133 abar m2048@0xfe9fb800 port 0xfe9fb980 irq 220
[   13.029814] ata3: SATA max UDMA/133 abar m2048@0xfe9fb800 port 0xfe9fba00 irq 220
[   13.049784] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[324fc000105269a1]
[   13.065114] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   13.529810] ata1.00: ATA-8: TOSHIBA MK2546GSX, LB012D, max UDMA/100
[   13.529815] ata1.00: 488397168 sectors, multi 8: LBA48 NCQ (depth 31/32)
[   13.530764] ata1.00: configured for UDMA/100
[   13.549766] ata2: SATA link down (SStatus 0 SControl 0)
[   13.568806] ata3: SATA link down (SStatus 0 SControl 300)
[   13.569040] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK2546GS LB01 PQ: 0 ANSI: 5
[   13.572259] ata_piix 0000:00:1f.1: version 2.12
[   13.572275] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 16 (level, low) -> IRQ 16
[   13.572311] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   13.572385] scsi3 : ata_piix
[   13.572443] scsi4 : ata_piix
[   13.573048] ata4: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x6fa0 irq 14
[   13.573051] ata5: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x6fa8 irq 15
[   13.578661] Driver 'sd' needs updating - please use bus_type methods
[   13.581844] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[   13.581864] sd 0:0:0:0: [sda] Write Protect is off
[   13.581868] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   13.581895] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   13.581961] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[   13.581970] sd 0:0:0:0: [sda] Write Protect is off
[   13.581972] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   13.581987] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   13.581990]  sda: sda1 sda2 < sda5 >
[   13.688890] sd 0:0:0:0: [sda] Attached SCSI disk
[   13.692892] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   13.860749] Attempting manual resume
[   13.860752] swsusp: Resume From Partition 8:5
[   13.860754] PM: Checking swsusp image.
[   13.860897] PM: Resume from disk failed.
[   13.882634] ata4.00: ATAPI: HL-DT-ST DVD+/-RW GSA-T21N, A102, max UDMA/33
[   13.918715] kjournald starting.  Commit interval 5 seconds
[   13.918750] EXT3-fs: mounted filesystem with ordered data mode.
[   14.054201] ata4.00: configured for UDMA/33
[   14.054278] ata5: port disabled. ignoring.
[   14.057965] scsi 3:0:0:0: CD-ROM            HL-DT-ST DVD+-RW GSA-T21N A102 PQ: 0 ANSI: 5
[   14.058033] scsi 3:0:0:0: Attached scsi generic sg1 type 5
[   22.431523] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   22.544753] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   22.554537] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   22.620590] iTCO_vendor_support: vendor-support=0
[   22.646821] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   22.722226] Linux agpgart interface v0.102
[   22.780607] agpgart: Detected an Intel 965GM Chipset.
[   22.781545] agpgart: Detected 7676K stolen memory.
[   22.795248] agpgart: AGP aperture is 256M @ 0xe0000000
[   22.797665] sdhci: Secure Digital Host Controller Interface driver
[   22.797667] sdhci: Copyright(c) Pierre Ossman
[   22.797702] sdhci: SDHCI controller found at 0000:02:09.1 [1180:0822] (rev 22)
[   22.797732] ACPI: PCI Interrupt 0000:02:09.1[B] -> GSI 18 (level, low) -> IRQ 21
[   22.797789] mmc0: SDHCI at 0xfe3ff400 irq 21 DMA
[   22.811367] ricoh-mmc: Ricoh MMC Controller disabling driver
[   22.811370] ricoh-mmc: Copyright(c) Philip Langdale
[   22.811410] ricoh-mmc: Ricoh MMC controller found at 0000:02:09.2 [1180:0843] (rev 12)
[   22.811423] ricoh-mmc: Controller is now disabled.
[   22.882262] input: PS/2 Mouse as /devices/virtual/input/input3
[   22.960060] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio2/input/input4
[   23.107917] ACPI: AC Adapter [AC] (on-line)
[   23.145400] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   23.145461] iTCO_wdt: Found a ICH8M TCO device (Version=2, TCOBASE=0x1060)
[   23.145503] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   23.183757] input: Lid Switch as /devices/virtual/input/input5
[   23.201523] ACPI: Lid Switch [LID]
[   23.201575] input: Power Button (CM) as /devices/virtual/input/input6
[   23.264483] ACPI: Power Button (CM) [PBTN]
[   23.264541] input: Sleep Button (CM) as /devices/virtual/input/input7
[   23.273068] ieee80211_crypt: registered algorithm 'NULL'
[   23.328353] ACPI: Sleep Button (CM) [SBTN]
[   23.354897] ACPI: Battery Slot [BAT0] (battery present)
[   23.361542] Driver 'sr' needs updating - please use bus_type methods
[   23.387138] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[   23.387142] Uniform CD-ROM driver Revision: 3.20
[   23.387187] sr 3:0:0:0: Attached scsi CD-ROM sr0
[   23.481582] ACPI: WMI-Acer: Mapper loaded
[   23.539055] ACPI: PCI Interrupt 0000:09:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   23.539070] PCI: Setting latency timer of device 0000:09:00.0 to 64
[   23.539107] sky2 0000:09:00.0: v1.20 addr 0xfe8fc000 irq 16 Yukon-FE+ (0xb8) rev 0
[   23.539547] sky2 eth0: addr 00:1d:09:40:bf:c9
[   23.617712] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:00/input/input8
[   23.649033] wl: module license 'unspecified' taints kernel.
[   23.678774] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   23.678939] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:01/input/input9
[   23.686841] ACPI: PCI Interrupt 0000:0b:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   23.686856] PCI: Setting latency timer of device 0000:0b:00.0 to 64
[   23.742642] ieee80211_crypt: registered algorithm 'TKIP'
[   23.743537] eth1: Broadcom BCM4315 802.11 Wireless Controller 5.10.18.0
[   23.746618] ACPI: Video Device [VID2] (multi-head: yes  rom: no  post: no)
[   24.189349] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 21 (level, low) -> IRQ 19
[   24.189370] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   24.230808] Linux video capture interface: v2.00
[   24.257768] uvcvideo: Found UVC 1.00 device Laptop Integrated Webcam (05a9:2640)
[   24.258083] uvcvideo: Failed to query (135) UVC control 1 (unit 0) : -32 (exp. 26).
[   24.315316] usbcore: registered new interface driver uvcvideo
[   24.315321] USB Video Class driver (v0.1.0)
[   25.164199] lp: driver loaded but no devices found
[   25.244354] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   25.301758] usbcore: registered new interface driver ndiswrapper
[   25.350759] Adding 9100780k swap on /dev/sda5.  Priority:-1 extents:1 across:9100780k
[   25.931175] EXT3 FS on sda1, internal journal
[   27.102996] ip_tables: (C) 2000-2006 Netfilter Core Team
[   27.726535] No dock devices found.
[   28.785622] apm: BIOS not found.
[   28.937915] ppdev: user-space parallel port driver
[   29.145690] audit(1214478731.101:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5160 profile="/usr/sbin/cupsd" namespace="default"
[   30.467886] sky2 eth0: enabling interface
[   30.474385] Bluetooth: Core ver 2.11
[   30.474616] NET: Registered protocol family 31
[   30.474619] Bluetooth: HCI device and connection manager initialized
[   30.474622] Bluetooth: HCI socket layer initialized
[   30.482600] Bluetooth: L2CAP ver 2.9
[   30.482604] Bluetooth: L2CAP socket layer initialized
[   30.559281] Bluetooth: RFCOMM socket layer initialized
[   30.559292] Bluetooth: RFCOMM TTY layer initialized
[   30.559294] Bluetooth: RFCOMM ver 1.8
[   31.252345] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control rx
[   33.235275] NET: Registered protocol family 17
[   33.262084] [drm] Initialized drm 1.1.0 20060810
[   33.283690] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[   33.283699] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   33.283748] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   47.522848] CPU0 attaching NULL sched-domain.
[   47.522858] CPU1 attaching NULL sched-domain.
[   47.530679] CPU0 attaching sched-domain:
[   47.530688]  domain 0: span 03
[   47.530692]   groups: 01 02
[   47.530697] CPU1 attaching sched-domain:
[   47.530700]  domain 0: span 03
[   47.530703]   groups: 02 01
[  231.612896] UDF-fs: No VRS found

---

### Post by issih on 2008-06-26
This post:

[http://forums.opensuse.org/archives/sf-archives/hardware/laptop-support/328469-hp-nx6325-wlan-broadcom-bcm4310-not-working.html](http://forums.opensuse.org/archives/sf-archives/hardware/laptop-support/328469-hp-nx6325-wlan-broadcom-bcm4310-not-working.html)

Claims to have got it running on suse using ndiswrapper and hp's xp driver.

So I'd have a look on dells site for some xp drivers, and if that no go, give this driver a go in ndiswrapper:

[http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareDescription.jsp?lang=en&cc=uk&prodTypeId=321957&prodSeriesId=1849082&prodNameId=1849083&swEnvOID=1098&swLang=8&mode=2&taskId=135&swItem=ob-53245-1](http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareDescription.jsp?lang=en&cc=uk&prodTypeId=321957&prodSeriesId=1849082&prodNameId=1849083&swEnvOID=1098&swLang=8&mode=2&taskId=135&swItem=ob-53245-1)

Might work :)

EDIT....

These pages will be useful:
[http://jigar-mehta.blogspot.com/2008/02/where-are-xp-drivers-for-dell-inspiron.html](http://jigar-mehta.blogspot.com/2008/02/where-are-xp-drivers-for-dell-inspiron.html)
[http://www.dellcommunity.com/supportforums/board/message?board.id=sw_winxp&message.id=234340&c=us&l=en&cs=&s=gen](http://www.dellcommunity.com/supportforums/board/message?board.id=sw_winxp&message.id=234340&c=us&l=en&cs=&s=gen)

and this link is apparently dells xp drivers for that card (veracity unknown :))
[http://ftp.us.dell.com/network/Dell_multi-device_](http://ftp.us.dell.com/network/Dell_multi-device_)...

---

