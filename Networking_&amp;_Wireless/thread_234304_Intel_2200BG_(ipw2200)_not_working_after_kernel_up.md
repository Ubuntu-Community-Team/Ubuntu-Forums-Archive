---
title: "Intel 2200BG (ipw2200) not working after kernel update"
date: 2006-08-11
forum: Networking &amp; Wireless
---

### Post by NiklasV on 2006-08-11
I also posted this in the wireless section, but this section seems to be more active, and the problem isn't really wireless-specific.

Hi

I installed Ubuntu on my brothers laptop (Toshiba Dynabook VX/470LS), and the wireless network was working great, until I updated the kernel.
It updated to kernel 2.6.15.26-386 from 2.6.15.23-386. The wireless card no longer shows up in the network settings and neither iwconfig or ifconfig has any record of it.

It's an Intel 2200BG, and as far as I know, it used the ipw2200 driver.

I tried booting with the old kernel, but I still had the same problem.

I grepped /var/log/messages and /var/log/dmesg:

grep ipw2200 /var/log/messages:
Aug 11 13:37:12 localhost kernel: [17179588.396000] ipw2200: Intel(R) PRO/Wirele ss 2200/2915 Network Driver, 1.1.1
Aug 11 13:37:12 localhost kernel: [17179588.396000] ipw2200: Copyright(c) 2003-2 006 Intel Corporation
Aug 11 13:37:12 localhost kernel: [17179588.396000] Warning: PCI driver ipw2200 has a struct device_driver shutdown method, please update!
Aug 11 13:37:12 localhost kernel: [17179588.920000] ipw2200: Detected Intel PRO/ Wireless 2200BG Network Connection
Aug 11 13:37:12 localhost kernel: [17179594.696000] ipw2200: probe of 0000:05:04 .0 failed with error -5
Aug 11 13:46:37 localhost kernel: [4294686.278000] ipw2200: Intel(R) PRO/Wireles s 2200/2915 Network Driver, 1.1.1
Aug 11 13:46:37 localhost kernel: [4294686.278000] ipw2200: Copyright(c) 2003-20 06 Intel Corporation
Aug 11 13:46:37 localhost kernel: [4294686.278000] Warning: PCI driver ipw2200 h as a struct device_driver shutdown method, please update!
Aug 11 13:46:37 localhost kernel: [4294686.278000] ipw2200: Detected Intel PRO/W ireless 2200BG Network Connection
Aug 11 13:46:37 localhost kernel: [4294692.422000] ipw2200: probe of 0000:05:04. 0 failed with error -5
Aug 11 13:51:18 localhost kernel: [17179591.132000] ipw2200: Intel(R) PRO/Wirele ss 2200/2915 Network Driver, 1.1.1
Aug 11 13:51:18 localhost kernel: [17179591.132000] ipw2200: Copyright(c) 2003-2 006 Intel Corporation
Aug 11 13:51:18 localhost kernel: [17179591.132000] Warning: PCI driver ipw2200 has a struct device_driver shutdown method, please update!
Aug 11 13:51:18 localhost kernel: [17179591.132000] ipw2200: Detected Intel PRO/ Wireless 2200BG Network Connection
Aug 11 13:51:18 localhost kernel: [17179596.924000] ipw2200: probe of 0000:05:04 .0 failed with error -5

