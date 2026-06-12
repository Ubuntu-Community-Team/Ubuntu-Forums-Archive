---
title: "Wireless keeps dropping?"
date: 2008-06-22
forum: Networking &amp; Wireless
---

### Post by Jordan777 on 2008-06-22
I just recently reinstalled Ubuntu 8.04 and it's been working great but I have one slight problem involving my wireless connection.  Ubuntu will automatically connect to my network and it'll work just fine but after a while or if I have a few pages or something like that my connection just drops.  But it won't reconnect.  I try to get it to reconnect but it's like the connection dies.  It even shows on the network bar that there is 0% signal strength.  This is weird and it shouldn't happen at all because when I boot up Windows XP my connection is always very good and never drops.  Any suggestions?

Oh i use an ASUS M2N 32-Sli deluxe board and it has an on board card if that helps.  It has software that came with it but it shouldn't be required.

---

### Post by pytheas22 on 2008-06-22
Please post the output of:
```

lspci
```

which will tell us exactly what the model of your card is.  Based on that we can solve the problem.  It's probably just a matter of using a different driver or possibly ndiswrapper.

---

### Post by Jordan777 on 2008-06-23
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:08.0 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a1)
00:09.0 ISA bridge: nVidia Corporation MCP55 LPC Bridge (rev a2)
00:09.1 SMBus: nVidia Corporation MCP55 SMBus (rev a2)
00:09.2 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a2)
00:0a.0 USB Controller: nVidia Corporation MCP55 USB Controller (rev a1)
00:0a.1 USB Controller: nVidia Corporation MCP55 USB Controller (rev a2)
00:0c.0 IDE interface: nVidia Corporation MCP55 IDE (rev a1)
00:0d.0 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:0d.1 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:0d.2 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:0e.0 PCI bridge: nVidia Corporation MCP55 PCI bridge (rev a2)
00:0e.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)
00:10.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
00:11.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
00:12.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:14.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:16.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:17.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:08.0 Multimedia audio controller: Creative Labs SB X-Fi
03:0b.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
06:00.0 Mass storage controller: Silicon Image, Inc. SiI 3132 Serial ATA Raid II Controller (rev 01)
07:00.0 VGA compatible controller: nVidia Corporation G80 [GeForce 8800 GTS] (rev a2)



That's the output it gave me.

Oh and also I think I incorrectly said onboard card.  It's not really a card as far as I remember.  It's just a built in feature of the motherboard.  Like I stated above I'm using an Asus M2N-32 Sli Deluxe motherboard.

---

### Post by pytheas22 on 2008-06-23
Strange, I don't see any network devices listed in the lspci output.  Could you try entering:
```

lshw -C Network
```

and post the output of that please?  Hopefully that will give better results.  I've never seen lspci miss a network device before.

---

### Post by Jordan777 on 2008-06-24
*-network               
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:15:af:09:b3:32
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.0.102 multicast=yes wireless=IEEE 802.11g


That's what it gave me.  Also it's weird because now my wireless isn't dropping out.  But it could just be a temporary thing.  Hopefully it's gone for good.

---

### Post by pytheas22 on 2008-06-24
I think you have a marvell chipset.  You could know for sure by running the command:
```

lsmod | grep marv
```

if it returns anything, you're using a marvell chipset.

Hopefully the problem is solved for you now.  But if it keeps occurring, let me know and I can give you instructions for driving the card with ndiswrapper, a utility allowing you to use native Windows drivers instead of the Linux ones.  But I couldn't find any other threads of people having issues with marvell chipsets, so hopefully your problem was just temporary.

---

### Post by Jordan777 on 2008-06-24
Well it didn't return anything and I don't seem to be having any more problems but if I do I'll come back to this thread.  Thanks a lot for trying to help me though. :P

---

### Post by boteeka on 2008-06-25
I updated my system to 2.6.24-19 kernel along with the linux-ubuntu-modules-2.6.24-19 and now I'm having the exact same problems as described here: connection keeps dropping and won't reconnect, and shows signal strength to be none. I have a Dell Inspiron 1525 laptop with Intel  Pro/Wireless 3945 ABG wireless chip. Before this update everything worked fine.

Any suggestions?

---

### Post by pytheas22 on 2008-06-25
boteeka,

You may want to start a new thread since you have a different chipset (I think).  But I can try to help you here if you could post the output of these commands:
```

iwlist scanning
iwconfig
```

and then after the connection drops, run this command and post the output:
```

dmesg
```

Also, if this problem just occurred with the new kernel update, keep in mind that you could boot into the old kernel until this problem gets fixed.  You should still have an entry for the old kernel in your boot menu.

---

### Post by boteeka on 2008-06-25
Thanks for your reply, and your help. Here are the outputs of the commands you requested.

My guess is that it's not a wireless driver issue, but more likely a network manager one. But that's just a guess, with no proof at all.

The wireless driver is iwl3945.

iwlist scanning:

```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results
```

