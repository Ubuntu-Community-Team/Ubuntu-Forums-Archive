---
title: "Ubuntu 7.10 and Realtek network card issues"
date: 2008-01-23
forum: Networking &amp; Wireless
---

### Post by sifter on 2008-01-23
Hello there, I am a long time Red Hat/Fedora user, but am keen to move to Ubuntu.  I have installed Ubuntu today on a brand new machine which does not have Windows on it.

$uname -r 
2.6.22-14-generic

The PC shipped with two network cards.  I presume one is built in to the motherboard, and the second was installed in addition to this.  After some problems with networking, I went to a local store and bought a new card.  This is currently in my machine.  

I have plugged my ethernet cable directly into the second network card (eth2) and rebooted.  I have the following information...

john@berrymead:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 01
       serial: 00:1c:c0:09:aa:d9
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=half latency=0 link=no module=r8169 multicast=yes port=twisted pair
  *-network
       description: Ethernet interface
       product: RTL-8169 Gigabit Ethernet
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth2
       version: 10
       serial: 00:08:54:53:29:ac
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=192.168.1.15 latency=64 link=yes maxlatency=64 mingnt=32 module=r8169 multicast=yes port=twisted 
pair speed=100MB/s


john@berrymead:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1C:C0:09:AA:D9  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:20 Base address:0x2000 

eth2      Link encap:Ethernet  HWaddr 00:08:54:53:29:AC  
          inet addr:192.168.1.15  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:141098 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8471998 (8.0 MB)  TX bytes:2853 (2.7 KB)
          Interrupt:16 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


