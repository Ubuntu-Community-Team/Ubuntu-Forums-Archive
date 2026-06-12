---
title: "[Ubuntu 7.04] WLAN-Card doesn't work after nvidia-driver"
date: 2007-06-23
forum: Networking &amp; Wireless
---

### Post by Silvestre on 2007-06-23
Hello,

after installing the nvidia driver from nvidia.com my **wlan-card D-Link DWL-G650 Airplus -- Chip Atheros** doesn't work more.
For installing i have made the following steps:
```



-nvidia-kernel-common and 
-linux-restricted-modules

```

uninstalled and i have made (recommendation nvidia.com):


```
modprobe -q agpgart

```

/etc/modules was edited and the line "nvidia" was added

lspcmcia show me:

```
Socket 0 Bridge: [yenta_cardbus] (bus ID: 0000:02:0b.0) 
CardBus card -- see "lspci" for more information 
Socket 1 Bridge: [yenta_cardbus] (bus ID: 0000:02:0b.1)

```

iwconfig show me:



```
lo no wireless extensions. eth0 no wireless extensions.

```

ifconfig show me:



```
eth0 Protokoll:Ethernet Hardware Adresse 00:07:0D:33:4E:47 inet Adresse:10.0.0.4 Bcast:10.0.0.255 Maske:255.255.255.0 inet6 Adresse: fe80::208:dff:fe44:4e61/64 Gültigkeitsbereich:Verbindung UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1 RX packets:2902 errors:0 dropped:0 overruns:0 frame:0 TX packets:2491 errors:0 dropped:0 overruns:0 carrier:0 Kollisionen:0 Sendewarteschlangenlänge:1000 RX bytes:2546351 (2.4 MiB) TX bytes:428409 (418.3 KiB) Interrupt:11 Basisadresse:0x2f00 lo Protokoll:Lokale Schleife inet Adresse:127.0.0.1 Maske:255.0.0.0 inet6 Adresse: ::1/128 Gültigkeitsbereich:Maschine UP LOOPBACK RUNNING MTU:16436 Metric:1 RX packets:358 errors:0 dropped:0 overruns:0 frame:0 TX packets:358 errors:0 dropped:0 overruns:0 carrier:0 Kollisionen:0 Sendewarteschlangenlänge:0 RX bytes:36215 (35.3 KiB) TX bytes:36215 (35.3 KiB)

```

nvidia-kernel-common und linux-restricted-modules-generic are installed again but the card doesn't work

Thanks a lot

Best regards

Silvestre

---

### Post by Silvestre on 2007-06-23
here the log /var/log/messages

