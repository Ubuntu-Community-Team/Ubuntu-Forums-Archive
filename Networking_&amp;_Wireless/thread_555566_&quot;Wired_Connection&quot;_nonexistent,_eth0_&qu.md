---
title: "&quot;Wired Connection&quot; nonexistent, eth0 &quot;no such device&quot;"
date: 2007-09-20
forum: Networking &amp; Wireless
---

### Post by 1212jtraceur on 2007-09-20
Hello all,

I was trying to change my Wireless Connection to not roam, and to not use any encryption to connect to my network. I couldn't get that to work, but that's for another thread... Anyway, when I was doing that, I disabled the Wired Connection, thinking (stupidly) that it would have anything to do with it.

Now the Wired Connection option in System>Administration>Network is no longer there. I've searched around a lot, but have found no solution (other then (dis/reen)abling it in the BIOS, which works until I reboot, as was found here : [http://ubuntuforums.org/showthread.php?t=461052&highlight=eth0+no+such+device](http://ubuntuforums.org/showthread.php?t=461052&highlight=eth0+no+such+device)). Oh yeah, the situation is the same even from the LiveCD.

Information follows:

I have a Lenovo Thinkpad t60p running Feisty.
In my Device Manager, I have "82573L Gigabit Ethernet Controller" listed.

"ifconfig -a" shows:
[PHP]ath0      Link encap:Ethernet  HWaddr 00:1C:26:19:0B:DC  
          inet addr:10.229.5.22  Bcast:10.229.7.255  Mask:255.255.248.0
          inet6 addr: fe80::21c:26ff:fe19:bdc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15427 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3252 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4646198 (4.4 MiB)  TX bytes:850292 (830.3 KiB)

irda0     Link encap:IrLAP  HWaddr 00:00:00:00  
          NOARP  MTU:2048  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:8 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:776321 errors:0 dropped:0 overruns:0 frame:0
          TX packets:776321 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:974254847 (929.1 MiB)  TX bytes:974254847 (929.1 MiB)

wifi0     Link encap:UNSPEC  HWaddr 00-1C-26-19-0B-DC-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:30537 errors:0 dropped:0 overruns:0 frame:44071
          TX packets:3506 errors:15 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:7415445 (7.0 MiB)  TX bytes:938018 (916.0 KiB)
          Interrupt:21 
[/PHP]

It's not even seeing the device.

"sudo dhclient eth0" gives me:
[PHP]There is already a pid file /var/run/dhclient.pid with pid 7563
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
wifi0: unknown hardware address type 801
Bind socket to interface: No such device
[/PHP]

// I'm not really worried about wifi0, in fact, I don't even no what it is

"sudo ifup eth0":
[PHP]eth0: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
wifi0: unknown hardware address type 801
Bind socket to interface: No such device
Failed to bring up eth0.
[/PHP]

nm-tool says nothing about eth0, and neither does dmesg

I'm sorry if that was too much information, I'm not sure of what will help and what won't. It *does* work, though, if I disable and reenable it in the BIOS.

Thanks for any help,
1212jtraceur

---

### Post by noob12 on 2007-09-20
Please post the output of these.  It suggests that the driver is having problems claiming or initializing the device.
```

sudo lshw -C network

dmesg

```

If the driver is e1000 and you see bad checksum messages, then there's an easy solution.  If not we have to do more diagnosis.  The bad checksum solution is just this

```

echo "options e1000 eeprom_bad_csum_allow=1" | sudo tee -a /etc/modprobe.d/options

```

and reboot.  _But only apply this if you are seeing bad checksum messages at boot in dmesg._

---

### Post by 1212jtraceur on 2007-09-20
sudo lshw -C network:
[PHP]  *-network               
       description: Ethernet interface
       product: 82573L Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@02:00.0
       logical name: eth0
       version: 00
       serial: 00:1a:6b:6c:de:91
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.15-k2-NAPI firmware=0.5-1 latency=0 link=no multicast=yes port=twisted pair
       resources: iomemory:ee000000-ee01ffff ioport:3000-301f irq:16
  *-network
       description: Wireless interface
       product: AR5212 802.11abg NIC
       vendor: Atheros Communications, Inc.
       physical id: 0
       bus info: pci@03:00.0
       logical name: wifi0
       version: 01
       serial: 00:1c:26:19:0b:dc
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci driverversion=0.9.4.5 (0.9.3.1) ip=10.229.5.22 latency=0 multicast=yes wireless=IEEE 802.11g
       resources: iomemory:edf00000-edf0ffff irq:21
[/PHP]