john@berrymead:~$ dmesg
[    0.000000] Linux version 2.6.22-14-generic (buildd@palmer) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 23:05:12 GMT 2007 (Ubuntu 2.6.22-14.46-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000008f000 (usable)
[    0.000000]  BIOS-e820: 000000000008f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007e5a4000 (usable)
[    0.000000]  BIOS-e820: 000000007e5a4000 - 000000007e692000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007e692000 - 000000007f574000 (usable)
[    0.000000]  BIOS-e820: 000000007f574000 - 000000007f57c000 (reserved)
[    0.000000]  BIOS-e820: 000000007f57c000 - 000000007f60b000 (usable)
[    0.000000]  BIOS-e820: 000000007f60b000 - 000000007f60f000 (reserved)
[    0.000000]  BIOS-e820: 000000007f60f000 - 000000007f6a8000 (usable)
[    0.000000]  BIOS-e820: 000000007f6a8000 - 000000007f6ea000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007f6ea000 - 000000007f6ee000 (usable)
[    0.000000]  BIOS-e820: 000000007f6ee000 - 000000007f6ff000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007f6ff000 - 000000007f700000 (usable)
[    0.000000]  BIOS-e820: 000000007f700000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] 1143MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000fe200
[    0.000000] Entering add_active_range(0, 0, 521984) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   521984
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   521984
[    0.000000] On node 0 totalpages: 521984
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2286 pages used for memmap
[    0.000000]   HighMem zone: 290322 pages, LIFO batch:31
[    0.000000] DMI 2.4 present.
[    0.000000] ACPI: RSDP signature @ 0xC00FE020 checksum 0
[    0.000000] ACPI: RSDP 000FE020, 0014 (r0 INTEL )
[    0.000000] ACPI: RSDT 7F6FD038, 0050 (r1 INTEL  D945GCR        32       1000013)
[    0.000000] ACPI: FACP 7F6FC000, 0074 (r1 INTEL  D945GCR        32 MSFT  1000013)
[    0.000000] ACPI: DSDT 7F6F8000, 3CE6 (r1 INTEL  D945GCR        32 MSFT  1000013)
[    0.000000] ACPI: FACS 7F6A8000, 0040
[    0.000000] ACPI: APIC 7F6F7000, 0078 (r1 INTEL  D945GCR        32 MSFT  1000013)
[    0.000000] ACPI: WDDT 7F6F6000, 0040 (r1 INTEL  D945GCR        32 MSFT  1000013)
[    0.000000] ACPI: MCFG 7F6F5000, 003C (r1 INTEL  D945GCR        32 MSFT  1000013)
[    0.000000] ACPI: ASF! 7F6F4000, 00A6 (r32 INTEL  D945GCR        32 MSFT  1000013)
[    0.000000] ACPI: HPET 7F6F3000, 0038 (r1 INTEL  D945GCR        32 MSFT  1000013)
[    0.000000] ACPI: SSDT 7F6F2000, 01BC (r1 INTEL     CpuPm       32 MSFT  1000013)
[    0.000000] ACPI: SSDT 7F6F1000, 01B7 (r1 INTEL   Cpu0Ist       32 MSFT  1000013)
[    0.000000] ACPI: SSDT 7F6F0000, 01B7 (r1 INTEL   Cpu1Ist       32 MSFT  1000013)
[    0.000000] ACPI: SSDT 7F6EF000, 01B7 (r1 INTEL   Cpu2Ist       32 MSFT  1000013)
[    0.000000] ACPI: SSDT 7F6EE000, 01B7 (r1 INTEL   Cpu3Ist       32 MSFT  1000013)
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:15 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] Processor #1 6:15 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
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
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:7ff80000)
[    0.000000] Built 1 zonelists.  Total pages: 517906
[    0.000000] Kernel command line: root=UUID=1803f517-eadb-4d41-b0c7-2a606dc6369e ro quiet splash
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 2194.580 MHz processor.
[   21.312713] Console: colour VGA+ 80x25
[   21.312928] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   21.313161] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   21.384856] Memory: 2056976k/2087936k available (2015k kernel code, 28392k reserved, 916k data, 364k init, 1169100k highmem)
[   21.384863] virtual kernel memory layout:
[   21.384863]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   21.384864]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   21.384865]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   21.384866]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   21.384867]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   21.384868]       .data : 0xc02f7d26 - 0xc03dce84   ( 916 kB)
[   21.384869]       .text : 0xc0100000 - 0xc02f7d26   (2015 kB)
[   21.384871] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   21.384905] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   21.385018] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   21.385024] hpet0: 3 64-bit timers, 14318180 Hz
[   21.465930] Calibrating delay using timer specific routine.. 4392.24 BogoMIPS (lpj=8784485)
[   21.465950] Security Framework v1.0.0 initialized
[   21.465955] SELinux:  Disabled at boot.
[   21.465965] Mount-cache hash table entries: 512
[   21.466073] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e39d 00000000 00000001
[   21.466079] monitor/mwait feature present.
[   21.466080] using mwait in idle threads.
[   21.466084] CPU: L1 I cache: 32K, L1 D cache: 32K
[   21.466086] CPU: L2 cache: 2048K
[   21.466088] CPU: Physical Processor ID: 0
[   21.466089] CPU: Processor Core ID: 0
[   21.466091] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e39d 00000000 00000001
[   21.466099] Compat vDSO mapped to ffffe000.
[   21.466109] Checking 'hlt' instruction... OK.
[   21.482041] SMP alternatives: switching to UP code
[   21.482422] Early unpacking initramfs... done
[   21.741993] ACPI: Core revision 20070126
[   21.742028] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   21.744564] CPU0: Intel(R) Core(TM)2 Duo CPU     E4500  @ 2.20GHz stepping 0d
[   21.744577] SMP alternatives: switching to SMP code
[   21.744646] Booting processor 1/1 eip 3000
[   21.754820] Initializing CPU#1
[   21.833434] Calibrating delay using timer specific routine.. 4388.99 BogoMIPS (lpj=8777999)
[   21.833439] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e39d 00000000 00000001
[   21.833443] monitor/mwait feature present.
[   21.833445] CPU: L1 I cache: 32K, L1 D cache: 32K
[   21.833447] CPU: L2 cache: 2048K
[   21.833449] CPU: Physical Processor ID: 0
[   21.833450] CPU: Processor Core ID: 1
[   21.833451] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e39d 00000000 00000001
[   21.833954] CPU1: Intel(R) Core(TM)2 Duo CPU     E4500  @ 2.20GHz stepping 0d
[   21.833970] Total of 2 processors activated (8781.24 BogoMIPS).
[   21.834113] ENABLING IO-APIC IRQs
[   21.834281] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   21.981313] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   22.001300] Brought up 2 CPUs
[   22.140548] migration_cost=85
[   22.140662] Booting paravirtualized kernel on bare hardware
[   22.140714] Time: 10:42:36  Date: 00/24/108
[   22.140730] NET: Registered protocol family 16
[   22.140797] EISA bus registered
[   22.140800] ACPI: bus type pci registered
[   22.142891] PCI: Using configuration type 1
[   22.142892] Setting up standard PCI resources
[   22.150023] ACPI: EC: Look up EC in DSDT
[   22.151344] ACPI: Interpreter enabled
[   22.151347] ACPI: (supports S0 S1 S3 S4 S5)
[   22.151360] ACPI: Using IOAPIC for interrupt routing
[   22.154207] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   22.154226] PCI: Probing PCI hardware (bus 00)
[   22.154681] PCI quirk: region 0400-047f claimed by ICH6 ACPI/GPIO/TCO
[   22.154684] PCI quirk: region 0500-053f claimed by ICH6 GPIO
[   22.155067] PCI: Transparent bridge - 0000:00:1e.0
[   22.155097] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   22.155294] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P32_._PRT]
[   22.155406] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
[   22.157462] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12)
[   22.157529] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 *10 11 12)
[   22.157597] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 *9 10 11 12)
[   22.157661] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11 12)
[   22.157726] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[   22.157791] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[   22.157878] Linux Plug and Play Support v0.97 (c) Adam Belay
[   22.157888] pnp: PnP ACPI init
[   22.157894] ACPI: bus type pnp registered
[   22.159525] pnp: PnP ACPI: found 13 devices
[   22.159527] ACPI: ACPI bus type pnp unregistered
[   22.159530] PnPBIOS: Disabled by ACPI PNP
[   22.159566] PCI: Using ACPI for IRQ routing
[   22.159568] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   22.159626] NET: Registered protocol family 8
[   22.159627] NET: Registered protocol family 20
[   22.159667] pnp: 00:01: iomem range 0xf0000000-0xf3ffffff has been reserved
[   22.159669] pnp: 00:01: iomem range 0xfed13000-0xfed13fff has been reserved
[   22.159672] pnp: 00:01: iomem range 0xfed14000-0xfed17fff has been reserved
[   22.159674] pnp: 00:01: iomem range 0xfed18000-0xfed18fff has been reserved
[   22.159680] pnp: 00:06: ioport range 0x500-0x53f has been reserved
[   22.159682] pnp: 00:06: ioport range 0x400-0x47f has been reserved
[   22.159684] pnp: 00:06: ioport range 0x680-0x6ff has been reserved
[   22.160999] Time: tsc clocksource has been installed.
[   22.161009] Switched to high resolution mode on CPU 0
[   22.161080] Switched to high resolution mode on CPU 1
[   22.189870] PCI: Bridge: 0000:00:1c.0
[   22.189873]   IO window: 2000-2fff
[   22.189877]   MEM window: 90100000-901fffff
[   22.189880]   PREFETCH window: 90300000-903fffff
[   22.189885] PCI: Bridge: 0000:00:1e.0
[   22.189887]   IO window: 1000-1fff
[   22.189891]   MEM window: 90000000-900fffff
[   22.189894]   PREFETCH window: 90400000-904fffff
[   22.189914] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 16
[   22.189919] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   22.189928] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   22.189936] NET: Registered protocol family 2
[   22.240899] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   22.240959] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[   22.241620] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   22.241849] TCP: Hash tables configured (established 131072 bind 65536)
[   22.241851] TCP reno registered
[   22.257037] checking if image is initramfs... it is
[   22.772153] Freeing initrd memory: 7335k freed
[   22.772647] audit: initializing netlink socket (disabled)
[   22.772663] audit(1201171356.152:1): initialized
[   22.772740] highmem bounce pool size: 64 pages
[   22.774182] VFS: Disk quotas dquot_6.5.1
[   22.774216] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   22.774292] io scheduler noop registered
[   22.774293] io scheduler anticipatory registered
[   22.774295] io scheduler deadline registered
[   22.774305] io scheduler cfq registered (default)
[   22.774319] Boot video device is 0000:00:02.0
[   22.774542] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   22.774579] assign_interrupt_mode Found MSI capability
[   22.774581] Allocate Port Service[0000:00:1c.0:pcie00]
[   22.774609] Allocate Port Service[0000:00:1c.0:pcie02]
[   22.774723] isapnp: Scanning for PnP cards...
[   23.127210] isapnp: No Plug & Play device found
[   23.142350] Real Time Clock Driver v1.12ac
[   23.142436] hpet_resources: 0xfed00000 is busy
[   23.142459] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   23.142547] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   23.143020] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   23.143522] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   23.143619] input: Macintosh mouse button emulation as /class/input/input0
[   23.143716] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[   23.144213] serio: i8042 KBD port at 0x60,0x64 irq 1
[   23.144219] serio: i8042 AUX port at 0x60,0x64 irq 12
[   23.144370] mice: PS/2 mouse device common for all mice
[   23.144475] EISA: Probing bus 0 at eisa.0
[   23.144480] Cannot allocate resource for EISA slot 1
[   23.144482] Cannot allocate resource for EISA slot 2
[   23.144484] Cannot allocate resource for EISA slot 3
[   23.144500] EISA: Detected 0 cards.
[   23.144577] TCP cubic registered
[   23.144588] NET: Registered protocol family 1
[   23.144604] Using IPI No-Shortcut mode
[   23.144727]   Magic number: 8:515:730
[   23.144970] Freeing unused kernel memory: 364k freed
[   24.298598] AppArmor: AppArmor initialized<5>audit(1201171357.652:2):  type=1505 info="AppArmor initialized" pid=1206
[   24.304394] fuse init (API version 7.8)
[   24.308392] Failure registering capabilities with primary security module.
[   24.331977] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   24.331986] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   24.644489] usbcore: registered new interface driver usbfs
[   24.644511] usbcore: registered new interface driver hub
[   24.656950] SCSI subsystem initialized
[   24.660533] libata version 2.21 loaded.
[   24.662713] ata_piix 0000:00:1f.1: version 2.11
[   24.662729] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 17
[   24.662756] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   24.662811] scsi0 : ata_piix
[   24.662843] scsi1 : ata_piix
[   24.662920] ata1: PATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x000130b0 irq 14
[   24.662922] ata2: PATA max UDMA/133 cmd 0x00010170 ctl 0x00010376 bmdma 0x000130b8 irq 15
[   24.663136] usbcore: registered new device driver usb
[   24.681761] USB Universal Host Controller Interface driver v3.0
[   24.981433] ata1.00: ATAPI: ASUS    DRW-1814BL, 1.13, max UDMA/66
[   25.153212] ata1.00: configured for UDMA/66
[   25.153235] ata2: port disabled. ignoring.
[   25.153808] scsi 0:0:0:0: CD-ROM            ASUS     DRW-1814BL       1.13 PQ: 0 ANSI: 5
[   25.153890] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[   25.308771] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 18
[   25.308806] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   25.308847] scsi2 : ata_piix
[   25.308903] scsi3 : ata_piix
[   25.308975] ata3: SATA max UDMA/133 cmd 0x000130c8 ctl 0x000130ee bmdma 0x000130a0 irq 18
[   25.308977] ata4: SATA max UDMA/133 cmd 0x000130c0 ctl 0x000130ea bmdma 0x000130a8 irq 18
[   25.472899] ata3.00: ATA-7: Hitachi HDT725025VLA380, V5DOA7EA, max UDMA/133
[   25.472904] ata3.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   25.488870] ata3.00: configured for UDMA/133
[   25.654984] scsi 2:0:0:0: Direct-Access     ATA      Hitachi HDT72502 V5DO PQ: 0 ANSI: 5
[   25.655101] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 19
[   25.655107] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   25.655110] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   25.655215] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   25.655239] uhci_hcd 0000:00:1d.0: irq 19, io base 0x00003080
[   25.655325] usb usb1: configuration #1 chosen from 1 choice
[   25.655345] hub 1-0:1.0: USB hub found
[   25.655350] hub 1-0:1.0: 2 ports detected
[   25.666633] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[   25.666639] Uniform CD-ROM driver Revision: 3.20
[   25.666687] sr 0:0:0:0: Attached scsi CD-ROM sr0
[   25.666825] sd 2:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[   25.666834] sd 2:0:0:0: [sda] Write Protect is off
[   25.666835] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   25.666847] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   25.666877] sd 2:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[   25.666885] sd 2:0:0:0: [sda] Write Protect is off
[   25.666886] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   25.666897] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   25.666900]  sda:<5>sr 0:0:0:0: Attached scsi generic sg0 type 5
[   25.669625] sd 2:0:0:0: Attached scsi generic sg1 type 0
[   25.676324]  sda1 sda2 < sda5 >
[   25.698282] sd 2:0:0:0: [sda] Attached SCSI disk
[   25.756258] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 19
[   25.756271] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   25.756274] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   25.756298] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[   25.756324] ehci_hcd 0000:00:1d.7: debug port 1
[   25.756330] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   25.756336] ehci_hcd 0000:00:1d.7: irq 19, io mem 0x902c4000
[   25.760225] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   25.760299] usb usb2: configuration #1 chosen from 1 choice
[   25.760321] hub 2-0:1.0: USB hub found
[   25.760326] hub 2-0:1.0: 8 ports detected
[   25.820611] Attempting manual resume
[   25.820613] swsusp: Resume From Partition 8:5
[   25.820615] PM: Checking swsusp image.
[   25.820741] PM: Resume from disk failed.
[   25.854302] kjournald starting.  Commit interval 5 seconds
[   25.854309] EXT3-fs: mounted filesystem with ordered data mode.
[   25.864069] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 18
[   25.864079] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   25.864082] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   25.864103] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[   25.864125] uhci_hcd 0000:00:1d.1: irq 18, io base 0x00003060
[   25.864203] usb usb3: configuration #1 chosen from 1 choice
[   25.864222] hub 3-0:1.0: USB hub found
[   25.864227] hub 3-0:1.0: 2 ports detected
[   25.967988] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 17
[   25.968001] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   25.968006] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   25.968032] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[   25.968057] uhci_hcd 0000:00:1d.2: irq 17, io base 0x00003040
[   25.968126] usb usb4: configuration #1 chosen from 1 choice
[   25.968144] hub 4-0:1.0: USB hub found
[   25.968148] hub 4-0:1.0: 2 ports detected
[   26.071797] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 20
[   26.071806] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   26.071811] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   26.071836] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[   26.071866] uhci_hcd 0000:00:1d.3: irq 20, io base 0x00003020
[   26.071930] usb usb5: configuration #1 chosen from 1 choice
[   26.071947] hub 5-0:1.0: USB hub found
[   26.071951] hub 5-0:1.0: 2 ports detected
[   26.175775] r8169 Gigabit Ethernet driver 2.2LK loaded
[   26.175796] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 20
[   26.175813] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   26.175990] eth0: RTL8101e at 0xf8822000, 00:1c:c0:09:aa:d9, XID 34200000 IRQ 20
[   26.176850] r8169 Gigabit Ethernet driver 2.2LK loaded
[   26.176861] ACPI: PCI Interrupt 0000:02:02.0[A] -> GSI 17 (level, low) -> IRQ 16
[   26.176966] eth1: RTL8169sb/8110sb at 0xf88aa000, 00:08:54:53:29:ac, XID 10000000 IRQ 16
[   26.523120] usb 2-5: new high speed USB device using ehci_hcd and address 4
[   26.659934] usb 2-5: configuration #1 chosen from 1 choice
[   26.898596] usb 3-2: new low speed USB device using uhci_hcd and address 2
[   27.074666] usb 3-2: configuration #1 chosen from 1 choice
[   27.441883] usb 1-2: new low speed USB device using uhci_hcd and address 2
[   27.620796] usb 1-2: configuration #1 chosen from 1 choice
[   29.700897] r8169: eth2: link up
[   30.460200] input: PC Speaker as /class/input/input1
[   30.570214] intel_rng: FWH not detected
[   30.579498] Linux agpgart interface v0.102 (c) Dave Jones
[   30.594751] agpgart: Detected an Intel 945G Chipset.
[   30.595547] agpgart: Detected 7932K stolen memory.
[   30.609565] agpgart: AGP aperture is 256M @ 0x80000000
[   30.616725] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   30.623368] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   30.626119] iTCO_vendor_support: vendor-support=0
[   30.627058] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
[   30.627350] iTCO_wdt: Found a ICH7 or ICH7R TCO device (Version=2, TCOBASE=0x0460)
[   30.627529] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   30.703698] usbcore: registered new interface driver hiddev
[   30.720102] input: Logitech USB-PS/2 Optical Mouse as /class/input/input2
[   30.720304] input: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.1-2
[   30.744896] input: BTC USB Multimedia Keyboard as /class/input/input3
[   30.744919] input: USB HID v1.10 Keyboard [BTC USB Multimedia Keyboard] on usb-0000:00:1d.0-2
[   30.793466] input: BTC USB Multimedia Keyboard as /class/input/input4
[   30.793698] input,hiddev96: USB HID v1.10 Device [BTC USB Multimedia Keyboard] on usb-0000:00:1d.0-2
[   30.793720] usbcore: registered new interface driver libusual
[   30.793722] usbcore: registered new interface driver xpad
[   30.793725] /build/buildd/linux-source-2.6.22-2.6.22/drivers/input/joystick/xpad.c: driver for Xbox controllers v0.1.6
[   30.793734] usbcore: registered new interface driver usbhid
[   30.794139] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   30.849935] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   30.849938] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   30.852783] Initializing USB Mass Storage driver...
[   30.852846] scsi4 : SCSI emulation for USB Mass Storage devices
[   30.852894] usb-storage: device found at 4
[   30.852896] usb-storage: waiting for device to settle before scanning
[   30.852903] usbcore: registered new interface driver usb-storage
[   30.852906] USB Mass Storage support registered.
[   30.990184] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 21
[   30.990202] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   31.196788] hda_codec: Unknown model for ALC662, trying auto-probe from BIOS...
[   31.449133] lp: driver loaded but no devices found
[   31.532243] Adding 6048432k swap on /dev/sda5.  Priority:-1 extents:1 across:6048432k
[   31.835371] EXT3 FS on sda1, internal journal
[   32.550734] No dock devices found.
[   32.683334] input: Power Button (FF) as /class/input/input5
[   32.683453] ACPI: Power Button (FF) [PWRF]
[   32.684085] input: Sleep Button (CM) as /class/input/input6
[   32.684201] ACPI: Sleep Button (CM) [SLPB]
[   33.555043] ppdev: user-space parallel port driver
[   33.663013] audit(1201171367.303:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4813 profile="/usr/sbin/cupsd"
[   33.694934] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   33.694938] apm: disabled - APM is not SMP safe.
[   33.736242] r8169: eth0: link down
[   33.847209] Failure registering capabilities with primary security module.
[   34.010571] Bluetooth: Core ver 2.11
[   34.010734] NET: Registered protocol family 31
[   34.010737] Bluetooth: HCI device and connection manager initialized
[   34.010741] Bluetooth: HCI socket layer initialized
[   34.022918] Bluetooth: L2CAP ver 2.8
[   34.022923] Bluetooth: L2CAP socket layer initialized
[   34.064203] Bluetooth: RFCOMM socket layer initialized
[   34.064362] Bluetooth: RFCOMM TTY layer initialized
[   34.064365] Bluetooth: RFCOMM ver 1.8
[   35.842790] usb-storage: device scan complete
[   35.843412] scsi 4:0:0:0: Direct-Access     OTi      Flash Disk       2.00 PQ: 0 ANSI: 2
[   35.844522] sd 4:0:0:0: [sdb] 1024000 512-byte hardware sectors (524 MB)
[   35.845143] sd 4:0:0:0: [sdb] Write Protect is off
[   35.845145] sd 4:0:0:0: [sdb] Mode Sense: 03 00 00 00
[   35.845147] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[   35.847765] sd 4:0:0:0: [sdb] 1024000 512-byte hardware sectors (524 MB)
[   35.848388] sd 4:0:0:0: [sdb] Write Protect is off
[   35.848391] sd 4:0:0:0: [sdb] Mode Sense: 03 00 00 00
[   35.848392] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[   35.848395]  sdb: sdb1
[   35.849430] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[   35.849458] sd 4:0:0:0: Attached scsi generic sg2 type 0
[   36.636378] [drm] Initialized drm 1.1.0 20060810
[   36.648244] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 20
[   36.648697] [drm] Initialized i915 1.6.0 20060119 on minor 0


