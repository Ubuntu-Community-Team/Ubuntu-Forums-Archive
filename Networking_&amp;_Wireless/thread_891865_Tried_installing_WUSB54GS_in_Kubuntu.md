---
title: "Tried installing WUSB54GS in Kubuntu"
date: 2008-08-16
forum: Networking &amp; Wireless
---

### Post by julain124 on 2008-08-16
I followed the tutorial here, ```
http://sudan.ubuntuforums.com/showthread.php?p=5601862#post5601862
```
And whenever I try the last command:
[PHP]cat /var/log/syslog[/PHP]

I get this:

```
Aug 16 09:28:12 recklezz-desktop kernel: [   12.422090] Memory: 1480556k/1506240k available (2177k kernel code, 24464k reserved, 1006k data, 368k init, 588736k highmem)
Aug 16 09:28:12 recklezz-desktop kernel: [   12.422097] virtual kernel memory layout:
Aug 16 09:28:12 recklezz-desktop kernel: [   12.422098]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
Aug 16 09:28:12 recklezz-desktop kernel: [   12.422099]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Aug 16 09:28:12 recklezz-desktop kernel: [   12.422100]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
Aug 16 09:28:12 recklezz-desktop kernel: [   12.422101]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Aug 16 09:28:12 recklezz-desktop kernel: [   12.422102]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
Aug 16 09:28:12 recklezz-desktop kernel: [   12.422103]       .data : 0xc0320474 - 0xc041bdc4   (1006 kB)
Aug 16 09:28:12 recklezz-desktop kernel: [   12.422104]       .text : 0xc0100000 - 0xc0320474   (2177 kB)
Aug 16 09:28:12 recklezz-desktop kernel: [   12.422107] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Aug 16 09:28:12 recklezz-desktop kernel: [   12.422144] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
Aug 16 09:28:12 recklezz-desktop kernel: [   12.502090] Calibrating delay using timer specific routine.. 4413.22 BogoMIPS (lpj=8826458)
Aug 16 09:28:12 recklezz-desktop kernel: [   12.502115] Security Framework initialized
Aug 16 09:28:12 recklezz-desktop kernel: [   12.502122] SELinux:  Disabled at boot.
Aug 16 09:28:12 recklezz-desktop kernel: [   12.502136] AppArmor: AppArmor initialized
Aug 16 09:28:12 recklezz-desktop kernel: [   12.502140] Failure registering capabilities with primary security module.
Aug 16 09:28:12 recklezz-desktop kernel: [   12.502148] Mount-cache hash table entries: 512
Aug 16 09:28:12 recklezz-desktop kernel: [   12.502259] Initializing cgroup subsys ns
Aug 16 09:28:12 recklezz-desktop kernel: [   12.502263] Initializing cgroup subsys cpuacct
Aug 16 09:28:12 recklezz-desktop kernel: [   12.502273] CPU: After generic identify, caps: 078bfbff e3d3fbff 00000000 00000000 00000001 00000000 00000001 00000000
Aug 16 09:28:12 recklezz-desktop kernel: [   12.502280] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Aug 16 09:28:12 recklezz-desktop kernel: [   12.502282] CPU: L2 Cache: 512K (64 bytes/line)
Aug 16 09:28:12 recklezz-desktop kernel: [   12.502285] CPU: After all inits, caps: 078bfbff e3d3fbff 00000000 00000410 00000001 00000000 00000001 00000000
Aug 16 09:28:12 recklezz-desktop kernel: [   12.502293] Compat vDSO mapped to ffffe000.
Aug 16 09:28:12 recklezz-desktop kernel: [   12.502304] Checking 'hlt' instruction... OK.
Aug 16 09:28:12 recklezz-desktop kernel: [   12.518357] SMP alternatives: switching to UP code
Aug 16 09:28:12 recklezz-desktop kernel: [   12.519373] Freeing SMP alternatives: 11k freed
Aug 16 09:28:12 recklezz-desktop kernel: [   12.519475] Early unpacking initramfs... done
Aug 16 09:28:12 recklezz-desktop kernel: [   12.810005] ACPI: Core revision 20070126
Aug 16 09:28:12 recklezz-desktop kernel: [   12.810071] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Aug 16 09:28:12 recklezz-desktop kernel: [   12.814874] CPU0: AMD Athlon(tm) 64 Processor 3500+ stepping 02
Aug 16 09:28:12 recklezz-desktop kernel: [   12.814892] Total of 1 processors activated (4413.22 BogoMIPS).
Aug 16 09:28:12 recklezz-desktop kernel: [   12.815189] ENABLING IO-APIC IRQs
Aug 16 09:28:12 recklezz-desktop kernel: [   12.815420] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
Aug 16 09:28:12 recklezz-desktop kernel: [   12.961687] Brought up 1 CPUs
Aug 16 09:28:12 recklezz-desktop kernel: [   12.961734] CPU0 attaching sched-domain:
Aug 16 09:28:12 recklezz-desktop kernel: [   12.961736]  domain 0: span 01
Aug 16 09:28:12 recklezz-desktop kernel: [   12.961738]   groups: 01
Aug 16 09:28:12 recklezz-desktop kernel: [   12.961871] net_namespace: 64 bytes
Aug 16 09:28:12 recklezz-desktop kernel: [   12.961877] Booting paravirtualized kernel on bare hardware
Aug 16 09:28:12 recklezz-desktop kernel: [   12.962258] Time: 16:27:48  Date: 08/16/08
Aug 16 09:28:12 recklezz-desktop kernel: [   12.962277] NET: Registered protocol family 16
Aug 16 09:28:12 recklezz-desktop kernel: [   12.962414] EISA bus registered
Aug 16 09:28:12 recklezz-desktop kernel: [   12.962440] ACPI: bus type pci registered
Aug 16 09:28:12 recklezz-desktop kernel: [   12.968885] PCI: PCI BIOS revision 3.00 entry at 0xf2060, last bus=3
Aug 16 09:28:12 recklezz-desktop kernel: [   12.968887] PCI: Using configuration type 1
Aug 16 09:28:12 recklezz-desktop kernel: [   12.968895] Setting up standard PCI resources
Aug 16 09:28:12 recklezz-desktop kernel: [   12.972636] ACPI: EC: Look up EC in DSDT
Aug 16 09:28:12 recklezz-desktop kernel: [   12.981227] ACPI: Interpreter enabled
Aug 16 09:28:12 recklezz-desktop kernel: [   12.981229] ACPI: (supports S0 S1 S3 S4 S5)
Aug 16 09:28:12 recklezz-desktop kernel: [   12.981241] ACPI: Using IOAPIC for interrupt routing
Aug 16 09:28:12 recklezz-desktop kernel: [   12.991227] ACPI: PCI Root Bridge [PCI0] (0000:00)
Aug 16 09:28:12 recklezz-desktop kernel: [   12.992143] PCI: Transparent bridge - 0000:00:10.0
Aug 16 09:28:12 recklezz-desktop kernel: [   12.992158] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Aug 16 09:28:12 recklezz-desktop kernel: [   12.992472] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
Aug 16 09:28:12 recklezz-desktop kernel: [   13.098102] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Aug 16 09:28:12 recklezz-desktop kernel: [   13.098329] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Aug 16 09:28:12 recklezz-desktop kernel: [   13.098551] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Aug 16 09:28:12 recklezz-desktop kernel: [   13.098772] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Aug 16 09:28:12 recklezz-desktop kernel: [   13.098993] ACPI: PCI Interrupt Link [LNK5] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Aug 16 09:28:12 recklezz-desktop kernel: [   13.099215] ACPI: PCI Interrupt Link [LNK6] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Aug 16 09:28:12 recklezz-desktop kernel: [   13.099437] ACPI: PCI Interrupt Link [LNK7] (IRQs *5 7 9 10 11 14 15)
Aug 16 09:28:12 recklezz-desktop kernel: [   13.099664] ACPI: PCI Interrupt Link [LNK8] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Aug 16 09:28:12 recklezz-desktop kernel: [   13.099885] ACPI: PCI Interrupt Link [LUBA] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Aug 16 09:28:12 recklezz-desktop kernel: [   13.100107] ACPI: PCI Interrupt Link [LUBB] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Aug 16 09:28:12 recklezz-desktop kernel: [   13.100329] ACPI: PCI Interrupt Link [LMAC] (IRQs 5 7 9 10 *11 14 15)
Aug 16 09:28:12 recklezz-desktop kernel: [   13.100550] ACPI: PCI Interrupt Link [LACI] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Aug 16 09:28:12 recklezz-desktop kernel: [   13.100773] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 *7 9 10 11 14 15)
Aug 16 09:28:12 recklezz-desktop kernel: [   13.100994] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Aug 16 09:28:12 recklezz-desktop kernel: [   13.101216] ACPI: PCI Interrupt Link [LMCI] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Aug 16 09:28:12 recklezz-desktop kernel: [   13.101438] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Aug 16 09:28:12 recklezz-desktop kernel: [   13.101663] ACPI: PCI Interrupt Link [LUB2] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Aug 16 09:28:12 recklezz-desktop kernel: [   13.101886] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Aug 16 09:28:12 recklezz-desktop kernel: [   13.102109] ACPI: PCI Interrupt Link [LSID] (IRQs 5 7 9 *10 11 14 15)
Aug 16 09:28:12 recklezz-desktop kernel: [   13.102340] ACPI: PCI Interrupt Link [LFID] (IRQs 5 7 9 10 *11 14 15)
Aug 16 09:28:12 recklezz-desktop kernel: [   13.102592] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
Aug 16 09:28:12 recklezz-desktop kernel: [   13.102837] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
Aug 16 09:28:12 recklezz-desktop kernel: [   13.103079] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.
Aug 16 09:28:12 recklezz-desktop kernel: [   13.103320] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
Aug 16 09:28:12 recklezz-desktop kernel: [   13.103562] ACPI: PCI Interrupt Link [APC5] (IRQs 16) *0, disabled.
Aug 16 09:28:12 recklezz-desktop kernel: [   13.103803] ACPI: PCI Interrupt Link [APC6] (IRQs 16) *0, disabled.
Aug 16 09:28:12 recklezz-desktop kernel: [   13.104045] ACPI: PCI Interrupt Link [APC7] (IRQs 16) *0
Aug 16 09:28:12 recklezz-desktop kernel: [   13.104286] ACPI: PCI Interrupt Link [APC8] (IRQs 16) *0, disabled.
Aug 16 09:28:12 recklezz-desktop kernel: [   13.104528] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0, disabled.
Aug 16 09:28:12 recklezz-desktop kernel: [   13.104770] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22 23) *0, disabled.
Aug 16 09:28:12 recklezz-desktop kernel: [   13.105013] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0
Aug 16 09:28:12 recklezz-desktop kernel: [   13.105254] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22 23) *0, disabled.
Aug 16 09:28:12 recklezz-desktop kernel: [   13.105497] ACPI: PCI Interrupt Link [APMU] (IRQs 20 21 22 23) *0, disabled.
Aug 16 09:28:12 recklezz-desktop kernel: [   13.105744] ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22 23) *0
Aug 16 09:28:12 recklezz-desktop kernel: [   13.105986] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22 23) *0, disabled.
Aug 16 09:28:12 recklezz-desktop kernel: [   13.106229] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0, disabled.
Aug 16 09:28:12 recklezz-desktop kernel: [   13.106474] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0, disabled.
Aug 16 09:28:12 recklezz-desktop kernel: [   13.106717] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22 23) *0, disabled.
Aug 16 09:28:12 recklezz-desktop kernel: [   13.106960] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
Aug 16 09:28:12 recklezz-desktop kernel: [   13.107202] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0
Aug 16 09:28:12 recklezz-desktop kernel: [   13.107445] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0
Aug 16 09:28:12 recklezz-desktop kernel: [   13.107570] Linux Plug and Play Support v0.97 (c) Adam Belay
Aug 16 09:28:12 recklezz-desktop kernel: [   13.107593] pnp: PnP ACPI init
Aug 16 09:28:12 recklezz-desktop kernel: [   13.107599] ACPI: bus type pnp registered
Aug 16 09:28:12 recklezz-desktop kernel: [   13.112593] pnpacpi: exceeded the max number of mem resources: 12
Aug 16 09:28:12 recklezz-desktop kernel: [   13.112646] pnp: PnP ACPI: found 11 devices
Aug 16 09:28:12 recklezz-desktop kernel: [   13.112648] ACPI: ACPI bus type pnp unregistered
Aug 16 09:28:12 recklezz-desktop kernel: [   13.112651] PnPBIOS: Disabled by ACPI PNP
Aug 16 09:28:12 recklezz-desktop kernel: [   13.112824] PCI: Using ACPI for IRQ routing
Aug 16 09:28:12 recklezz-desktop kernel: [   13.112828] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Aug 16 09:28:12 recklezz-desktop kernel: [   13.189433] NET: Registered protocol family 8
Aug 16 09:28:12 recklezz-desktop kernel: [   13.189435] NET: Registered protocol family 20
Aug 16 09:28:12 recklezz-desktop kernel: [   13.189490] AppArmor: AppArmor Filesystem Enabled
Aug 16 09:28:12 recklezz-desktop kernel: [   13.193424] Time: tsc clocksource has been installed.
Aug 16 09:28:12 recklezz-desktop kernel: [   13.201442] system 00:01: ioport range 0x4000-0x407f has been reserved
Aug 16 09:28:12 recklezz-desktop kernel: [   13.201445] system 00:01: ioport range 0x4080-0x40ff has been reserved
Aug 16 09:28:12 recklezz-desktop kernel: [   13.201447] system 00:01: ioport range 0x4400-0x447f has been reserved
Aug 16 09:28:12 recklezz-desktop kernel: [   13.201450] system 00:01: ioport range 0x4480-0x44ff has been reserved
Aug 16 09:28:12 recklezz-desktop kernel: [   13.201452] system 00:01: ioport range 0x4800-0x487f has been reserved
Aug 16 09:28:12 recklezz-desktop kernel: [   13.201454] system 00:01: ioport range 0x4880-0x48ff has been reserved
Aug 16 09:28:12 recklezz-desktop kernel: [   13.201456] system 00:01: ioport range 0x2000-0x207f has been reserved
Aug 16 09:28:12 recklezz-desktop kernel: [   13.201459] system 00:01: ioport range 0x2080-0x20ff has been reserved
Aug 16 09:28:12 recklezz-desktop kernel: [   13.201461] system 00:01: iomem range 0x5c000000-0x5fffffff could not be reserved
Aug 16 09:28:12 recklezz-desktop kernel: [   13.201466] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
Aug 16 09:28:12 recklezz-desktop kernel: [   13.201468] system 00:02: ioport range 0x800-0x87f has been reserved
Aug 16 09:28:12 recklezz-desktop kernel: [   13.201474] system 00:09: iomem range 0xf0000000-0xf3ffffff could not be reserved
Aug 16 09:28:12 recklezz-desktop kernel: [   13.201479] system 00:0a: iomem range 0xcec00-0xcffff has been reserved
Aug 16 09:28:12 recklezz-desktop kernel: [   13.201481] system 00:0a: iomem range 0xf0000-0xf7fff could not be reserved
Aug 16 09:28:12 recklezz-desktop kernel: [   13.201483] system 00:0a: iomem range 0xf8000-0xfbfff could not be reserved
Aug 16 09:28:12 recklezz-desktop kernel: [   13.201486] system 00:0a: iomem range 0xfc000-0xfffff could not be reserved
Aug 16 09:28:12 recklezz-desktop kernel: [   13.201488] system 00:0a: iomem range 0x5bef0000-0x5befffff could not be reserved
Aug 16 09:28:12 recklezz-desktop kernel: [   13.201490] system 00:0a: iomem range 0xffff0000-0xffffffff could not be reserved
Aug 16 09:28:12 recklezz-desktop kernel: [   13.201493] system 00:0a: iomem range 0x0-0x9ffff could not be reserved
Aug 16 09:28:12 recklezz-desktop kernel: [   13.201495] system 00:0a: iomem range 0x100000-0x5beeffff could not be reserved
Aug 16 09:28:12 recklezz-desktop kernel: [   13.201497] system 00:0a: iomem range 0x5bf00000-0x5fefffff could not be reserved
Aug 16 09:28:12 recklezz-desktop kernel: [   13.201500] system 00:0a: iomem range 0xfec00000-0xfec00fff could not be reserved
Aug 16 09:28:12 recklezz-desktop kernel: [   13.201502] system 00:0a: iomem range 0xfee00000-0xfeefffff could not be reserved
Aug 16 09:28:12 recklezz-desktop kernel: [   13.201505] system 00:0a: iomem range 0xfefff000-0xfeffffff could not be reserved
Aug 16 09:28:12 recklezz-desktop kernel: [   13.231785] PCI: Bridge: 0000:00:02.0
Aug 16 09:28:12 recklezz-desktop kernel: [   13.231787]   IO window: e000-efff
Aug 16 09:28:12 recklezz-desktop kernel: [   13.231790]   MEM window: fde00000-fdefffff
Aug 16 09:28:12 recklezz-desktop kernel: [   13.231792]   PREFETCH window: fdb00000-fdbfffff
Aug 16 09:28:12 recklezz-desktop kernel: [   13.231794] PCI: Bridge: 0000:00:04.0
Aug 16 09:28:12 recklezz-desktop kernel: [   13.231795]   IO window: c000-cfff
Aug 16 09:28:12 recklezz-desktop kernel: [   13.231798]   MEM window: fda00000-fdafffff
Aug 16 09:28:12 recklezz-desktop kernel: [   13.231800]   PREFETCH window: fd900000-fd9fffff
Aug 16 09:28:12 recklezz-desktop kernel: [   13.231802] PCI: Bridge: 0000:00:10.0
Aug 16 09:28:12 recklezz-desktop kernel: [   13.231804]   IO window: d000-dfff
Aug 16 09:28:12 recklezz-desktop kernel: [   13.231807]   MEM window: fdd00000-fddfffff
Aug 16 09:28:12 recklezz-desktop kernel: [   13.231809]   PREFETCH window: fdc00000-fdcfffff
Aug 16 09:28:12 recklezz-desktop kernel: [   13.231821] PCI: Setting latency timer of device 0000:00:02.0 to 64
Aug 16 09:28:12 recklezz-desktop kernel: [   13.231827] PCI: Setting latency timer of device 0000:00:04.0 to 64
Aug 16 09:28:12 recklezz-desktop kernel: [   13.231833] PCI: Setting latency timer of device 0000:00:10.0 to 64
Aug 16 09:28:12 recklezz-desktop kernel: [   13.231842] NET: Registered protocol family 2
Aug 16 09:28:12 recklezz-desktop kernel: [   13.269417] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Aug 16 09:28:12 recklezz-desktop kernel: [   13.269689] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Aug 16 09:28:12 recklezz-desktop kernel: [   13.270658] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Aug 16 09:28:12 recklezz-desktop kernel: [   13.271178] TCP: Hash tables configured (established 131072 bind 65536)
Aug 16 09:28:12 recklezz-desktop kernel: [   13.271180] TCP reno registered
Aug 16 09:28:12 recklezz-desktop kernel: [   13.281459] checking if image is initramfs... it is
Aug 16 09:28:12 recklezz-desktop kernel: [   13.732901] Switched to high resolution mode on CPU 0
Aug 16 09:28:12 recklezz-desktop kernel: [   13.840987] Freeing initrd memory: 7735k freed
Aug 16 09:28:12 recklezz-desktop kernel: [   13.841484] audit: initializing netlink socket (disabled)
Aug 16 09:28:12 recklezz-desktop kernel: [   13.841497] audit(1218904068.320:1): initialized
Aug 16 09:28:12 recklezz-desktop kernel: [   13.841632] highmem bounce pool size: 64 pages
Aug 16 09:28:12 recklezz-desktop kernel: [   13.842930] VFS: Disk quotas dquot_6.5.1
Aug 16 09:28:12 recklezz-desktop kernel: [   13.842978] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Aug 16 09:28:12 recklezz-desktop kernel: [   13.843081] io scheduler noop registered
Aug 16 09:28:12 recklezz-desktop kernel: [   13.843083] io scheduler anticipatory registered
Aug 16 09:28:12 recklezz-desktop kernel: [   13.843085] io scheduler deadline registered
Aug 16 09:28:12 recklezz-desktop kernel: [   13.843092] io scheduler cfq registered (default)
Aug 16 09:28:12 recklezz-desktop kernel: [   13.843105] pci 0000:00:00.0: Enabling HT MSI Mapping
Aug 16 09:28:12 recklezz-desktop kernel: [   13.843131] pci 0000:00:02.0: Enabling HT MSI Mapping
Aug 16 09:28:12 recklezz-desktop kernel: [   13.843138] pci 0000:00:04.0: Enabling HT MSI Mapping
Aug 16 09:28:12 recklezz-desktop kernel: [   13.843145] Boot video device is 0000:00:05.0
Aug 16 09:28:12 recklezz-desktop kernel: [   13.843165] pci 0000:00:09.0: Enabling HT MSI Mapping
Aug 16 09:28:12 recklezz-desktop kernel: [   13.843214] pci 0000:00:0e.0: Enabling HT MSI Mapping
Aug 16 09:28:12 recklezz-desktop kernel: [   13.843224] pci 0000:00:0f.0: Enabling HT MSI Mapping
Aug 16 09:28:12 recklezz-desktop kernel: [   13.843231] pci 0000:00:10.0: Enabling HT MSI Mapping
Aug 16 09:28:12 recklezz-desktop kernel: [   13.843242] pci 0000:00:10.1: Enabling HT MSI Mapping
Aug 16 09:28:12 recklezz-desktop kernel: [   13.843334] PCI: Setting latency timer of device 0000:00:02.0 to 64
Aug 16 09:28:12 recklezz-desktop kernel: [   13.843353] assign_interrupt_mode Found MSI capability
Aug 16 09:28:12 recklezz-desktop kernel: [   13.843371] Allocate Port Service[0000:00:02.0:pcie00]
Aug 16 09:28:12 recklezz-desktop kernel: [   13.843421] PCI: Setting latency timer of device 0000:00:04.0 to 64
Aug 16 09:28:12 recklezz-desktop kernel: [   13.843439] assign_interrupt_mode Found MSI capability
Aug 16 09:28:12 recklezz-desktop kernel: [   13.843453] Allocate Port Service[0000:00:04.0:pcie00]
Aug 16 09:28:12 recklezz-desktop kernel: [   13.843610] isapnp: Scanning for PnP cards...
Aug 16 09:28:12 recklezz-desktop kernel: [   14.196382] isapnp: No Plug & Play device found
Aug 16 09:28:12 recklezz-desktop kernel: [   14.217790] Real Time Clock Driver v1.12ac
Aug 16 09:28:12 recklezz-desktop kernel: [   14.217880] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Aug 16 09:28:12 recklezz-desktop kernel: [   14.218688] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Aug 16 09:28:12 recklezz-desktop kernel: [   14.218742] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Aug 16 09:28:12 recklezz-desktop kernel: [   14.218808] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Aug 16 09:28:12 recklezz-desktop kernel: [   14.221423] serio: i8042 KBD port at 0x60,0x64 irq 1
Aug 16 09:28:12 recklezz-desktop kernel: [   14.221427] serio: i8042 AUX port at 0x60,0x64 irq 12
Aug 16 09:28:12 recklezz-desktop kernel: [   14.228376] mice: PS/2 mouse device common for all mice
Aug 16 09:28:12 recklezz-desktop kernel: [   14.228463] EISA: Probing bus 0 at eisa.0
Aug 16 09:28:12 recklezz-desktop kernel: [   14.228471] Cannot allocate resource for EISA slot 2
Aug 16 09:28:12 recklezz-desktop kernel: [   14.228475] Cannot allocate resource for EISA slot 4
Aug 16 09:28:12 recklezz-desktop kernel: [   14.228487] EISA: Detected 0 cards.
Aug 16 09:28:12 recklezz-desktop kernel: [   14.228490] cpuidle: using governor ladder
Aug 16 09:28:12 recklezz-desktop kernel: [   14.228492] cpuidle: using governor menu
Aug 16 09:28:12 recklezz-desktop kernel: [   14.228565] NET: Registered protocol family 1
Aug 16 09:28:12 recklezz-desktop kernel: [   14.228585] Using IPI No-Shortcut mode
Aug 16 09:28:12 recklezz-desktop kernel: [   14.228612] registered taskstats version 1
Aug 16 09:28:12 recklezz-desktop kernel: [   14.228720]   Magic number: 4:836:489
Aug 16 09:28:12 recklezz-desktop kernel: [   14.228897] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Aug 16 09:28:12 recklezz-desktop kernel: [   14.228899] EDD information not available.
Aug 16 09:28:12 recklezz-desktop kernel: [   14.229116] Freeing unused kernel memory: 368k freed
Aug 16 09:28:12 recklezz-desktop kernel: [   14.260259] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Aug 16 09:28:12 recklezz-desktop kernel: [   15.436803] fuse init (API version 7.9)
Aug 16 09:28:12 recklezz-desktop kernel: [   15.450899] ACPI: Fan [FAN] (on)
Aug 16 09:28:12 recklezz-desktop kernel: [   15.456061] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
Aug 16 09:28:12 recklezz-desktop kernel: [   15.459173] ACPI: Thermal Zone [THRM] (40 C)
Aug 16 09:28:12 recklezz-desktop kernel: [   16.385967] usbcore: registered new interface driver usbfs
Aug 16 09:28:12 recklezz-desktop kernel: [   16.385989] usbcore: registered new interface driver hub
Aug 16 09:28:12 recklezz-desktop kernel: [   16.393921] usbcore: registered new device driver usb
Aug 16 09:28:12 recklezz-desktop kernel: [   16.399779] SCSI subsystem initialized
Aug 16 09:28:12 recklezz-desktop kernel: [   16.425920] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
Aug 16 09:28:12 recklezz-desktop kernel: [   16.426377] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 23
Aug 16 09:28:12 recklezz-desktop kernel: [   16.426387] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [APCF] -> GSI 23 (level, low) -> IRQ 16
Aug 16 09:28:12 recklezz-desktop kernel: [   16.426399] PCI: Setting latency timer of device 0000:00:0b.0 to 64
Aug 16 09:28:12 recklezz-desktop kernel: [   16.426402] ohci_hcd 0000:00:0b.0: OHCI Host Controller
Aug 16 09:28:12 recklezz-desktop kernel: [   16.426659] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 1
Aug 16 09:28:12 recklezz-desktop kernel: [   16.426676] ohci_hcd 0000:00:0b.0: irq 16, io mem 0xfe02f000
Aug 16 09:28:12 recklezz-desktop kernel: [   16.457150] libata version 3.00 loaded.
Aug 16 09:28:12 recklezz-desktop kernel: [   16.483910] usb usb1: configuration #1 chosen from 1 choice
Aug 16 09:28:12 recklezz-desktop kernel: [   16.483930] hub 1-0:1.0: USB hub found
Aug 16 09:28:12 recklezz-desktop kernel: [   16.483938] hub 1-0:1.0: 8 ports detected
Aug 16 09:28:12 recklezz-desktop kernel: [   16.586285] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 22
Aug 16 09:28:12 recklezz-desktop kernel: [   16.586297] ACPI: PCI Interrupt 0000:00:0b.1[b] -> Link [APCL] -> GSI 22 (level, low) -> IRQ 17
Aug 16 09:28:12 recklezz-desktop kernel: [   16.586307] PCI: Setting latency timer of device 0000:00:0b.1 to 64
Aug 16 09:28:12 recklezz-desktop kernel: [   16.586310] ehci_hcd 0000:00:0b.1: EHCI Host Controller
Aug 16 09:28:12 recklezz-desktop kernel: [   16.586331] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 2
Aug 16 09:28:12 recklezz-desktop kernel: [   16.586357] ehci_hcd 0000:00:0b.1: debug port 1
Aug 16 09:28:12 recklezz-desktop kernel: [   16.586361] PCI: cache line size of 64 is not supported by device 0000:00:0b.1
Aug 16 09:28:12 recklezz-desktop kernel: [   16.586373] ehci_hcd 0000:00:0b.1: irq 17, io mem 0xfe02e000
Aug 16 09:28:12 recklezz-desktop kernel: [   16.597683] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Aug 16 09:28:12 recklezz-desktop kernel: [   16.597786] usb usb2: configuration #1 chosen from 1 choice
Aug 16 09:28:12 recklezz-desktop kernel: [   16.597805] hub 2-0:1.0: USB hub found
Aug 16 09:28:12 recklezz-desktop kernel: [   16.597810] hub 2-0:1.0: 8 ports detected
Aug 16 09:28:12 recklezz-desktop kernel: [   16.701753] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
Aug 16 09:28:12 recklezz-desktop kernel: [   16.702180] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 21
Aug 16 09:28:12 recklezz-desktop kernel: [   16.702189] ACPI: PCI Interrupt 0000:00:14.0[A] -> Link [APCH] -> GSI 21 (level, low) -> IRQ 18
Aug 16 09:28:12 recklezz-desktop kernel: [   16.702195] PCI: Setting latency timer of device 0000:00:14.0 to 64
Aug 16 09:28:12 recklezz-desktop kernel: [   17.113109] usb 2-2: new high speed USB device using ehci_hcd and address 2
Aug 16 09:28:12 recklezz-desktop kernel: [   17.221388] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x20 @ 13, addr 00:17:31:cd:61:90
Aug 16 09:28:12 recklezz-desktop kernel: [   17.221392] forcedeth 0000:00:14.0: highdma pwrctl timirq lnktim desc-v3
Aug 16 09:28:12 recklezz-desktop kernel: [   17.221704] PCI: Setting latency timer of device 0000:00:0d.0 to 64
Aug 16 09:28:12 recklezz-desktop kernel: [   17.222126] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 20
Aug 16 09:28:12 recklezz-desktop kernel: [   17.222136] ACPI: PCI Interrupt 0000:00:0e.0[A] -> Link [APSI] -> GSI 20 (level, low) -> IRQ 19
Aug 16 09:28:12 recklezz-desktop kernel: [   17.222153] PCI: Setting latency timer of device 0000:00:0e.0 to 64
Aug 16 09:28:12 recklezz-desktop kernel: [   17.222159] ACPI: PCI interrupt for device 0000:00:0e.0 disabled
Aug 16 09:28:12 recklezz-desktop kernel: [   17.222515] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 23
Aug 16 09:28:12 recklezz-desktop kernel: [   17.222517] ACPI: PCI Interrupt 0000:00:0f.0[A] -> Link [APSJ] -> GSI 23 (level, low) -> IRQ 16
Aug 16 09:28:12 recklezz-desktop kernel: [   17.222533] PCI: Setting latency timer of device 0000:00:0f.0 to 64
Aug 16 09:28:12 recklezz-desktop kernel: [   17.222539] ACPI: PCI interrupt for device 0000:00:0f.0 disabled
Aug 16 09:28:12 recklezz-desktop kernel: [   17.225928] pata_amd 0000:00:0d.0: version 0.3.10
Aug 16 09:28:12 recklezz-desktop kernel: [   17.225976] PCI: Setting latency timer of device 0000:00:0d.0 to 64
Aug 16 09:28:12 recklezz-desktop kernel: [   17.229987] scsi0 : pata_amd
Aug 16 09:28:12 recklezz-desktop kernel: [   17.232370] scsi1 : pata_amd
Aug 16 09:28:12 recklezz-desktop kernel: [   17.233045] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xfd00 irq 14
Aug 16 09:28:12 recklezz-desktop kernel: [   17.233048] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xfd08 irq 15
Aug 16 09:28:12 recklezz-desktop kernel: [   17.246652] usb 2-2: configuration #1 chosen from 1 choice
Aug 16 09:28:12 recklezz-desktop kernel: [   17.788364] usb 1-8: new full speed USB device using ohci_hcd and address 2
Aug 16 09:28:12 recklezz-desktop kernel: [   17.920511] ata2.00: ATAPI: TSSTcorpCD/DVDW TS-H552L, 0614, max UDMA/33
Aug 16 09:28:12 recklezz-desktop kernel: [   17.920528] ata2.01: ATAPI: Hewlett-Packard DVD Writer 300, 1.25, max UDMA/33
Aug 16 09:28:12 recklezz-desktop kernel: [   18.003325] usb 1-8: configuration #1 chosen from 1 choice
Aug 16 09:28:12 recklezz-desktop kernel: [   18.017953] usbcore: registered new interface driver libusual
Aug 16 09:28:12 recklezz-desktop kernel: [   18.023093] Initializing USB Mass Storage driver...
Aug 16 09:28:12 recklezz-desktop kernel: [   18.023971] scsi2 : SCSI emulation for USB Mass Storage devices
Aug 16 09:28:12 recklezz-desktop kernel: [   18.024662] usbcore: registered new interface driver usb-storage
Aug 16 09:28:12 recklezz-desktop kernel: [   18.024666] USB Mass Storage support registered.
Aug 16 09:28:12 recklezz-desktop kernel: [   18.024751] usb-storage: device found at 2
Aug 16 09:28:12 recklezz-desktop kernel: [   18.024752] usb-storage: waiting for device to settle before scanning
Aug 16 09:28:12 recklezz-desktop kernel: [   18.132223] ata2.00: configured for UDMA/33
Aug 16 09:28:12 recklezz-desktop kernel: [   18.304144] ata2.01: configured for UDMA/33
Aug 16 09:28:12 recklezz-desktop kernel: [   18.305153] scsi 1:0:0:0: CD-ROM            TSSTcorp CD/DVDW TS-H552L 0614 PQ: 0 ANSI: 5
Aug 16 09:28:12 recklezz-desktop kernel: [   18.307665] scsi 1:0:1:0: CD-ROM            HP       DVD Writer 300n  1.25 PQ: 0 ANSI: 5
Aug 16 09:28:12 recklezz-desktop kernel: [   18.309996] sata_nv 0000:00:0e.0: version 3.5
Aug 16 09:28:12 recklezz-desktop kernel: [   18.310010] ACPI: PCI Interrupt 0000:00:0e.0[A] -> Link [APSI] -> GSI 20 (level, low) -> IRQ 19
Aug 16 09:28:12 recklezz-desktop kernel: [   18.310049] PCI: Setting latency timer of device 0000:00:0e.0 to 64
Aug 16 09:28:12 recklezz-desktop kernel: [   18.311376] scsi3 : sata_nv
Aug 16 09:28:12 recklezz-desktop kernel: [   18.311566] scsi4 : sata_nv
Aug 16 09:28:12 recklezz-desktop kernel: [   18.311744] ata3: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xf800 irq 19
Aug 16 09:28:12 recklezz-desktop kernel: [   18.311747] ata4: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xf808 irq 19
Aug 16 09:28:12 recklezz-desktop kernel: [   18.775294] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Aug 16 09:28:12 recklezz-desktop kernel: [   18.783429] ata3.00: ATA-7: ST3200827AS, 3.AHH, max UDMA/100
Aug 16 09:28:12 recklezz-desktop kernel: [   18.783431] ata3.00: 390721968 sectors, multi 1: LBA48 NCQ (depth 0/32)
Aug 16 09:28:12 recklezz-desktop kernel: [   18.799411] ata3.00: configured for UDMA/100
Aug 16 09:28:12 recklezz-desktop kernel: [   19.110912] ata4: SATA link down (SStatus 0 SControl 310)
Aug 16 09:28:12 recklezz-desktop kernel: [   19.121426] scsi 3:0:0:0: Direct-Access     ATA      ST3200827AS      3.AH PQ: 0 ANSI: 5
Aug 16 09:28:12 recklezz-desktop kernel: [   19.121490] ACPI: PCI Interrupt 0000:00:0f.0[A] -> Link [APSJ] -> GSI 23 (level, low) -> IRQ 16
Aug 16 09:28:12 recklezz-desktop kernel: [   19.121529] PCI: Setting latency timer of device 0000:00:0f.0 to 64
Aug 16 09:28:12 recklezz-desktop kernel: [   19.121831] scsi5 : sata_nv
Aug 16 09:28:12 recklezz-desktop kernel: [   19.121949] scsi6 : sata_nv
Aug 16 09:28:12 recklezz-desktop kernel: [   19.122125] ata5: SATA max UDMA/133 cmd 0x9e0 ctl 0xbe0 bmdma 0xf300 irq 16
Aug 16 09:28:12 recklezz-desktop kernel: [   19.122128] ata6: SATA max UDMA/133 cmd 0x960 ctl 0xb60 bmdma 0xf308 irq 16
Aug 16 09:28:12 recklezz-desktop kernel: [   19.430561] ata5: SATA link down (SStatus 0 SControl 310)
Aug 16 09:28:12 recklezz-desktop kernel: [   19.750209] ata6: SATA link down (SStatus 0 SControl 310)
Aug 16 09:28:12 recklezz-desktop kernel: [   19.772531] Driver 'sr' needs updating - please use bus_type methods
Aug 16 09:28:12 recklezz-desktop kernel: [   19.779661] Driver 'sd' needs updating - please use bus_type methods
Aug 16 09:28:12 recklezz-desktop kernel: [   19.784142] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
Aug 16 09:28:12 recklezz-desktop kernel: [   19.784147] Uniform CD-ROM driver Revision: 3.20
Aug 16 09:28:12 recklezz-desktop kernel: [   19.784189] sr 1:0:0:0: Attached scsi CD-ROM sr0
Aug 16 09:28:12 recklezz-desktop kernel: [   19.789500] sr1: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
Aug 16 09:28:12 recklezz-desktop kernel: [   19.789529] sr 1:0:1:0: Attached scsi CD-ROM sr1
Aug 16 09:28:12 recklezz-desktop kernel: [   19.789872] sd 3:0:0:0: [sda] 390721968 512-byte hardware sectors (200050 MB)
Aug 16 09:28:12 recklezz-desktop kernel: [   19.793519] sd 3:0:0:0: [sda] Write Protect is off
Aug 16 09:28:12 recklezz-desktop kernel: [   19.793524] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00
Aug 16 09:28:12 recklezz-desktop kernel: [   19.796087] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug 16 09:28:12 recklezz-desktop kernel: [   19.796143] sd 3:0:0:0: [sda] 390721968 512-byte hardware sectors (200050 MB)
Aug 16 09:28:12 recklezz-desktop kernel: [   19.796151] sd 3:0:0:0: [sda] Write Protect is off
Aug 16 09:28:12 recklezz-desktop kernel: [   19.796154] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00
Aug 16 09:28:12 recklezz-desktop kernel: [   19.796165] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug 16 09:28:12 recklezz-desktop kernel: [   19.796168]  sda:<5>sr 1:0:0:0: Attached scsi generic sg0 type 5
Aug 16 09:28:12 recklezz-desktop kernel: [   19.797095] sr 1:0:1:0: Attached scsi generic sg1 type 5
Aug 16 09:28:12 recklezz-desktop kernel: [   19.797109] sd 3:0:0:0: Attached scsi generic sg2 type 0
Aug 16 09:28:12 recklezz-desktop kernel: [   19.816736]  sda1 sda2 < sda5 >
Aug 16 09:28:12 recklezz-desktop kernel: [   19.841101] sd 3:0:0:0: [sda] Attached SCSI disk
Aug 16 09:28:12 recklezz-desktop kernel: [   20.113089] Attempting manual resume
Aug 16 09:28:12 recklezz-desktop kernel: [   20.113093] swsusp: Resume From Partition 8:5
Aug 16 09:28:12 recklezz-desktop kernel: [   20.113095] PM: Checking swsusp image.
Aug 16 09:28:12 recklezz-desktop kernel: [   20.113251] PM: Resume from disk failed.
Aug 16 09:28:12 recklezz-desktop kernel: [   20.156973] kjournald starting.  Commit interval 5 seconds
Aug 16 09:28:12 recklezz-desktop kernel: [   20.156986] EXT3-fs: mounted filesystem with ordered data mode.
Aug 16 09:28:12 recklezz-desktop kernel: [   23.020051] usb-storage: device scan complete
Aug 16 09:28:12 recklezz-desktop kernel: [   23.027028] scsi 2:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
Aug 16 09:28:12 recklezz-desktop kernel: [   23.034019] scsi 2:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
Aug 16 09:28:12 recklezz-desktop kernel: [   23.041012] scsi 2:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
Aug 16 09:28:12 recklezz-desktop kernel: [   23.048005] scsi 2:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
Aug 16 09:28:12 recklezz-desktop kernel: [   23.059013] sd 2:0:0:0: [sdb] Attached SCSI removable disk
Aug 16 09:28:12 recklezz-desktop kernel: [   23.059036] sd 2:0:0:0: Attached scsi generic sg3 type 0
Aug 16 09:28:12 recklezz-desktop kernel: [   23.069994] sd 2:0:0:1: [sdc] Attached SCSI removable disk
Aug 16 09:28:12 recklezz-desktop kernel: [   23.070013] sd 2:0:0:1: Attached scsi generic sg4 type 0
Aug 16 09:28:12 recklezz-desktop kernel: [   23.080982] sd 2:0:0:2: [sdd] Attached SCSI removable disk
Aug 16 09:28:12 recklezz-desktop kernel: [   23.081001] sd 2:0:0:2: Attached scsi generic sg5 type 0
Aug 16 09:28:12 recklezz-desktop kernel: [   23.091970] sd 2:0:0:3: [sde] Attached SCSI removable disk
Aug 16 09:28:12 recklezz-desktop kernel: [   23.091990] sd 2:0:0:3: Attached scsi generic sg6 type 0
Aug 16 09:28:12 recklezz-desktop kernel: [   27.821380] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Aug 16 09:28:12 recklezz-desktop kernel: [   27.856403] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Aug 16 09:28:12 recklezz-desktop kernel: [   27.993171] Linux agpgart interface v0.102
Aug 16 09:28:12 recklezz-desktop kernel: [   28.098261] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x4c00
Aug 16 09:28:12 recklezz-desktop kernel: [   28.098300] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x4c40
Aug 16 09:28:12 recklezz-desktop kernel: [   28.225050] input: Power Button (FF) as /devices/virtual/input/input2
Aug 16 09:28:12 recklezz-desktop kernel: [   28.240909] ACPI: Power Button (FF) [PWRF]
Aug 16 09:28:12 recklezz-desktop kernel: [   28.241017] input: Power Button (CM) as /devices/virtual/input/input3
Aug 16 09:28:12 recklezz-desktop kernel: [   28.256879] ACPI: Power Button (CM) [PWRB]
Aug 16 09:28:12 recklezz-desktop kernel: [   30.821423] rndis_wlan: Unknown symbol rndis_tx_fixup
Aug 16 09:28:12 recklezz-desktop kernel: [   30.821476] rndis_wlan: Unknown symbol rndis_unbind
Aug 16 09:28:12 recklezz-desktop kernel: [   30.821619] rndis_wlan: Unknown symbol rndis_status
Aug 16 09:28:12 recklezz-desktop kernel: [   30.821688] rndis_wlan: Unknown symbol rndis_command
Aug 16 09:28:12 recklezz-desktop kernel: [   30.821735] rndis_wlan: Unknown symbol generic_rndis_bind
Aug 16 09:28:12 recklezz-desktop kernel: [   30.821829] rndis_wlan: Unknown symbol rndis_rx_fixup
Aug 16 09:28:12 recklezz-desktop kernel: [   30.825996] rndis_wlan: Unknown symbol rndis_tx_fixup
Aug 16 09:28:12 recklezz-desktop kernel: [   30.826064] rndis_wlan: Unknown symbol rndis_unbind
Aug 16 09:28:12 recklezz-desktop kernel: [   30.826205] rndis_wlan: Unknown symbol rndis_status
Aug 16 09:28:12 recklezz-desktop kernel: [   30.826273] rndis_wlan: Unknown symbol rndis_command
Aug 16 09:28:12 recklezz-desktop kernel: [   30.826320] rndis_wlan: Unknown symbol generic_rndis_bind
Aug 16 09:28:12 recklezz-desktop kernel: [   30.826412] rndis_wlan: Unknown symbol rndis_rx_fixup
Aug 16 09:28:12 recklezz-desktop kernel: [   30.921984] usbcore: registered new interface driver cdc_ether
Aug 16 09:28:12 recklezz-desktop kernel: [   30.945998] usb 2-2: bad CDC descriptors
Aug 16 09:28:12 recklezz-desktop kernel: [   30.946015] usbcore: registered new interface driver rndis_host
Aug 16 09:28:12 recklezz-desktop kernel: [   31.757214] input: PC Speaker as /devices/platform/pcspkr/input/input4
Aug 16 09:28:12 recklezz-desktop kernel: [   32.088583] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 22
Aug 16 09:28:12 recklezz-desktop kernel: [   32.088589] ACPI: PCI Interrupt 0000:00:10.1[b] -> Link [AAZA] -> GSI 22 (level, low) -> IRQ 17
Aug 16 09:28:12 recklezz-desktop kernel: [   32.088609] PCI: Setting latency timer of device 0000:00:10.1 to 64
Aug 16 09:28:12 recklezz-desktop kernel: [   32.119411] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
Aug 16 09:28:12 recklezz-desktop kernel: [   32.504350] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input5
Aug 16 09:28:12 recklezz-desktop kernel: [   33.100267] rndis_wlan: Unknown symbol rndis_tx_fixup
Aug 16 09:28:12 recklezz-desktop kernel: [   33.100324] rndis_wlan: Unknown symbol rndis_unbind
Aug 16 09:28:12 recklezz-desktop kernel: [   33.100470] rndis_wlan: Unknown symbol rndis_status
Aug 16 09:28:12 recklezz-desktop kernel: [   33.100545] rndis_wlan: Unknown symbol rndis_command
Aug 16 09:28:12 recklezz-desktop kernel: [   33.100595] rndis_wlan: Unknown symbol generic_rndis_bind
Aug 16 09:28:12 recklezz-desktop kernel: [   33.100694] rndis_wlan: Unknown symbol rndis_rx_fixup
Aug 16 09:28:12 recklezz-desktop kernel: [   33.112870] rndis_wlan: Unknown symbol rndis_tx_fixup
Aug 16 09:28:12 recklezz-desktop kernel: [   33.112926] rndis_wlan: Unknown symbol rndis_unbind
Aug 16 09:28:12 recklezz-desktop kernel: [   33.113073] rndis_wlan: Unknown symbol rndis_status
Aug 16 09:28:12 recklezz-desktop kernel: [   33.113148] rndis_wlan: Unknown symbol rndis_command
Aug 16 09:28:12 recklezz-desktop kernel: [   33.113197] rndis_wlan: Unknown symbol generic_rndis_bind
Aug 16 09:28:12 recklezz-desktop kernel: [   33.113296] rndis_wlan: Unknown symbol rndis_rx_fixup
Aug 16 09:28:12 recklezz-desktop kernel: [   33.886923] lp: driver loaded but no devices found
Aug 16 09:28:12 recklezz-desktop kernel: [   34.058281] Adding 4361608k swap on /dev/sda5.  Priority:-1 extents:1 across:4361608k
Aug 16 09:28:12 recklezz-desktop kernel: [   34.614192] EXT3 FS on sda1, internal journal
Aug 16 09:28:12 recklezz-desktop kernel: [   34.755195] device-mapper: uevent: version 1.0.3
Aug 16 09:28:12 recklezz-desktop kernel: [   34.755221] device-mapper: ioctl: 4.12.0-ioctl (2007-10-02) initialised: dm-devel@redhat.com
Aug 16 09:28:12 recklezz-desktop kernel: [   36.029841] ip_tables: (C) 2000-2006 Netfilter Core Team
Aug 16 09:28:12 recklezz-desktop kernel: [   36.387616] No dock devices found.
Aug 16 09:28:12 recklezz-desktop kernel: [   36.732460] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3500+ processors (1 cpu cores) (version 2.20.00)
Aug 16 09:28:12 recklezz-desktop kernel: [   36.732494] powernow-k8:    0 : fid 0xe (2200 MHz), vid 0x6
Aug 16 09:28:12 recklezz-desktop kernel: [   36.732496] powernow-k8:    1 : fid 0xc (2000 MHz), vid 0x8
Aug 16 09:28:12 recklezz-desktop kernel: [   36.732498] powernow-k8:    2 : fid 0xa (1800 MHz), vid 0xa
Aug 16 09:28:12 recklezz-desktop kernel: [   36.732500] powernow-k8:    3 : fid 0x2 (1000 MHz), vid 0x12
Aug 16 09:28:12 recklezz-desktop NetworkManager: <info>  starting...
Aug 16 09:28:13 recklezz-desktop avahi-daemon[5249]: Found user 'avahi' (UID 107) and group 'avahi' (GID 116).
Aug 16 09:28:13 recklezz-desktop avahi-daemon[5249]: Successfully dropped root privileges.
Aug 16 09:28:13 recklezz-desktop avahi-daemon[5249]: avahi-daemon 0.6.22 starting up.
Aug 16 09:28:13 recklezz-desktop avahi-daemon[5249]: Successfully called chroot().
Aug 16 09:28:13 recklezz-desktop avahi-daemon[5249]: Successfully dropped remaining capabilities.
Aug 16 09:28:13 recklezz-desktop avahi-daemon[5249]: No service file found in /etc/avahi/services.
Aug 16 09:28:13 recklezz-desktop avahi-daemon[5249]: Network interface enumeration completed.
Aug 16 09:28:13 recklezz-desktop avahi-daemon[5249]: Registering HINFO record with values 'I686'/'LINUX'.
Aug 16 09:28:13 recklezz-desktop avahi-daemon[5249]: Server startup complete. Host name is recklezz-desktop.local. Local service cookie is 3436240200.
Aug 16 09:28:14 recklezz-desktop kdm[5229]: StartServerSucces
Aug 16 09:28:14 recklezz-desktop kernel: [   38.877346] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
Aug 16 09:28:14 recklezz-desktop kernel: [   38.877351] apm: overridden by ACPI.
Aug 16 09:28:14 recklezz-desktop kernel: [   39.174653] ppdev: user-space parallel port driver
Aug 16 09:28:14 recklezz-desktop kernel: [   39.459366] audit(1218904094.722:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5292 profile="/usr/sbin/cupsd" namespace="default"
Aug 16 09:28:15 recklezz-desktop dhcdbd: Started up.
Aug 16 09:28:15 recklezz-desktop kernel: [   89.485680] Marking TSC unstable due to: cpufreq changes.
Aug 16 09:28:15 recklezz-desktop kernel: [   89.494151] Time: acpi_pm clocksource has been installed.
Aug 16 09:28:16 recklezz-desktop kernel: [   90.021736] Clocksource tsc unstable (delta = -272748409 ns)
Aug 16 09:28:16 recklezz-desktop NetworkManager: <info>  eth0: Device is fully-supported using driver 'forcedeth'.
Aug 16 09:28:16 recklezz-desktop NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start
Aug 16 09:28:16 recklezz-desktop NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing.
Aug 16 09:28:16 recklezz-desktop NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth0'.
Aug 16 09:28:16 recklezz-desktop NetworkManager: <info>  Deactivating device eth0.
Aug 16 09:28:16 recklezz-desktop NetworkManager: <info>  Will activate wired connection 'eth0' because it now has a link.
Aug 16 09:28:16 recklezz-desktop NetworkManager: <debug> [1218904096.957949] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_model_DVD_Writer_300n').
Aug 16 09:28:16 recklezz-desktop NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth0'.
Aug 16 09:28:17 recklezz-desktop hcid[5544]: Bluetooth HCI daemon
Aug 16 09:28:17 recklezz-desktop kernel: [   90.654759] Bluetooth: Core ver 2.11
Aug 16 09:28:17 recklezz-desktop kernel: [   90.655616] NET: Registered protocol family 31
Aug 16 09:28:17 recklezz-desktop kernel: [   90.655623] Bluetooth: HCI device and connection manager initialized
Aug 16 09:28:17 recklezz-desktop kernel: [   90.655628] Bluetooth: HCI socket layer initialized
Aug 16 09:28:17 recklezz-desktop hcid[5544]: Starting SDP server
Aug 16 09:28:17 recklezz-desktop kernel: [   41.274701] Bluetooth: L2CAP ver 2.9
Aug 16 09:28:17 recklezz-desktop kernel: [   41.274706] Bluetooth: L2CAP socket layer initialized
Aug 16 09:28:17 recklezz-desktop hcid[5544]: Created local server at unix:abstract=/var/run/dbus-EkQ0VYd1ZH,guid=126455b3235f0c2fb8f9e88248a70021
Aug 16 09:28:17 recklezz-desktop kernel: [   41.336363] Bluetooth: RFCOMM socket layer initialized
Aug 16 09:28:17 recklezz-desktop kernel: [   41.336380] Bluetooth: RFCOMM TTY layer initialized
Aug 16 09:28:17 recklezz-desktop kernel: [   41.336382] Bluetooth: RFCOMM ver 1.8
Aug 16 09:28:17 recklezz-desktop input[5587]: Bluetooth Input daemon
Aug 16 09:28:17 recklezz-desktop input[5587]: Registered input manager path:/org/bluez/input
Aug 16 09:28:17 recklezz-desktop anacron[5589]: Anacron 2.3 started on 2008-08-16
Aug 16 09:28:17 recklezz-desktop anacron[5589]: Normal exit (0 jobs run)
Aug 16 09:28:17 recklezz-desktop audio[5565]: Bluetooth Audio daemon
Aug 16 09:28:17 recklezz-desktop audio[5565]: Unix socket created: 5
Aug 16 09:28:17 recklezz-desktop audio[5565]: audio.conf: Key file does not have key 'Enable'
Aug 16 09:28:17 recklezz-desktop audio[5565]: audio.conf: Key file does not have key 'Disable'
Aug 16 09:28:17 recklezz-desktop audio[5565]: add_service_record: got record id 0x10000
Aug 16 09:28:17 recklezz-desktop audio[5565]: audio.conf: Key file does not have key 'Disable'
Aug 16 09:28:17 recklezz-desktop audio[5565]: audio.conf: Key file does not have group 'A2DP'
Aug 16 09:28:17 recklezz-desktop last message repeated 3 times
Aug 16 09:28:17 recklezz-desktop audio[5565]: SEP 0x806d648 registered: type:0 codec:0 seid:1
Aug 16 09:28:17 recklezz-desktop audio[5565]: add_service_record: got record id 0x10001
Aug 16 09:28:17 recklezz-desktop audio[5565]: add_service_record: got record id 0x10002
Aug 16 09:28:17 recklezz-desktop audio[5565]: add_service_record: got record id 0x10003
Aug 16 09:28:17 recklezz-desktop audio[5565]: Registered manager path:/org/bluez/audio
Aug 16 09:28:17 recklezz-desktop /usr/sbin/cron[5616]: (CRON) INFO (pidfile fd = 3)
Aug 16 09:28:17 recklezz-desktop /usr/sbin/cron[5617]: (CRON) STARTUP (fork ok)
Aug 16 09:28:17 recklezz-desktop /usr/sbin/cron[5617]: (CRON) INFO (Running @reboot jobs)
Aug 16 09:28:17 recklezz-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Aug 16 09:28:17 recklezz-desktop NetworkManager: <info>  Will activate connection 'eth0'.
Aug 16 09:28:17 recklezz-desktop NetworkManager: <info>  Device eth0 activation scheduled...
Aug 16 09:28:17 recklezz-desktop NetworkManager: <debug> [1218904097.967647] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_bluetooth').
Aug 16 09:28:17 recklezz-desktop NetworkManager: <info>  Activation (eth0) started...
Aug 16 09:28:17 recklezz-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Aug 16 09:28:17 recklezz-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Aug 16 09:28:17 recklezz-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Aug 16 09:28:17 recklezz-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Aug 16 09:28:17 recklezz-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Aug 16 09:28:17 recklezz-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Aug 16 09:28:17 recklezz-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Aug 16 09:28:17 recklezz-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Aug 16 09:28:17 recklezz-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Aug 16 09:28:18 recklezz-desktop NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction.
Aug 16 09:28:18 recklezz-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Aug 16 09:28:18 recklezz-desktop NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth0
Aug 16 09:28:20 recklezz-desktop NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth0
Aug 16 09:28:20 recklezz-desktop kernel: [   95.553866] NET: Registered protocol family 17
Aug 16 09:28:22 recklezz-desktop dhclient: DHCPREQUEST of 192.168.1.103 on eth0 to 255.255.255.255 port 67
Aug 16 09:28:23 recklezz-desktop dhclient: DHCPACK of 192.168.1.103 from 192.168.1.1
Aug 16 09:28:23 recklezz-desktop avahi-daemon[5249]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.103.
Aug 16 09:28:23 recklezz-desktop avahi-daemon[5249]: New relevant interface eth0.IPv4 for mDNS.
Aug 16 09:28:23 recklezz-desktop avahi-daemon[5249]: Registering new address record for 192.168.1.103 on eth0.IPv4.
Aug 16 09:28:23 recklezz-desktop NetworkManager: <info>  DHCP daemon state is now 4 (reboot) for interface eth0
Aug 16 09:28:23 recklezz-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) scheduled...
Aug 16 09:28:23 recklezz-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) started...
Aug 16 09:28:23 recklezz-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Aug 16 09:28:23 recklezz-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.domain_name
Aug 16 09:28:23 recklezz-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Aug 16 09:28:23 recklezz-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Aug 16 09:28:23 recklezz-desktop NetworkManager: <info>  Retrieved the following IP4 configuration from the DHCP daemon:
Aug 16 09:28:23 recklezz-desktop NetworkManager: <info>    address 192.168.1.103
Aug 16 09:28:23 recklezz-desktop NetworkManager: <info>    netmask 255.255.255.0
Aug 16 09:28:23 recklezz-desktop NetworkManager: <info>    broadcast 192.168.1.255
Aug 16 09:28:23 recklezz-desktop NetworkManager: <info>    gateway 192.168.1.1
Aug 16 09:28:23 recklezz-desktop NetworkManager: <info>    nameserver 208.67.222.222
Aug 16 09:28:23 recklezz-desktop NetworkManager: <info>    nameserver 208.67.220.220
Aug 16 09:28:23 recklezz-desktop NetworkManager: <info>    nameserver 24.205.1.14
Aug 16 09:28:23 recklezz-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.interface_mtu
Aug 16 09:28:23 recklezz-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled...
Aug 16 09:28:23 recklezz-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) complete.
Aug 16 09:28:23 recklezz-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...
Aug 16 09:28:23 recklezz-desktop dhclient: bound to 192.168.1.103 -- renewal in 84542 seconds.
Aug 16 09:28:23 recklezz-desktop avahi-daemon[5249]: Withdrawing address record for 192.168.1.103 on eth0.
Aug 16 09:28:23 recklezz-desktop avahi-daemon[5249]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.1.103.
Aug 16 09:28:23 recklezz-desktop avahi-daemon[5249]: Interface eth0.IPv4 no longer relevant for mDNS.
Aug 16 09:28:23 recklezz-desktop avahi-daemon[5249]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.103.
Aug 16 09:28:23 recklezz-desktop avahi-daemon[5249]: New relevant interface eth0.IPv4 for mDNS.
Aug 16 09:28:23 recklezz-desktop avahi-daemon[5249]: Registering new address record for 192.168.1.103 on eth0.IPv4.
Aug 16 09:28:24 recklezz-desktop NetworkManager: <info>  Clearing nscd hosts cache.
Aug 16 09:28:24 recklezz-desktop NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))
Aug 16 09:28:24 recklezz-desktop NetworkManager: <info>  Activation (eth0) successful, device activated.
Aug 16 09:28:24 recklezz-desktop NetworkManager: <info>  Activation (eth0) Finish handler scheduled.
Aug 16 09:28:24 recklezz-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.
Aug 16 09:28:24 recklezz-desktop kernel: [   56.528269] NET: Registered protocol family 10
Aug 16 09:28:24 recklezz-desktop kernel: [   56.528740] lo: Disabled Privacy Extensions
Aug 16 09:28:25 recklezz-desktop ntpdate[5781]: adjust time server 91.189.94.4 offset 0.000691 sec
Aug 16 09:28:25 recklezz-desktop avahi-daemon[5249]: Registering new address record for fe80::217:31ff:fecd:6190 on eth0.*.
Aug 16 09:28:34 recklezz-desktop kernel: [  112.655268] eth0: no IPv6 routers present
Aug 16 09:29:08 recklezz-desktop NetworkManager: <info>  Updating allowed wireless network lists.
Aug 16 09:29:08 recklezz-desktop NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - org.freedesktop.NetworkManagerInfo.NoNetworks.
Aug 16 09:36:05 recklezz-desktop kernel: [  583.969500] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
Aug 16 09:36:05 recklezz-desktop kernel: [  584.128271] usb 2-2: reset high speed USB device using ehci_hcd and address 2
Aug 16 09:36:05 recklezz-desktop kernel: [  584.269058] ndiswrapper: driver wusb54gs (Linksys,06/18/2004, 3.60.9.0) loaded
Aug 16 09:36:05 recklezz-desktop kernel: [  584.635310] wlan0: ethernet device 00:12:17:a0:db:7a using NDIS driver: wusb54gs, version: 0x33c0d03, NDIS version: 0x501, vendor: 'Linksys Wireless-G USB Network Adapter with SpeedBooster', 13B1:000E.F.conf
Aug 16 09:36:05 recklezz-desktop NetworkManager: <debug> [1218904565.836232] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_12_17_a0_db_7a').
Aug 16 09:36:05 recklezz-desktop kernel: [  584.674256] wlan0: encryption modes supported: WEP; TKIP with WPA; AES/CCMP with WPA
Aug 16 09:36:05 recklezz-desktop kernel: [  584.684298] usbcore: registered new interface driver ndiswrapper
Aug 16 09:36:05 recklezz-desktop NetworkManager: <info>  wlan0: Device is fully-supported using driver 'ndiswrapper'.
Aug 16 09:36:05 recklezz-desktop NetworkManager: <info>  wlan0: driver does not support SSID scans (scan_capa 0x00).
Aug 16 09:36:05 recklezz-desktop NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start
Aug 16 09:36:05 recklezz-desktop NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing.
Aug 16 09:36:05 recklezz-desktop NetworkManager: <info>  Now managing wireless (802.11) device 'wlan0'.
Aug 16 09:36:05 recklezz-desktop NetworkManager: <info>  Deactivating device wlan0.
Aug 16 09:36:05 recklezz-desktop NetworkManager: <WARN>  nm_device_802_11_wireless_set_essid(): error setting ESSID to '' for device wlan0: Invalid argument
Aug 16 09:48:12 recklezz-desktop -- MARK --
Aug 16 10:08:12 recklezz-desktop -- MARK --
```

---

### Post by julain124 on 2008-08-16
lol nvm it works. :D

---