```
Jun 23 15:43:17 pinguino syslogd 1.4.1#20ubuntu4: restart.
Jun 23 15:43:17 pinguino kernel: Inspecting /boot/System.map-2.6.20-16-386
Jun 23 15:43:17 pinguino kernel: Loaded 24502 symbols from /boot/System.map-2.6.20-16-386.
Jun 23 15:43:17 pinguino kernel: Symbols match kernel version 2.6.20.
Jun 23 15:43:17 pinguino kernel: No module symbols loaded - kernel modules not enabled. 
Jun 23 15:43:17 pinguino kernel: [    0.000000] Linux version 2.6.20-16-386 (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 Thu Jun 7 20:16:13 UTC 2007 (Ubuntu 2.6.20-16.29-386)
Jun 23 15:43:17 pinguino kernel: [    0.000000] BIOS-provided physical RAM map:
Jun 23 15:43:17 pinguino kernel: [    0.000000] sanitize start
Jun 23 15:43:17 pinguino kernel: [    0.000000] sanitize end
Jun 23 15:43:17 pinguino kernel: [    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009fc00 end: 000000000009fc00 type: 1
Jun 23 15:43:17 pinguino kernel: [    0.000000] copy_e820_map() type is E820_RAM
Jun 23 15:43:17 pinguino kernel: [    0.000000] copy_e820_map() start: 000000000009fc00 size: 0000000000000400 end: 00000000000a0000 type: 2
Jun 23 15:43:17 pinguino kernel: [    0.000000] copy_e820_map() start: 00000000000e0000 size: 000000000000ee00 end: 00000000000eee00 type: 2
Jun 23 15:43:17 pinguino kernel: [    0.000000] copy_e820_map() start: 00000000000eee00 size: 0000000000000200 end: 00000000000ef000 type: 4
Jun 23 15:43:17 pinguino kernel: [    0.000000] copy_e820_map() start: 00000000000ef000 size: 0000000000011000 end: 0000000000100000 type: 2
Jun 23 15:43:17 pinguino kernel: [    0.000000] copy_e820_map() start: 0000000000100000 size: 000000002fed0000 end: 000000002ffd0000 type: 1
Jun 23 15:43:17 pinguino kernel: [    0.000000] copy_e820_map() type is E820_RAM
Jun 23 15:43:17 pinguino kernel: [    0.000000] copy_e820_map() start: 000000002ffd0000 size: 0000000000010000 end: 000000002ffe0000 type: 3
Jun 23 15:43:17 pinguino kernel: [    0.000000] copy_e820_map() start: 000000002ffe0000 size: 0000000000020000 end: 0000000030000000 type: 2
Jun 23 15:43:17 pinguino kernel: [    0.000000] copy_e820_map() start: 00000000feda0000 size: 0000000000020000 end: 00000000fedc0000 type: 2
Jun 23 15:43:17 pinguino kernel: [    0.000000] copy_e820_map() start: 00000000ffb80000 size: 0000000000080000 end: 00000000ffc00000 type: 2
Jun 23 15:43:17 pinguino kernel: [    0.000000] copy_e820_map() start: 00000000fff00000 size: 0000000000100000 end: 0000000100000000 type: 2
Jun 23 15:43:17 pinguino kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Jun 23 15:43:17 pinguino kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Jun 23 15:43:17 pinguino kernel: [    0.000000]  BIOS-e820: 00000000000e0000 - 00000000000eee00 (reserved)
Jun 23 15:43:17 pinguino kernel: [    0.000000]  BIOS-e820: 00000000000eee00 - 00000000000ef000 (ACPI NVS)
Jun 23 15:43:17 pinguino kernel: [    0.000000]  BIOS-e820: 00000000000ef000 - 0000000000100000 (reserved)
Jun 23 15:43:17 pinguino kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000002ffd0000 (usable)
Jun 23 15:43:17 pinguino kernel: [    0.000000]  BIOS-e820: 000000002ffd0000 - 000000002ffe0000 (ACPI data)
Jun 23 15:43:17 pinguino kernel: [    0.000000]  BIOS-e820: 000000002ffe0000 - 0000000030000000 (reserved)
Jun 23 15:43:17 pinguino kernel: [    0.000000]  BIOS-e820: 00000000feda0000 - 00000000fedc0000 (reserved)
Jun 23 15:43:17 pinguino kernel: [    0.000000]  BIOS-e820: 00000000ffb80000 - 00000000ffc00000 (reserved)
Jun 23 15:43:17 pinguino kernel: [    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
Jun 23 15:43:17 pinguino kernel: [    0.000000] 0MB HIGHMEM available.
Jun 23 15:43:17 pinguino kernel: [    0.000000] 767MB LOWMEM available.
Jun 23 15:43:17 pinguino kernel: [    0.000000] Zone PFN ranges:
Jun 23 15:43:17 pinguino kernel: [    0.000000]   DMA             0 ->     4096
Jun 23 15:43:17 pinguino kernel: [    0.000000]   Normal       4096 ->   196560
Jun 23 15:43:17 pinguino kernel: [    0.000000]   HighMem    196560 ->   196560
Jun 23 15:43:17 pinguino kernel: [    0.000000] early_node_map[1] active PFN ranges
Jun 23 15:43:17 pinguino kernel: [    0.000000]     0:        0 ->   196560
Jun 23 15:43:17 pinguino kernel: [    0.000000] DMI 2.3 present.
Jun 23 15:43:17 pinguino kernel: [    0.000000] ACPI: PM-Timer IO Port: 0xd808
Jun 23 15:43:17 pinguino kernel: [    0.000000] Allocating PCI resources starting at 40000000 (gap: 30000000:ceda0000)
Jun 23 15:43:17 pinguino kernel: [    0.000000] Detected 2793.188 MHz processor.
Jun 23 15:43:17 pinguino kernel: [10608.013566] Built 1 zonelists.  Total pages: 195025
Jun 23 15:43:17 pinguino kernel: [10608.013568] Kernel command line: root=UUID=7e56dbcf-f39a-4531-9029-245b209e2a4c ro quiet splash
Jun 23 15:43:17 pinguino kernel: [10608.013727] Local APIC disabled by BIOS -- you can enable it with "lapic"
Jun 23 15:43:17 pinguino kernel: [10608.013742] Enabling fast FPU save and restore... done.
Jun 23 15:43:17 pinguino kernel: [10608.013744] Enabling unmasked SIMD FPU exception support... done.
Jun 23 15:43:17 pinguino kernel: [10608.013760] Initializing CPU#0
Jun 23 15:43:17 pinguino kernel: [10608.013861] PID hash table entries: 4096 (order: 12, 16384 bytes)
Jun 23 15:43:17 pinguino kernel: [10608.015387] Console: colour VGA+ 80x25
Jun 23 15:43:17 pinguino kernel: [10608.016330] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Jun 23 15:43:17 pinguino kernel: [10608.017220] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Jun 23 15:43:17 pinguino kernel: [10608.038109] Memory: 767048k/786240k available (1917k kernel code, 18520k reserved, 868k data, 328k init, 0k highmem)
Jun 23 15:43:17 pinguino kernel: [10608.038119] virtual kernel memory layout:
Jun 23 15:43:17 pinguino kernel: [10608.038120]     fixmap  : 0xfffa9000 - 0xfffff000   ( 344 kB)
Jun 23 15:43:17 pinguino kernel: [10608.038121]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Jun 23 15:43:17 pinguino kernel: [10608.038122]     vmalloc : 0xf0800000 - 0xff7fe000   ( 239 MB)
Jun 23 15:43:17 pinguino kernel: [10608.038123]     lowmem  : 0xc0000000 - 0xeffd0000   ( 767 MB)
Jun 23 15:43:17 pinguino kernel: [10608.038124]       .init : 0xc03bc000 - 0xc040e000   ( 328 kB)
Jun 23 15:43:17 pinguino kernel: [10608.038125]       .data : 0xc02df423 - 0xc03b8434   ( 868 kB)
Jun 23 15:43:17 pinguino kernel: [10608.038126]       .text : 0xc0100000 - 0xc02df423   (1917 kB)
Jun 23 15:43:17 pinguino kernel: [10608.038129] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Jun 23 15:43:17 pinguino kernel: [10608.117693] Calibrating delay using timer specific routine.. 5589.96 BogoMIPS (lpj=11179932)
Jun 23 15:43:17 pinguino kernel: [10608.117725] Security Framework v1.0.0 initialized
Jun 23 15:43:17 pinguino kernel: [10608.117732] SELinux:  Disabled at boot.
Jun 23 15:43:17 pinguino kernel: [10608.117743] Mount-cache hash table entries: 512
Jun 23 15:43:17 pinguino kernel: [10608.117847] CPU: Trace cache: 12K uops, L1 D cache: 8K
Jun 23 15:43:17 pinguino kernel: [10608.117849] CPU: L2 cache: 512K
Jun 23 15:43:17 pinguino kernel: [10608.117862] Compat vDSO mapped to ffffe000.
Jun 23 15:43:17 pinguino kernel: [10608.117865] Remapping vsyscall page to ffffe000
Jun 23 15:43:17 pinguino kernel: [10608.117874] CPU: Intel(R) Pentium(R) 4 CPU 2.80GHz stepping 09
Jun 23 15:43:17 pinguino kernel: [10608.117881] Checking 'hlt' instruction... OK.
Jun 23 15:43:17 pinguino kernel: [10608.134045] Early unpacking initramfs... done
Jun 23 15:43:17 pinguino kernel: [10608.455897] ACPI: Core revision 20060707
Jun 23 15:43:17 pinguino kernel: [10608.456039] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
Jun 23 15:43:17 pinguino kernel: [10608.457775] ACPI: setting ELCR to 0200 (from 0e00)
Jun 23 15:43:17 pinguino kernel: [10608.458651] Booting paravirtualized kernel on bare hardware
Jun 23 15:43:17 pinguino kernel: [10608.458711] Time: 13:42:48  Date: 05/23/107
Jun 23 15:43:17 pinguino kernel: [10608.458742] NET: Registered protocol family 16
Jun 23 15:43:17 pinguino kernel: [10608.458832] EISA bus registered
Jun 23 15:43:17 pinguino kernel: [10608.458837] ACPI: bus type pci registered
Jun 23 15:43:17 pinguino kernel: [10608.458928] PCI: PCI BIOS revision 2.10 entry at 0xfd4bd, last bus=5
Jun 23 15:43:17 pinguino kernel: [10608.458930] PCI: Using configuration type 1
Jun 23 15:43:17 pinguino kernel: [10608.458932] Setting up standard PCI resources
Jun 23 15:43:17 pinguino kernel: [10608.463605] ACPI: Interpreter enabled
Jun 23 15:43:17 pinguino kernel: [10608.463610] ACPI: Using PIC for interrupt routing
Jun 23 15:43:17 pinguino kernel: [10608.464090] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *11)
Jun 23 15:43:17 pinguino kernel: [10608.464437] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *11)
Jun 23 15:43:17 pinguino kernel: [10608.464722] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *11)
Jun 23 15:43:17 pinguino kernel: [10608.465009] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *11)
Jun 23 15:43:17 pinguino kernel: [10608.465303] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 *11)
Jun 23 15:43:17 pinguino kernel: [10608.465647] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 *11)
Jun 23 15:43:17 pinguino kernel: [10608.465931] ACPI: PCI Interrupt Link [LNKG] (IRQs *10)
Jun 23 15:43:17 pinguino kernel: [10608.466214] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *11)
Jun 23 15:43:17 pinguino kernel: [10608.466353] ACPI: PCI Root Bridge [PCI0] (0000:00)
Jun 23 15:43:17 pinguino kernel: [10608.466955] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
Jun 23 15:43:17 pinguino kernel: [10608.467292] * The chipset may have PM-Timer Bug. Due to workarounds for a bug,
Jun 23 15:43:17 pinguino kernel: [10608.467293] * this clock source is slow. If you are sure your timer does not have
Jun 23 15:43:17 pinguino kernel: [10608.467294] * this bug, please use "acpi_pm_good" to disable the workaround
Jun 23 15:43:17 pinguino kernel: [10608.467335] PCI quirk: region d800-d87f claimed by ICH4 ACPI/GPIO/TCO
Jun 23 15:43:17 pinguino kernel: [10608.467338] PCI quirk: region eec0-eeff claimed by ICH4 GPIO
Jun 23 15:43:17 pinguino kernel: [10608.467889] PCI: Transparent bridge - 0000:00:1e.0
Jun 23 15:43:17 pinguino kernel: [10608.467992] PCI: Bus #05 (-#08) is hidden behind transparent bridge #02 (-#05) (try 'pci=assign-busses')
Jun 23 15:43:17 pinguino kernel: [10608.467995] Please report the result to linux-kernel to fix this permanently
Jun 23 15:43:17 pinguino kernel: [10608.473699] ACPI: Power Resource [PFAN] (off)
Jun 23 15:43:17 pinguino kernel: [10608.473776] Linux Plug and Play Support v0.97 (c) Adam Belay
Jun 23 15:43:17 pinguino kernel: [10608.473787] pnp: PnP ACPI init
Jun 23 15:43:17 pinguino kernel: [10608.477445] pnp: PnP ACPI: found 11 devices
Jun 23 15:43:17 pinguino kernel: [10608.477451] PnPBIOS: Disabled by ACPI PNP
Jun 23 15:43:17 pinguino kernel: [10608.477504] PCI: Using ACPI for IRQ routing
Jun 23 15:43:17 pinguino kernel: [10608.477507] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Jun 23 15:43:17 pinguino kernel: [10608.483158] NET: Registered protocol family 8
Jun 23 15:43:17 pinguino kernel: [10608.483160] NET: Registered protocol family 20
Jun 23 15:43:17 pinguino kernel: [10608.484129] PCI: Bridge: 0000:00:01.0
Jun 23 15:43:17 pinguino kernel: [10608.484132]   IO window: disabled.
Jun 23 15:43:17 pinguino kernel: [10608.484136]   MEM window: fd000000-fdffffff
Jun 23 15:43:17 pinguino kernel: [10608.484139]   PREFETCH window: dbf00000-dfffffff
Jun 23 15:43:17 pinguino kernel: [10608.484159] PCI: Bus 3, cardbus bridge: 0000:02:0b.0
Jun 23 15:43:17 pinguino kernel: [10608.484161]   IO window: 0000c000-0000c0ff
Jun 23 15:43:17 pinguino kernel: [10608.484166]   IO window: 0000c400-0000c4ff
Jun 23 15:43:17 pinguino kernel: [10608.484170]   PREFETCH window: 40000000-43ffffff
Jun 23 15:43:17 pinguino kernel: [10608.484174]   MEM window: 4c000000-4fffffff
Jun 23 15:43:17 pinguino kernel: [10608.484178] PCI: Bus 5, cardbus bridge: 0000:02:0b.1
Jun 23 15:43:17 pinguino kernel: [10608.484180]   IO window: 0000c800-0000c8ff
Jun 23 15:43:17 pinguino kernel: [10608.484184]   IO window: 0000cc00-0000ccff
Jun 23 15:43:17 pinguino kernel: [10608.484188]   PREFETCH window: 44000000-47ffffff
Jun 23 15:43:17 pinguino kernel: [10608.484192]   MEM window: 50000000-53ffffff
Jun 23 15:43:17 pinguino kernel: [10608.484196] PCI: Bridge: 0000:00:1e.0
Jun 23 15:43:17 pinguino kernel: [10608.484199]   IO window: c000-cfff
Jun 23 15:43:17 pinguino kernel: [10608.484204]   MEM window: fce00000-fcefffff
Jun 23 15:43:17 pinguino kernel: [10608.484208]   PREFETCH window: 40000000-47ffffff
Jun 23 15:43:17 pinguino kernel: [10608.484239] PCI: Enabling device 0000:02:0b.0 (0000 -> 0003)
Jun 23 15:43:17 pinguino kernel: [10608.484472] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
Jun 23 15:43:17 pinguino kernel: [10608.484479] ACPI: PCI Interrupt 0000:02:0b.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
Jun 23 15:43:17 pinguino kernel: [10608.484495] PCI: Enabling device 0000:02:0b.1 (0000 -> 0003)
Jun 23 15:43:17 pinguino kernel: [10608.484691] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
Jun 23 15:43:17 pinguino kernel: [10608.484693] ACPI: PCI Interrupt 0000:02:0b.1[B] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
Jun 23 15:43:17 pinguino kernel: [10608.484724] NET: Registered protocol family 2
Jun 23 15:43:17 pinguino kernel: [10608.521081] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Jun 23 15:43:17 pinguino kernel: [10608.521310] TCP established hash table entries: 131072 (order: 7, 524288 bytes)
Jun 23 15:43:17 pinguino kernel: [10608.521828] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
Jun 23 15:43:17 pinguino kernel: [10608.522301] TCP: Hash tables configured (established 131072 bind 65536)
Jun 23 15:43:17 pinguino kernel: [10608.522304] TCP reno registered
Jun 23 15:43:17 pinguino kernel: [10608.533173] checking if image is initramfs... it is
Jun 23 15:43:17 pinguino kernel: [10609.176393] Freeing initrd memory: 8055k freed
Jun 23 15:43:17 pinguino kernel: [10609.176627] Simple Boot Flag at 0x7c set to 0x1
Jun 23 15:43:17 pinguino kernel: [10609.176801] audit: initializing netlink socket (disabled)
Jun 23 15:43:17 pinguino kernel: [10609.176819] audit(1182606169.352:1): initialized
Jun 23 15:43:17 pinguino kernel: [10609.176933] VFS: Disk quotas dquot_6.5.1
Jun 23 15:43:17 pinguino kernel: [10609.176952] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Jun 23 15:43:17 pinguino kernel: [10609.177010] io scheduler noop registered
Jun 23 15:43:17 pinguino kernel: [10609.177013] io scheduler anticipatory registered
Jun 23 15:43:17 pinguino kernel: [10609.177015] io scheduler deadline registered
Jun 23 15:43:17 pinguino kernel: [10609.177022] io scheduler cfq registered (default)
Jun 23 15:43:17 pinguino kernel: [10609.177279] isapnp: Scanning for PnP cards...
Jun 23 15:43:17 pinguino kernel: [10609.529583] isapnp: No Plug & Play device found
Jun 23 15:43:17 pinguino kernel: [10609.553900] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Jun 23 15:43:17 pinguino kernel: [10609.554730] PCI: Enabling device 0000:00:1f.6 (0000 -> 0001)
Jun 23 15:43:17 pinguino kernel: [10609.554963] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
Jun 23 15:43:17 pinguino kernel: [10609.554967] ACPI: PCI Interrupt 0000:00:1f.6[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
Jun 23 15:43:17 pinguino kernel: [10609.554974] ACPI: PCI interrupt for device 0000:00:1f.6 disabled
Jun 23 15:43:17 pinguino kernel: [10609.555042] mice: PS/2 mouse device common for all mice
Jun 23 15:43:17 pinguino kernel: [10609.555566] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Jun 23 15:43:17 pinguino kernel: [10609.555794] input: Macintosh mouse button emulation as /class/input/input0
Jun 23 15:43:17 pinguino kernel: [10609.555824] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Jun 23 15:43:17 pinguino kernel: [10609.555828] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Jun 23 15:43:17 pinguino kernel: [10609.556015] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Jun 23 15:43:17 pinguino kernel: [10609.563154] serio: i8042 KBD port at 0x60,0x64 irq 1
Jun 23 15:43:17 pinguino kernel: [10609.563161] serio: i8042 AUX port at 0x60,0x64 irq 12
Jun 23 15:43:17 pinguino kernel: [10609.563344] EISA: Probing bus 0 at eisa.0
Jun 23 15:43:17 pinguino kernel: [10609.563353] Cannot allocate resource for EISA slot 1
Jun 23 15:43:17 pinguino kernel: [10609.563369] EISA: Detected 0 cards.
Jun 23 15:43:17 pinguino kernel: [10609.593418] TCP cubic registered
Jun 23 15:43:17 pinguino kernel: [10609.593425] NET: Registered protocol family 1
Jun 23 15:43:17 pinguino kernel: [10609.593448] Using IPI Shortcut mode
Jun 23 15:43:17 pinguino kernel: [10609.593518] ACPI: (supports S0 S3 S4 S5)
Jun 23 15:43:17 pinguino kernel: [10609.593560]   Magic number: 11:789:736
Jun 23 15:43:17 pinguino kernel: [10609.594246] Freeing unused kernel memory: 328k freed
Jun 23 15:43:17 pinguino kernel: [10609.595235] Time: tsc clocksource has been installed.
Jun 23 15:43:17 pinguino kernel: [10609.607019] input: AT Translated Set 2 keyboard as /class/input/input1
Jun 23 15:43:17 pinguino kernel: [10610.812191] Capability LSM initialized
Jun 23 15:43:17 pinguino kernel: [10610.827791] device-mapper: ioctl: 4.11.0-ioctl (2006-10-12) initialised: dm-devel@redhat.com
Jun 23 15:43:17 pinguino kernel: [10610.853865] ACPI: Transitioning device [FAN] to D3
Jun 23 15:43:17 pinguino kernel: [10610.853869] ACPI: Transitioning device [FAN] to D3
Jun 23 15:43:17 pinguino kernel: [10610.853872] ACPI: Fan [FAN] (off)
Jun 23 15:43:17 pinguino kernel: [10610.857846] ACPI: CPU0 (power states: C1[C1] C2[C2])
Jun 23 15:43:17 pinguino kernel: [10610.858764] ACPI: Thermal Zone [THRM] (49 C)
Jun 23 15:43:17 pinguino kernel: [10610.916789] md: linear personality registered for level -1
Jun 23 15:43:17 pinguino kernel: [10610.920258] md: multipath personality registered for level -4
Jun 23 15:43:17 pinguino kernel: [10610.923536] md: raid0 personality registered for level 0
Jun 23 15:43:17 pinguino kernel: [10610.927351] md: raid1 personality registered for level 1
Jun 23 15:43:17 pinguino kernel: [10610.930562] raid5: automatically using best checksumming function: pIII_sse
Jun 23 15:43:17 pinguino kernel: [10610.948997]    pIII_sse  :  3493.000 MB/sec
Jun 23 15:43:17 pinguino kernel: [10610.949000] raid5: using function: pIII_sse (3493.000 MB/sec)
Jun 23 15:43:17 pinguino kernel: [10611.020875] raid6: int32x1    804 MB/s
Jun 23 15:43:17 pinguino kernel: [10611.088820] raid6: int32x2    774 MB/s
Jun 23 15:43:17 pinguino kernel: [10611.156661] raid6: int32x4    788 MB/s
Jun 23 15:43:17 pinguino kernel: [10611.224560] raid6: int32x8    522 MB/s
Jun 23 15:43:17 pinguino kernel: [10611.292430] raid6: mmxx1     2232 MB/s
Jun 23 15:43:17 pinguino kernel: [10611.360298] raid6: mmxx2     2873 MB/s
Jun 23 15:43:17 pinguino kernel: [10611.428190] raid6: sse1x1    1341 MB/s
Jun 23 15:43:17 pinguino kernel: [10611.496085] raid6: sse1x2    2540 MB/s
Jun 23 15:43:17 pinguino kernel: [10611.563954] raid6: sse2x1    2091 MB/s
Jun 23 15:43:17 pinguino kernel: [10611.631849] raid6: sse2x2    3157 MB/s
Jun 23 15:43:17 pinguino kernel: [10611.631850] raid6: using algorithm sse2x2 (3157 MB/s)
Jun 23 15:43:17 pinguino kernel: [10611.631854] md: raid6 personality registered for level 6
Jun 23 15:43:17 pinguino kernel: [10611.631856] md: raid5 personality registered for level 5
Jun 23 15:43:17 pinguino kernel: [10611.631857] md: raid4 personality registered for level 4
Jun 23 15:43:17 pinguino kernel: [10611.679306] md: raid10 personality registered for level 10
Jun 23 15:43:17 pinguino kernel: [10612.085791] usbcore: registered new interface driver usbfs
Jun 23 15:43:17 pinguino kernel: [10612.085817] usbcore: registered new interface driver hub
Jun 23 15:43:17 pinguino kernel: [10612.085841] usbcore: registered new device driver usb
Jun 23 15:43:17 pinguino kernel: [10612.086731] USB Universal Host Controller Interface driver v3.0
Jun 23 15:43:17 pinguino kernel: [10612.086790] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
Jun 23 15:43:17 pinguino kernel: [10612.086808] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Jun 23 15:43:17 pinguino kernel: [10612.086970] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
Jun 23 15:43:17 pinguino kernel: [10612.086995] uhci_hcd 0000:00:1d.0: irq 11, io base 0x0000efe0
Jun 23 15:43:17 pinguino kernel: [10612.087140] usb usb1: configuration #1 chosen from 1 choice
Jun 23 15:43:17 pinguino kernel: [10612.087167] hub 1-0:1.0: USB hub found
Jun 23 15:43:17 pinguino kernel: [10612.087174] hub 1-0:1.0: 2 ports detected
Jun 23 15:43:17 pinguino kernel: [10612.162005] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
Jun 23 15:43:17 pinguino kernel: [10612.191083] ACPI: PCI Interrupt 0000:00:1d.1[B] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
Jun 23 15:43:17 pinguino kernel: [10612.191103] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Jun 23 15:43:17 pinguino kernel: [10612.191123] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
Jun 23 15:43:17 pinguino kernel: [10612.191148] uhci_hcd 0000:00:1d.1: irq 11, io base 0x0000ef80
Jun 23 15:43:17 pinguino kernel: [10612.191244] usb usb2: configuration #1 chosen from 1 choice
Jun 23 15:43:17 pinguino kernel: [10612.191268] hub 2-0:1.0: USB hub found
Jun 23 15:43:17 pinguino kernel: [10612.191277] hub 2-0:1.0: 2 ports detected
Jun 23 15:43:17 pinguino kernel: [10612.294908] PCI: Enabling device 0000:00:1d.2 (0000 -> 0001)
Jun 23 15:43:17 pinguino kernel: [10612.295187] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
Jun 23 15:43:17 pinguino kernel: [10612.295191] ACPI: PCI Interrupt 0000:00:1d.2[C] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
Jun 23 15:43:17 pinguino kernel: [10612.295207] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Jun 23 15:43:17 pinguino kernel: [10612.295229] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
Jun 23 15:43:17 pinguino kernel: [10612.295254] uhci_hcd 0000:00:1d.2: irq 11, io base 0x000018c0
Jun 23 15:43:17 pinguino kernel: [10612.295355] usb usb3: configuration #1 chosen from 1 choice
Jun 23 15:43:17 pinguino kernel: [10612.295385] hub 3-0:1.0: USB hub found
Jun 23 15:43:17 pinguino kernel: [10612.295396] hub 3-0:1.0: 2 ports detected
Jun 23 15:43:17 pinguino kernel: [    4.364000] Time: acpi_pm clocksource has been installed.
Jun 23 15:43:17 pinguino kernel: [    4.400000] SCSI subsystem initialized
Jun 23 15:43:17 pinguino kernel: [    4.404000] PCI: Enabling device 0000:02:07.0 (0000 -> 0002)
Jun 23 15:43:17 pinguino kernel: [    4.404000] ACPI: PCI Interrupt Link [LNKF] enabled at IRQ 11
Jun 23 15:43:17 pinguino kernel: [    4.404000] ACPI: PCI Interrupt 0000:02:07.0[A] -> Link [LNKF] -> GSI 11 (level, low) -> IRQ 11
Jun 23 15:43:17 pinguino kernel: [    4.452000] usb 1-1: new low speed USB device using uhci_hcd and address 2
Jun 23 15:43:17 pinguino kernel: [    4.452000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[11]  MMIO=[fce06000-fce067ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
Jun 23 15:43:17 pinguino kernel: [    4.452000] 8139cp 0000:02:09.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
Jun 23 15:43:17 pinguino kernel: [    4.452000] 8139cp 0000:02:09.0: Try the "8139too" driver instead.
Jun 23 15:43:17 pinguino kernel: [    4.464000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
Jun 23 15:43:17 pinguino kernel: [    4.464000] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001bfa0 irq 14
Jun 23 15:43:17 pinguino kernel: [    4.464000] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001bfa8 irq 15
Jun 23 15:43:17 pinguino kernel: [    4.464000] scsi0 : ata_piix
Jun 23 15:43:17 pinguino kernel: [    4.468000] 8139too Fast Ethernet driver 0.9.28
Jun 23 15:43:17 pinguino kernel: [    4.628000] ata1.00: ata_hpa_resize 1: sectors = 78140160, hpa_sectors = 78140160
Jun 23 15:43:17 pinguino kernel: [    4.628000] ata1.00: ATA-5: TOSHIBA MK4021GAS, GA224A, max UDMA/100
Jun 23 15:43:17 pinguino kernel: [    4.628000] ata1.00: 78140160 sectors, multi 16: LBA 
Jun 23 15:43:17 pinguino kernel: [    4.628000] usb 1-1: configuration #1 chosen from 1 choice
Jun 23 15:43:17 pinguino kernel: [    4.636000] ata1.00: ata_hpa_resize 1: sectors = 78140160, hpa_sectors = 78140160
Jun 23 15:43:17 pinguino kernel: [    4.636000] ata1.00: configured for UDMA/100
Jun 23 15:43:17 pinguino kernel: [    4.636000] scsi1 : ata_piix
Jun 23 15:43:17 pinguino kernel: [    4.644000] usbcore: registered new interface driver hiddev
Jun 23 15:43:17 pinguino kernel: [    4.660000] input: Logitech Optical USB Mouse as /class/input/input2
Jun 23 15:43:17 pinguino kernel: [    4.660000] input: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:1d.0-1
Jun 23 15:43:17 pinguino kernel: [    4.660000] usbcore: registered new interface driver usbhid
Jun 23 15:43:17 pinguino kernel: [    4.660000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
Jun 23 15:43:17 pinguino kernel: [    5.020000] ata2.00: ATAPI, max UDMA/33
Jun 23 15:43:17 pinguino kernel: [    5.208000] ata2.00: configured for UDMA/33
Jun 23 15:43:17 pinguino kernel: [    5.208000] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK4021GA GA22 PQ: 0 ANSI: 5
Jun 23 15:43:17 pinguino kernel: [    5.212000] scsi 1:0:0:0: CD-ROM            TOSHIBA  CD/DVDW SDR6572M TR05 PQ: 0 ANSI: 5
Jun 23 15:43:17 pinguino kernel: [    5.216000] PCI: Enabling device 0000:00:1d.7 (0000 -> 0002)
Jun 23 15:43:17 pinguino kernel: [    5.216000] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11
Jun 23 15:43:17 pinguino kernel: [    5.216000] ACPI: PCI Interrupt 0000:00:1d.7[D] -> Link [LNKH] -> GSI 11 (level, low) -> IRQ 11
Jun 23 15:43:17 pinguino kernel: [    5.216000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Jun 23 15:43:17 pinguino kernel: [    5.216000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
Jun 23 15:43:17 pinguino kernel: [    5.216000] ehci_hcd 0000:00:1d.7: debug port 1
Jun 23 15:43:17 pinguino kernel: [    5.216000] ehci_hcd 0000:00:1d.7: irq 11, io mem 0x48000000
Jun 23 15:43:17 pinguino kernel: [    5.220000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Jun 23 15:43:17 pinguino kernel: [    5.220000] usb usb4: configuration #1 chosen from 1 choice
Jun 23 15:43:17 pinguino kernel: [    5.220000] hub 4-0:1.0: USB hub found
Jun 23 15:43:17 pinguino kernel: [    5.220000] hub 4-0:1.0: 6 ports detected
Jun 23 15:43:17 pinguino kernel: [    5.236000] SCSI device sda: 78140160 512-byte hdwr sectors (40008 MB)
Jun 23 15:43:17 pinguino kernel: [    5.236000] sda: Write Protect is off
Jun 23 15:43:17 pinguino kernel: [    5.236000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jun 23 15:43:17 pinguino kernel: [    5.236000] SCSI device sda: 78140160 512-byte hdwr sectors (40008 MB)
Jun 23 15:43:17 pinguino kernel: [    5.236000] sda: Write Protect is off
Jun 23 15:43:17 pinguino kernel: [    5.236000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jun 23 15:43:17 pinguino kernel: [    5.236000]  sda: sda1 sda2 <ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 11
Jun 23 15:43:17 pinguino kernel: [    5.324000] ACPI: PCI Interrupt 0000:02:09.0[A] -> Link [LNKE] -> GSI 11 (level, low) -> IRQ 11
Jun 23 15:43:17 pinguino kernel: [    5.324000] eth0: RealTek RTL8139 at 0xf08b2f00, 00:07:0D:33:4E:47, IRQ 11
Jun 23 15:43:17 pinguino kernel: [    5.336000]  sda5 >
Jun 23 15:43:17 pinguino kernel: [    5.336000] sd 0:0:0:0: Attached scsi disk sda
Jun 23 15:43:17 pinguino kernel: [    5.340000] sd 0:0:0:0: Attached scsi generic sg0 type 0
Jun 23 15:43:17 pinguino kernel: [    5.340000] scsi 1:0:0:0: Attached scsi generic sg1 type 5
Jun 23 15:43:17 pinguino kernel: [    5.364000] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
Jun 23 15:43:17 pinguino kernel: [    5.364000] Uniform CD-ROM driver Revision: 3.20
Jun 23 15:43:17 pinguino kernel: [    5.508000] usb 1-1: USB disconnect, address 2
Jun 23 15:43:17 pinguino kernel: [    5.624000] kjournald starting.  Commit interval 5 seconds
Jun 23 15:43:17 pinguino kernel: [    5.624000] EXT3-fs: mounted filesystem with ordered data mode.
Jun 23 15:43:17 pinguino kernel: [    5.748000] usb 1-1: new low speed USB device using uhci_hcd and address 3
Jun 23 15:43:17 pinguino kernel: [    5.920000] usb 1-1: configuration #1 chosen from 1 choice
Jun 23 15:43:17 pinguino kernel: [    5.936000] input: Logitech Optical USB Mouse as /class/input/input3
Jun 23 15:43:17 pinguino kernel: [    5.936000] input: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:1d.0-1
Jun 23 15:43:17 pinguino kernel: [   19.628000] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
Jun 23 15:43:17 pinguino kernel: [   21.200000] NET: Registered protocol family 17
Jun 23 15:43:17 pinguino kernel: [   21.248000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jun 23 15:43:17 pinguino kernel: [   21.256000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Jun 23 15:43:17 pinguino kernel: [   21.316000] iTCO_vendor_support: vendor-support=0
Jun 23 15:43:17 pinguino kernel: [   21.320000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
Jun 23 15:43:17 pinguino kernel: [   21.320000] iTCO_wdt: Found a ICH4 TCO device (Version=1, TCOBASE=0x5860)
Jun 23 15:43:17 pinguino kernel: [   21.320000] iTCO_wdt: heartbeat value must be 2<heartbeat<39 (TCO v1) or 613 (TCO v2), using 30
Jun 23 15:43:17 pinguino kernel: [   21.320000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
Jun 23 15:43:17 pinguino kernel: [   21.636000] Linux agpgart interface v0.102 (c) Dave Jones
Jun 23 15:43:17 pinguino kernel: [   21.640000] agpgart: Detected an Intel i845 Chipset.
Jun 23 15:43:17 pinguino kernel: [   21.652000] agpgart: AGP aperture is 256M @ 0xe0000000
Jun 23 15:43:17 pinguino kernel: [   22.012000] input: PC Speaker as /class/input/input4
Jun 23 15:43:17 pinguino kernel: [   22.052000] Real Time Clock Driver v1.12ac
Jun 23 15:43:17 pinguino kernel: [   22.280000] Yenta: CardBus bridge found at 0000:02:0b.0 [1179:0001]
Jun 23 15:43:17 pinguino kernel: [   22.408000] Yenta: ISA IRQ mask 0x04b8, PCI irq 11
Jun 23 15:43:17 pinguino kernel: [   22.408000] Socket status: 30000020
Jun 23 15:43:17 pinguino kernel: [   22.408000] pcmcia: parent PCI bridge I/O window: 0xc000 - 0xcfff
Jun 23 15:43:17 pinguino kernel: [   22.408000] cs: IO port probe 0xc000-0xcfff: clean.
Jun 23 15:43:17 pinguino kernel: [   22.408000] pcmcia: parent PCI bridge Memory window: 0xfce00000 - 0xfcefffff
Jun 23 15:43:17 pinguino kernel: [   22.408000] pcmcia: parent PCI bridge Memory window: 0x40000000 - 0x47ffffff
Jun 23 15:43:17 pinguino kernel: [   22.408000] Yenta: CardBus bridge found at 0000:02:0b.1 [1179:0001]
Jun 23 15:43:17 pinguino kernel: [   22.536000] Yenta: ISA IRQ mask 0x04b8, PCI irq 11
Jun 23 15:43:17 pinguino kernel: [   22.536000] Socket status: 30000007
Jun 23 15:43:17 pinguino kernel: [   22.536000] Yenta: Raising subordinate bus# of parent bus (#02) from #05 to #08
Jun 23 15:43:17 pinguino kernel: [   22.536000] pcmcia: parent PCI bridge I/O window: 0xc000 - 0xcfff
Jun 23 15:43:17 pinguino kernel: [   22.536000] cs: IO port probe 0xc000-0xcfff: clean.
Jun 23 15:43:17 pinguino kernel: [   22.536000] pcmcia: parent PCI bridge Memory window: 0xfce00000 - 0xfcefffff
Jun 23 15:43:17 pinguino kernel: [   22.536000] pcmcia: parent PCI bridge Memory window: 0x40000000 - 0x47ffffff
Jun 23 15:43:17 pinguino kernel: [   22.704000] Synaptics Touchpad, model: 1, fw: 5.9, id: 0xf6eb1, caps: 0x804713/0x0
Jun 23 15:43:17 pinguino kernel: [   22.708000] PCI: Enabling device 0000:00:1f.5 (0000 -> 0003)
Jun 23 15:43:17 pinguino kernel: [   22.708000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
Jun 23 15:43:17 pinguino kernel: [   22.760000] input: SynPS/2 Synaptics TouchPad as /class/input/input5
Jun 23 15:43:17 pinguino kernel: [   22.916000] pnp: Device 00:0a activated.
Jun 23 15:43:17 pinguino kernel: [   22.916000] parport: PnPBIOS parport detected.
Jun 23 15:43:17 pinguino kernel: [   22.916000] pnp: Device 00:0a disabled.
Jun 23 15:43:17 pinguino kernel: [   23.044000] pccard: CardBus card inserted into slot 0
Jun 23 15:43:17 pinguino kernel: [   23.496000] nvidia: module license 'NVIDIA' taints kernel.
Jun 23 15:43:17 pinguino kernel: [   23.752000] intel8x0_measure_ac97_clock: measured 280193 usecs
Jun 23 15:43:17 pinguino kernel: [   23.752000] intel8x0: clocking to 48000
Jun 23 15:43:17 pinguino kernel: [   23.756000] ACPI: PCI Interrupt Link [LNKG] enabled at IRQ 10
Jun 23 15:43:17 pinguino kernel: [   23.756000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKG] -> GSI 10 (level, low) -> IRQ 10
Jun 23 15:43:17 pinguino kernel: [   23.756000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-9639  Mon Apr 16 20:20:06 PDT 2007
Jun 23 15:43:17 pinguino kernel: [   24.416000] cs: IO port probe 0x100-0x3af: excluding 0x1e0-0x1e7
Jun 23 15:43:17 pinguino kernel: [   24.420000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
Jun 23 15:43:17 pinguino kernel: [   24.420000] cs: IO port probe 0x820-0x8ff: clean.
Jun 23 15:43:17 pinguino kernel: [   24.420000] cs: IO port probe 0xc00-0xcf7: clean.
Jun 23 15:43:17 pinguino kernel: [   24.420000] cs: IO port probe 0xa00-0xaff: clean.
Jun 23 15:43:17 pinguino kernel: [   24.420000] cs: IO port probe 0x100-0x3af: excluding 0x1e0-0x1e7
Jun 23 15:43:17 pinguino kernel: [   24.424000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
Jun 23 15:43:17 pinguino kernel: [   24.424000] cs: IO port probe 0x820-0x8ff: clean.
Jun 23 15:43:17 pinguino kernel: [   24.424000] cs: IO port probe 0xc00-0xcf7: clean.
Jun 23 15:43:17 pinguino kernel: [   24.424000] cs: IO port probe 0xa00-0xaff: clean.
Jun 23 15:43:17 pinguino kernel: [   24.568000] lp: driver loaded but no devices found
Jun 23 15:43:17 pinguino kernel: [   24.732000] EXT3 FS on sda1, internal journal
Jun 23 15:43:17 pinguino kernel: [   28.536000] ACPI: AC Adapter [ADP1] (on-line)
Jun 23 15:43:17 pinguino kernel: [   28.576000] ACPI: Battery Slot [BAT1] (battery present)
Jun 23 15:43:17 pinguino kernel: [   28.628000] input: Power Button (FF) as /class/input/input6
Jun 23 15:43:17 pinguino kernel: [   28.632000] ACPI: Power Button (FF) [PWRF]
Jun 23 15:43:17 pinguino kernel: [   28.668000] input: Power Button (CM) as /class/input/input7
Jun 23 15:43:17 pinguino kernel: [   28.672000] ACPI: Power Button (CM) [PWRB]
Jun 23 15:43:17 pinguino kernel: [   28.704000] input: Lid Switch as /class/input/input8
Jun 23 15:43:17 pinguino kernel: [   28.712000] ACPI: Lid Switch [LID]
Jun 23 15:43:17 pinguino kernel: [   28.728000] Using specific hotkey driver
Jun 23 15:43:17 pinguino kernel: [   28.760000] No dock devices found.
Jun 23 15:43:17 pinguino kernel: [   28.856000] toshiba_acpi: Toshiba Laptop ACPI Extras version 0.19a-dev
Jun 23 15:43:17 pinguino kernel: [   28.856000] toshiba_acpi:     HCI method: \_SB_.VALD.GHCI
Jun 23 15:43:17 pinguino kernel: [   28.860000] toshiba_acpi: Toshiba hotkeys are sent as ACPI events
Jun 23 15:43:17 pinguino kernel: [   28.860000] toshiba_acpi: ktoshkeyd will check 2 times per second
Jun 23 15:43:17 pinguino kernel: [   28.864000] toshiba_acpi: Dropped 0 keys from the queue on startup
Jun 23 15:43:17 pinguino kernel: [   28.880000] ACPI: Video Device [VGA] (multi-head: yes  rom: yes  post: no)
Jun 23 15:43:17 pinguino kernel: [   28.944000] pcc_acpi: loading...
Jun 23 15:43:23 pinguino dhcdbd: Started up.
Jun 23 15:43:23 pinguino dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Jun 23 15:43:23 pinguino dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Jun 23 15:43:26 pinguino hpiod: 1.7.3 accepting connections at 2208... 
Jun 23 15:43:26 pinguino dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Jun 23 15:43:26 pinguino dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Jun 23 15:43:26 pinguino dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Jun 23 15:43:26 pinguino kernel: [   38.280000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
Jun 23 15:43:26 pinguino kernel: [   38.280000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
Jun 23 15:43:26 pinguino kernel: [   38.280000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
Jun 23 15:43:32 pinguino kernel: [   43.920000] NET: Registered protocol family 10
Jun 23 15:43:32 pinguino kernel: [   43.920000] lo: Disabled Privacy Extensions
Jun 23 15:43:32 pinguino kernel: [   44.308000] ppdev: user-space parallel port driver
Jun 23 15:43:32 pinguino kernel: [   44.876000] apm: BIOS not found.
Jun 23 15:43:37 pinguino kernel: [   49.188000] vboxdrv: Trying to deactivate NMI watchdog permanently...
Jun 23 15:43:37 pinguino kernel: [   49.188000] vboxdrv: Successfully done.
Jun 23 15:43:48 pinguino gconfd (silvestre-5468): (Version 2.18.0.1) wird gestartet, Prozesskennung 5468, Benutzer »silvestre«
Jun 23 15:43:48 pinguino gconfd (silvestre-5468): Die Adresse »xml:readonly:/etc/gconf/gconf.xml.mandatory« wurde an der Position 0 zu einer nur lesbaren Konfigurationsquelle aufgelöst
Jun 23 15:43:48 pinguino gconfd (silvestre-5468): Die Adresse »xml:readwrite:/home/silvestre/.gconf« wurde an der Position 1 zu einer schreibbaren Konfigurationsquelle aufgelöst
Jun 23 15:43:48 pinguino gconfd (silvestre-5468): Die Adresse »xml:readonly:/etc/gconf/gconf.xml.defaults« wurde an der Position 2 zu einer nur lesbaren Konfigurationsquelle aufgelöst
Jun 23 15:43:48 pinguino gconfd (silvestre-5468): Die Adresse »xml:readonly:/var/lib/gconf/debian.defaults« wurde an der Position 3 zu einer nur lesbaren Konfigurationsquelle aufgelöst
Jun 23 15:43:48 pinguino gconfd (silvestre-5468): Die Adresse »xml:readonly:/var/lib/gconf/defaults« wurde an der Position 4 zu einer nur lesbaren Konfigurationsquelle aufgelöst
Jun 23 15:44:00 pinguino gconfd (silvestre-5468): Die Adresse »xml:readwrite:/home/silvestre/.gconf« wurde an der Position 0 zu einer schreibbaren Konfigurationsquelle aufgelöst
```

---