An earlier attempt with this card had dmesg output with the last line:

[   41.579969] eth2: no IPv6 routers present

I followed the Ubuntu help instructions for disabling IPv6.  This line vanishes from the dmesg output as seen above..

I have no /etc/iftab file

The Network icon shows at the top right of the screen.  If I left-click on this, it has two entries (greyed-out) Wired Network and (selectable) Manual configuration.

The command  "sudo dhclient eth2" does not produce a connection.


Your help would be greatly appreciated!

---

### Post by sifter on 2008-01-23
In the interim, I have seen the following suggestion, and followed it, to no avail.  

[http://ubuntuforums.org/showthread.php?t=670027&page=3](http://ubuntuforums.org/showthread.php?t=670027&page=3)

My (cable) modem is a Motorola Surfboard.  

Here is additional output

john@berrymead:~$ sudo dhclient eth2
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth2/00:08:54:53:29:ac
Sending on   LPF/eth2/00:08:54:53:29:ac
Sending on   Socket/fallback
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


Additional output, with cable connected, one green light flashes on the network card.

john@berrymead:~$ sudo ethtool eth2
Settings for eth2:
        Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Advertised auto-negotiation: Yes
        Speed: 100Mb/s
        Duplex: Full
        Port: Twisted Pair
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: pumbg
        Wake-on: g
        Current message level: 0x00000033 (51)
        Link detected: yes

---

### Post by sifter on 2008-01-24
I ordered an install DVD for Fedora Core 8 today :(

---