iwconfig:
```

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"otamot_13"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1C:10:3C:C6:0E   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality=93/100  Signal level=-27 dBm  Noise level=-64 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

I'll post the dmesg output, but oddly enough, today seems to work fine. It haven't dropped the connection so far.

 dmesg:

```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-19-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Jun 18 14:43:41 UTC 2008 (Ubuntu 2.6.24-19.34-generic)
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
[    0.000000]  BIOS-e820: 00000000ffe00000 - 0000000100000000 (reserved)
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
[    0.000000] ACPI: RSDP signature @ 0xC00FBC60 checksum 0
[    0.000000] ACPI: RSDP 000FBC60, 0024 (r2 DELL  )
[    0.000000] ACPI: XSDT 7F66F200, 0064 (r1 DELL    M08     27D8030A ASL        61)
[    0.000000] ACPI: FACP 7F66F09C, 00F4 (r4 DELL    M08     27D8030A ASL        61)
[    0.000000] ACPI: DSDT 7F66F800, 5495 (r2 INT430 SYSFexxx     1001 INTL 20050624)
[    0.000000] ACPI: FACS 7F67E000, 0040
[    0.000000] ACPI: HPET 7F66F300, 0038 (r1 DELL    M08            1 ASL        61)
[    0.000000] ACPI: APIC 7F66F400, 0068 (r1 DELL    M08     27D8030A ASL        47)
[    0.000000] ACPI: MCFG 7F66F3C0, 003E (r16 DELL    M08     27D8030A ASL        61)
[    0.000000] ACPI: SLIC 7F66F49C, 0176 (r1 DELL    M08     27D8030A ASL        61)
[    0.000000] ACPI: OSFR 7F66EA00, 002C (r1 DELL    M08     27D8030A ASL        61)
[    0.000000] ACPI: BOOT 7F66EFC0, 0028 (r1 DELL    M08     27D8030A ASL        61)
[    0.000000] ACPI: SSDT 7F66DA02, 04CC (r1  PmRef    CpuPm     3000 INTL 20050624)
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
[    0.000000] Kernel command line: root=UUID=cde10cc9-f6a0-4227-ba6e-b1e5696d03f7 ro quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1995.179 MHz processor.
[   27.388675] Console: colour VGA+ 80x25
[   27.388678] console [tty0] enabled
[   27.388970] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   27.389249] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   27.468798] Memory: 2057520k/2087348k available (2177k kernel code, 28652k reserved, 1006k data, 368k init, 1169844k highmem)
[   27.468805] virtual kernel memory layout:
[   27.468806]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   27.468807]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   27.468807]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   27.468808]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   27.468809]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
[   27.468810]       .data : 0xc0320434 - 0xc041bdc4   (1006 kB)
[   27.468811]       .text : 0xc0100000 - 0xc0320434   (2177 kB)
[   27.468814] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   27.468851] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   27.468983] hpet clockevent registered
[   27.548946] Calibrating delay using timer specific routine.. 3994.72 BogoMIPS (lpj=7989459)
[   27.548965] Security Framework initialized
[   27.548971] SELinux:  Disabled at boot.
[   27.548983] AppArmor: AppArmor initialized
[   27.548987] Failure registering capabilities with primary security module.
[   27.548994] Mount-cache hash table entries: 512
[   27.549107] Initializing cgroup subsys ns
[   27.549111] Initializing cgroup subsys cpuacct
[   27.549121] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e39d 00000000 00000001 00000000
[   27.549127] monitor/mwait feature present.
[   27.549128] using mwait in idle threads.
[   27.549132] CPU: L1 I cache: 32K, L1 D cache: 32K
[   27.549134] CPU: L2 cache: 2048K
[   27.549136] CPU: Physical Processor ID: 0
[   27.549137] CPU: Processor Core ID: 0
[   27.549139] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e39d 00000000 00000001 00000000
[   27.549147] Compat vDSO mapped to ffffe000.
[   27.549158] Checking 'hlt' instruction... OK.
[   27.565278] SMP alternatives: switching to UP code
[   27.566701] Early unpacking initramfs... done
[   27.855966] ACPI: Core revision 20070126
[   27.856003] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   27.861446] CPU0: Intel(R) Core(TM)2 Duo CPU     T5750  @ 2.00GHz stepping 0d
[   27.861461] SMP alternatives: switching to SMP code
[   27.862078] Booting processor 1/1 eip 3000
[   27.872264] Initializing CPU#1
[   27.952715] Calibrating delay using timer specific routine.. 3990.01 BogoMIPS (lpj=7980031)
[   27.952721] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e39d 00000000 00000001 00000000
[   27.952725] monitor/mwait feature present.
[   27.952728] CPU: L1 I cache: 32K, L1 D cache: 32K
[   27.952729] CPU: L2 cache: 2048K
[   27.952731] CPU: Physical Processor ID: 0
[   27.952732] CPU: Processor Core ID: 1
[   27.952733] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e39d 00000000 00000001 00000000
[   27.953191] CPU1: Intel(R) Core(TM)2 Duo CPU     T5750  @ 2.00GHz stepping 0d
[   27.953211] Total of 2 processors activated (7984.74 BogoMIPS).
[   27.953411] ENABLING IO-APIC IRQs
[   27.953600] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   28.100730] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   28.120734] Brought up 2 CPUs
[   28.120755] CPU0 attaching sched-domain:
[   28.120757]  domain 0: span 03
[   28.120759]   groups: 01 02
[   28.120761] CPU1 attaching sched-domain:
[   28.120763]  domain 0: span 03
[   28.120764]   groups: 02 01
[   28.120948] net_namespace: 64 bytes
[   28.120957] Booting paravirtualized kernel on bare hardware
[   28.121351] Time:  9:44:10  Date: 06/25/08
[   28.121375] NET: Registered protocol family 16
[   28.121528] EISA bus registered
[   28.121532] ACPI: bus type pci registered
[   28.132105] PCI: PCI BIOS revision 2.10 entry at 0xfad46, last bus=13
[   28.132107] PCI: Using configuration type 1
[   28.132120] Setting up standard PCI resources
[   28.139442] ACPI: EC: Look up EC in DSDT
[   28.139559] ACPI: BIOS _OSI(Linux) query ignored
[   28.139560] ACPI: DMI System Vendor: Dell Inc.
[   28.139562] ACPI: DMI Product Name: Inspiron 1525                   
[   28.139563] ACPI: DMI Product Version: 
[   28.139564] ACPI: DMI Board Name: 0U990C
[   28.139566] ACPI: DMI BIOS Vendor: Dell Inc.
[   28.139567] ACPI: DMI BIOS Date: 03/10/2008
[   28.139568] ACPI: Please send DMI info above to linux-acpi@vger.kernel.org
[   28.139570] ACPI: If "acpi_osi=Linux" works better, please notify linux-acpi@vger.kernel.org
[   28.147945] ACPI: Interpreter enabled
[   28.147948] ACPI: (supports S0 S3 S4 S5)
[   28.147960] ACPI: Using IOAPIC for interrupt routing
[   28.170528] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   28.171533] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[   28.171538] PCI quirk: region 1080-10bf claimed by ICH6 GPIO
[   28.172949] PCI: Transparent bridge - 0000:00:1e.0
[   28.172993] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   28.173404] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
[   28.173538] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[   28.173644] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[   28.173747] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP05._PRT]
[   28.183678] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 *11)
[   28.183780] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *10
[   28.183879] ACPI: PCI Interrupt Link [LNKC] (IRQs 9 10 11) *5
[   28.183969] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 9 10 11) *0, disabled.
[   28.184069] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[   28.184170] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[   28.184270] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 *7 9 10 11 12 14 15)
[   28.184362] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   28.184489] Linux Plug and Play Support v0.97 (c) Adam Belay
[   28.184516] pnp: PnP ACPI init
[   28.184522] ACPI: bus type pnp registered
[   28.220452] pnpacpi: exceeded the max number of mem resources: 12
[   28.220632] pnp: PnP ACPI: found 13 devices
[   28.220634] ACPI: ACPI bus type pnp unregistered
[   28.220636] PnPBIOS: Disabled by ACPI PNP
[   28.220810] PCI: Using ACPI for IRQ routing
[   28.220812] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   28.312525] NET: Registered protocol family 8
[   28.312527] NET: Registered protocol family 20
[   28.312555] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   28.312558] hpet0: 3 64-bit timers, 14318180 Hz
[   28.313590] AppArmor: AppArmor Filesystem Enabled
[   28.316518] Time: tsc clocksource has been installed.
[   28.316530] Switched to high resolution mode on CPU 0
[   28.316621] Switched to high resolution mode on CPU 1
[   28.332497] system 00:01: iomem range 0xff800000-0xff8fffff has been reserved
[   28.332500] system 00:01: iomem range 0xffc00000-0xffcfffff has been reserved
[   28.332507] system 00:06: ioport range 0xc80-0xcff could not be reserved
[   28.332513] system 00:09: iomem range 0xfed00000-0xfed003ff has been reserved
[   28.332518] system 00:0a: ioport range 0x900-0x97f has been reserved
[   28.332520] system 00:0a: ioport range 0x4d0-0x4d1 has been reserved
[   28.332523] system 00:0a: ioport range 0x1000-0x1005 has been reserved
[   28.332525] system 00:0a: ioport range 0x1008-0x100f has been reserved
[   28.332530] system 00:0b: ioport range 0xf400-0xf4fe has been reserved
[   28.332532] system 00:0b: ioport range 0x1006-0x1007 has been reserved
[   28.332534] system 00:0b: ioport range 0x100a-0x1059 could not be reserved
[   28.332536] system 00:0b: ioport range 0x1060-0x107f has been reserved
[   28.332538] system 00:0b: ioport range 0x1080-0x10bf has been reserved
[   28.332541] system 00:0b: ioport range 0x10c0-0x10df has been reserved
[   28.332543] system 00:0b: ioport range 0x1010-0x102f has been reserved
[   28.332545] system 00:0b: ioport range 0x809-0x809 has been reserved
[   28.332550] system 00:0c: iomem range 0x0-0x9efff could not be reserved
[   28.332552] system 00:0c: iomem range 0x9f000-0x9ffff could not be reserved
[   28.332555] system 00:0c: iomem range 0xc0000-0xcffff could not be reserved
[   28.332557] system 00:0c: iomem range 0xe0000-0xfffff could not be reserved
[   28.332559] system 00:0c: iomem range 0x100000-0x7f66d7ff could not be reserved
[   28.332562] system 00:0c: iomem range 0x7f66d800-0x7f6fffff could not be reserved
[   28.332564] system 00:0c: iomem range 0x7f700000-0x7f7fffff could not be reserved
[   28.332566] system 00:0c: iomem range 0x7f700000-0x7fefffff could not be reserved
[   28.332569] system 00:0c: iomem range 0xffe00000-0xffffffff could not be reserved
[   28.332571] system 00:0c: iomem range 0xffa00000-0xffbfffff has been reserved
[   28.332573] system 00:0c: iomem range 0xfec00000-0xfec0ffff could not be reserved
[   28.332576] system 00:0c: iomem range 0xfee00000-0xfee0ffff could not be reserved
[   28.362913] PCI: Bridge: 0000:00:1c.0
[   28.362916]   IO window: d000-dfff
[   28.362922]   MEM window: fe800000-fe8fffff
[   28.362927]   PREFETCH window: disabled.
[   28.362933] PCI: Bridge: 0000:00:1c.1
[   28.362934]   IO window: disabled.
[   28.362940]   MEM window: fe700000-fe7fffff
[   28.362944]   PREFETCH window: disabled.
[   28.362949] PCI: Bridge: 0000:00:1c.4
[   28.362952]   IO window: c000-cfff
[   28.362958]   MEM window: fe400000-fe6fffff
[   28.362962]   PREFETCH window: f0000000-f01fffff
[   28.362968] PCI: Bridge: 0000:00:1e.0
[   28.362970]   IO window: disabled.
[   28.362975]   MEM window: fe300000-fe3fffff
[   28.362980]   PREFETCH window: disabled.
[   28.363011] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
[   28.363018] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   28.363043] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 17 (level, low) -> IRQ 17
[   28.363048] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   28.363072] ACPI: PCI Interrupt 0000:00:1c.4[A] -> GSI 16 (level, low) -> IRQ 16
[   28.363078] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[   28.363092] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   28.363102] NET: Registered protocol family 2
[   28.400485] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   28.400672] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   28.401054] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   28.401259] TCP: Hash tables configured (established 131072 bind 65536)
[   28.401261] TCP reno registered
[   28.412543] checking if image is initramfs... it is
[   28.980064] Freeing initrd memory: 7333k freed
[   28.980216] Simple Boot Flag at 0x79 set to 0x1
[   28.980735] audit: initializing netlink socket (disabled)
[   28.980747] audit(1214387050.385:1): initialized
[   28.980929] highmem bounce pool size: 64 pages
[   28.982533] VFS: Disk quotas dquot_6.5.1
[   28.982600] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   28.982711] io scheduler noop registered
[   28.982713] io scheduler anticipatory registered
[   28.982715] io scheduler deadline registered
[   28.982723] io scheduler cfq registered (default)
[   28.982734] Boot video device is 0000:00:02.0
[   28.982954] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   28.983016] assign_interrupt_mode Found MSI capability
[   28.983067] Allocate Port Service[0000:00:1c.0:pcie00]
[   28.983097] Allocate Port Service[0000:00:1c.0:pcie02]
[   28.983199] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   28.983260] assign_interrupt_mode Found MSI capability
[   28.983308] Allocate Port Service[0000:00:1c.1:pcie00]
[   28.983334] Allocate Port Service[0000:00:1c.1:pcie02]
[   28.983431] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[   28.983491] assign_interrupt_mode Found MSI capability
[   28.983539] Allocate Port Service[0000:00:1c.4:pcie00]
[   28.983565] Allocate Port Service[0000:00:1c.4:pcie02]
[   28.983787] isapnp: Scanning for PnP cards...
[   29.338021] isapnp: No Plug & Play device found
[   29.358591] Real Time Clock Driver v1.12ac
[   29.358716] hpet_resources: 0xfed00000 is busy
[   29.358769] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   29.359719] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   29.359776] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   29.359854] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   29.374815] i8042.c: Detected active multiplexing controller, rev 1.1.
[   29.383901] serio: i8042 KBD port at 0x60,0x64 irq 1
[   29.383904] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   29.383906] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   29.383908] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   29.383910] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   29.407998] mice: PS/2 mouse device common for all mice
[   29.408088] EISA: Probing bus 0 at eisa.0
[   29.408095] Cannot allocate resource for EISA slot 1
[   29.408126] EISA: Detected 0 cards.
[   29.408129] cpuidle: using governor ladder
[   29.408130] cpuidle: using governor menu
[   29.408203] NET: Registered protocol family 1
[   29.408226] Using IPI No-Shortcut mode
[   29.408250] registered taskstats version 1
[   29.408363]   Magic number: 12:515:728
[   29.408428] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   29.408429] EDD information not available.
[   29.408611] Freeing unused kernel memory: 368k freed
[   29.432158] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   30.660159] fuse init (API version 7.9)
[   30.677858] ACPI: SSDT 7F66E538, 0244 (r1  PmRef  Cpu0Ist     3000 INTL 20050624)
[   30.678038] ACPI: SSDT 7F66DECE, 05E5 (r1  PmRef  Cpu0Cst     3001 INTL 20050624)
[   30.678544] Monitor-Mwait will be used to enter C-1 state
[   30.678547] Monitor-Mwait will be used to enter C-2 state
[   30.678549] Monitor-Mwait will be used to enter C-3 state
[   30.678659] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   30.678663] ACPI: Processor [CPU0] (supports 8 throttling states)
[   30.678849] ACPI: SSDT 7F66E77C, 00C4 (r1  PmRef  Cpu1Ist     3000 INTL 20050624)
[   30.679013] ACPI: SSDT 7F66E4B3, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20050624)
[   30.679674] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[   30.679678] ACPI: Processor [CPU1] (supports 8 throttling states)
[   30.680841] ACPI: Thermal Zone [THM] (46 C)
[   30.807991] usbcore: registered new interface driver usbfs
[   30.808010] usbcore: registered new interface driver hub
[   30.808309] usbcore: registered new device driver usb
[   30.809258] USB Universal Host Controller Interface driver v3.0
[   30.809305] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 20 (level, low) -> IRQ 18
[   30.809315] PCI: Setting latency timer of device 0000:00:1a.0 to 64
[   30.809320] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[   30.809536] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[   30.809569] uhci_hcd 0000:00:1a.0: irq 18, io base 0x00006f20
[   30.809678] usb usb1: configuration #1 chosen from 1 choice
[   30.809698] hub 1-0:1.0: USB hub found
[   30.809701] hub 1-0:1.0: 2 ports detected
[   30.911282] ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 21 (level, low) -> IRQ 19
[   30.911294] PCI: Setting latency timer of device 0000:00:1a.1 to 64
[   30.911298] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[   30.911317] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
[   30.911349] uhci_hcd 0000:00:1a.1: irq 19, io base 0x00006f00
[   30.911445] usb usb2: configuration #1 chosen from 1 choice
[   30.911467] hub 2-0:1.0: USB hub found
[   30.911472] hub 2-0:1.0: 2 ports detected
[   31.015223] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 20 (level, low) -> IRQ 18
[   31.015235] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   31.015239] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   31.015259] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 3
[   31.015289] uhci_hcd 0000:00:1d.0: irq 18, io base 0x00006f80
[   31.015388] usb usb3: configuration #1 chosen from 1 choice
[   31.015410] hub 3-0:1.0: USB hub found
[   31.015414] hub 3-0:1.0: 2 ports detected
[   31.044859] SCSI subsystem initialized
[   31.079354] libata version 3.00 loaded.
[   31.119173] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 21 (level, low) -> IRQ 19
[   31.119185] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   31.119189] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   31.119209] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 4
[   31.119239] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00006f60
[   31.119338] usb usb4: configuration #1 chosen from 1 choice
[   31.119358] hub 4-0:1.0: USB hub found
[   31.119362] hub 4-0:1.0: 2 ports detected
[   31.223098] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 22 (level, low) -> IRQ 20
[   31.223112] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   31.223116] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   31.223136] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 5
[   31.223169] uhci_hcd 0000:00:1d.2: irq 20, io base 0x00006f40
[   31.223278] usb usb5: configuration #1 chosen from 1 choice
[   31.223298] hub 5-0:1.0: USB hub found
[   31.223302] hub 5-0:1.0: 2 ports detected
[   31.327078] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 22 (level, low) -> IRQ 20
[   31.327092] PCI: Setting latency timer of device 0000:00:1a.7 to 64
[   31.327096] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[   31.327119] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 6
[   31.331020] ehci_hcd 0000:00:1a.7: debug port 1
[   31.331027] PCI: cache line size of 32 is not supported by device 0000:00:1a.7
[   31.331033] ehci_hcd 0000:00:1a.7: irq 20, io mem 0xfed1c400
[   31.343959] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   31.344062] usb usb6: configuration #1 chosen from 1 choice
[   31.344084] hub 6-0:1.0: USB hub found
[   31.344089] hub 6-0:1.0: 4 ports detected
[   31.447976] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 20 (level, low) -> IRQ 18
[   31.447992] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   31.447996] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   31.448016] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 7
[   31.451916] ehci_hcd 0000:00:1d.7: debug port 1
[   31.451922] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   31.451928] ehci_hcd 0000:00:1d.7: irq 18, io mem 0xfed1c000
[   31.463879] usb 4-1: new low speed USB device using uhci_hcd and address 2
[   31.475887] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   31.475998] usb usb7: configuration #1 chosen from 1 choice
[   31.476018] hub 7-0:1.0: USB hub found
[   31.476023] hub 7-0:1.0: 6 ports detected
[   31.579011] ata_piix 0000:00:1f.1: version 2.12
[   31.579035] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 16 (level, low) -> IRQ 16
[   31.579081] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   31.580243] scsi0 : ata_piix
[   31.580288] scsi1 : ata_piix
[   31.580842] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x6fa0 irq 14
[   31.580844] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x6fa8 irq 15
[   31.590808] Clocksource tsc unstable (delta = -1052658846 ns)
[   31.594831] Time: hpet clocksource has been installed.
[   31.620211] ata1.00: ATAPI: TSSTcorp DVD+/-RW TS-L632H, D400, max UDMA/33
[   31.626533] usb 4-1: new low speed USB device using uhci_hcd and address 3
[   31.634718] ata1.00: configured for UDMA/33
[   31.634814] ata2: port disabled. ignoring.
[   31.635634] scsi 0:0:0:0: CD-ROM            TSSTcorp DVD+-RW TS-L632H D400 PQ: 0 ANSI: 5
[   31.635972] ACPI: PCI Interrupt 0000:02:09.0[A] -> GSI 16 (level, low) -> IRQ 16
[   31.688710] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[16]  MMIO=[fe3ff800-fe3fffff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[   31.693880] ahci 0000:00:1f.2: version 3.0
[   31.693905] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 17 (level, low) -> IRQ 17
[   31.693953] ahci 0000:00:1f.2: nr_ports (3) and implemented port map (0x5) don't match, using nr_ports
[   31.693955] ahci 0000:00:1f.2: forcing PORTS_IMPL to 0x7
[   31.703425] usb 4-1: configuration #1 chosen from 1 choice
[   31.720403] usbcore: registered new interface driver hiddev
[   31.725096] input: USB Optical Mouse USB Optical Mouse as /devices/pci0000:00/0000:00:1d.1/usb4/4-1/4-1:1.0/input/input2
[   31.729189] input,hidraw0: USB HID v1.10 Mouse [USB Optical Mouse USB Optical Mouse] on usb-0000:00:1d.1-1
[   31.729211] usbcore: registered new interface driver usbhid
[   31.729217] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   31.791679] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x7 impl SATA mode
[   31.791686] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part 
[   31.791695] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   31.791968] scsi2 : ahci
[   31.792026] scsi3 : ahci
[   31.792078] scsi4 : ahci
[   31.792307] ata3: SATA max UDMA/133 abar m2048@0xfe9fb800 port 0xfe9fb900 irq 220
[   31.792311] ata4: SATA max UDMA/133 abar m2048@0xfe9fb800 port 0xfe9fb980 irq 220
[   31.792314] ata5: SATA max UDMA/133 abar m2048@0xfe9fb800 port 0xfe9fba00 irq 220
[   31.812298] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[344fc00027bed070]
[   31.845724] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   31.846816] ata3.00: ATA-8: ST9160827AS, 3.ADA, max UDMA/133
[   31.846821] ata3.00: 312581808 sectors, multi 8: LBA48 NCQ (depth 31/32)
[   31.848135] ata3.00: configured for UDMA/133
[   31.868426] ata4: SATA link down (SStatus 0 SControl 0)
[   31.887432] ata5: SATA link down (SStatus 0 SControl 300)
[   31.887669] scsi 2:0:0:0: Direct-Access     ATA      ST9160827AS      3.AD PQ: 0 ANSI: 5
[   31.897961] Driver 'sd' needs updating - please use bus_type methods
[   31.900689] Driver 'sr' needs updating - please use bus_type methods
[   31.904252] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   31.904264] sd 2:0:0:0: [sda] Write Protect is off
[   31.904266] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   31.904281] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   31.904328] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   31.904336] sd 2:0:0:0: [sda] Write Protect is off
[   31.904338] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   31.904352] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   31.904355]  sda:sr0: scsi3-mmc drive: 62x/62x writer dvd-ram cd/rw xa/form2 cdda tray
[   31.905656] Uniform CD-ROM driver Revision: 3.20
[   31.905726] sr 0:0:0:0: Attached scsi CD-ROM sr0
[   31.919174]  sda1 sda2 sda3 sda4 < sda5 sda6 >
[   31.949641] sd 2:0:0:0: [sda] Attached SCSI disk
[   31.953944] sr 0:0:0:0: Attached scsi generic sg0 type 5
[   31.953963] sd 2:0:0:0: Attached scsi generic sg1 type 0
[   32.368994] Attempting manual resume
[   32.368997] swsusp: Resume From Partition 8:6
[   32.368999] PM: Checking swsusp image.
[   32.369145] PM: Resume from disk failed.
[   32.395465] kjournald starting.  Commit interval 5 seconds
[   32.395495] EXT3-fs: mounted filesystem with ordered data mode.
[   41.467054] Linux agpgart interface v0.102
[   41.593344] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   41.643255] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   41.705328] agpgart: Detected an Intel 965GM Chipset.
[   41.706225] agpgart: Detected 7676K stolen memory.
[   41.719547] agpgart: AGP aperture is 256M @ 0xe0000000
[   41.833342] ACPI: AC Adapter [AC] (on-line)
[   41.919344] ACPI: Battery Slot [BAT0] (battery present)
[   41.947614] input: Lid Switch as /devices/virtual/input/input3
[   41.948229] ACPI: Lid Switch [LID]
[   41.948269] input: Power Button (CM) as /devices/virtual/input/input4
[   41.965082] ACPI: Power Button (CM) [PBTN]
[   41.965134] input: Sleep Button (CM) as /devices/virtual/input/input5
[   41.997052] ACPI: Sleep Button (CM) [SBTN]
[   42.177077] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:00/input/input6
[   42.208918] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   42.209060] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:01/input/input7
[   42.246784] ACPI: Video Device [VID2] (multi-head: yes  rom: no  post: no)
[   42.247107] ACPI: WMI-Acer: Mapper loaded
[   42.352965] ACPI: PCI Interrupt 0000:09:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   42.352981] PCI: Setting latency timer of device 0000:09:00.0 to 64
[   42.353022] sky2 0000:09:00.0: v1.20 addr 0xfe8fc000 irq 16 Yukon-FE+ (0xb8) rev 0
[   42.353427] sky2 eth0: addr 00:1d:09:56:68:fc
[   42.649725] iTCO_vendor_support: vendor-support=0
[   42.689693] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   42.689776] iTCO_wdt: Found a ICH8M TCO device (Version=2, TCOBASE=0x1060)
[   42.689815] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   42.761659] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.25
[   42.761663] iwl3945: Copyright(c) 2003-2007 Intel Corporation
[   42.761812] ACPI: PCI Interrupt 0000:0b:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   42.761827] PCI: Setting latency timer of device 0000:0b:00.0 to 64
[   42.761851] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   42.869907] wmaster0: Selected rate control algorithm 'iwl-3945-rs'
[   42.916516] ricoh-mmc: Ricoh MMC Controller disabling driver
[   42.916519] ricoh-mmc: Copyright(c) Philip Langdale
[   42.974234] sdhci: Secure Digital Host Controller Interface driver
[   42.974237] sdhci: Copyright(c) Pierre Ossman
[   43.098998] ACPI: PCI interrupt for device 0000:0b:00.0 disabled
[   43.099028] ricoh-mmc: Ricoh MMC controller found at 0000:02:09.2 [1180:0843] (rev 12)
[   43.099042] ricoh-mmc: Controller is now disabled.
[   43.099057] sdhci: SDHCI controller found at 0000:02:09.1 [1180:0822] (rev 22)
[   43.099083] ACPI: PCI Interrupt 0000:02:09.1[B] -> GSI 18 (level, low) -> IRQ 21
[   43.099140] mmc0: SDHCI at 0xfe3ff400 irq 21 DMA
[   43.099177] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 21 (level, low) -> IRQ 19
[   43.099190] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   43.224599] input: PC Speaker as /devices/platform/pcspkr/input/input8
[   43.604132] input: PS/2 Mouse as /devices/virtual/input/input9
[   43.677083] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio2/input/input10
[   43.853646] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   44.478644] lp: driver loaded but no devices found
[   44.579657] Adding 1220868k swap on /dev/sda6.  Priority:-1 extents:1 across:1220868k
[   44.989045] EXT3 FS on sda2, internal journal
[   45.468080] kjournald starting.  Commit interval 5 seconds
[   45.468361] EXT3 FS on sda3, internal journal
[   45.468367] EXT3-fs: mounted filesystem with ordered data mode.
[   45.943739] ip_tables: (C) 2000-2006 Netfilter Core Team
[   46.330654] No dock devices found.
[   47.443246] apm: BIOS not found.
[   47.681910] ppdev: user-space parallel port driver
[   48.129633] audit(1214376275.030:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5389 profile="/usr/sbin/cupsd" namespace="default"
[   48.637156] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   48.637163] vboxdrv: Successfully done.
[   48.637220] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   48.637224] vboxdrv: Successfully loaded version 1.5.6_OSE (interface 0x00050002).
[   48.982902] NET: Registered protocol family 10
[   48.983298] lo: Disabled Privacy Extensions
[   49.775833] ACPI: PCI Interrupt 0000:0b:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   49.775983] PM: Writing back config space on device 0000:0b:00.0 at offset 1 (was 100102, writing 100106)
[   49.801505] iwl3945: Tunable channels: 13 802.11bg, 23 802.11a channels
[   49.806358] Registered led device: iwl-phy0:RX
[   49.806392] Registered led device: iwl-phy0:TX
[   49.814447] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   49.835767] sky2 eth0: enabling interface
[   49.842271] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   50.174507] Bluetooth: Core ver 2.11
[   50.175178] NET: Registered protocol family 31
[   50.175184] Bluetooth: HCI device and connection manager initialized
[   50.175189] Bluetooth: HCI socket layer initialized
[   50.191825] Bluetooth: L2CAP ver 2.9
[   50.191831] Bluetooth: L2CAP socket layer initialized
[   50.273138] Bluetooth: RFCOMM socket layer initialized
[   50.273151] Bluetooth: RFCOMM TTY layer initialized
[   50.273153] Bluetooth: RFCOMM ver 1.8
[   50.498613] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control both
[   50.502084] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   52.307469] NET: Registered protocol family 17
[   52.664313] [drm] Initialized drm 1.1.0 20060810
[   52.667717] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[   52.667730] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   52.667810] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   56.823315] eth0: no IPv6 routers present
[   66.936162] CPU0 attaching NULL sched-domain.
[   66.936169] CPU1 attaching NULL sched-domain.
[   66.959824] CPU0 attaching sched-domain:
[   66.959830]  domain 0: span 03
[   66.959833]   groups: 01 02
[   66.959839] CPU1 attaching sched-domain:
[   66.959841]  domain 0: span 03
[   66.959844]   groups: 02 01
[   69.052030] UDF-fs: No VRS found
[   69.112213] ISO 9660 Extensions: Microsoft Joliet Level 3
[   69.113485] ISOFS: changing to secondary root
[ 6121.216682] wlan0: Initial auth_alg=0
[ 6121.216691] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 6121.218510] wlan0: RX authentication from 00:1c:10:3c:c6:0e (alg=0 transaction=2 status=0)
[ 6121.218517] wlan0: authenticated
[ 6121.218521] wlan0: associate with AP 00:1c:10:3c:c6:0e
[ 6121.220375] wlan0: RX AssocResp from 00:1c:10:3c:c6:0e (capab=0x411 status=0 aid=1)
[ 6121.220384] wlan0: associated
[ 6121.224156] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 6121.396905] padlock: VIA PadLock not detected.
[ 6131.057317] wlan0: no IPv6 routers present
[ 6151.624336] sky2 eth0: Link is down.
[ 6153.160720] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control both
[ 6153.164242] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 6156.012944] eth0: no IPv6 routers present
[ 6186.241082] wlan0: deauthenticate(reason=3)
[ 6186.450640] ACPI: PCI interrupt for device 0000:0b:00.0 disabled
[ 6186.460171] sky2 eth0: disabling interface
[ 6186.483785] ACPI: PCI Interrupt 0000:0b:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[ 6186.483934] PM: Writing back config space on device 0000:0b:00.0 at offset 1 (was 100102, writing 100106)
[ 6186.508927] Registered led device: iwl-phy0:RX
[ 6186.508946] Registered led device: iwl-phy0:TX
[ 6186.512674] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 6186.536639] sky2 eth0: enabling interface
[ 6186.542911] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 6187.052398] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control both
[ 6187.055923] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 6188.894363] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6188.894370] wlan0: deauthenticated
[ 6188.894376] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6188.894382] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6188.894388] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6188.894393] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6188.894399] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6188.894404] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6188.894410] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6188.894416] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6188.894421] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6188.894427] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6188.894432] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6188.894438] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6188.894443] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6188.894449] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6188.894454] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6188.894460] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6188.894465] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6188.894471] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6188.894476] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6188.894482] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6188.894487] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6188.894493] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6188.894498] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6188.894504] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6188.894510] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6188.894515] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6188.894521] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6188.894527] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6188.894533] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6188.894538] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6188.894544] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6188.894549] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6188.894555] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6188.894561] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6188.894566] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6188.894572] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6188.894577] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6188.894583] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6188.894588] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6188.894594] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6188.894599] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6188.894604] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6188.895133] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6191.146950] eth0: no IPv6 routers present
[ 6192.791059] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6192.791070] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6192.791076] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6192.791081] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6192.791087] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6192.791093] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6192.791098] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6192.791103] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6192.791108] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6192.791113] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6192.791118] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6192.791131] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6192.791137] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6192.791142] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6192.791147] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6192.791152] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6192.791158] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6192.791163] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6192.791168] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6192.791173] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6192.791179] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6192.791184] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6192.791189] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6192.791194] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6192.791199] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6192.791204] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6192.791210] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6192.791215] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6192.791220] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6192.791225] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6192.791230] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6192.791236] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6192.791241] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6192.791246] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6192.791251] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6192.792906] wlan0: Initial auth_alg=0
[ 6192.792914] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 6192.792937] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6192.795019] wlan0: Initial auth_alg=0
[ 6192.795024] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 6192.795039] wlan0: RX authentication from 00:1c:10:3c:c6:0e (alg=0 transaction=2 status=0)
[ 6192.795043] wlan0: authenticated
[ 6192.795046] wlan0: associate with AP 00:1c:10:3c:c6:0e
[ 6192.800764] wlan0: Initial auth_alg=0
[ 6192.800770] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 6192.802683] wlan0: RX authentication from 00:1c:10:3c:c6:0e (alg=0 transaction=2 status=0)
[ 6192.802688] wlan0: authenticated
[ 6192.802692] wlan0: associate with AP 00:1c:10:3c:c6:0e
[ 6192.804993] wlan0: RX AssocResp from 00:1c:10:3c:c6:0e (capab=0x411 status=0 aid=1)
[ 6192.804998] wlan0: associated
[ 6192.808848] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 6196.617148] wlan0: no IPv6 routers present
[ 6869.427174] wlan0: No ProbeResp from current AP 00:1c:10:3c:c6:0e - assume out of range
[ 6871.831648] wlan0: No STA entry for own AP 00:1c:10:3c:c6:0e
[ 6874.464175] wlan0: No STA entry for own AP 00:1c:10:3c:c6:0e
[ 6876.802972] wlan0: No STA entry for own AP 00:1c:10:3c:c6:0e
[ 6876.804185] wlan0: Initial auth_alg=0
[ 6876.804195] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 6876.804812] wlan0: Initial auth_alg=0
[ 6876.804819] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 6876.844206] wlan0: RX authentication from 00:1c:10:3c:c6:0e (alg=0 transaction=2 status=0)
[ 6876.844216] wlan0: authenticated
[ 6876.844220] wlan0: associate with AP 00:1c:10:3c:c6:0e
[ 6876.848209] wlan0: RX ReassocResp from 00:1c:10:3c:c6:0e (capab=0x411 status=0 aid=1)
[ 6876.848219] wlan0: associated
[ 6892.021400] wlan0: No ProbeResp from current AP 00:1c:10:3c:c6:0e - assume out of range
[ 6893.529252] wlan0: No STA entry for own AP 00:1c:10:3c:c6:0e
[ 6897.402862] wlan0: No STA entry for own AP 00:1c:10:3c:c6:0e
[ 6901.077291] wlan0: No STA entry for own AP 00:1c:10:3c:c6:0e
[ 6903.909007] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6903.909059] wlan0: deauthenticated
[ 6903.909074] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6903.909080] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6903.909086] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6903.909091] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6903.909096] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6903.909102] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6903.909107] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6903.909112] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 6903.956959] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 6903.999619] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 6904.037029] wlan0: authentication with AP 00:1c:10:3c:c6:0e timed out
[ 6906.449632] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614231] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614241] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614288] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614293] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614298] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614303] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614309] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614314] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614320] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614325] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614330] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614342] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614347] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614352] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614358] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614363] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614368] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614373] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614378] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614383] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614388] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614394] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614399] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614404] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614409] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614414] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614420] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614425] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614430] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614435] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614440] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614445] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614450] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614455] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614460] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614466] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614471] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614476] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614482] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614486] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614492] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614497] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614508] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614514] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614519] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614524] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614529] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614534] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614539] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614545] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614550] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614555] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614560] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614565] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614570] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614576] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614582] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614587] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614592] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614598] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614603] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614609] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614614] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614620] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614625] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614631] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614636] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614642] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614647] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614653] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614658] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614664] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614669] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614679] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614685] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614690] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614696] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614701] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614707] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614712] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614717] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614723] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614728] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614734] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614739] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614745] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614750] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614756] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614761] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614766] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614772] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614777] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614782] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614788] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614793] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614798] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614804] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614809] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614814] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614820] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614825] wlan0: authentication frame received from 00:1c:10:3c:c6:0e, but not in authenticate state - ignored
[ 6911.614832] wlan0: authentication frame received from 00:1c:10:3c:c6:0e, but not in authenticate state - ignored
[ 6911.614838] wlan0: authentication frame received from 00:1c:10:3c:c6:0e, but not in authenticate state - ignored
[ 6911.614845] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614855] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614861] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614866] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614872] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614877] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614883] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614888] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614894] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614899] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614905] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614911] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614916] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614921] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614927] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614932] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614938] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614943] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614948] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614953] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614959] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614964] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614969] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614974] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614980] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614985] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614990] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.614995] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.615001] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.615006] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.615012] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.615017] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.615027] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.615032] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.615038] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.615043] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.615049] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.615055] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.615060] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.615065] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.615071] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.615076] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.615081] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.615087] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.615092] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.615097] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.615103] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.615109] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.615114] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.615120] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.615125] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.615130] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.615136] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.615141] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.615147] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.615152] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.615157] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.615163] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.615168] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.615173] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.615179] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.615185] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.615190] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.615200] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 6911.616586] wlan0: Initial auth_alg=0
[ 6911.616592] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 6911.618698] wlan0: Initial auth_alg=0
[ 6911.618704] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 6911.700283] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 6911.732978] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 6911.767102] wlan0: authentication with AP 00:1c:10:3c:c6:0e timed out
[ 6915.494998] wlan0: Initial auth_alg=0
[ 6915.495006] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 6915.496287] wlan0: Initial auth_alg=0
[ 6915.496294] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 6915.526351] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 6915.557490] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 6915.589296] wlan0: authentication with AP 00:1c:10:3c:c6:0e timed out
[ 6917.996768] wlan0: Initial auth_alg=0
[ 6917.996777] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 6917.997910] wlan0: Initial auth_alg=0
[ 6917.997916] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 6918.044448] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 6918.085898] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 6918.119950] wlan0: authentication with AP 00:1c:10:3c:c6:0e timed out
[ 6920.462881] wlan0: Initial auth_alg=0
[ 6920.462889] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 6920.502801] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 6920.543180] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 6920.584131] wlan0: authentication with AP 00:1c:10:3c:c6:0e timed out
[ 6922.837544] wlan0: Initial auth_alg=0
[ 6922.837553] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 6922.882178] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 6922.920462] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 6922.958432] wlan0: authentication with AP 00:1c:10:3c:c6:0e timed out
[ 6928.250001] wlan0: Initial auth_alg=0
[ 6928.250009] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 6928.251657] wlan0: Initial auth_alg=0
[ 6928.251664] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 6928.291454] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 6928.331025] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 6928.375592] wlan0: authentication with AP 00:1c:10:3c:c6:0e timed out
[ 6930.663173] wlan0: Initial auth_alg=0
[ 6930.663181] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 6930.703067] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 6930.737993] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 6930.775288] wlan0: authentication with AP 00:1c:10:3c:c6:0e timed out
[ 6934.584552] wlan0: Initial auth_alg=0
[ 6934.584561] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 6934.586923] wlan0: Initial auth_alg=0
[ 6934.586931] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 6934.620011] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 6934.653629] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 6934.691664] wlan0: authentication with AP 00:1c:10:3c:c6:0e timed out
[ 6937.020225] wlan0: Initial auth_alg=0
[ 6937.020233] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 6937.021751] wlan0: Initial auth_alg=0
[ 6937.021758] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 6937.061043] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 6937.095858] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 6937.127133] wlan0: authentication with AP 00:1c:10:3c:c6:0e timed out
[ 6939.493701] wlan0: Initial auth_alg=0
[ 6939.493710] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 6939.495185] wlan0: Initial auth_alg=0
[ 6939.495195] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 6939.526287] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 6939.558561] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 6939.586860] wlan0: authentication with AP 00:1c:10:3c:c6:0e timed out
[ 6947.709849] wlan0: Initial auth_alg=0
[ 6947.709857] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 6947.710521] wlan0: Initial auth_alg=0
[ 6947.710527] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 6947.750547] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 6947.777060] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 6947.804762] wlan0: authentication with AP 00:1c:10:3c:c6:0e timed out
[ 6950.180860] wlan0: Initial auth_alg=0
[ 6950.180869] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 6950.182000] wlan0: Initial auth_alg=0
[ 6950.182007] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 6950.216659] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 6950.249025] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 6950.287502] wlan0: authentication with AP 00:1c:10:3c:c6:0e timed out
[ 6952.544661] wlan0: Initial auth_alg=0
[ 6952.544670] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 6952.545704] wlan0: Initial auth_alg=0
[ 6952.545711] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 6952.600273] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 6952.639259] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 6952.676139] wlan0: authentication with AP 00:1c:10:3c:c6:0e timed out
[ 6954.979356] wlan0: Initial auth_alg=0
[ 6954.979364] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 6954.980944] wlan0: Initial auth_alg=0
[ 6954.980951] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 6955.029037] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 6955.069557] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 6955.112275] wlan0: authentication with AP 00:1c:10:3c:c6:0e timed out
[ 6957.506060] wlan0: Initial auth_alg=0
[ 6957.506068] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 6957.507456] wlan0: Initial auth_alg=0
[ 6957.507461] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 6957.546186] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 6957.585555] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 6957.625444] wlan0: authentication with AP 00:1c:10:3c:c6:0e timed out
[ 6959.910135] wlan0: Initial auth_alg=0
[ 6959.910143] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 6959.947415] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 6959.981844] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 6960.019730] wlan0: authentication with AP 00:1c:10:3c:c6:0e timed out
[ 6963.651317] wlan0: Initial auth_alg=0
[ 6963.651325] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 6963.689748] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 6963.718590] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 6963.744669] wlan0: authentication with AP 00:1c:10:3c:c6:0e timed out
[ 6966.222911] wlan0: Initial auth_alg=0
[ 6966.222918] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 6966.224402] wlan0: Initial auth_alg=0
[ 6966.224410] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 6966.252043] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 6966.287001] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 6966.318528] wlan0: authentication with AP 00:1c:10:3c:c6:0e timed out
[ 6968.565304] wlan0: Initial auth_alg=0
[ 6968.565312] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 6968.566312] wlan0: Initial auth_alg=0
[ 6968.566319] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 6968.607663] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 6968.646445] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 6968.686980] wlan0: authentication with AP 00:1c:10:3c:c6:0e timed out
[ 6970.897658] wlan0: Initial auth_alg=0
[ 6970.897667] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 6970.898833] wlan0: Initial auth_alg=0
[ 6970.898841] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 6970.899492] wlan0: Initial auth_alg=0
[ 6970.899498] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 6970.938044] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 6970.976080] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 6971.018696] wlan0: authentication with AP 00:1c:10:3c:c6:0e timed out
[ 6976.215497] wlan0: authentication frame received from 00:1c:10:3c:c6:0e, but not in authenticate state - ignored
[ 6976.216349] wlan0: authentication frame received from 00:1c:10:3c:c6:0e, but not in authenticate state - ignored
[ 6976.218922] wlan0: Initial auth_alg=0
[ 6976.218930] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 6976.218959] wlan0: RX authentication from 00:1c:10:3c:c6:0e (alg=0 transaction=2 status=0)
[ 6976.218963] wlan0: authenticated
[ 6976.218966] wlan0: associate with AP 00:1c:10:3c:c6:0e
[ 6976.218982] wlan0: authentication frame received from 00:1c:10:3c:c6:0e, but not in authenticate state - ignored
[ 6976.218988] wlan0: authentication frame received from 00:1c:10:3c:c6:0e, but not in authenticate state - ignored
[ 6976.220930] wlan0: Initial auth_alg=0
[ 6976.220937] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 6976.220956] wlan0: RX authentication from 00:1c:10:3c:c6:0e (alg=0 transaction=2 status=0)
[ 6976.220960] wlan0: authenticated
[ 6976.220964] wlan0: associate with AP 00:1c:10:3c:c6:0e
[ 6976.221776] wlan0: authentication frame received from 00:1c:10:3c:c6:0e, but not in authenticate state - ignored
[ 6976.222706] wlan0: authentication frame received from 00:1c:10:3c:c6:0e, but not in authenticate state - ignored
[ 6976.223652] wlan0: authentication frame received from 00:1c:10:3c:c6:0e, but not in authenticate state - ignored
[ 6976.224597] wlan0: authentication frame received from 00:1c:10:3c:c6:0e, but not in authenticate state - ignored
[ 6976.225495] wlan0: authentication frame received from 00:1c:10:3c:c6:0e, but not in authenticate state - ignored
[ 6976.226566] wlan0: authentication frame received from 00:1c:10:3c:c6:0e, but not in authenticate state - ignored
[ 6976.227398] wlan0: authentication frame received from 00:1c:10:3c:c6:0e, but not in authenticate state - ignored
[ 6976.228388] wlan0: authentication frame received from 00:1c:10:3c:c6:0e, but not in authenticate state - ignored
[ 6976.229366] wlan0: authentication frame received from 00:1c:10:3c:c6:0e, but not in authenticate state - ignored
[ 6976.230185] wlan0: RX ReassocResp from 00:1c:10:3c:c6:0e (capab=0x411 status=0 aid=1)
[ 6976.230191] wlan0: associated
[ 7085.443019] wlan0: No ProbeResp from current AP 00:1c:10:3c:c6:0e - assume out of range
[ 7087.223058] wlan0: No STA entry for own AP 00:1c:10:3c:c6:0e
[ 7090.853274] wlan0: No STA entry for own AP 00:1c:10:3c:c6:0e
[ 7094.563858] wlan0: No STA entry for own AP 00:1c:10:3c:c6:0e
[ 7098.174217] wlan0: No STA entry for own AP 00:1c:10:3c:c6:0e
[ 7101.955669] wlan0: No STA entry for own AP 00:1c:10:3c:c6:0e
[ 7104.440454] wlan0: No STA entry for own AP 00:1c:10:3c:c6:0e
[ 7108.259838] wlan0: No STA entry for own AP 00:1c:10:3c:c6:0e
[ 7110.870463] wlan0: No STA entry for own AP 00:1c:10:3c:c6:0e
[ 7114.442845] wlan0: No STA entry for own AP 00:1c:10:3c:c6:0e
[ 7116.544995] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 7116.545003] wlan0: deauthenticated
[ 7116.545017] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 7116.545022] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 7116.545028] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 7116.545033] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 7116.545038] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 7116.545044] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 7116.545049] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 7116.545055] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 7116.545060] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 7116.545065] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 7116.545070] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 7116.545076] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 7116.545081] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 7116.545086] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 7116.545091] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 7116.545096] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 7116.545101] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 7116.545107] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 7116.545119] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 7116.545125] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 7116.545130] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 7116.545135] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 7116.545140] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 7116.545146] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 7116.545151] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 7116.545156] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 7116.545162] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 7116.545167] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 7116.545172] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 7116.545177] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 7116.546530] wlan0: Initial auth_alg=0
[ 7116.546536] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 7116.546558] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 7116.549248] wlan0: Initial auth_alg=0
[ 7116.549253] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 7116.549269] wlan0: RX authentication from 00:1c:10:3c:c6:0e (alg=0 transaction=2 status=0)
[ 7116.549273] wlan0: authenticated
[ 7116.549277] wlan0: associate with AP 00:1c:10:3c:c6:0e
[ 7116.550748] wlan0: authentication frame received from 00:1c:10:3c:c6:0e, but not in authenticate state - ignored
[ 7116.555420] wlan0: authentication frame received from 00:1c:10:3c:c6:0e, but not in authenticate state - ignored
[ 7116.556267] wlan0: RX ReassocResp from 00:1c:10:3c:c6:0e (capab=0x411 status=0 aid=1)
[ 7116.556283] wlan0: associated
[ 7166.705605] wlan0: No ProbeResp from current AP 00:1c:10:3c:c6:0e - assume out of range
[ 7167.876006] wlan0: Initial auth_alg=0
[ 7167.876019] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 7167.876807] wlan0: Initial auth_alg=0
[ 7167.876815] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 7167.879380] wlan0: RX authentication from 00:1c:10:3c:c6:0e (alg=0 transaction=2 status=0)
[ 7167.879389] wlan0: authenticated
[ 7167.879393] wlan0: associate with AP 00:1c:10:3c:c6:0e
[ 7167.881852] wlan0: RX ReassocResp from 00:1c:10:3c:c6:0e (capab=0x411 status=0 aid=1)
[ 7167.881859] wlan0: associated
[ 7295.856305] wlan0: No ProbeResp from current AP 00:1c:10:3c:c6:0e - assume out of range
[ 7297.336916] wlan0: No STA entry for own AP 00:1c:10:3c:c6:0e
[ 7299.964094] wlan0: Initial auth_alg=0
[ 7299.964106] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 7299.964773] wlan0: Initial auth_alg=0
[ 7299.964779] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 7299.996816] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 7300.025771] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 7300.054973] wlan0: authentication with AP 00:1c:10:3c:c6:0e timed out
[ 7303.816963] wlan0: Initial auth_alg=0
[ 7303.816972] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 7303.817638] wlan0: Initial auth_alg=0
[ 7303.817645] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 7303.854754] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 7303.888221] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 7303.916058] wlan0: authentication with AP 00:1c:10:3c:c6:0e timed out
[ 7306.107270] wlan0: Initial auth_alg=0
[ 7306.107279] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 7306.145870] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 7306.192170] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 7306.231911] wlan0: authentication with AP 00:1c:10:3c:c6:0e timed out
[ 7308.617762] wlan0: Initial auth_alg=0
[ 7308.617771] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 7308.619711] wlan0: Initial auth_alg=0
[ 7308.619719] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 7308.656288] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 7308.696780] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 7308.733044] wlan0: authentication with AP 00:1c:10:3c:c6:0e timed out
[ 7310.931235] wlan0: Initial auth_alg=0
[ 7310.931244] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 7310.932139] wlan0: Initial auth_alg=0
[ 7310.932144] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 7310.968239] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 7311.020718] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 7311.060558] wlan0: authentication with AP 00:1c:10:3c:c6:0e timed out
[ 7313.400269] wlan0: authentication frame received from 00:1c:10:3c:c6:0e, but not in authenticate state - ignored
[ 7313.400280] wlan0: authentication frame received from 00:1c:10:3c:c6:0e, but not in authenticate state - ignored
[ 7313.400286] wlan0: authentication frame received from 00:1c:10:3c:c6:0e, but not in authenticate state - ignored
[ 7313.401478] wlan0: Initial auth_alg=0
[ 7313.401484] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 7313.402933] wlan0: Initial auth_alg=0
[ 7313.402940] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 7313.435018] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 7313.468744] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 7313.502580] wlan0: authentication with AP 00:1c:10:3c:c6:0e timed out
[ 7315.897769] wlan0: authentication frame received from 00:1c:10:3c:c6:0e, but not in authenticate state - ignored
[ 7315.897780] wlan0: authentication frame received from 00:1c:10:3c:c6:0e, but not in authenticate state - ignored
[ 7315.897787] wlan0: authentication frame received from 00:1c:10:3c:c6:0e, but not in authenticate state - ignored
[ 7315.898710] wlan0: Initial auth_alg=0
[ 7315.898716] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 7315.899932] wlan0: Initial auth_alg=0
[ 7315.899939] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 7315.901107] wlan0: Initial auth_alg=0
[ 7315.901113] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 7315.939629] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 7315.972848] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 7316.007010] wlan0: authentication with AP 00:1c:10:3c:c6:0e timed out
[ 7318.259727] wlan0: authentication frame received from 00:1c:10:3c:c6:0e, but not in authenticate state - ignored
[ 7318.259738] wlan0: authentication frame received from 00:1c:10:3c:c6:0e, but not in authenticate state - ignored
[ 7318.259745] wlan0: authentication frame received from 00:1c:10:3c:c6:0e, but not in authenticate state - ignored
[ 7318.259751] wlan0: authentication frame received from 00:1c:10:3c:c6:0e, but not in authenticate state - ignored
[ 7318.259757] wlan0: authentication frame received from 00:1c:10:3c:c6:0e, but not in authenticate state - ignored
[ 7318.259764] wlan0: authentication frame received from 00:1c:10:3c:c6:0e, but not in authenticate state - ignored
[ 7318.259769] wlan0: authentication frame received from 00:1c:10:3c:c6:0e, but not in authenticate state - ignored
[ 7318.260681] wlan0: Initial auth_alg=0
[ 7318.260686] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 7318.262087] wlan0: Initial auth_alg=0
[ 7318.262092] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 7318.264059] wlan0: Initial auth_alg=0
[ 7318.264067] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 7318.306908] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 7318.347996] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 7318.383721] wlan0: authentication with AP 00:1c:10:3c:c6:0e timed out
[ 7320.675311] wlan0: Initial auth_alg=0
[ 7320.675320] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 7320.676679] wlan0: Initial auth_alg=0
[ 7320.676688] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 7320.712511] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 7320.744075] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 7320.780987] wlan0: authentication with AP 00:1c:10:3c:c6:0e timed out
[ 7323.165508] wlan0: authentication frame received from 00:1c:10:3c:c6:0e, but not in authenticate state - ignored
[ 7323.165518] wlan0: authentication frame received from 00:1c:10:3c:c6:0e, but not in authenticate state - ignored
[ 7323.165525] wlan0: authentication frame received from 00:1c:10:3c:c6:0e, but not in authenticate state - ignored
[ 7323.165531] wlan0: authentication frame received from 00:1c:10:3c:c6:0e, but not in authenticate state - ignored
[ 7323.165537] wlan0: authentication frame received from 00:1c:10:3c:c6:0e, but not in authenticate state - ignored
[ 7323.165543] wlan0: authentication frame received from 00:1c:10:3c:c6:0e, but not in authenticate state - ignored
[ 7323.165549] wlan0: authentication frame received from 00:1c:10:3c:c6:0e, but not in authenticate state - ignored
[ 7323.165555] wlan0: authentication frame received from 00:1c:10:3c:c6:0e, but not in authenticate state - ignored
[ 7323.165561] wlan0: authentication frame received from 00:1c:10:3c:c6:0e, but not in authenticate state - ignored
[ 7323.169681] wlan0: Initial auth_alg=0
[ 7323.169687] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 7323.170927] wlan0: Initial auth_alg=0
[ 7323.170933] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 7323.205755] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 7323.248266] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 7323.293302] wlan0: authentication with AP 00:1c:10:3c:c6:0e timed out
[ 7325.602025] wlan0: authentication frame received from 00:1c:10:3c:c6:0e, but not in authenticate state - ignored
[ 7325.602861] wlan0: authentication frame received from 00:1c:10:3c:c6:0e, but not in authenticate state - ignored
[ 7325.603779] wlan0: authentication frame received from 00:1c:10:3c:c6:0e, but not in authenticate state - ignored
[ 7326.998654] wlan0: authentication frame received from 00:1c:10:3c:c6:0e, but not in authenticate state - ignored
[ 7326.999836] wlan0: Initial auth_alg=0
[ 7326.999845] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 7327.001241] wlan0: Initial auth_alg=0
[ 7327.001247] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 7327.001269] wlan0: RX authentication from 00:1c:10:3c:c6:0e (alg=0 transaction=2 status=0)
[ 7327.001273] wlan0: authenticated
[ 7327.001277] wlan0: associate with AP 00:1c:10:3c:c6:0e
[ 7327.003662] wlan0: Initial auth_alg=0
[ 7327.003671] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 7327.003697] wlan0: RX authentication from 00:1c:10:3c:c6:0e (alg=0 transaction=2 status=0)
[ 7327.003701] wlan0: authenticated
[ 7327.003705] wlan0: associate with AP 00:1c:10:3c:c6:0e
[ 7327.003720] wlan0: authentication frame received from 00:1c:10:3c:c6:0e, but not in authenticate state - ignored
[ 7327.005661] wlan0: authentication frame received from 00:1c:10:3c:c6:0e, but not in authenticate state - ignored
[ 7327.006848] wlan0: RX ReassocResp from 00:1c:10:3c:c6:0e (capab=0x411 status=0 aid=1)
[ 7327.006856] wlan0: associated
[ 7327.010611] wlan0: authentication frame received from 00:1c:10:3c:c6:0e, but not in authenticate state - ignored
[ 7327.011469] wlan0: association frame received from 00:1c:10:3c:c6:0e, but not in associate state - ignored
[ 7329.329239] wlan0: No ProbeResp from current AP 00:1c:10:3c:c6:0e - assume out of range
[ 7331.143343] wlan0: No STA entry for own AP 00:1c:10:3c:c6:0e
[ 7334.723217] wlan0: No STA entry for own AP 00:1c:10:3c:c6:0e
[ 7337.941707] wlan0: No STA entry for own AP 00:1c:10:3c:c6:0e
[ 7341.682871] wlan0: No STA entry for own AP 00:1c:10:3c:c6:0e
[ 7345.258597] wlan0: No STA entry for own AP 00:1c:10:3c:c6:0e
[ 7347.567296] wlan0: Initial auth_alg=0
[ 7347.567309] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 7347.568698] wlan0: Initial auth_alg=0
[ 7347.568707] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 7347.568730] wlan0: RX authentication from 00:1c:10:3c:c6:0e (alg=0 transaction=2 status=0)
[ 7347.568735] wlan0: authenticated
[ 7347.568739] wlan0: associate with AP 00:1c:10:3c:c6:0e
[ 7347.580016] wlan0: authentication frame received from 00:1c:10:3c:c6:0e, but not in authenticate state - ignored
[ 7347.580923] wlan0: authentication frame received from 00:1c:10:3c:c6:0e, but not in authenticate state - ignored
[ 7347.582020] wlan0: RX ReassocResp from 00:1c:10:3c:c6:0e (capab=0x411 status=0 aid=1)
[ 7347.582027] wlan0: associated
[ 7377.511359] wlan0: No ProbeResp from current AP 00:1c:10:3c:c6:0e - assume out of range
[ 7378.784918] wlan0: Initial auth_alg=0
[ 7378.784930] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 7378.786792] wlan0: Initial auth_alg=0
[ 7378.786800] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 7378.786817] wlan0: RX authentication from 00:1c:10:3c:c6:0e (alg=0 transaction=2 status=0)
[ 7378.786821] wlan0: authenticated
[ 7378.786825] wlan0: associate with AP 00:1c:10:3c:c6:0e
[ 7378.789198] wlan0: authentication frame received from 00:1c:10:3c:c6:0e, but not in authenticate state - ignored
[ 7378.790382] wlan0: authentication frame received from 00:1c:10:3c:c6:0e, but not in authenticate state - ignored
[ 7378.794269] wlan0: RX ReassocResp from 00:1c:10:3c:c6:0e (capab=0x411 status=0 aid=1)
[ 7378.794277] wlan0: associated
[ 7402.865278] wlan0: No ProbeResp from current AP 00:1c:10:3c:c6:0e - assume out of range
[ 7404.276834] wlan0: No STA entry for own AP 00:1c:10:3c:c6:0e
[ 7406.902677] wlan0: No STA entry for own AP 00:1c:10:3c:c6:0e
[ 7409.663667] wlan0: No STA entry for own AP 00:1c:10:3c:c6:0e
[ 7412.237160] wlan0: No STA entry for own AP 00:1c:10:3c:c6:0e
[ 7414.665235] wlan0: Initial auth_alg=0
[ 7414.665247] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 7414.666354] wlan0: Initial auth_alg=0
[ 7414.666360] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 7414.705313] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 7414.732975] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 7414.768467] wlan0: authentication with AP 00:1c:10:3c:c6:0e timed out
[ 7417.024307] wlan0: Initial auth_alg=0
[ 7417.024316] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 7417.025159] wlan0: Initial auth_alg=0
[ 7417.025166] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 7417.057865] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 7417.089768] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 7417.121253] wlan0: authentication with AP 00:1c:10:3c:c6:0e timed out
[ 7419.575205] wlan0: Initial auth_alg=0
[ 7419.575214] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 7419.613968] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 7419.657501] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 7419.690975] wlan0: authentication with AP 00:1c:10:3c:c6:0e timed out
[ 7421.908061] wlan0: Initial auth_alg=0
[ 7421.908070] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 7421.909151] wlan0: Initial auth_alg=0
[ 7421.909157] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 7421.954798] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 7421.994412] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 7422.043606] wlan0: authentication with AP 00:1c:10:3c:c6:0e timed out
[ 7424.308537] wlan0: Initial auth_alg=0
[ 7424.308545] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 7424.309713] wlan0: Initial auth_alg=0
[ 7424.309720] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 7424.347040] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 7424.391368] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 7424.429955] wlan0: authentication with AP 00:1c:10:3c:c6:0e timed out
[ 7431.093028] wlan0: Initial auth_alg=0
[ 7431.093036] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 7431.094044] wlan0: Initial auth_alg=0
[ 7431.094049] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 7431.137411] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 7431.177807] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 7431.220912] wlan0: authentication with AP 00:1c:10:3c:c6:0e timed out
[ 7437.925509] wlan0: authentication frame received from 00:1c:10:3c:c6:0e, but not in authenticate state - ignored
[ 7437.925520] wlan0: authentication frame received from 00:1c:10:3c:c6:0e, but not in authenticate state - ignored
[ 7437.925527] wlan0: authentication frame received from 00:1c:10:3c:c6:0e, but not in authenticate state - ignored
[ 7437.926236] wlan0: Initial auth_alg=0
[ 7437.926241] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 7437.927527] wlan0: Initial auth_alg=0
[ 7437.927534] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 7437.971160] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 7438.008522] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 7438.052779] wlan0: authentication with AP 00:1c:10:3c:c6:0e timed out
[ 7440.282602] wlan0: authentication frame received from 00:1c:10:3c:c6:0e, but not in authenticate state - ignored
[ 7440.284131] wlan0: Initial auth_alg=0
[ 7440.284139] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 7440.324269] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 7440.360646] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 7440.405245] wlan0: authentication with AP 00:1c:10:3c:c6:0e timed out
[ 7442.947127] wlan0: authentication frame received from 00:1c:10:3c:c6:0e, but not in authenticate state - ignored
[ 7442.947139] wlan0: authentication frame received from 00:1c:10:3c:c6:0e, but not in authenticate state - ignored
[ 7442.947145] wlan0: authentication frame received from 00:1c:10:3c:c6:0e, but not in authenticate state - ignored
[ 7442.948628] wlan0: Initial auth_alg=0
[ 7442.948634] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 7442.991390] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 7443.034528] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 7443.077278] wlan0: authentication with AP 00:1c:10:3c:c6:0e timed out
[ 7445.256405] wlan0: authentication frame received from 00:1c:10:3c:c6:0e, but not in authenticate state - ignored
[ 7445.256416] wlan0: authentication frame received from 00:1c:10:3c:c6:0e, but not in authenticate state - ignored
[ 7445.256423] wlan0: authentication frame received from 00:1c:10:3c:c6:0e, but not in authenticate state - ignored
[ 7445.257834] wlan0: Initial auth_alg=0
[ 7445.257841] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 7445.292000] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 7445.321635] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 7445.361954] wlan0: authentication with AP 00:1c:10:3c:c6:0e timed out
[ 7449.245764] wlan0: authentication frame received from 00:1c:10:3c:c6:0e, but not in authenticate state - ignored
[ 7449.246609] wlan0: authentication frame received from 00:1c:10:3c:c6:0e, but not in authenticate state - ignored
[ 7449.247446] wlan0: authentication frame received from 00:1c:10:3c:c6:0e, but not in authenticate state - ignored
[ 7449.305437] wlan0: authentication frame received from 00:1c:10:3c:c6:0e, but not in authenticate state - ignored
[ 7450.659941] wlan0: authentication frame received from 00:1c:10:3c:c6:0e, but not in authenticate state - ignored
[ 7450.659952] wlan0: authentication frame received from 00:1c:10:3c:c6:0e, but not in authenticate state - ignored
[ 7450.659958] wlan0: authentication frame received from 00:1c:10:3c:c6:0e, but not in authenticate state - ignored
[ 7450.659964] wlan0: authentication frame received from 00:1c:10:3c:c6:0e, but not in authenticate state - ignored
[ 7450.660011] wlan0: authentication frame received from 00:1c:10:3c:c6:0e, but not in authenticate state - ignored
[ 7450.660017] wlan0: authentication frame received from 00:1c:10:3c:c6:0e, but not in authenticate state - ignored
[ 7450.660023] wlan0: authentication frame received from 00:1c:10:3c:c6:0e, but not in authenticate state - ignored
[ 7450.661459] wlan0: Initial auth_alg=0
[ 7450.661466] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 7450.695774] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 7450.731374] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 7450.775726] wlan0: authentication with AP 00:1c:10:3c:c6:0e timed out
[ 7453.117602] wlan0: authentication frame received from 00:1c:10:3c:c6:0e, but not in authenticate state - ignored
[ 7453.117613] wlan0: authentication frame received from 00:1c:10:3c:c6:0e, but not in authenticate state - ignored
[ 7453.117619] wlan0: authentication frame received from 00:1c:10:3c:c6:0e, but not in authenticate state - ignored
[ 7453.118761] wlan0: Initial auth_alg=0
[ 7453.118767] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 7453.120166] wlan0: Initial auth_alg=0
[ 7453.120174] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 7453.152181] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 7453.183457] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 7453.218463] wlan0: authentication with AP 00:1c:10:3c:c6:0e timed out
[ 7455.485227] wlan0: authentication frame received from 00:1c:10:3c:c6:0e, but not in authenticate state - ignored
[ 7457.087310] wlan0: authentication frame received from 00:1c:10:3c:c6:0e, but not in authenticate state - ignored
[ 7457.087320] wlan0: authentication frame received from 00:1c:10:3c:c6:0e, but not in authenticate state - ignored
[ 7457.087327] wlan0: authentication frame received from 00:1c:10:3c:c6:0e, but not in authenticate state - ignored
[ 7457.087333] wlan0: authentication frame received from 00:1c:10:3c:c6:0e, but not in authenticate state - ignored
[ 7457.088343] wlan0: Initial auth_alg=0
[ 7457.088350] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 7457.089934] wlan0: Initial auth_alg=0
[ 7457.089941] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 7457.089957] wlan0: RX authentication from 00:1c:10:3c:c6:0e (alg=0 transaction=2 status=0)
[ 7457.089961] wlan0: authenticated
[ 7457.089965] wlan0: associate with AP 00:1c:10:3c:c6:0e
[ 7457.091773] wlan0: authentication frame received from 00:1c:10:3c:c6:0e, but not in authenticate state - ignored
[ 7457.093343] wlan0: authentication frame received from 00:1c:10:3c:c6:0e, but not in authenticate state - ignored
[ 7457.094217] wlan0: RX ReassocResp from 00:1c:10:3c:c6:0e (capab=0x411 status=0 aid=1)
[ 7457.094223] wlan0: associated
[ 7464.908351] wlan0: No ProbeResp from current AP 00:1c:10:3c:c6:0e - assume out of range
[ 7466.033823] wlan0: No STA entry for own AP 00:1c:10:3c:c6:0e
[ 7466.036086] wlan0: Initial auth_alg=0
[ 7466.036113] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 7466.037078] wlan0: Initial auth_alg=0
[ 7466.037084] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 7466.038987] wlan0: RX authentication from 00:1c:10:3c:c6:0e (alg=0 transaction=2 status=0)
[ 7466.038994] wlan0: authenticated
[ 7466.038998] wlan0: associate with AP 00:1c:10:3c:c6:0e
[ 7466.040569] wlan0: RX ReassocResp from 00:1c:10:3c:c6:0e (capab=0x411 status=0 aid=1)
[ 7466.040576] wlan0: associated
[ 7488.526120] wlan0: No ProbeResp from current AP 00:1c:10:3c:c6:0e - assume out of range
[ 7489.607264] wlan0: Initial auth_alg=0
[ 7489.607276] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 7489.609392] wlan0: Initial auth_alg=0
[ 7489.609400] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 7489.609420] wlan0: RX authentication from 00:1c:10:3c:c6:0e (alg=0 transaction=2 status=0)
[ 7489.609424] wlan0: authenticated
[ 7489.609428] wlan0: associate with AP 00:1c:10:3c:c6:0e
[ 7489.610522] wlan0: Initial auth_alg=0
[ 7489.610526] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 7489.612174] wlan0: RX authentication from 00:1c:10:3c:c6:0e (alg=0 transaction=2 status=0)
[ 7489.612180] wlan0: authenticated
[ 7489.612183] wlan0: associate with AP 00:1c:10:3c:c6:0e
[ 7489.614744] wlan0: authentication frame received from 00:1c:10:3c:c6:0e, but not in authenticate state - ignored
[ 7489.615825] wlan0: RX ReassocResp from 00:1c:10:3c:c6:0e (capab=0x411 status=0 aid=1)
[ 7489.615831] wlan0: associated
[ 7553.054742] wlan0: No ProbeResp from current AP 00:1c:10:3c:c6:0e - assume out of range
[ 7554.103251] wlan0: Initial auth_alg=0
[ 7554.103263] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 7554.105127] wlan0: RX authentication from 00:1c:10:3c:c6:0e (alg=0 transaction=2 status=0)
[ 7554.105134] wlan0: authenticated
[ 7554.105138] wlan0: associate with AP 00:1c:10:3c:c6:0e
[ 7554.107537] wlan0: Initial auth_alg=0
[ 7554.107547] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 7554.107574] wlan0: RX authentication from 00:1c:10:3c:c6:0e (alg=0 transaction=2 status=0)
[ 7554.107578] wlan0: authenticated
[ 7554.107582] wlan0: associate with AP 00:1c:10:3c:c6:0e
[ 7554.107599] wlan0: authentication frame received from 00:1c:10:3c:c6:0e, but not in authenticate state - ignored
[ 7554.109860] wlan0: RX ReassocResp from 00:1c:10:3c:c6:0e (capab=0x411 status=0 aid=1)
[ 7554.109866] wlan0: associated
[ 8532.043671] wlan0: deauthenticate(reason=3)
[ 8536.230165] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 8536.230173] wlan0: deauthenticated
[ 8536.230181] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 8536.230186] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 8536.230192] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 8536.230197] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 8536.230202] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 8536.230208] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 8536.230220] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 8536.230225] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 8536.230230] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 8536.230235] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 8536.230241] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 8536.230247] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 8536.230252] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 8536.230258] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 8536.230263] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 8536.230268] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 8536.230273] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 8536.230278] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 8536.230284] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 8536.230289] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 8536.230295] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 8536.230300] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 8536.230330] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 8536.230336] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 8536.230341] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 8536.230347] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 8536.230352] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 8536.230358] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 8536.230363] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 8536.230368] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 8536.230374] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 8536.230380] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 8536.230998] wlan0: RX deauthentication from 00:1c:10:3c:c6:0e (reason=7)
[ 8536.233021] wlan0: RX authentication from 00:1c:10:3c:c6:0e (alg=0 transaction=2 status=0)
[ 8536.233026] wlan0: authenticated
[ 8536.233030] wlan0: associate with AP 00:1c:10:3c:c6:0e
[ 8536.235336] wlan0: invalid aid value 0; bits 15:14 not set
[ 8536.235342] wlan0: RX AssocResp from 00:1c:10:3c:c6:0e (capab=0x411 status=12 aid=0)
[ 8536.235347] wlan0: AP denied association (code=12)
[ 8536.380343] wlan0: associate with AP 00:1c:10:3c:c6:0e
[ 8536.381806] wlan0: invalid aid value 0; bits 15:14 not set
[ 8536.381816] wlan0: RX AssocResp from 00:1c:10:3c:c6:0e (capab=0x411 status=12 aid=0)
[ 8536.381820] wlan0: AP denied association (code=12)
[ 8536.527744] wlan0: associate with AP 00:1c:10:3c:c6:0e
[ 8536.529959] wlan0: invalid aid value 0; bits 15:14 not set
[ 8536.529969] wlan0: RX AssocResp from 00:1c:10:3c:c6:0e (capab=0x411 status=12 aid=0)
[ 8536.529974] wlan0: AP denied association (code=12)
[ 8536.675907] wlan0: association with AP 00:1c:10:3c:c6:0e timed out
[ 8541.544865] eth0: no IPv6 routers present
[ 8541.728212] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8541.728223] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8541.728229] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8541.728234] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8541.728239] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8541.728244] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8541.728249] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8541.728254] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8541.728259] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8541.728265] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8541.728270] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8541.728275] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8541.728280] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8541.728286] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8541.728291] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8541.728296] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8541.728301] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8541.728307] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8541.728312] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8541.728317] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8541.728322] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8541.728328] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8541.728333] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8541.728338] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8541.728343] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8541.728348] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8541.728354] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8541.728369] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8541.728374] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8541.728380] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8541.728384] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8541.729032] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8547.311542] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8547.311570] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8547.311576] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8547.311582] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8547.311588] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8547.311593] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8547.311598] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8547.311603] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8547.311609] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8547.311615] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8547.311620] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8547.311626] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8547.311631] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8547.311637] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8547.311642] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8547.311648] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8547.311653] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8547.311658] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8547.311664] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8547.311669] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8547.311675] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8547.311680] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8547.311686] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8547.311692] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8547.311698] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8547.311703] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8547.311709] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8547.311714] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8547.311719] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8547.311725] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8547.312337] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8553.122148] sky2 eth0: Link is down.
[ 8560.198042] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8560.198055] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8560.198061] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8560.198066] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8560.198071] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8560.198076] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8560.198082] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8560.198087] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8560.198092] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8560.198097] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8560.198103] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8560.198108] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8560.198113] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8560.198118] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8560.198123] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8560.198129] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8560.198134] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8560.198139] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8560.198145] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8560.198150] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8560.198155] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8560.198160] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8560.198166] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8560.198171] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8560.198176] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8560.198181] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8560.198186] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8560.198191] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8560.198196] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8560.198201] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8560.198206] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8560.198211] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8563.612234] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8563.612247] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8563.612252] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8563.612258] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8563.612263] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8563.612268] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8563.612274] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8563.612279] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8563.612285] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8563.612290] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8563.612295] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8563.612300] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8563.612306] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8563.612311] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8563.612317] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8563.612322] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8563.612327] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8563.612332] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8563.612337] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8563.612342] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8563.612347] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8563.612352] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8563.612358] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8563.612363] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8563.612368] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8563.612373] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8563.612378] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8563.612383] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8563.612388] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8563.613907] wlan0: Initial auth_alg=0
[ 8563.613912] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 8563.613936] wlan0: RX disassociation from 00:1c:10:3c:c6:0e (reason=7)
[ 8563.615898] wlan0: Initial auth_alg=0
[ 8563.615904] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 8563.616783] wlan0: RX authentication from 00:1c:10:3c:c6:0e (alg=0 transaction=2 status=0)
[ 8563.616788] wlan0: authenticated
[ 8563.616792] wlan0: associate with AP 00:1c:10:3c:c6:0e
[ 8563.620847] wlan0: Initial auth_alg=0
[ 8563.620853] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[ 8563.622753] wlan0: RX authentication from 00:1c:10:3c:c6:0e (alg=0 transaction=2 status=0)
[ 8563.622759] wlan0: authenticated
[ 8563.622763] wlan0: associate with AP 00:1c:10:3c:c6:0e
[ 8563.624431] wlan0: RX AssocResp from 00:1c:10:3c:c6:0e (capab=0x411 status=0 aid=1)
[ 8563.624439] wlan0: associated
[ 8563.628221] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 8568.866704] wlan0: no IPv6 routers present
```

---

### Post by pytheas22 on 2008-06-25
Thanks for the information.  I'd need to see dmesg after the disconnect though because it's only then that it would contain information about why it s disconnecting.  If the problem happens again, run dmesg immediately after and please post that.

Also, are you within solid range of your router?  iwlist scanning doesn't see your router, so I'm wondering if the connection might be flaky because you're too far away?  It could also be the driver's fault, however.

And if you think it could be NM's fault (it is flaky sometimes), you could try using [wicd]("http://wicd.sourceforge.net") instead.

---

### Post by boteeka on 2008-06-25
Thanks for your quick reply. I'll try to post the dmesg output when the connection drops next time.

My laptop is at 50 cm from my router right now :), but when not on the table, it is still in the room, which is a small room. The farthest I take my laptop from my router is maximum 5 meters. So, range should not be a problem.

I will take a look at wicd, though.

---

### Post by boteeka on 2008-07-04
It happened to me again. Here it is the dmesg output.

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-19-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Jun 18 14:43:41 UTC 2008 (Ubuntu 2.6.24-19.34-generic)
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
[    0.000000]  BIOS-e820: 00000000ffe00000 - 0000000100000000 (reserved)
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
[    0.000000] ACPI: RSDP signature @ 0xC00FBC60 checksum 0
[    0.000000] ACPI: RSDP 000FBC60, 0024 (r2 DELL  )
[    0.000000] ACPI: XSDT 7F66F200, 0064 (r1 DELL    M08     27D8030A ASL        61)
[    0.000000] ACPI: FACP 7F66F09C, 00F4 (r4 DELL    M08     27D8030A ASL        61)
[    0.000000] ACPI: DSDT 7F66F800, 5495 (r2 INT430 SYSFexxx     1001 INTL 20050624)
[    0.000000] ACPI: FACS 7F67E000, 0040
[    0.000000] ACPI: HPET 7F66F300, 0038 (r1 DELL    M08            1 ASL        61)
[    0.000000] ACPI: APIC 7F66F400, 0068 (r1 DELL    M08     27D8030A ASL        47)
[    0.000000] ACPI: MCFG 7F66F3C0, 003E (r16 DELL    M08     27D8030A ASL        61)
[    0.000000] ACPI: SLIC 7F66F49C, 0176 (r1 DELL    M08     27D8030A ASL        61)
[    0.000000] ACPI: OSFR 7F66EA00, 002C (r1 DELL    M08     27D8030A ASL        61)
[    0.000000] ACPI: BOOT 7F66EFC0, 0028 (r1 DELL    M08     27D8030A ASL        61)
[    0.000000] ACPI: SSDT 7F66DA02, 04CC (r1  PmRef    CpuPm     3000 INTL 20050624)
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
[    0.000000] Kernel command line: root=UUID=cde10cc9-f6a0-4227-ba6e-b1e5696d03f7 ro quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1995.047 MHz processor.
[    7.581889] Console: colour VGA+ 80x25
[    7.581892] console [tty0] enabled
[    7.582184] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    7.582462] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    7.662017] Memory: 2057520k/2087348k available (2177k kernel code, 28652k reserved, 1006k data, 368k init, 1169844k highmem)
[    7.662023] virtual kernel memory layout:
[    7.662024]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[    7.662025]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    7.662026]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[    7.662027]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    7.662027]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
[    7.662028]       .data : 0xc0320434 - 0xc041bdc4   (1006 kB)
[    7.662029]       .text : 0xc0100000 - 0xc0320434   (2177 kB)
[    7.662032] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[    7.662070] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[    7.662202] hpet clockevent registered
[    7.742164] Calibrating delay using timer specific routine.. 3994.76 BogoMIPS (lpj=7989535)
[    7.742184] Security Framework initialized
[    7.742190] SELinux:  Disabled at boot.
[    7.742202] AppArmor: AppArmor initialized
[    7.742206] Failure registering capabilities with primary security module.
[    7.742213] Mount-cache hash table entries: 512
[    7.742327] Initializing cgroup subsys ns
[    7.742332] Initializing cgroup subsys cpuacct
[    7.742341] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e39d 00000000 00000001 00000000
[    7.742347] monitor/mwait feature present.
[    7.742348] using mwait in idle threads.
[    7.742352] CPU: L1 I cache: 32K, L1 D cache: 32K
[    7.742354] CPU: L2 cache: 2048K
[    7.742356] CPU: Physical Processor ID: 0
[    7.742358] CPU: Processor Core ID: 0
[    7.742359] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e39d 00000000 00000001 00000000
[    7.742368] Compat vDSO mapped to ffffe000.
[    7.742379] Checking 'hlt' instruction... OK.
[    7.758496] SMP alternatives: switching to UP code
[    7.759919] Early unpacking initramfs... done
[    8.048838] ACPI: Core revision 20070126
[    8.048875] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[    8.054696] CPU0: Intel(R) Core(TM)2 Duo CPU     T5750  @ 2.00GHz stepping 0d
[    8.054711] SMP alternatives: switching to SMP code
[    8.055329] Booting processor 1/1 eip 3000
[    8.065514] Initializing CPU#1
[    8.145934] Calibrating delay using timer specific routine.. 3990.02 BogoMIPS (lpj=7980049)
[    8.145939] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e39d 00000000 00000001 00000000
[    8.145944] monitor/mwait feature present.
[    8.145947] CPU: L1 I cache: 32K, L1 D cache: 32K
[    8.145948] CPU: L2 cache: 2048K
[    8.145950] CPU: Physical Processor ID: 0
[    8.145951] CPU: Processor Core ID: 1
[    8.145952] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e39d 00000000 00000001 00000000
[    8.146437] CPU1: Intel(R) Core(TM)2 Duo CPU     T5750  @ 2.00GHz stepping 0d
[    8.146457] Total of 2 processors activated (7984.79 BogoMIPS).
[    8.146657] ENABLING IO-APIC IRQs
[    8.146846] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    8.293948] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    8.313950] Brought up 2 CPUs
[    8.313971] CPU0 attaching sched-domain:
[    8.313973]  domain 0: span 03
[    8.313975]   groups: 01 02
[    8.313978] CPU1 attaching sched-domain:
[    8.313979]  domain 0: span 03
[    8.313980]   groups: 02 01
[    8.314165] net_namespace: 64 bytes
[    8.314174] Booting paravirtualized kernel on bare hardware
[    8.314569] Time: 17:47:06  Date: 07/04/08
[    8.314593] NET: Registered protocol family 16
[    8.314745] EISA bus registered
[    8.314749] ACPI: bus type pci registered
[    8.325395] PCI: PCI BIOS revision 2.10 entry at 0xfad46, last bus=13
[    8.325397] PCI: Using configuration type 1
[    8.325410] Setting up standard PCI resources
[    8.332736] ACPI: EC: Look up EC in DSDT
[    8.332852] ACPI: BIOS _OSI(Linux) query ignored
[    8.332854] ACPI: DMI System Vendor: Dell Inc.
[    8.332856] ACPI: DMI Product Name: Inspiron 1525                   
[    8.332857] ACPI: DMI Product Version: 
[    8.332858] ACPI: DMI Board Name: 0U990C
[    8.332859] ACPI: DMI BIOS Vendor: Dell Inc.
[    8.332861] ACPI: DMI BIOS Date: 03/10/2008
[    8.332862] ACPI: Please send DMI info above to linux-acpi@vger.kernel.org
[    8.332864] ACPI: If "acpi_osi=Linux" works better, please notify linux-acpi@vger.kernel.org
[    8.344299] ACPI: Interpreter enabled
[    8.344302] ACPI: (supports S0 S3 S4 S5)
[    8.344314] ACPI: Using IOAPIC for interrupt routing
[    8.362938] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    8.363944] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    8.363948] PCI quirk: region 1080-10bf claimed by ICH6 GPIO
[    8.365359] PCI: Transparent bridge - 0000:00:1e.0
[    8.365404] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    8.365807] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
[    8.365944] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    8.366050] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    8.366154] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP05._PRT]
[    8.376065] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 *11)
[    8.376167] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *10
[    8.376266] ACPI: PCI Interrupt Link [LNKC] (IRQs 9 10 11) *5
[    8.376356] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 9 10 11) *0, disabled.
[    8.376456] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    8.376557] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[    8.376657] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 *7 9 10 11 12 14 15)
[    8.376748] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    8.376874] Linux Plug and Play Support v0.97 (c) Adam Belay
[    8.376899] pnp: PnP ACPI init
[    8.376905] ACPI: bus type pnp registered
[    8.412863] pnpacpi: exceeded the max number of mem resources: 12
[    8.413043] pnp: PnP ACPI: found 13 devices
[    8.413045] ACPI: ACPI bus type pnp unregistered
[    8.413047] PnPBIOS: Disabled by ACPI PNP
[    8.413222] PCI: Using ACPI for IRQ routing
[    8.413224] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    8.501746] NET: Registered protocol family 8
[    8.501748] NET: Registered protocol family 20
[    8.501776] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    8.501779] hpet0: 3 64-bit timers, 14318180 Hz
[    8.502812] AppArmor: AppArmor Filesystem Enabled
[    8.505739] Time: tsc clocksource has been installed.
[    8.505751] Switched to high resolution mode on CPU 0
[    8.505840] Switched to high resolution mode on CPU 1
[    8.521717] system 00:01: iomem range 0xff800000-0xff8fffff has been reserved
[    8.521719] system 00:01: iomem range 0xffc00000-0xffcfffff has been reserved
[    8.521727] system 00:06: ioport range 0xc80-0xcff could not be reserved
[    8.521733] system 00:09: iomem range 0xfed00000-0xfed003ff has been reserved
[    8.521738] system 00:0a: ioport range 0x900-0x97f has been reserved
[    8.521741] system 00:0a: ioport range 0x4d0-0x4d1 has been reserved
[    8.521743] system 00:0a: ioport range 0x1000-0x1005 has been reserved
[    8.521745] system 00:0a: ioport range 0x1008-0x100f has been reserved
[    8.521750] system 00:0b: ioport range 0xf400-0xf4fe has been reserved
[    8.521752] system 00:0b: ioport range 0x1006-0x1007 has been reserved
[    8.521754] system 00:0b: ioport range 0x100a-0x1059 could not be reserved
[    8.521757] system 00:0b: ioport range 0x1060-0x107f has been reserved
[    8.521759] system 00:0b: ioport range 0x1080-0x10bf has been reserved
[    8.521761] system 00:0b: ioport range 0x10c0-0x10df has been reserved
[    8.521763] system 00:0b: ioport range 0x1010-0x102f has been reserved
[    8.521765] system 00:0b: ioport range 0x809-0x809 has been reserved
[    8.521770] system 00:0c: iomem range 0x0-0x9efff could not be reserved
[    8.521773] system 00:0c: iomem range 0x9f000-0x9ffff could not be reserved
[    8.521775] system 00:0c: iomem range 0xc0000-0xcffff could not be reserved
[    8.521777] system 00:0c: iomem range 0xe0000-0xfffff could not be reserved
[    8.521780] system 00:0c: iomem range 0x100000-0x7f66d7ff could not be reserved
[    8.521782] system 00:0c: iomem range 0x7f66d800-0x7f6fffff could not be reserved
[    8.521784] system 00:0c: iomem range 0x7f700000-0x7f7fffff could not be reserved
[    8.521787] system 00:0c: iomem range 0x7f700000-0x7fefffff could not be reserved
[    8.521789] system 00:0c: iomem range 0xffe00000-0xffffffff could not be reserved
[    8.521791] system 00:0c: iomem range 0xffa00000-0xffbfffff has been reserved
[    8.521794] system 00:0c: iomem range 0xfec00000-0xfec0ffff could not be reserved
[    8.521796] system 00:0c: iomem range 0xfee00000-0xfee0ffff could not be reserved
[    8.552133] PCI: Bridge: 0000:00:1c.0
[    8.552136]   IO window: d000-dfff
[    8.552143]   MEM window: fe800000-fe8fffff
[    8.552147]   PREFETCH window: disabled.
[    8.552153] PCI: Bridge: 0000:00:1c.1
[    8.552154]   IO window: disabled.
[    8.552160]   MEM window: fe700000-fe7fffff
[    8.552164]   PREFETCH window: disabled.
[    8.552170] PCI: Bridge: 0000:00:1c.4
[    8.552173]   IO window: c000-cfff
[    8.552179]   MEM window: fe400000-fe6fffff
[    8.552183]   PREFETCH window: f0000000-f01fffff
[    8.552189] PCI: Bridge: 0000:00:1e.0
[    8.552191]   IO window: disabled.
[    8.552196]   MEM window: fe300000-fe3fffff
[    8.552201]   PREFETCH window: disabled.
[    8.552232] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
[    8.552238] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    8.552263] ACPI: PCI Interrupt 0000:00:1c.1[b] -> GSI 17 (level, low) -> IRQ 17
[    8.552269] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[    8.552293] ACPI: PCI Interrupt 0000:00:1c.4[A] -> GSI 16 (level, low) -> IRQ 16
[    8.552298] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[    8.552313] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    8.552322] NET: Registered protocol family 2
[    8.589701] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    8.589891] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    8.590271] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    8.590473] TCP: Hash tables configured (established 131072 bind 65536)
[    8.590475] TCP reno registered
[    8.601762] checking if image is initramfs... it is
[    9.170900] Freeing initrd memory: 7333k freed
[    9.171038] Simple Boot Flag at 0x79 set to 0x1
[    9.171556] audit: initializing netlink socket (disabled)
[    9.171568] audit(1215193626.385:1): initialized
[    9.171751] highmem bounce pool size: 64 pages
[    9.173353] VFS: Disk quotas dquot_6.5.1
[    9.173417] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    9.173529] io scheduler noop registered
[    9.173531] io scheduler anticipatory registered
[    9.173533] io scheduler deadline registered
[    9.173541] io scheduler cfq registered (default)
[    9.173552] Boot video device is 0000:00:02.0
[    9.173774] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    9.173836] assign_interrupt_mode Found MSI capability
[    9.173887] Allocate Port Service[0000:00:1c.0:pcie00]
[    9.173918] Allocate Port Service[0000:00:1c.0:pcie02]
[    9.174018] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[    9.174079] assign_interrupt_mode Found MSI capability
[    9.174127] Allocate Port Service[0000:00:1c.1:pcie00]
[    9.174154] Allocate Port Service[0000:00:1c.1:pcie02]
[    9.174252] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[    9.174313] assign_interrupt_mode Found MSI capability
[    9.174361] Allocate Port Service[0000:00:1c.4:pcie00]
[    9.174387] Allocate Port Service[0000:00:1c.4:pcie02]
[    9.174612] isapnp: Scanning for PnP cards...
[    9.528850] isapnp: No Plug & Play device found
[    9.549318] Real Time Clock Driver v1.12ac
[    9.549445] hpet_resources: 0xfed00000 is busy
[    9.549497] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    9.550454] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    9.550508] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    9.550586] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    9.567878] i8042.c: Detected active multiplexing controller, rev 1.1.
[    9.578040] serio: i8042 KBD port at 0x60,0x64 irq 1
[    9.578044] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    9.578046] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    9.578048] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    9.578050] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    9.593145] mice: PS/2 mouse device common for all mice
[    9.593236] EISA: Probing bus 0 at eisa.0
[    9.593244] Cannot allocate resource for EISA slot 1
[    9.593274] EISA: Detected 0 cards.
[    9.593277] cpuidle: using governor ladder
[    9.593278] cpuidle: using governor menu
[    9.593348] NET: Registered protocol family 1
[    9.593371] Using IPI No-Shortcut mode
[    9.593396] registered taskstats version 1
[    9.593507]   Magic number: 0:345:794
[    9.593548]   hash matches device ptyr2
[    9.593573] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    9.593575] EDD information not available.
[    9.593760] Freeing unused kernel memory: 368k freed
[    9.615636] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   10.781777] fuse init (API version 7.9)
[   10.799483] ACPI: SSDT 7F66E538, 0244 (r1  PmRef  Cpu0Ist     3000 INTL 20050624)
[   10.799662] ACPI: SSDT 7F66DECE, 05E5 (r1  PmRef  Cpu0Cst     3001 INTL 20050624)
[   10.800170] Monitor-Mwait will be used to enter C-1 state
[   10.800173] Monitor-Mwait will be used to enter C-2 state
[   10.800175] Monitor-Mwait will be used to enter C-3 state
[   10.800286] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   10.800290] ACPI: Processor [CPU0] (supports 8 throttling states)
[   10.800483] ACPI: SSDT 7F66E77C, 00C4 (r1  PmRef  Cpu1Ist     3000 INTL 20050624)
[   10.800649] ACPI: SSDT 7F66E4B3, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20050624)
[   10.801300] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[   10.801305] ACPI: Processor [CPU1] (supports 8 throttling states)
[   10.802535] ACPI: Thermal Zone [THM] (35 C)
[   10.949411] usbcore: registered new interface driver usbfs
[   10.949430] usbcore: registered new interface driver hub
[   10.964466] usbcore: registered new device driver usb
[   10.967431] USB Universal Host Controller Interface driver v3.0
[   10.967479] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 20 (level, low) -> IRQ 18
[   10.967490] PCI: Setting latency timer of device 0000:00:1a.0 to 64
[   10.967494] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[   10.967722] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[   10.967756] uhci_hcd 0000:00:1a.0: irq 18, io base 0x00006f20
[   10.967873] usb usb1: configuration #1 chosen from 1 choice
[   10.967894] hub 1-0:1.0: USB hub found
[   10.967898] hub 1-0:1.0: 2 ports detected
[   11.068331] ACPI: PCI Interrupt 0000:00:1a.1[b] -> GSI 21 (level, low) -> IRQ 19
[   11.068343] PCI: Setting latency timer of device 0000:00:1a.1 to 64
[   11.068347] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[   11.068371] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
[   11.068405] uhci_hcd 0000:00:1a.1: irq 19, io base 0x00006f00
[   11.068505] usb usb2: configuration #1 chosen from 1 choice
[   11.068530] hub 2-0:1.0: USB hub found
[   11.068534] hub 2-0:1.0: 2 ports detected
[   11.174287] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 20 (level, low) -> IRQ 18
[   11.174300] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   11.174304] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   11.174328] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 3
[   11.174359] uhci_hcd 0000:00:1d.0: irq 18, io base 0x00006f80
[   11.174462] usb usb3: configuration #1 chosen from 1 choice
[   11.174485] hub 3-0:1.0: USB hub found
[   11.174489] hub 3-0:1.0: 2 ports detected
[   11.185970] SCSI subsystem initialized
[   11.211571] libata version 3.00 loaded.
[   11.276213] ACPI: PCI Interrupt 0000:00:1d.1[b] -> GSI 21 (level, low) -> IRQ 19
[   11.276225] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   11.276229] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   11.276249] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 4
[   11.276278] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00006f60
[   11.276378] usb usb4: configuration #1 chosen from 1 choice
[   11.276397] hub 4-0:1.0: USB hub found
[   11.276401] hub 4-0:1.0: 2 ports detected
[   11.380173] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 22 (level, low) -> IRQ 20
[   11.380186] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   11.380190] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   11.380211] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 5
[   11.380243] uhci_hcd 0000:00:1d.2: irq 20, io base 0x00006f40
[   11.380346] usb usb5: configuration #1 chosen from 1 choice
[   11.380367] hub 5-0:1.0: USB hub found
[   11.380371] hub 5-0:1.0: 2 ports detected
[   11.484217] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 22 (level, low) -> IRQ 20
[   11.484232] PCI: Setting latency timer of device 0000:00:1a.7 to 64
[   11.484235] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[   11.484260] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 6
[   11.488176] ehci_hcd 0000:00:1a.7: debug port 1
[   11.488183] PCI: cache line size of 32 is not supported by device 0000:00:1a.7
[   11.488188] ehci_hcd 0000:00:1a.7: irq 20, io mem 0xfed1c400
[   11.503979] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   11.504083] usb usb6: configuration #1 chosen from 1 choice
[   11.504104] hub 6-0:1.0: USB hub found
[   11.504109] hub 6-0:1.0: 4 ports detected
[   11.608014] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 20 (level, low) -> IRQ 18
[   11.608031] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   11.608035] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   11.608055] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 7
[   11.611971] ehci_hcd 0000:00:1d.7: debug port 1
[   11.611978] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   11.611983] ehci_hcd 0000:00:1d.7: irq 18, io mem 0xfed1c000
[   11.619954] usb 4-1: new low speed USB device using uhci_hcd and address 2
[   11.631919] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   11.632033] usb usb7: configuration #1 chosen from 1 choice
[   11.632054] hub 7-0:1.0: USB hub found
[   11.632060] hub 7-0:1.0: 6 ports detected
[   11.737196] ACPI: PCI Interrupt 0000:02:09.0[A] -> GSI 16 (level, low) -> IRQ 16
[   11.787806] Clocksource tsc unstable (delta = -1494435721 ns)
[   11.788986] Time: hpet clocksource has been installed.
[   11.789980] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[16]  MMIO=[fe3ff800-fe3fffff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[   11.794082] ata_piix 0000:00:1f.1: version 2.12
[   11.794098] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 16 (level, low) -> IRQ 16
[   11.794133] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   11.794201] scsi0 : ata_piix
[   11.795033] scsi1 : ata_piix
[   11.795593] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x6fa0 irq 14
[   11.795595] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x6fa8 irq 15
[   11.823774] ata1.00: ATAPI: TSSTcorp DVD+/-RW TS-L632H, D400, max UDMA/33
[   11.829500] usb 4-1: new low speed USB device using uhci_hcd and address 3
[   11.839556] ata1.00: configured for UDMA/33
[   11.839646] ata2: port disabled. ignoring.
[   11.841993] scsi 0:0:0:0: CD-ROM            TSSTcorp DVD+-RW TS-L632H D400 PQ: 0 ANSI: 5
[   11.842304] ahci 0000:00:1f.2: version 3.0
[   11.842328] ACPI: PCI Interrupt 0000:00:1f.2[b] -> GSI 17 (level, low) -> IRQ 17
[   11.842376] ahci 0000:00:1f.2: nr_ports (3) and implemented port map (0x5) don't match, using nr_ports
[   11.842378] ahci 0000:00:1f.2: forcing PORTS_IMPL to 0x7
[   11.851442] usb 4-1: configuration #1 chosen from 1 choice
[   11.869337] usbcore: registered new interface driver hiddev
[   11.873322] input: USB Optical Mouse USB Optical Mouse as /devices/pci0000:00/0000:00:1d.1/usb4/4-1/4-1:1.0/input/input2
[   11.877532] input,hidraw0: USB HID v1.10 Mouse [USB Optical Mouse USB Optical Mouse] on usb-0000:00:1d.1-1
[   11.877552] usbcore: registered new interface driver usbhid
[   11.877557] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   11.932472] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[344fc00027bed070]
[   11.948811] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x7 impl SATA mode
[   11.948817] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part 
[   11.948826] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   11.949089] scsi2 : ahci
[   11.949229] scsi3 : ahci
[   11.949347] scsi4 : ahci
[   11.949594] ata3: SATA max UDMA/133 abar m2048@0xfe9fb800 port 0xfe9fb900 irq 220
[   11.949598] ata4: SATA max UDMA/133 abar m2048@0xfe9fb800 port 0xfe9fb980 irq 220
[   11.949601] ata5: SATA max UDMA/133 abar m2048@0xfe9fb800 port 0xfe9fba00 irq 220
[   11.999978] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   12.001017] ata3.00: ATA-8: ST9160827AS, 3.ADA, max UDMA/133
[   12.001021] ata3.00: 312581808 sectors, multi 8: LBA48 NCQ (depth 31/32)
[   12.002342] ata3.00: configured for UDMA/133
[   12.022362] ata4: SATA link down (SStatus 0 SControl 0)
[   12.040818] ata5: SATA link down (SStatus 0 SControl 300)
[   12.041058] scsi 2:0:0:0: Direct-Access     ATA      ST9160827AS      3.AD PQ: 0 ANSI: 5
[   12.052136] Driver 'sd' needs updating - please use bus_type methods
[   12.054321] Driver 'sr' needs updating - please use bus_type methods
[   12.056759] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   12.056812] sd 2:0:0:0: [sda] Write Protect is off
[   12.056817] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   12.056893] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   12.056982] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   12.057013] sd 2:0:0:0: [sda] Write Protect is off
[   12.057015] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   12.057076] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   12.057079]  sda:sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[   12.073617] Uniform CD-ROM driver Revision: 3.20
[   12.073670] sr 0:0:0:0: Attached scsi CD-ROM sr0
[   12.073803]  sda1 sda2 sda3 sda4 < sda5 sda6 >
[   12.104293] sd 2:0:0:0: [sda] Attached SCSI disk
[   12.108186] sr 0:0:0:0: Attached scsi generic sg0 type 5
[   12.108205] sd 2:0:0:0: Attached scsi generic sg1 type 0
[   12.579029] Attempting manual resume
[   12.579031] swsusp: Resume From Partition 8:6
[   12.579033] PM: Checking swsusp image.
[   12.579187] PM: Resume from disk failed.
[   12.605531] kjournald starting.  Commit interval 5 seconds
[   12.605565] EXT3-fs: mounted filesystem with ordered data mode.
[   22.062976] Linux agpgart interface v0.102
[   22.151921] agpgart: Detected an Intel 965GM Chipset.
[   22.152812] agpgart: Detected 7676K stolen memory.
[   22.165635] agpgart: AGP aperture is 256M @ 0xe0000000
[   22.214704] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   22.225448] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   22.549060] ACPI: Battery Slot [BAT0] (battery present)
[   22.582528] ACPI: AC Adapter [AC] (on-line)
[   22.638739] input: Lid Switch as /devices/virtual/input/input3
[   22.639619] ACPI: Lid Switch [LID]
[   22.639658] input: Power Button (CM) as /devices/virtual/input/input4
[   22.662390] ACPI: Power Button (CM) [PBTN]
[   22.662455] input: Sleep Button (CM) as /devices/virtual/input/input5
[   22.694358] ACPI: Sleep Button (CM) [SBTN]
[   22.694433] ACPI: WMI-Acer: Mapper loaded
[   22.758619] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:00/input/input6
[   22.790309] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   22.790458] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:01/input/input7
[   22.822284] ACPI: Video Device [VID2] (multi-head: yes  rom: no  post: no)
[   23.075255] ACPI: PCI Interrupt 0000:09:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   23.075270] PCI: Setting latency timer of device 0000:09:00.0 to 64
[   23.075307] sky2 0000:09:00.0: v1.20 addr 0xfe8fc000 irq 16 Yukon-FE+ (0xb8) rev 0
[   23.075702] sky2 eth0: addr 00:1d:09:56:68:fc
[   23.256697] iTCO_vendor_support: vendor-support=0
[   23.370006] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   23.370090] iTCO_wdt: Found a ICH8M TCO device (Version=2, TCOBASE=0x1060)
[   23.370129] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   23.562498] ricoh-mmc: Ricoh MMC Controller disabling driver
[   23.562501] ricoh-mmc: Copyright(c) Philip Langdale
[   23.562542] ricoh-mmc: Ricoh MMC controller found at 0000:02:09.2 [1180:0843] (rev 12)
[   23.562554] ricoh-mmc: Controller is now disabled.
[   23.637849] sdhci: Secure Digital Host Controller Interface driver
[   23.637852] sdhci: Copyright(c) Pierre Ossman
[   23.637892] sdhci: SDHCI controller found at 0000:02:09.1 [1180:0822] (rev 22)
[   23.637920] ACPI: PCI Interrupt 0000:02:09.1[b] -> GSI 18 (level, low) -> IRQ 21
[   23.637979] mmc0: SDHCI at 0xfe3ff400 irq 21 DMA
[   23.673791] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.25
[   23.673794] iwl3945: Copyright(c) 2003-2007 Intel Corporation
[   23.673941] ACPI: PCI Interrupt 0000:0b:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   23.673956] PCI: Setting latency timer of device 0000:0b:00.0 to 64
[   23.673980] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   23.753890] input: PC Speaker as /devices/platform/pcspkr/input/input8
[   23.754580] wmaster0: Selected rate control algorithm 'iwl-3945-rs'
[   23.946828] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 21 (level, low) -> IRQ 19
[   23.946851] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   23.992583] ACPI: PCI interrupt for device 0000:0b:00.0 disabled
[   24.255834] input: PS/2 Mouse as /devices/virtual/input/input9
[   24.370391] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio2/input/input10
[   24.551180] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   25.137156] lp: driver loaded but no devices found
[   25.216508] Adding 1220868k swap on /dev/sda6.  Priority:-1 extents:1 across:1220868k
[   25.600750] EXT3 FS on sda2, internal journal
[  273.017278] kjournald starting.  Commit interval 5 seconds
[  273.017589] EXT3 FS on sda3, internal journal
[  273.017595] EXT3-fs: mounted filesystem with ordered data mode.
[  273.603611] ip_tables: (C) 2000-2006 Netfilter Core Team
[  274.135300] No dock devices found.
[  275.642134] apm: BIOS not found.
[  275.934971] ppdev: user-space parallel port driver
[  276.686902] audit(1215183099.154:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=8458 profile="/usr/sbin/cupsd" namespace="default"
[  277.125604] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[  277.125611] vboxdrv: Successfully done.
[  277.125672] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[  277.125675] vboxdrv: Successfully loaded version 1.5.6_OSE (interface 0x00050002).
[  277.448092] NET: Registered protocol family 10
[  277.448796] lo: Disabled Privacy Extensions
[  278.252169] ACPI: PCI Interrupt 0000:0b:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[  278.252319] PM: Writing back config space on device 0000:0b:00.0 at offset 1 (was 100102, writing 100106)
[  278.313146] iwl3945: Tunable channels: 13 802.11bg, 23 802.11a channels
[  278.319559] Registered led device: iwl-phy0:RX
[  278.319591] Registered led device: iwl-phy0:TX
[  278.324461] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  278.343276] sky2 eth0: enabling interface
[  278.349501] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  278.759606] Bluetooth: Core ver 2.11
[  278.759958] NET: Registered protocol family 31
[  278.759963] Bluetooth: HCI device and connection manager initialized
[  278.759968] Bluetooth: HCI socket layer initialized
[  278.811416] Bluetooth: L2CAP ver 2.9
[  278.811422] Bluetooth: L2CAP socket layer initialized
[  278.969383] Bluetooth: RFCOMM socket layer initialized
[  278.969400] Bluetooth: RFCOMM TTY layer initialized
[  278.969403] Bluetooth: RFCOMM ver 1.8
[  281.596366] [drm] Initialized drm 1.1.0 20060810
[  281.599772] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[  281.599786] PCI: Setting latency timer of device 0000:00:02.0 to 64
[  281.599869] [drm] Initialized i915 1.6.0 20060119 on minor 0
[  296.874234] CPU0 attaching NULL sched-domain.
[  296.874241] CPU1 attaching NULL sched-domain.
[  296.888105] CPU0 attaching sched-domain:
[  296.888110]  domain 0: span 03
[  296.888111]   groups: 01 02
[  296.888114] CPU1 attaching sched-domain:
[  296.888115]  domain 0: span 03
[  296.888117]   groups: 02 01
[  297.349578] NET: Registered protocol family 17
[  299.417780] wlan0: Initial auth_alg=0
[  299.417785] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[  299.419604] wlan0: RX authentication from 00:1c:10:3c:c6:0e (alg=0 transaction=2 status=0)
[  299.419610] wlan0: authenticated
[  299.419612] wlan0: associate with AP 00:1c:10:3c:c6:0e
[  299.422126] wlan0: RX AssocResp from 00:1c:10:3c:c6:0e (capab=0x411 status=0 aid=1)
[  299.422132] wlan0: associated
[  299.423989] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  299.932673] padlock: VIA PadLock not detected.
[  308.269858] wlan0: no IPv6 routers present
[  523.159158] wlan0: No ProbeResp from current AP 00:1c:10:3c:c6:0e - assume out of range
[  527.055686] wlan0: No STA entry for own AP 00:1c:10:3c:c6:0e
[  536.739962] wlan0: Initial auth_alg=0
[  536.739975] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[  536.798230] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[  536.864577] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[  536.903118] wlan0: authentication with AP 00:1c:10:3c:c6:0e timed out
[  544.857809] wlan0: Initial auth_alg=0
[  544.857817] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[  544.858987] wlan0: Initial auth_alg=0
[  544.858994] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[  544.995893] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[  545.030222] wlan0: authenticate with AP 00:1c:10:3c:c6:0e
[  545.075160] wlan0: authentication with AP 00:1c:10:3c:c6:0e timed out
```