dmesg:
[PHP][    0.000000] Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Fri Aug 31 00:55:27 UTC 2007 (Ubuntu 2.6.20-16.31-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f000 end: 000000000009f000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009f000 size: 0000000000001000 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000d2000 size: 0000000000002000 end: 00000000000d4000 type: 2
[    0.000000] copy_e820_map() start: 00000000000dc000 size: 0000000000024000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000007fdd0000 end: 000000007fed0000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000007fed0000 size: 000000000000f000 end: 000000007fedf000 type: 3
[    0.000000] copy_e820_map() start: 000000007fedf000 size: 0000000000021000 end: 000000007ff00000 type: 4
[    0.000000] copy_e820_map() start: 000000007ff00000 size: 0000000000100000 end: 0000000080000000 type: 2
[    0.000000] copy_e820_map() start: 00000000f0000000 size: 0000000004000000 end: 00000000f4000000 type: 2
[    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000000010000 end: 00000000fec10000 type: 2
[    0.000000] copy_e820_map() start: 00000000fed00000 size: 0000000000000400 end: 00000000fed00400 type: 2
[    0.000000] copy_e820_map() start: 00000000fed14000 size: 0000000000006000 end: 00000000fed1a000 type: 2
[    0.000000] copy_e820_map() start: 00000000fed1c000 size: 0000000000074000 end: 00000000fed90000 type: 2
[    0.000000] copy_e820_map() start: 00000000fee00000 size: 0000000000001000 end: 00000000fee01000 type: 2
[    0.000000] copy_e820_map() start: 00000000ff800000 size: 0000000000800000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d2000 - 00000000000d4000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007fed0000 (usable)
[    0.000000]  BIOS-e820: 000000007fed0000 - 000000007fedf000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007fedf000 - 000000007ff00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007ff00000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff800000 - 0000000100000000 (reserved)
[    0.000000] 1150MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f6810
[    0.000000] Entering add_active_range(0, 0, 523984) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   523984
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   523984
[    0.000000] On node 0 totalpages: 523984
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2301 pages used for memmap
[    0.000000]   HighMem zone: 292307 pages, LIFO batch:31
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP (v002 LENOVO                                ) @ 0x000f67e0
[    0.000000] ACPI: XSDT (v001 LENOVO TP-7I    0x00001110  LTP 0x00000000) @ 0x7fed1555
[    0.000000] ACPI: FADT (v003 LENOVO TP-7I    0x00001110 LNVO 0x00000001) @ 0x7fed1600
[    0.000000] ACPI: SSDT (v001 LENOVO TP-7I    0x00001110 MSFT 0x0100000e) @ 0x7fed17b4
[    0.000000] ACPI: ECDT (v001 LENOVO TP-7I    0x00001110 LNVO 0x00000001) @ 0x7fedeb92
[    0.000000] ACPI: TCPA (v002 LENOVO TP-7I    0x00001110 LNVO 0x00000001) @ 0x7fedebe4
[    0.000000] ACPI: MADT (v001 LENOVO TP-7I    0x00001110 LNVO 0x00000001) @ 0x7fedec16
[    0.000000] ACPI: MCFG (v001 LENOVO TP-7I    0x00001110 LNVO 0x00000001) @ 0x7fedec7e
[    0.000000] ACPI: HPET (v001 LENOVO TP-7I    0x00001110 LNVO 0x00000001) @ 0x7fedecba
[    0.000000] ACPI: SLIC (v001 LENOVO TP-7I    0x00001110  LTP 0x00000000) @ 0x7fedee62
[    0.000000] ACPI: BOOT (v001 LENOVO TP-7I    0x00001110  LTP 0x00000001) @ 0x7fedefd8
[    0.000000] ACPI: SSDT (v001 LENOVO TP-7I    0x00001110 INTL 0x20050513) @ 0x7fef2697
[    0.000000] ACPI: SSDT (v001 LENOVO TP-7I    0x00001110 INTL 0x20050513) @ 0x7fef28f6
[    0.000000] ACPI: SSDT (v001 LENOVO TP-7I    0x00001110 INTL 0x20050513) @ 0x7fef299c
[    0.000000] ACPI: SSDT (v001 LENOVO TP-7I    0x00001110 INTL 0x20050513) @ 0x7fef2e93
[    0.000000] ACPI: DSDT (v001 LENOVO TP-7I    0x00001110 MSFT 0x0100000e) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:15 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 6:15 APIC version 20
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:70000000)
[    0.000000] Detected 1995.235 MHz processor.
[   11.117765] Built 1 zonelists.  Total pages: 519891
[   11.117771] Kernel command line: root=UUID=932f541d-8674-4acb-a791-b248a9d89ffb ro quiet splash resume=/dev/sda4
[   11.118017] mapped APIC to ffffd000 (fee00000)
[   11.118021] mapped IOAPIC to ffffc000 (fec00000)
[   11.118025] Enabling fast FPU save and restore... done.
[   11.118029] Enabling unmasked SIMD FPU exception support... done.
[   11.118039] Initializing CPU#0
[   11.118120] PID hash table entries: 4096 (order: 12, 16384 bytes)
[   11.121371] Console: colour VGA+ 80x25
[   11.121687] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   11.122112] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   11.247007] Memory: 2066640k/2095936k available (1993k kernel code, 27920k reserved, 900k data, 328k init, 1178432k highmem)
[   11.247022] virtual kernel memory layout:
[   11.247024]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   11.247026]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   11.247028]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   11.247030]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   11.247032]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
[   11.247034]       .data : 0xc02f2434 - 0xc03d36d4   ( 900 kB)
[   11.247035]       .text : 0xc0100000 - 0xc02f2434   (1993 kB)
[   11.247041] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   11.247268] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   11.247276] hpet0: 3 64-bit timers, 14318180 Hz
[   11.248283] Using HPET for base-timer
[   11.327229] Calibrating delay using timer specific routine.. 3995.28 BogoMIPS (lpj=7990573)
[   11.327289] Security Framework v1.0.0 initialized
[   11.327298] SELinux:  Disabled at boot.
[   11.327321] Mount-cache hash table entries: 512
[   11.327511] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e3bd 00000000 00000001
[   11.327523] monitor/mwait feature present.
[   11.327526] using mwait in idle threads.
[   11.327533] CPU: L1 I cache: 32K, L1 D cache: 32K
[   11.327537] CPU: L2 cache: 4096K
[   11.327541] CPU: Physical Processor ID: 0
[   11.327543] CPU: Processor Core ID: 0
[   11.327546] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e3bd 00000000 00000001
[   11.327560] Compat vDSO mapped to ffffe000.
[   11.327566] Remapping vsyscall page to ffffe000
[   11.327584] Checking 'hlt' instruction... OK.
[   11.343363] SMP alternatives: switching to UP code
[   11.343875] Early unpacking initramfs... done
[   11.886581] ACPI: Core revision 20060707
[   11.886944] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   11.919878] CPU0: Intel(R) Core(TM)2 CPU         T7200  @ 2.00GHz stepping 06
[   11.919903] SMP alternatives: switching to SMP code
[   11.919991] Booting processor 1/1 eip 3000
[   11.931299] Initializing CPU#1
[   12.011161] Calibrating delay using timer specific routine.. 3990.17 BogoMIPS (lpj=7980358)
[   12.011171] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e3bd 00000000 00000001
[   12.011179] monitor/mwait feature present.
[   12.011183] CPU: L1 I cache: 32K, L1 D cache: 32K
[   12.011186] CPU: L2 cache: 4096K
[   12.011190] CPU: Physical Processor ID: 0
[   12.011192] CPU: Processor Core ID: 1
[   12.011194] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e3bd 00000000 00000001
[   12.011949] CPU1: Intel(R) Core(TM)2 CPU         T7200  @ 2.00GHz stepping 06
[   12.011981] Total of 2 processors activated (7985.46 BogoMIPS).
[   12.012184] ENABLING IO-APIC IRQs
[   12.012406] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   12.158770] checking TSC synchronization across 2 CPUs: 
[    0.000002] CPU#0 had -154 usecs TSC skew, fixed it up.
[    0.000006] CPU#1 had 154 usecs TSC skew, fixed it up.
[    0.004002] Brought up 2 CPUs
[    0.214377] migration_cost=39
[    0.214771] Booting paravirtualized kernel on bare hardware
[    0.214890] Time: 12:36:25  Date: 08/20/107
[    0.214934] NET: Registered protocol family 16
[    0.215050] EISA bus registered
[    0.215060] ACPI: bus type pci registered
[    0.215199] PCI: PCI BIOS revision 2.10 entry at 0xfd84b, last bus=24
[    0.215203] PCI: Using configuration type 1
[    0.215205] Setting up standard PCI resources
[    0.234018] ACPI: Interpreter enabled
[    0.234022] ACPI: Using IOAPIC for interrupt routing
[    0.235403] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11)
[    0.236405] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11)
[    0.237389] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11)
[    0.238376] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11)
[    0.239359] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11)
[    0.240377] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 *11)
[    0.241357] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 *11)
[    0.242335] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 *11)
[    0.242979] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.242987] PCI: Probing PCI hardware (bus 00)
[    0.245897] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    0.245904] PCI quirk: region 1180-11bf claimed by ICH6 GPIO
[    0.246453] Boot video device is 0000:01:00.0
[    0.247453] PCI: Transparent bridge - 0000:00:1e.0
[    0.247668] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.256371] ACPI: Power Resource [PUBS] (on)
[    0.258057] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.258611] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP0._PRT]
[    0.258910] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP1._PRT]
[    0.259206] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP2._PRT]
[    0.259568] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP3._PRT]
[    0.259935] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[    0.263431] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.263449] pnp: PnP ACPI init
[    0.271537] pnp: PnP ACPI: found 12 devices
[    0.271543] PnPBIOS: Disabled by ACPI PNP
[    0.271608] PCI: Using ACPI for IRQ routing
[    0.271612] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    0.335597] NET: Registered protocol family 8
[    0.335600] NET: Registered protocol family 20
[    0.337285] PCI: Bridge: 0000:00:01.0
[    0.337290]   IO window: 2000-2fff
[    0.337297]   MEM window: ee100000-ee1fffff
[    0.337302]   PREFETCH window: d0000000-dfffffff
[    0.337308] PCI: Bridge: 0000:00:1c.0
[    0.337313]   IO window: 3000-3fff
[    0.337321]   MEM window: ee000000-ee0fffff
[    0.337327]   PREFETCH window: disabled.
[    0.337334] PCI: Bridge: 0000:00:1c.1
[    0.337339]   IO window: 4000-5fff
[    0.337347]   MEM window: ec000000-edffffff
[    0.337354]   PREFETCH window: e4000000-e40fffff
[    0.337362] PCI: Bridge: 0000:00:1c.2
[    0.337366]   IO window: 6000-7fff
[    0.337374]   MEM window: e8000000-e9ffffff
[    0.337381]   PREFETCH window: e4100000-e41fffff
[    0.337389] PCI: Bridge: 0000:00:1c.3
[    0.337393]   IO window: 8000-9fff
[    0.337401]   MEM window: ea000000-ebffffff
[    0.337408]   PREFETCH window: e4200000-e42fffff
[    0.337420] PCI: Bus 22, cardbus bridge: 0000:15:00.0
[    0.337423]   IO window: 0000a000-0000a0ff
[    0.337430]   IO window: 0000a400-0000a4ff
[    0.337438]   PREFETCH window: e0000000-e3ffffff
[    0.337446]   MEM window: 88000000-8bffffff
[    0.337453] PCI: Bridge: 0000:00:1e.0
[    0.337457]   IO window: a000-dfff
[    0.337465]   MEM window: e4300000-e7ffffff
[    0.337472]   PREFETCH window: e0000000-e3ffffff
[    0.337495] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[    0.337503] PCI: Setting latency timer of device 0000:00:01.0 to 64
[    0.337534] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 20 (level, low) -> IRQ 17
[    0.337542] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    0.337573] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 21 (level, low) -> IRQ 18
[    0.337582] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[    0.337612] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 22 (level, low) -> IRQ 19
[    0.337620] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[    0.337651] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 23 (level, low) -> IRQ 20
[    0.337660] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[    0.337674] PCI: Enabling device 0000:00:1e.0 (0005 -> 0007)
[    0.337683] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    0.337706] ACPI: PCI Interrupt 0000:15:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[    0.337750] NET: Registered protocol family 2
[    0.391840] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.391972] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.392649] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.392976] TCP: Hash tables configured (established 131072 bind 65536)
[    0.392980] TCP reno registered
[    0.407940] checking if image is initramfs... it is
[    1.477438] Freeing initrd memory: 6983k freed
[    1.477666] Simple Boot Flag at 0x35 set to 0x1
[    1.478348] audit: initializing netlink socket (disabled)
[    1.478370] audit(1190291786.448:1): initialized
[    1.478517] highmem bounce pool size: 64 pages
[    1.478640] VFS: Disk quotas dquot_6.5.1
[    1.478666] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.478732] io scheduler noop registered
[    1.478736] io scheduler anticipatory registered
[    1.478739] io scheduler deadline registered
[    1.478757] io scheduler cfq registered (default)
[    1.479085] PCI: Setting latency timer of device 0000:00:01.0 to 64
[    1.479143] assign_interrupt_mode Found MSI capability
[    1.479148] Allocate Port Service[0000:00:01.0:pcie00]
[    1.479297] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    1.479370] assign_interrupt_mode Found MSI capability
[    1.479374] Allocate Port Service[0000:00:1c.0:pcie00]
[    1.479429] Allocate Port Service[0000:00:1c.0:pcie02]
[    1.479595] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[    1.479668] assign_interrupt_mode Found MSI capability
[    1.479672] Allocate Port Service[0000:00:1c.1:pcie00]
[    1.479724] Allocate Port Service[0000:00:1c.1:pcie02]
[    1.479887] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[    1.479960] assign_interrupt_mode Found MSI capability
[    1.479964] Allocate Port Service[0000:00:1c.2:pcie00]
[    1.480015] Allocate Port Service[0000:00:1c.2:pcie02]
[    1.480181] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[    1.480255] assign_interrupt_mode Found MSI capability
[    1.480258] Allocate Port Service[0000:00:1c.3:pcie00]
[    1.480317] Allocate Port Service[0000:00:1c.3:pcie02]
[    1.480573] isapnp: Scanning for PnP cards...
[    1.835563] isapnp: No Plug & Play device found
[    1.869229] Real Time Clock Driver v1.12ac
[    1.869309] hpet_resources: 0xfed00000 is busy
[    1.869345] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    1.870395] mice: PS/2 mouse device common for all mice
[    1.871430] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    1.871644] input: Macintosh mouse button emulation as /class/input/input0
[    1.871699] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    1.871704] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    1.872069] PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
[    1.879705] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.879712] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.879848] EISA: Probing bus 0 at eisa.0
[    1.879858] Cannot allocate resource for EISA slot 1
[    1.879863] Cannot allocate resource for EISA slot 2
[    1.879866] Cannot allocate resource for EISA slot 3
[    1.879870] Cannot allocate resource for EISA slot 4
[    1.879873] Cannot allocate resource for EISA slot 5
[    1.879877] Cannot allocate resource for EISA slot 6
[    1.879880] Cannot allocate resource for EISA slot 7
[    1.879883] Cannot allocate resource for EISA slot 8
[    1.879886] EISA: Detected 0 cards.
[    1.894966] input: AT Translated Set 2 keyboard as /class/input/input1
[    1.909995] TCP cubic registered
[    1.910007] NET: Registered protocol family 1
[    1.910037] Starting balanced_irq
[    1.910046] Using IPI No-Shortcut mode
[    1.910146] swsusp: Resume From Partition /dev/sda4
[    1.910149] PM: Checking swsusp image.
[    1.910158] swsusp: Error -6 check for resume file
[    1.910161] PM: Resume from disk failed.
[    1.910282] ACPI: (supports S0 S3 S4 S5)
[    1.910351]   Magic number: 7:374:633
[    1.910376]   hash matches device ptycc
[    1.910602] Freeing unused kernel memory: 328k freed
[    1.910951] Time: tsc clocksource has been installed.
[    3.237659] Capability LSM initialized
[    3.298867] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu0Ist] [20060707]
[    3.299474] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu0Cst] [20060707]
[    3.300761] Monitor-Mwait will be used to enter C-1 state
[    3.300767] Monitor-Mwait will be used to enter C-2 state
[    3.300771] Monitor-Mwait will be used to enter C-3 state
[    3.300781] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    3.300789] ACPI: Processor [CPU0] (supports 8 throttling states)
[    3.301741] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu1Ist] [20060707]
[    3.302226] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu1Cst] [20060707]
[    3.303571] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    3.303580] ACPI: Processor [CPU1] (supports 8 throttling states)
[    4.096000] ACPI: Thermal Zone [THM0] (34 C)
[    4.096000] ACPI: Thermal Zone [THM1] (33 C)
[    4.100000] Time: hpet clocksource has been installed.
[    4.592000] Intel(R) PRO/1000 Network Driver - version 7.3.15-k2-NAPI
[    4.592000] Copyright (c) 1999-2006 Intel Corporation.
[    4.592000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[    4.592000] PCI: Setting latency timer of device 0000:02:00.0 to 64
[    4.612000] usbcore: registered new interface driver usbfs
[    4.612000] usbcore: registered new interface driver hub
[    4.612000] usbcore: registered new device driver usb
[    4.612000] USB Universal Host Controller Interface driver v3.0
[    4.708000] SCSI subsystem initialized
[    4.716000] libata version 2.20 loaded.
[    4.756000] e1000: 0000:02:00.0: e1000_probe: (PCI Express:2.5Gb/s:Width x1) 00:1a:6b:6c:de:91
[    4.816000] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
[    4.816000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16
[    4.816000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[    4.816000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    4.816000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    4.816000] uhci_hcd 0000:00:1d.0: irq 16, io base 0x00001800
[    4.816000] usb usb1: configuration #1 chosen from 1 choice
[    4.816000] hub 1-0:1.0: USB hub found
[    4.816000] hub 1-0:1.0: 2 ports detected
[    4.920000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 17 (level, low) -> IRQ 21
[    4.920000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[    4.920000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    4.920000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[    4.920000] uhci_hcd 0000:00:1d.1: irq 21, io base 0x00001820
[    4.920000] usb usb2: configuration #1 chosen from 1 choice
[    4.920000] hub 2-0:1.0: USB hub found
[    4.920000] hub 2-0:1.0: 2 ports detected
[    5.024000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 22
[    5.024000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[    5.024000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    5.024000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[    5.024000] uhci_hcd 0000:00:1d.2: irq 22, io base 0x00001840
[    5.024000] usb usb3: configuration #1 chosen from 1 choice
[    5.024000] hub 3-0:1.0: USB hub found
[    5.024000] hub 3-0:1.0: 2 ports detected
[    5.128000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 19 (level, low) -> IRQ 23
[    5.128000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[    5.128000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    5.128000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[    5.128000] uhci_hcd 0000:00:1d.3: irq 23, io base 0x00001860
[    5.128000] usb usb4: configuration #1 chosen from 1 choice
[    5.128000] hub 4-0:1.0: USB hub found
[    5.128000] hub 4-0:1.0: 2 ports detected
[    5.232000] ahci 0000:00:1f.2: version 2.1
[    5.232000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 16 (level, low) -> IRQ 16
[    5.472000] usb 4-2: new full speed USB device using uhci_hcd and address 2
[    5.648000] usb 4-2: configuration #1 chosen from 1 choice
[    6.236000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[    6.236000] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 4 ports 1.5 Gbps 0x1 impl SATA mode
[    6.236000] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part 
[    6.236000] ata1: SATA max UDMA/133 cmd 0xf8890500 ctl 0x00000000 bmdma 0x00000000 irq 16
[    6.236000] ata2: SATA max UDMA/133 cmd 0xf8890580 ctl 0x00000000 bmdma 0x00000000 irq 16
[    6.236000] ata3: SATA max UDMA/133 cmd 0xf8890600 ctl 0x00000000 bmdma 0x00000000 irq 16
[    6.236000] ata4: SATA max UDMA/133 cmd 0xf8890680 ctl 0x00000000 bmdma 0x00000000 irq 16
[    6.236000] scsi0 : ahci
[    6.720000] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    6.720000] ata1.00: ata_hpa_resize 1: sectors = 312581808, hpa_sectors = 312581808
[    6.720000] ata1.00: ATA-7: HITACHI HTS541616J9SA00, SB4IC7UP, max UDMA/100
[    6.720000] ata1.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    6.720000] ata1.00: ata_hpa_resize 1: sectors = 312581808, hpa_sectors = 312581808
[    6.720000] ata1.00: configured for UDMA/100
[    6.720000] scsi1 : ahci
[    7.032000] ata2: SATA link down (SStatus 0 SControl 0)
[    7.032000] scsi2 : ahci
[    7.344000] ata3: SATA link down (SStatus 0 SControl 0)
[    7.344000] scsi3 : ahci
[    7.656000] ata4: SATA link down (SStatus 0 SControl 0)
[    7.656000] scsi 0:0:0:0: Direct-Access     ATA      HITACHI HTS54161 SB4I PQ: 0 ANSI: 5
[    7.656000] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 19 (level, low) -> IRQ 23
[    7.656000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    7.656000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    7.656000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[    7.656000] ehci_hcd 0000:00:1d.7: debug port 1
[    7.656000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[    7.656000] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xee404000
[    7.660000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    7.664000] usb usb5: configuration #1 chosen from 1 choice
[    7.664000] hub 5-0:1.0: USB hub found
[    7.664000] hub 5-0:1.0: 8 ports detected
[    7.668000] SCSI device sda: 312581808 512-byte hdwr sectors (160042 MB)
[    7.668000] sda: Write Protect is off
[    7.668000] sda: Mode Sense: 00 3a 00 00
[    7.668000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.668000] SCSI device sda: 312581808 512-byte hdwr sectors (160042 MB)
[    7.668000] sda: Write Protect is off
[    7.668000] sda: Mode Sense: 00 3a 00 00
[    7.668000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.668000]  sda:<6>usb 4-2: USB disconnect, address 2
[    7.768000] ata_piix 0000:00:1f.1: version 2.10ac1
[    7.768000] ACPI: PCI Interrupt 0000:00:1f.1[C] -> GSI 16 (level, low) -> IRQ 16
[    7.768000] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[    7.768000] ata5: PATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00011880 irq 14
[    7.768000] ata6: PATA max UDMA/133 cmd 0x00010170 ctl 0x00010376 bmdma 0x00011888 irq 15
[    7.768000] scsi4 : ata_piix
[    8.084000]  sda1 sda2 sda3 sda4
[    8.088000] ata5.00: ATAPI, max UDMA/33
[    8.112000] sd 0:0:0:0: Attached scsi disk sda
[    8.116000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    8.252000] ata5.00: configured for UDMA/33
[    8.252000] scsi5 : ata_piix
[    8.252000] ata6: port disabled. ignoring.
[    8.252000] scsi 4:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-4083N 1.00 PQ: 0 ANSI: 5
[    8.252000] scsi 4:0:0:0: Attached scsi generic sg1 type 5
[    8.276000] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    8.276000] Uniform CD-ROM driver Revision: 3.20
[    8.276000] sr 4:0:0:0: Attached scsi CD-ROM sr0
[    8.360000] Attempting manual resume
[    8.360000] swsusp: Resume From Partition 8:4
[    8.360000] PM: Checking swsusp image.
[    8.360000] PM: Resume from disk failed.
[    8.404000] kjournald starting.  Commit interval 5 seconds
[    8.404000] EXT3-fs: mounted filesystem with ordered data mode.
[    8.496000] usb 4-2: new full speed USB device using uhci_hcd and address 3
[    8.672000] usb 4-2: configuration #1 chosen from 1 choice
[   19.784000] e1000: eth0: e1000_request_irq: Unable to allocate MSI interrupt Error: -22
[   21.240000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   21.256000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   21.276000] Linux agpgart interface v0.102 (c) Dave Jones
[   21.300000] agpgart: Detected an Intel 945GM Chipset.
[   21.320000] agpgart: AGP aperture is 256M @ 0x0
[   21.332000] NET: Registered protocol family 17
[   21.564000] input: PC Speaker as /class/input/input2
[   21.572000] Yenta: CardBus bridge found at 0000:15:00.0 [17aa:2012]
[   21.572000] Yenta: Using INTVAL to route CSC interrupts to PCI
[   21.572000] Yenta: Routing CardBus interrupts to PCI
[   21.572000] Yenta TI: socket 0000:15:00.0, mfunc 0x01d01002, devctl 0x64
[   21.604000] iTCO_vendor_support: vendor-support=0
[   21.612000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[   21.612000] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x1060)
[   21.612000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   21.776000] intel_rng: FWH not detected
[   21.780000] ath_hal: module license 'Proprietary' taints kernel.
[   21.780000] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   21.804000] Yenta: ISA IRQ mask 0x0cf8, PCI irq 16
[   21.804000] Socket status: 30000007
[   21.804000] pcmcia: parent PCI bridge I/O window: 0xa000 - 0xdfff
[   21.804000] cs: IO port probe 0xa000-0xdfff: clean.
[   21.804000] pcmcia: parent PCI bridge Memory window: 0xe4300000 - 0xe7ffffff
[   21.804000] pcmcia: parent PCI bridge Memory window: 0xe0000000 - 0xe3ffffff
[   21.864000] irda_init()
[   21.864000] NET: Registered protocol family 23
[   21.984000] wlan: 0.8.4.2 (0.9.3.1)
[   21.992000] pnp: Device 00:0a activated.
[   21.992000] nsc_ircc_pnp_probe() : From PnP, found firbase 0x2F8 ; irq 3 ; dma 1.
[   21.992000] nsc-ircc, chip->init
[   21.992000] nsc-ircc, Found chip at base=0x164e
[   21.992000] nsc-ircc, driver loaded (Dag Brattli)
[   21.992000] IrDA: Registered device irda0
[   21.992000] nsc-ircc, Using dongle: IBM31T1100 or Temic TFDS6000/TFDS6500
[   22.112000] ath_pci: 0.9.4.5 (0.9.3.1)
[   22.112000] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 21
[   22.112000] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   22.700000] ath_rate_sample: 1.2 (0.9.3.1)
[   22.700000] wifi0: 11a rates: 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   22.700000] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[   22.700000] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   22.700000] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
[   22.700000] wifi0: mac 10.3 phy 6.1 radio 10.2
[   22.700000] wifi0: Use hw queue 1 for WME_AC_BE traffic
[   22.700000] wifi0: Use hw queue 0 for WME_AC_BK traffic
[   22.700000] wifi0: Use hw queue 2 for WME_AC_VI traffic
[   22.700000] wifi0: Use hw queue 3 for WME_AC_VO traffic
[   22.700000] wifi0: Use hw queue 8 for CAB traffic
[   22.700000] wifi0: Use hw queue 9 for beacons
[   22.740000] wifi0: Atheros 5212: mem=0xedf00000, irq=21
[   22.804000] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x81a0b1, caps: 0xa04793/0x300000
[   22.804000] serio: Synaptics pass-through port at isa0060/serio1/input0
[   22.848000] input: SynPS/2 Synaptics TouchPad as /class/input/input3
[   22.888000] cs: IO port probe 0x100-0x3af: clean.
[   22.888000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   22.888000] cs: IO port probe 0x820-0x8ff: clean.
[   22.892000] cs: IO port probe 0xc00-0xcf7: clean.
[   22.892000] cs: IO port probe 0xa00-0xaff: clean.
[   22.960000] ACPI: PCI Interrupt 0000:00:1b.0[B] -> GSI 17 (level, low) -> IRQ 21
[   22.960000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   23.452000] fuse init (API version 7.8)
[   23.532000] lp: driver loaded but no devices found
[   23.572000] Adding 1992052k swap on /dev/disk/by-uuid/170ce00d-97ba-425c-9144-25111ed8d1d9.  Priority:-1 extents:1 across:1992052k
[   23.752000] EXT3 FS on sda3, internal journal
[   24.116000] kjournald starting.  Commit interval 5 seconds
[   24.116000] EXT3 FS on sda2, internal journal
[   24.116000] EXT3-fs: mounted filesystem with ordered data mode.
[   24.160000] NTFS driver 2.1.28 [Flags: R/O MODULE].
[   24.164000] NTFS-fs warning (device sda1): parse_options(): Option utf8 is no longer supported, using option nls=utf8. Please use option nls=utf8 in the future and make sure utf8 is compiled either as a module or into the kernel.
[   24.252000] NTFS volume version 3.1.
[   24.364000] hda_intel: azx_get_response timeout, switching to polling mode...
[   28.012000] IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   28.284000] input: TPPS/2 IBM TrackPoint as /class/input/input4
[   28.784000] Using specific hotkey driver
[   28.908000] input: Power Button (FF) as /class/input/input5
[   28.908000] ACPI: Power Button (FF) [PWRF]
[   28.908000] input: Lid Switch as /class/input/input6
[   28.908000] ACPI: Lid Switch [LID]
[   28.908000] input: Sleep Button (CM) as /class/input/input7
[   28.908000] ACPI: Sleep Button (CM) [SLPB]
[   29.152000] ibm_acpi: ThinkPad EC firmware 79HT50WW-1.07
[   29.152000] ibm_acpi: IBM ThinkPad ACPI Extras v0.13
[   29.152000] ibm_acpi: http://ibm-acpi.sf.net/
[   29.188000] ACPI: AC Adapter [AC] (off-line)
[   29.212000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   29.212000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   29.252000] ACPI: Battery Slot [BAT0] (battery present)
[   29.276000] ACPI: ACPI Dock Station Driver 
[   29.332000] pcc_acpi: loading...
[   33.424000] ppdev: user-space parallel port driver
[   34.204000] apm: BIOS not found.
[   34.232000] [fglrx] Maximum main memory to use for locked dma buffers: 1898 MBytes.
[   34.232000] [fglrx] module loaded - fglrx 8.34.8 [Feb 20 2007] on minor 0
[   34.252000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   34.416000] Non-volatile memory driver v1.2
[   34.472000] input: /usr/sbin/thinkpad-keys as /class/input/input8
[   34.576000] Bluetooth: Core ver 2.11
[   34.576000] NET: Registered protocol family 31
[   34.576000] Bluetooth: HCI device and connection manager initialized
[   34.576000] Bluetooth: HCI socket layer initialized
[   34.588000] Bluetooth: L2CAP ver 2.8
[   34.588000] Bluetooth: L2CAP socket layer initialized
[   34.812000] Bluetooth: RFCOMM socket layer initialized
[   34.812000] Bluetooth: RFCOMM TTY layer initialized
[   34.812000] Bluetooth: RFCOMM ver 1.8
[   36.260000] [fglrx] total      GART = 130023424
[   36.260000] [fglrx] free       GART = 114032640
[   36.260000] [fglrx] max single GART = 114032640
[   36.260000] [fglrx] total      LFB  = 268304384
[   36.260000] [fglrx] free       LFB  = 244305920
[   36.260000] [fglrx] max single LFB  = 244305920
[   36.260000] [fglrx] total      Inv  = 0
[   36.260000] [fglrx] free       Inv  = 0
[   36.260000] [fglrx] max single Inv  = 0
[   36.260000] [fglrx] total      TIM  = 0
[   42.296000] input: Virtual ThinkFinger Keyboard as /class/input/input9
[   46.948000] NET: Registered protocol family 10
[   46.948000] lo: Disabled Privacy Extensions
[   46.948000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   57.396000] ath0: no IPv6 routers present
[   82.228000] ath0: no IPv6 routers present
[  200.444000] input: Virtual ThinkFinger Keyboard as /class/input/input10
[  203.876000] pcmcia: Detected deprecated PCMCIA ioctl usage from process: lshw.
[  203.876000] pcmcia: This interface will soon be removed from the kernel; please expect breakage unless you upgrade to new tools.
[  203.876000] pcmcia: see http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html for details.
[  204.020000] sr 4:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[  204.020000]     Additional sense: Medium not present
[  204.020000] end_request: I/O error, dev sr0, sector 0
[  204.020000] Buffer I/O error on device sr0, logical block 0
[  204.020000] Buffer I/O error on device sr0, logical block 1
[  204.020000] Buffer I/O error on device sr0, logical block 2
[  204.020000] Buffer I/O error on device sr0, logical block 3
[  204.020000] Buffer I/O error on device sr0, logical block 4
[  204.020000] Buffer I/O error on device sr0, logical block 5
[  204.020000] Buffer I/O error on device sr0, logical block 6
[  204.020000] Buffer I/O error on device sr0, logical block 7
[  204.024000] sr 4:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[  204.024000]     Additional sense: Medium not present
[  204.024000] end_request: I/O error, dev sr0, sector 0
[  204.024000] Buffer I/O error on device sr0, logical block 0
[  204.024000] sr 4:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[  204.024000]     Additional sense: Medium not present
[  204.024000] end_request: I/O error, dev sr0, sector 4
[  204.024000] Buffer I/O error on device sr0, logical block 1
[  204.028000] sr 4:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[  204.028000]     Additional sense: Medium not present
[  204.028000] end_request: I/O error, dev sr0, sector 0
[  204.028000] sr 4:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[  204.028000]     Additional sense: Medium not present
[  204.028000] end_request: I/O error, dev sr0, sector 4
[  204.032000] sr 4:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[  204.032000]     Additional sense: Medium not present
[  204.032000] end_request: I/O error, dev sr0, sector 0
[  204.032000] sr 4:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[  204.032000]     Additional sense: Medium not present
[  204.032000] end_request: I/O error, dev sr0, sector 4
[  204.036000] sr 4:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[  204.036000]     Additional sense: Medium not present
[  204.036000] end_request: I/O error, dev sr0, sector 0
[  204.036000] sr 4:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[  204.036000]     Additional sense: Medium not present
[  204.036000] end_request: I/O error, dev sr0, sector 4
[  204.036000] sr 4:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[  204.036000]     Additional sense: Medium not present
[  204.036000] end_request: I/O error, dev sr0, sector 0
[  204.040000] sr 4:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[  204.040000]     Additional sense: Medium not present
[  204.040000] end_request: I/O error, dev sr0, sector 4
[  274.980000] input: Virtual ThinkFinger Keyboard as /class/input/input11
[/PHP]

dmesg | grep e1000:
[PHP][    0.337297]   MEM window: ee100000-ee1fffff
[    4.756000] e1000: 0000:02:00.0: e1000_probe: (PCI Express:2.5Gb/s:Width x1) 00:1a:6b:6c:de:91
[    4.816000] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
[   19.784000] e1000: eth0: e1000_request_irq: Unable to allocate MSI interrupt Error: -22
[/PHP]

"dmesg | grep checksum" prints nothing, so I'm guessing that fix doesn't apply to this situation. What else should I do?

Thanks,
1212jtraceur

EDIT : A friend says that problem is common, and that rebooting fixes it. I just checked, and the Wired Connection is there this time, but I would still like to find a true solution.

---

### Post by noob12 on 2007-09-20
Right.  What you have appears to be a PCI routing issue.  You should file a bug on launchpad and you may find that booting with **pci=noacpi** or **pci=routeirq** helps.

---

### Post by noob12 on 2007-09-20
One more thing.  Using the latest e1000 driver (7.6.5) may also help, but I'm not sure about that.
Instructions for that if you are interested can be gleaned from this thread, although it is written for users with no support in the current drivers:  [http://ubuntuforums.org/showthread.php?t=551720](http://ubuntuforums.org/showthread.php?t=551720)

If you do try that and learn anything positive or negative from it, I'd be interested.

---

### Post by 1212jtraceur on 2007-09-20
Hmm...It's working now. I have no idea why, though... Do you think they updated e1000 driver would help in case the problem returns (my device id is 8086:109a, not one of those you listed), or should I just leave things how they are?

Thanks for your help,
1212jtraceur

---

### Post by noob12 on 2007-09-20
The new e1000 driver will work for you but it may not solve your problem.  The device ids listed there are ones for which you *must* upgrade to the new driver to even get supported, but all of the old device ids covered by the current Feisty e1000 driver are also covered by the new one.

You can try to live with the current one and just rebooting when needed or using one of the suggested boot flags.  If you are feeling adventurous, you can try the new e1000 driver and see if things improve.

---

### Post by 1212jtraceur on 2007-09-20
Ok, I've tried installing the drivers found [here]("http://sourceforge.net/project/showfiles.php?group_id=42302&package_id=54835"), but it still doesn't seem to work, even after 2 reboots, adding "e1000" to /etc/modules and running /etc/init.d/networking restart. Is there any way to see which version is loaded as shown by lsmod?

I didn't install the drivers in your other thread because I didn't see the attachments anywhere. Could you attach e1000-7.6.5-i386-bin-1b.tar.bz2 to your next message? That way I could try that.

EDIT : I tried the boot pci flag options. "routeirq" did nothing and my computer wouldn't start with "pci=noacpi"

---

### Post by noob12 on 2007-09-20
I don't know why they disappeared, but I reattached them to the original posting on that thread.  I won't post them here.  It may be that the forum staff or the forum software is removing them due to some policy issue, but I haven't been PM-ed about that.  Anyway, they are there now for you to try.

The 7.6.5 driver will announce itself as such while loading.  Look at the dmesg for something like this:  "Intel(R) PRO/1000 Network Driver - version 7.6.5-NAPI".

---

### Post by 1212jtraceur on 2007-09-21
It still doesn't work. When I use the checksum fix and run 'sudo modprobe e1000', I get:
	FATAL: Error inserting e1000 (/lib/modules/2.6.20-16-generic/kernel/drivers/net/e1000/e1000.ko): Unknown symbol in module, or unknown parameter (see dmesg)

dmesg then shows:
	e1000: Unknown parameter `eeprom_bad_csum_allow'

---

### Post by noob12 on 2007-09-21
The new driver doesn't have the same options as the old one.  Don't set the option on the new driver.  It is complaining because that's an unknown option for the new one.

You can see the options available by typing **modinfo e1000**

Edit your **/etc/modules** file or your **/etc/modprobe.d/options** file to take out that option setting for e1000.

---