grep ipw2200 /var/log/dmesg:
[17179591.132000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.1.1
[17179591.132000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[17179591.132000] Warning: PCI driver ipw2200 has a struct device_driver shutdown method, please update!
[17179591.132000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[17179592.460000] ipw2200: Failed to send TX_POWER: Command timed out.
[17179593.576000] ipw2200: Failed to send TX_POWER: Command timed out.
[17179594.692000] ipw2200: Failed to send TX_POWER: Command timed out.
[17179595.808000] ipw2200: Failed to send TX_POWER: Command timed out.
[17179596.924000] ipw2200: Failed to send TX_POWER: Command timed out.
[17179596.924000] ipw2200: Unable to initialize device after 5 attempts.
[17179596.924000] ipw2200: failed to register network device
[17179596.924000] ipw2200: probe of 0000:05:04.0 failed with error -5

Any help with this would be greatly appreciated.

/Niklas

---

### Post by NiklasV on 2006-08-13
Bump

I still have the same problem even though I reinstalled and the kernel is once again 2.6.15-23, so the kernel upgrade can probably be ruled out as the source of the problem. What's really frustrating is the fact that it actually did work when I first installed and booted, right up until I rebooted because of the updated the kernel.

Excerpts from dmesg (I will post the entire dmesg below):
```
[4294688.467000] ipw2200: Failed to send TX_POWER: Command timed out.
[4294689.594000] ipw2200: Failed to send TX_POWER: Command timed out.
[4294690.721000] ipw2200: Failed to send TX_POWER: Command timed out.
[4294691.848000] ipw2200: Failed to send TX_POWER: Command timed out.
[4294692.974000] ipw2200: Failed to send TX_POWER: Command timed out.
[4294692.979000] ipw2200: Unable to initialize device after 5 attempts.
[4294692.985000] ipw2200: failed to register network device
[4294692.991000] ACPI: PCI interrupt for device 0000:05:04.0 disabled
[4294692.991000] ipw2200: probe of 0000:05:04.0 failed with error -5
.
.
[4294677.145000] irq 11: nobody cared (try booting with the "irqpoll" option)
.
.
[4294677.145000] Disabling IRQ #11

```

I should probably add that the card works in Windows, so it doesn't appear to be a hardware problem.

Can someone please help, I've been trying to get this to work for 3 days now and I'm about ready to give up.

/Niklas

---

### Post by NiklasV on 2006-08-13
dmesg
```

[4294667.296000] Linux version 2.6.15-23-386 (buildd@rothera) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Tue May 23 13:49:40 UTC 2006
[4294667.296000] BIOS-provided physical RAM map:
[4294667.296000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[4294667.296000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[4294667.296000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[4294667.296000]  BIOS-e820: 0000000000100000 - 000000001f7dfffc (usable)
[4294667.296000]  BIOS-e820: 000000001f7dfffc - 000000001f7fffc0 (ACPI data)
[4294667.296000]  BIOS-e820: 000000001f7fffc0 - 000000001f800000 (ACPI NVS)
[4294667.296000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[4294667.296000] 0MB HIGHMEM available.
[4294667.296000] 503MB LOWMEM available.
[4294667.296000] On node 0 totalpages: 128991
[4294667.296000]   DMA zone: 4096 pages, LIFO batch:0
[4294667.296000]   DMA32 zone: 0 pages, LIFO batch:0
[4294667.296000]   Normal zone: 124895 pages, LIFO batch:31
[4294667.296000]   HighMem zone: 0 pages, LIFO batch:0
[4294667.296000] DMI 2.3 present.
[4294667.296000] ACPI: RSDP (v000 TOSINV                                ) @ 0x000e5010
[4294667.296000] ACPI: RSDT (v001 INSYDE RSDT_000 0x00000100 ABCD 0x00010200) @ 0x1f7f86d7
[4294667.296000] ACPI: FADT (v001 TOSINV FACP_000 0x00000100 0000 0x00010200) @ 0x1f7ffb30
[4294667.296000] ACPI: MCFG (v001 INSYDE MCFG_000 0x30303030 0000 0x30303030) @ 0x1f7ffbc0
[4294667.296000] ACPI: SSDT (v001  PmRef  Cpu0Ist 0x00003000 INTL 0x20030522) @ 0x1f7f88c5
[4294667.296000] ACPI: SSDT (v001  PmRef  Cpu0Cst 0x00003001 INTL 0x20030522) @ 0x1f7f870b
[4294667.296000] ACPI: DSDT (v001 TOSINV SONOMA   0x00001004 INTL 0x02002036) @ 0x00000000
[4294667.296000] ACPI: PM-Timer IO Port: 0x1008
[4294667.296000] Allocating PCI resources starting at 20000000 (gap: 1f800000:e0700000)
[4294667.296000] Built 1 zonelists
[4294667.296000] Kernel command line: root=/dev/sda2 ro lapic quiet splash
[4294667.296000] Local APIC disabled by BIOS -- reenabling.
[4294667.296000] Found and enabled local APIC!
[4294667.296000] mapped APIC to ffffd000 (fee00000)
[4294667.296000] Initializing CPU#0
[4294667.296000] PID hash table entries: 2048 (order: 11, 32768 bytes)
[4294667.296000] Detected 1596.108 MHz processor.
[4294667.296000] Using pmtmr for high-res timesource
[4294667.296000] Console: colour VGA+ 80x25
[4294670.606000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[4294670.607000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[4294670.619000] Memory: 501044k/515964k available (1976k kernel code, 14348k reserved, 606k data, 288k init, 0k highmem)
[4294670.619000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[4294670.679000] Calibrating delay using timer specific routine.. 3195.15 BogoMIPS (lpj=1597579)
[4294670.679000] Security Framework v1.0.0 initialized
[4294670.679000] SELinux:  Disabled at boot.
[4294670.679000] Mount-cache hash table entries: 512
[4294670.679000] CPU: After generic identify, caps: afe9fbff 00000000 00000000 00000000 00000180 00000000 00000000
[4294670.679000] CPU: After vendor identify, caps: afe9fbff 00000000 00000000 00000000 00000180 00000000 00000000
[4294670.679000] CPU: L1 I cache: 32K, L1 D cache: 32K
[4294670.679000] CPU: L2 cache: 2048K
[4294670.679000] CPU: After all inits, caps: afe9fbff 00000000 00000000 00000040 00000180 00000000 00000000
[4294670.679000] mtrr: v2.0 (20020519)
[4294670.679000] CPU: Intel(R) Pentium(R) M processor 1.60GHz stepping 08
[4294670.679000] Enabling fast FPU save and restore... done.
[4294670.679000] Enabling unmasked SIMD FPU exception support... done.
[4294670.679000] Checking 'hlt' instruction... OK.
[4294670.683000] checking if image is initramfs... it is
[4294671.340000] Freeing initrd memory: 6608k freed
[4294671.347000] ACPI: Looking for DSDT ... not found!
[4294671.350000] ACPI: setting ELCR to 0200 (from 0c20)
[4294671.439000] NET: Registered protocol family 16
[4294671.439000] EISA bus registered
[4294671.439000] ACPI: bus type pci registered
[4294671.439000] PCI: PCI BIOS revision 2.10 entry at 0xea7d4, last bus=5
[4294671.439000] PCI: Using MMCONFIG
[4294671.440000] ACPI: Subsystem revision 20051216
[4294671.443000] ACPI: Interpreter enabled
[4294671.443000] ACPI: Using PIC for interrupt routing
[4294671.443000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[4294671.443000] PCI: Probing PCI hardware (bus 00)
[4294671.448000] Boot video device is 0000:00:02.0
[4294671.448000] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[4294671.448000] PCI quirk: region 1300-133f claimed by ICH6 GPIO
[4294671.448000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.2
[4294671.449000] PCI: Transparent bridge - 0000:00:1e.0
[4294671.449000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[4294671.475000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[4294671.475000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[4294671.477000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[4294671.482000] ACPI: PCI Interrupt Link [LNKA] (IRQs 5 *11)
[4294671.482000] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 *10 11)
[4294671.483000] ACPI: PCI Interrupt Link [LNKC] (IRQs 5 *11)
[4294671.483000] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 10 *11)
[4294671.483000] ACPI: PCI Interrupt Link [LNKE] (IRQs *5 11)
[4294671.483000] ACPI: PCI Interrupt Link [LNKF] (IRQs 5 10) *0, disabled.
[4294671.484000] ACPI: PCI Interrupt Link [LNKG] (IRQs 6) *11
[4294671.484000] ACPI: PCI Interrupt Link [LNKH] (IRQs 5 10) *11
[4294671.484000] ACPI: Embedded Controller [EC0] (gpe 16) interrupt mode.
[4294671.487000] ACPI: Power Resource [PFA1] (off)
[4294671.487000] Linux Plug and Play Support v0.97 (c) Adam Belay
[4294671.487000] pnp: PnP ACPI init
[4294671.494000] pnp: PnP ACPI: found 9 devices
[4294671.494000] PnPBIOS: Disabled by ACPI PNP
[4294671.494000] PCI: Using ACPI for IRQ routing
[4294671.494000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[4294671.494000] PCI: Cannot allocate resource region 0 of device 0000:05:06.0
[4294671.503000] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
[4294671.503000] PCI: Bridge: 0000:00:1c.0
[4294671.503000]   IO window: c000-dfff
[4294671.503000]   MEM window: cc000000-cfffffff
[4294671.503000]   PREFETCH window: 9c000000-9fffffff
[4294671.503000] PCI: Bridge: 0000:00:1c.1
[4294671.503000]   IO window: a000-bfff
[4294671.503000]   MEM window: c8000000-cbffffff
[4294671.503000]   PREFETCH window: 98000000-9bffffff
[4294671.503000] PCI: Bus 6, cardbus bridge: 0000:05:06.0
[4294671.503000]   IO window: 00008000-000080ff
[4294671.503000]   IO window: 00008400-000084ff
[4294671.503000]   PREFETCH window: 88000000-89ffffff
[4294671.503000]   MEM window: ba000000-bbffffff
[4294671.503000] PCI: Bridge: 0000:00:1e.0
[4294671.503000]   IO window: 8000-9fff
[4294671.503000]   MEM window: b8000000-c7ffffff
[4294671.503000]   PREFETCH window: 88000000-97ffffff
[4294671.503000] **** SET: Misaligned resource pointer: df7473c2 Type 07 Len 0
[4294671.503000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10
[4294671.503000] PCI: setting IRQ 10 as level-triggered
[4294671.503000] ACPI: PCI Interrupt 0000:00:1c.0[A] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[4294671.503000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[4294671.503000] **** SET: Misaligned resource pointer: df7473c2 Type 07 Len 0
[4294671.504000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[4294671.504000] PCI: setting IRQ 11 as level-triggered
[4294671.504000] ACPI: PCI Interrupt 0000:00:1c.1[B] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[4294671.504000] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[4294671.504000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[4294671.504000] **** SET: Misaligned resource pointer: df7473c2 Type 07 Len 0
[4294671.504000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[4294671.504000] ACPI: PCI Interrupt 0000:05:06.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[4294671.504000] audit: initializing netlink socket (disabled)
[4294671.504000] audit(1155518536.503:1): initialized
[4294671.504000] VFS: Disk quotas dquot_6.5.1
[4294671.504000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[4294671.504000] Initializing Cryptographic API
[4294671.504000] io scheduler noop registered
[4294671.504000] io scheduler anticipatory registered
[4294671.504000] io scheduler deadline registered
[4294671.504000] io scheduler cfq registered
[4294671.505000] ACPI: PCI Interrupt 0000:00:1c.0[A] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[4294671.505000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[4294671.505000] assign_interrupt_mode Found MSI capability
[4294671.505000] Allocate Port Service[pcie00]
[4294671.505000] Allocate Port Service[pcie02]
[4294671.505000] Allocate Port Service[pcie03]
[4294671.505000] ACPI: PCI Interrupt 0000:00:1c.1[B] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[4294671.505000] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[4294671.505000] assign_interrupt_mode Found MSI capability
[4294671.505000] Allocate Port Service[pcie00]
[4294671.505000] Allocate Port Service[pcie02]
[4294671.505000] Allocate Port Service[pcie03]
[4294671.505000] isapnp: Scanning for PnP cards...
[4294671.862000] isapnp: No Plug & Play device found
[4294671.876000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[4294671.881000] i8042.c: Detected active multiplexing controller, rev 1.1.
[4294671.883000] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[4294671.884000] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[4294671.884000] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[4294671.884000] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[4294671.884000] serio: i8042 KBD port at 0x60,0x64 irq 1
[4294671.884000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[4294671.886000] **** SET: Misaligned resource pointer: df6f0f02 Type 07 Len 0
[4294671.886000] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 5
[4294671.886000] PCI: setting IRQ 5 as level-triggered
[4294671.886000] ACPI: PCI Interrupt 0000:00:1e.3[B] -> Link [LNKE] -> GSI 5 (level, low) -> IRQ 5
[4294671.886000] ACPI: PCI interrupt for device 0000:00:1e.3 disabled
[4294671.886000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[4294671.887000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294671.887000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[4294671.887000] mice: PS/2 mouse device common for all mice
[4294671.887000] EISA: Probing bus 0 at eisa.0
[4294671.887000] Cannot allocate resource for EISA slot 1
[4294671.887000] Cannot allocate resource for EISA slot 8
[4294671.887000] EISA: Detected 0 cards.
[4294671.887000] NET: Registered protocol family 2
[4294671.897000] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[4294671.897000] TCP established hash table entries: 16384 (order: 4, 65536 bytes)
[4294671.897000] TCP bind hash table entries: 16384 (order: 4, 65536 bytes)
[4294671.897000] TCP: Hash tables configured (established 16384 bind 16384)
[4294671.897000] TCP reno registered
[4294671.897000] TCP bic registered
[4294671.897000] NET: Registered protocol family 1
[4294671.897000] NET: Registered protocol family 8
[4294671.897000] NET: Registered protocol family 20
[4294671.897000] Using IPI Shortcut mode
[4294671.897000] ACPI wakeup devices:
[4294671.897000] LID0 RP01 RP02 RP03 RP04 USB1 USB2 USB3 USB4 USB7 MODM PS2K
[4294671.897000] ACPI: (supports S0 S3 S4 S5)
[4294671.897000] Freeing unused kernel memory: 288k freed
[4294671.903000] input: AT Translated Set 2 keyboard as /class/input/input0
[4294671.939000] vga16fb: initializing
[4294671.939000] vga16fb: mapped to 0xc00a0000
[4294672.066000] Console: switching to colour frame buffer device 80x25
[4294672.066000] fb0: VGA16 VGA frame buffer device
[4294673.158000] Capability LSM initialized
[4294673.181000] ACPI: Fan [FAN1] (off)
[4294673.185000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[4294673.185000] ACPI: Processor [CPU0] (supports 8 throttling states)
[4294673.204000] ACPI: Thermal Zone [TZCR] (66 C)
[4294673.208000] ACPI: Thermal Zone [TZCL] (49 C)
[4294673.589000] SCSI subsystem initialized
[4294673.591000] ACPI: bus type scsi registered
[4294673.591000] libata version 1.20 loaded.
[4294673.592000] ahci 0000:00:1f.2: version 1.2
[4294673.592000] **** SET: Misaligned resource pointer: df49ea02 Type 07 Len 0
[4294673.592000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[4294673.592000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[4294673.593000] ACPI: PCI interrupt for device 0000:00:1f.2 disabled
[4294673.593000] ahci: probe of 0000:00:1f.2 failed with error -12
[4294673.594000] ata_piix 0000:00:1f.2: version 1.05
[4294673.594000] ata_pci_init_one: pci_dev class+intf: 0x10180
[4294673.594000] ata_pci_init_one: NO_LEGACY == 0
[4294673.594000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[4294673.594000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[4294673.594000] ata1: PATA max UDMA/133 cmd 0x1F0 ctl 0x3F6 bmdma 0x1100 irq 14
[4294673.748000] ata1: dev 0 cfg 00:045a 49:0f00 82:746b 83:7fe8 84:4023 85:f468 86:3c48 87:4023 88:203f 93:600b
[4294673.748000] ata1: dev 0 ATA-6, max UDMA/100, 156301488 sectors: LBA48
[4294673.748000] ata1(0): applying bridge limits
[4294673.748000] ata_acpi_push_id: skipping for PATA mode
[4294673.748000] ata1: dev 0 configured for UDMA/100
[4294673.748000] pata_get_dev_handle: ENTER: dev->bus_id='0000:00:1f.2'
[4294673.748000] pata_get_dev_handle: dev_handle: 0xdf7c39e0, parent_handle: 0xdf7c9480
[4294673.748000] pata_get_dev_handle: for dev=0x1f.2, addr=0x1f0002, parent=0xdf750800, *handle=0xdf7c39e0
[4294673.748000] do_drive_get_GTF:   drive w/ adr=0: v: 0xdf7c2700
[4294673.749000] scsi0 : ata_piix
[4294673.749000]   Vendor: ATA       Model: IC25N080ATMR04-0  Rev: MO4O
[4294673.749000]   Type:   Direct-Access                      ANSI SCSI revision: 05
[4294673.750000] pata_get_dev_handle: ENTER: dev->bus_id='0000:00:1f.2'
[4294673.750000] pata_get_dev_handle: dev_handle: 0xdf7c39e0, parent_handle: 0xdf7c9480
[4294673.750000] pata_get_dev_handle: for dev=0x1f.2, addr=0x1f0002, parent=0xdf750800, *handle=0xdf7c39e0
[4294673.750000] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x1108 irq 15
[4294674.058000] ata2: dev 0 cfg 00:85c0 49:0f00 82:0000 83:0000 84:0000 85:0000 86:0000 87:0000 88:0407 93:4000
[4294674.058000] ata2: dev 0 ATAPI, max UDMA/33
[4294674.058000] ata2(0): applying bridge limits
[4294674.058000] ata_acpi_push_id: skipping for PATA mode
[4294674.058000] ata2: dev 0 configured for UDMA/33
[4294674.058000] pata_get_dev_handle: ENTER: dev->bus_id='0000:00:1f.2'
[4294674.058000] pata_get_dev_handle: dev_handle: 0xdf7c39e0, parent_handle: 0xdf7c9480
[4294674.058000] pata_get_dev_handle: for dev=0x1f.2, addr=0x1f0002, parent=0xdf750800, *handle=0xdf7c39e0
[4294674.058000] do_drive_get_GTF:   drive w/ adr=0: v: 0xdf7c25c0
[4294674.059000] scsi1 : ata_piix
[4294674.061000]   Vendor: MATSHITA  Model: DVD-RAM UJ-831S   Rev: 1.01
[4294674.061000]   Type:   CD-ROM                             ANSI SCSI revision: 05
[4294674.061000] pata_get_dev_handle: ENTER: dev->bus_id='0000:00:1f.2'
[4294674.061000] pata_get_dev_handle: dev_handle: 0xdf7c39e0, parent_handle: 0xdf7c9480
[4294674.061000] pata_get_dev_handle: for dev=0x1f.2, addr=0x1f0002, parent=0xdf750800, *handle=0xdf7c39e0
[4294674.068000] Driver 'sd' needs updating - please use bus_type methods
[4294674.083000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[4294674.083000] SCSI device sda: drive cache: write back
[4294674.086000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[4294674.086000] SCSI device sda: drive cache: write back
[4294674.086000]  sda: sda1 sda2 sda3 sda4
[4294674.137000] sd 0:0:0:0: Attached scsi disk sda
[4294674.435000] usbcore: registered new driver usbfs
[4294674.435000] usbcore: registered new driver hub
[4294674.436000] USB Universal Host Controller Interface driver v2.3
[4294674.437000] **** SET: Misaligned resource pointer: df49e202 Type 07 Len 0
[4294674.437000] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 10
[4294674.437000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKH] -> GSI 10 (level, low) -> IRQ 10
[4294674.437000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[4294674.437000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[4294674.437000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[4294674.437000] uhci_hcd 0000:00:1d.0: irq 10, io base 0x00001200

```

---

### Post by NiklasV on 2006-08-13
continued..
```

[4294674.438000] hub 1-0:1.0: USB hub found
[4294674.438000] hub 1-0:1.0: 2 ports detected
[4294674.506000] ieee1394: Initialized config rom entry `ip1394'
[4294674.543000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[4294674.543000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[4294674.543000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[4294674.543000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[4294674.543000] uhci_hcd 0000:00:1d.1: irq 11, io base 0x00001220
[4294674.543000] hub 2-0:1.0: USB hub found
[4294674.543000] hub 2-0:1.0: 2 ports detected
[4294674.644000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[4294674.644000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[4294674.644000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[4294674.644000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[4294674.644000] uhci_hcd 0000:00:1d.2: irq 11, io base 0x00001240
[4294674.644000] hub 3-0:1.0: USB hub found
[4294674.644000] hub 3-0:1.0: 2 ports detected
[4294674.745000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[4294674.745000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[4294674.745000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[4294674.745000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[4294674.745000] uhci_hcd 0000:00:1d.3: irq 11, io base 0x00001260
[4294674.745000] hub 4-0:1.0: USB hub found
[4294674.745000] hub 4-0:1.0: 2 ports detected
[4294674.749000] usb 1-2: new low speed USB device using uhci_hcd and address 2
[4294674.847000] PCI: Enabling device 0000:00:1d.7 (0000 -> 0002)
[4294674.847000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> Link [LNKH] -> GSI 10 (level, low) -> IRQ 10
[4294674.847000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[4294674.847000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[4294674.847000] ehci_hcd 0000:00:1d.7: debug port 1
[4294674.847000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[4294674.847000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[4294674.847000] ehci_hcd 0000:00:1d.7: irq 10, io mem 0xf4000000
[4294674.851000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[4294674.852000] hub 5-0:1.0: USB hub found
[4294674.852000] hub 5-0:1.0: 8 ports detected
[4294674.953000] ohci1394: $Rev: 1313 $ Ben Collins <bcollins@debian.org>
[4294674.953000] **** SET: Misaligned resource pointer: de0c51c2 Type 07 Len 0
[4294674.953000] ACPI: PCI Interrupt Link [LNKG] enabled at IRQ 6
[4294674.953000] PCI: setting IRQ 6 as level-triggered
[4294674.953000] ACPI: PCI Interrupt 0000:05:06.2[C] -> Link [LNKG] -> GSI 6 (level, low) -> IRQ 6
[4294675.004000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[6]  MMIO=[b8000000-b80007ff]  Max Packet=[2048]
[4294675.037000] ide0: I/O resource 0x1F0-0x1F7 not free.
[4294675.037000] ide0: ports already in use, skipping probe
[4294675.037000] ide1: I/O resource 0x170-0x177 not free.
[4294675.037000] ide1: ports already in use, skipping probe
[4294675.075000] Attempting manual resume
[4294675.102000] EXT3-fs: mounted filesystem with ordered data mode.
[4294675.103000] kjournald starting.  Commit interval 5 seconds
[4294675.266000] usb 1-2: device not accepting address 2, error -71
[4294675.749000] usb 1-2: new low speed USB device using uhci_hcd and address 4
[4294677.145000] irq 11: nobody cared (try booting with the "irqpoll" option)
[4294677.145000]  [<c013ee42>] __report_bad_irq+0x22/0x80
[4294677.145000]  [<c013ef38>] note_interrupt+0x68/0xc0
[4294677.145000]  [<c013e7fc>] __do_IRQ+0xbc/0xe0
[4294677.145000]  [<c010597a>] do_IRQ+0x1a/0x30
[4294677.145000]  [<c01040ea>] common_interrupt+0x1a/0x20
[4294677.145000]  [<c013e6e5>] handle_IRQ_event+0x15/0x70
[4294677.145000]  [<c013e7b3>] __do_IRQ+0x73/0xe0
[4294677.145000]  [<c010597a>] do_IRQ+0x1a/0x30
[4294677.145000]  [<c01040ea>] common_interrupt+0x1a/0x20
[4294677.145000]  [<e0103148>] set_phy_reg+0x78/0xc0 [ohci1394]
[4294677.145000]  [<e01041db>] ohci_devctl+0x40b/0x5c0 [ohci1394]
[4294677.145000]  [<e019d5e6>] csr1212_fill_cache+0xe6/0x170 [ieee1394]
[4294677.145000]  [<e0193161>] hpsb_reset_bus+0x31/0x40 [ieee1394]
[4294677.145000]  [<e0195608>] delayed_reset_bus+0x98/0xe0 [ieee1394]
[4294677.145000]  [<c012caca>] worker_thread+0x1ba/0x290
[4294677.145000]  [<e0195570>] delayed_reset_bus+0x0/0xe0 [ieee1394]
[4294677.145000]  [<c0118940>] default_wake_function+0x0/0x20
[4294677.145000]  [<c012c910>] worker_thread+0x0/0x290
[4294677.145000]  [<c0130d53>] kthread+0x93/0xa0
[4294677.145000]  [<c0130cc0>] kthread+0x0/0xa0
[4294677.145000]  [<c0101385>] kernel_thread_helper+0x5/0x10
[4294677.145000] handlers:
[4294677.145000] [<e011b330>] (usb_hcd_irq+0x0/0x60 [usbcore])
[4294677.145000] [<e011b330>] (usb_hcd_irq+0x0/0x60 [usbcore])
[4294677.145000] [<e011b330>] (usb_hcd_irq+0x0/0x60 [usbcore])
[4294677.145000] Disabling IRQ #11
[4294677.404000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00080da0d1bb8fef]
[4294684.632000] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[4294684.632000] Uniform CD-ROM driver Revision: 3.20
[4294684.632000] sr 1:0:0:0: Attached scsi CD-ROM sr0
[4294684.637000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[4294684.637000] sr 1:0:0:0: Attached scsi generic sg1 type 5
[4294684.787000] Linux agpgart interface v0.101 (c) Dave Jones
[4294684.805000] agpgart: Detected an Intel 915GM Chipset.
[4294684.805000] agpgart: Detected 7932K stolen memory.
[4294684.823000] agpgart: AGP aperture is 256M @ 0xa0000000
[4294684.905000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294684.910000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[4294685.711000] hw_random: cannot enable RNG, aborting
[4294685.729000] ACPI: PCI Interrupt 0000:00:1e.2[A] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[4294685.729000] PCI: Setting latency timer of device 0000:00:1e.2 to 64
[4294685.833000] Real Time Clock Driver v1.12
[4294686.073000] Synaptics Touchpad, model: 1, fw: 5.9, id: 0xa56eb1, caps: 0x804713/0x0
[4294686.073000] synaptics: Toshiba dynabook VX/470LS detected, limiting rate to 40pps.
[4294686.131000] input: SynPS/2 Synaptics TouchPad as /class/input/input1
[4294686.329000] usbcore: registered new driver hiddev
[4294686.506000] ts: Compaq touchscreen protocol output
[4294686.527000] input: Microsoft Microsoft USB Wireless Mouse as /class/input/input2
[4294686.527000] input: USB HID v1.11 Mouse [Microsoft Microsoft USB Wireless Mouse] on usb-0000:00:1d.0-2
[4294686.527000] usbcore: registered new driver usbhid
[4294686.527000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[4294686.541000] intel8x0_measure_ac97_clock: measured 51406 usecs
[4294686.541000] intel8x0: clocking to 48000
[4294686.551000] ACPI: PCI Interrupt 0000:05:06.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[4294686.551000] Yenta: CardBus bridge found at 0000:05:06.0 [1179:ff10]
[4294686.551000] Yenta: Enabling burst memory read transactions
[4294686.551000] Yenta: Using CSCINT to route CSC interrupts to PCI
[4294686.551000] Yenta: Routing CardBus interrupts to PCI
[4294686.551000] Yenta TI: socket 0000:05:06.0, mfunc 0x01aa1b22, devctl 0x66
[4294686.593000] sdhci: Secure Digital Host Controller Interface driver, 0.10
[4294686.593000] sdhci: Copyright(c) Pierre Ossman
[4294686.595000] ieee80211_1_1_13_crypt: registered algorithm 'NULL'
[4294686.597000] ieee80211_1_1_13: 802.11 data/management/control stack, 1.1.13
[4294686.597000] ieee80211_1_1_13: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[4294686.652000] Yenta TI: socket 0000:05:06.0 probing PCI interrupt failed, trying to fix
[4294686.652000] Yenta TI: socket 0000:05:06.0 falling back to parallel PCI interrupts
[4294686.679000] ieee80211_crypt: registered algorithm 'NULL'
[4294686.681000] ieee80211: 802.11 data/management/control stack, git-1.1.7
[4294686.681000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[4294686.745000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.1.1
[4294686.745000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[4294686.745000] Warning: PCI driver ipw2200 has a struct device_driver shutdown method, please update!
[4294686.745000] ACPI: PCI Interrupt 0000:05:04.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[4294686.745000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[4294686.753000] Yenta TI: socket 0000:05:06.0 no PCI interrupts. Fish. Please report.
[4294686.753000] Yenta: no PCI IRQ, CardBus support disabled for this socket.
[4294686.753000] Yenta: check your BIOS CardBus, BIOS IRQ or ACPI settings.
[4294686.875000] Yenta: ISA IRQ mask 0x0098, PCI irq 0
[4294686.875000] Socket status: 30000006
[4294686.875000] Yenta: Raising subordinate bus# of parent bus (#05) from #05 to #09
[4294686.875000] pcmcia: parent PCI bridge I/O window: 0x8000 - 0x9fff
[4294686.875000] cs: IO port probe 0x8000-0x9fff: clean.
[4294686.875000] pcmcia: parent PCI bridge Memory window: 0xb8000000 - 0xc7ffffff
[4294686.875000] pcmcia: parent PCI bridge Memory window: 0x88000000 - 0x97ffffff
[4294686.882000] ACPI: PCI Interrupt 0000:05:06.4[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[4294686.932000] sdhci: ============== REGISTER DUMP ==============
[4294686.932000] sdhci: Sys addr: 0x00000000 | Version:  0x00008400
[4294686.932000] sdhci: Blk size: 0x00000000 | Blk cnt:  0x00000000
[4294686.932000] sdhci: Argument: 0x00000000 | Trn mode: 0x00000000
[4294686.932000] sdhci: Present:  0x00020000 | Host ctl: 0x00000000
[4294686.932000] sdhci: Power:    0x00000000 | Blk gap:  0x00000000
[4294686.932000] sdhci: Walk up:  0x00000000 | Clock:    0x00000002
[4294686.932000] sdhci: Timeout:  0x0000000e | Int stat: 0x00000000
[4294686.932000] sdhci: Int enab: 0x11ff00cf | Sig enab: 0x11ff00cf
[4294686.932000] sdhci: AC12 err: 0x00000000 | Slot int: 0x00000000
[4294686.932000] sdhci: Caps:     0x01821090 | Max curr: 0x00000000
[4294686.932000] sdhci: ===========================================
[4294686.982000] mmc0: SDHCI at 0xb800a000 irq 11 DMA
[4294687.081000] sdhci: ============== REGISTER DUMP ==============
[4294687.081000] sdhci: Sys addr: 0x00000000 | Version:  0x00008400
[4294687.081000] sdhci: Blk size: 0x00000000 | Blk cnt:  0x00000000
[4294687.081000] sdhci: Argument: 0x00000000 | Trn mode: 0x00000000
[4294687.081000] sdhci: Present:  0x00020000 | Host ctl: 0x00000000
[4294687.081000] sdhci: Power:    0x00000000 | Blk gap:  0x00000000
[4294687.081000] sdhci: Walk up:  0x00000000 | Clock:    0x00000002
[4294687.081000] sdhci: Timeout:  0x0000000e | Int stat: 0x00000000
[4294687.081000] sdhci: Int enab: 0x11ff00cf | Sig enab: 0x11ff00cf
[4294687.081000] sdhci: AC12 err: 0x00000000 | Slot int: 0x00000000
[4294687.081000] sdhci: Caps:     0x01821090 | Max curr: 0x00000000
[4294687.081000] sdhci: ===========================================
[4294687.132000] mmc1: SDHCI at 0xb800a100 irq 11 DMA
[4294687.232000] sdhci: ============== REGISTER DUMP ==============
[4294687.232000] sdhci: Sys addr: 0x00000000 | Version:  0x00008400
[4294687.232000] sdhci: Blk size: 0x00000000 | Blk cnt:  0x00000000
[4294687.232000] sdhci: Argument: 0x00000000 | Trn mode: 0x00000000
[4294687.232000] sdhci: Present:  0x000a0000 | Host ctl: 0x00000000
[4294687.232000] sdhci: Power:    0x00000000 | Blk gap:  0x00000000
[4294687.232000] sdhci: Walk up:  0x00000000 | Clock:    0x00000002
[4294687.232000] sdhci: Timeout:  0x0000000e | Int stat: 0x00000000
[4294687.232000] sdhci: Int enab: 0x11ff00cf | Sig enab: 0x11ff00cf
[4294687.232000] sdhci: AC12 err: 0x00000000 | Slot int: 0x00000000
[4294687.232000] sdhci: Caps:     0x01821898 | Max curr: 0x00000000
[4294687.232000] sdhci: ===========================================
[4294687.283000] mmc2: SDHCI at 0xb800a200 irq 11 DMA
[4294687.887000] cs: IO port probe 0x100-0x3af: excluding 0x300-0x307 0x310-0x31f 0x370-0x377
[4294687.889000] cs: IO port probe 0x3e0-0x4ff: excluding 0x3f0-0x3f7 0x4d0-0x4d7
[4294687.890000] cs: IO port probe 0x820-0x8ff: clean.
[4294687.890000] cs: IO port probe 0xc00-0xcf7: clean.
[4294687.891000] cs: IO port probe 0xa00-0xaff: clean.
[4294688.467000] ipw2200: Failed to send TX_POWER: Command timed out.
[4294689.594000] ipw2200: Failed to send TX_POWER: Command timed out.
[4294690.721000] ipw2200: Failed to send TX_POWER: Command timed out.
[4294691.848000] ipw2200: Failed to send TX_POWER: Command timed out.
[4294692.974000] ipw2200: Failed to send TX_POWER: Command timed out.
[4294692.979000] ipw2200: Unable to initialize device after 5 attempts.
[4294692.985000] ipw2200: failed to register network device
[4294692.991000] ACPI: PCI interrupt for device 0000:05:04.0 disabled
[4294692.991000] ipw2200: probe of 0000:05:04.0 failed with error -5
[4294693.131000] lp: driver loaded but no devices found
[4294693.162000] sbp2: $Rev: 1306 $ Ben Collins <bcollins@debian.org>
[4294693.162000] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[4294693.162000] ieee1394: sbp2: Try serialize_io=0 for better performance
[4294693.200000] Adding 979956k swap on /dev/sda3.  Priority:-1 extents:1 across:979956k
[4294693.248000] EXT3 FS on sda2, internal journal
[4294693.429000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294693.429000] md: bitmap version 4.39
[4294693.892000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[4294694.390000] cdrom: open failed.
[4294706.361000] kjournald starting.  Commit interval 5 seconds
[4294706.361000] EXT3 FS on sda4, internal journal
[4294706.361000] EXT3-fs: mounted filesystem with ordered data mode.
[4294707.764000] ACPI: AC Adapter [AC] (on-line)
[4294707.781000] ACPI: Battery Slot [BAT1] (battery present)
[4294707.846000] ACPI: Power Button (FF) [PWRF]
[4294707.846000] ACPI: Lid Switch [LID0]
[4294707.846000] ACPI: Power Button (CM) [PWRB]
[4294707.937000] ibm_acpi: ec object not found
[4294707.956000] pcc_acpi: loading...
[4294708.027000] ACPI: Video Device [GFX0] (multi-head: yes  rom: yes  post: no)
[4294708.380000] acpi-cpufreq: CPU0 - ACPI performance management activated.
[4294711.766000] [drm] Initialized drm 1.0.1 20051102
[4294711.769000] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[4294711.769000] [drm] Initialized i915 1.4.0 20060119 on minor 0
[4294713.852000] ppdev: user-space parallel port driver
[4294714.086000] apm: BIOS not found.
[4294716.991000] Bluetooth: Core ver 2.8
[4294716.991000] NET: Registered protocol family 31
[4294716.991000] Bluetooth: HCI device and connection manager initialized
[4294716.991000] Bluetooth: HCI socket layer initialized
[4294717.133000] Bluetooth: L2CAP ver 2.8
[4294717.133000] Bluetooth: L2CAP socket layer initialized
[4294717.142000] Bluetooth: RFCOMM socket layer initialized
[4294717.142000] Bluetooth: RFCOMM TTY layer initialized
[4294717.142000] Bluetooth: RFCOMM ver 1.7
[4294741.750000] NET: Registered protocol family 10
[4294741.750000] lo: Disabled Privacy Extensions
[4294741.750000] IPv6 over IPv4 tunneling driver

```

---

### Post by NiklasV on 2006-08-13
Nevermind, I added the boot options lapic and irqpoll, and now it works.

---