---

### Post by pytheas22 on 2008-07-04
Thanks for the dmesg.

I'm not sure exactly what's wrong, but I found this [bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/200500") about the problem.  It seems like the problem is that the wireless card thinks it's moved out of range of the router, even though it hasn't.

Unfortunately there's no concrete solution in the bug report, although there are some suggestions.  It's not clear whether the source of this problem is the wireless driver, Network Manager or something else.

The first thing to try I think is this: the next time you reboot your computer, run the command:
```

sudo iwconfig wlan0 retry 14
```

and see if that seems to keep it more stable.

---

### Post by pytheas22 on 2008-07-04
Here is a [possibly]("http://intellinuxwireless.org/bugzilla/show_bug.cgi?id=1548") more relevant bug report, specific to your kind of wireless driver (Intel iwl3945).  They suggest that downloading the latest driver from [http://linuxwireless.org/en/users/Download](http://linuxwireless.org/en/users/Download) might help.  You could try that if you have a little time.

Also, from what I'm reading, when your connection breaks, these commands should fix it (no need for reboot, just reinserting the module):
```

sudo rmmod iwl3945
sudo modprobe iwl3945
sudo ifconfig wlan0 up
sudo iwconfig wlan0 retry 14
```

Then wait a few seconds and you should be able to connect again.

---

