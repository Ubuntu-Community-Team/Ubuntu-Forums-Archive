---
title: "Dlink DWL-G650 card freezes computer"
date: 2007-05-31
forum: Networking &amp; Wireless
---

### Post by xzero1 on 2007-05-31
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.15/+bug/37773](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.15/+bug/37773) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				This card is listed under supported cards. There are no freezing problems without the card. I have posted the relevant dmesg output. I am running Ubuntu generic Feisty Fawn.

[    0.000000] Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Wed May 23 01:46:23 UTC 2007 (Ubuntu 2.6.20-16.28-generic)
... skipped to relevant lines

[   26.540000] pccard: PCMCIA card inserted into slot 0
[   26.668000] pccard: CardBus card inserted into slot 1
[   26.960000] ath_hal: module license 'Proprietary' taints kernel.
[   26.964000] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   27.104000] wlan: 0.8.4.2 (0.9.3)
[   27.148000] ath_pci: 0.9.4.5 (0.9.3)
[   27.508000] cs: IO port probe 0x100-0x3af: excluding 0x1e0-0x1e7 0x200-0x207 0x220-0x22f 0x330-0x33f 0x388-0x38f
[   27.512000] cs: IO port probe 0x3e0-0x4ff: excluding 0x408-0x40f 0x480-0x48f 0x4d0-0x4d7
[   27.512000] cs: IO port probe 0x820-0x8ff: clean.
[   27.512000] cs: IO port probe 0xc00-0xcf7: clean.
[   27.516000] cs: IO port probe 0xa00-0xaff: clean.
[   27.520000] cs: IO port probe 0x100-0x3af: excluding 0x1e0-0x1e7 0x200-0x207 0x220-0x22f 0x330-0x33f 0x388-0x38f
[   27.524000] cs: IO port probe 0x3e0-0x4ff: excluding 0x408-0x40f 0x480-0x48f 0x4d0-0x4d7
[   27.524000] cs: IO port probe 0x820-0x8ff: clean.
[   27.524000] cs: IO port probe 0xc00-0xcf7: clean.
[   27.528000] cs: IO port probe 0xa00-0xaff: clean.
[   27.528000] cs: memory probe 0xa0000000-0xa0ffffff: clean.
[   27.536000] pcmcia: registering new device pcmcia0.0
[   27.540000] cs: IO port probe 0x100-0x3af: excluding 0x1e0-0x1e7 0x200-0x207 0x220-0x22f 0x330-0x33f 0x388-0x38f
[   27.620000] cs: IO port probe 0x3e0-0x4ff: excluding 0x408-0x40f 0x480-0x48f 0x4d0-0x4d7
[   27.624000] cs: IO port probe 0x820-0x8ff: clean.
[   27.624000] cs: IO port probe 0xc00-0xcf7: clean.
[   27.624000] cs: IO port probe 0xa00-0xaff: clean.
[   27.676000] orinoco 0.15 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
[   27.684000] orinoco_cs 0.15 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
[   27.684000] pcmcia: request for exclusive IRQ could not be fulfilled.
[   27.684000] pcmcia: the driver needs updating to supported shared IRQ lines.
[   27.772000] eth1: Hardware identity 0005:0004:0005:0000
[   27.772000] eth1: Station identity  001f:0001:0008:000a
[   27.772000] eth1: Firmware determined as Lucent/Agere 8.10
[   27.772000] eth1: Ad-hoc demo mode supported
[   27.772000] eth1: IEEE standard IBSS ad-hoc mode supported
[   27.772000] eth1: WEP supported, 104-bit key
[   27.772000] eth1: MAC address 00:02:2D:6F:38:12
[   27.772000] eth1: Station name "HERMES I"
[   27.772000] eth1: ready
[   27.776000] eth1: orinoco_cs at 0.0, irq 11, io 0x0100-0x013f
[   28.728000] PCI: Enabling device 0000:06:00.0 (0000 -> 0002)
[   28.728000] ACPI: PCI Interrupt 0000:06:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   29.028000] ath_rate_sample: 1.2 (0.9.3)
[   29.028000] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[   29.028000] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   29.028000] wifi0: turboG rates: 6Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   29.028000] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
[   29.028000] wifi0: mac 5.6 phy 4.1 radio 4.6
[   29.028000] wifi0: Use hw queue 1 for WME_AC_BE traffic
[   29.028000] wifi0: Use hw queue 0 for WME_AC_BK traffic
[   29.028000] wifi0: Use hw queue 2 for WME_AC_VI traffic
[   29.028000] wifi0: Use hw queue 3 for WME_AC_VO traffic
[   29.028000] wifi0: Use hw queue 8 for CAB traffic
[   29.028000] wifi0: Use hw queue 9 for beacons
[   29.096000] wifi0: Atheros 5212: mem=0x3c000000, irq=11
[   29.344000] lp: driver loaded but no devices found
[   29.400000] Adding 465844k swap on /dev/disk/by-uuid/bd5ad238-8276-46b8-b1d4-231cea35dc6f.  Priority:-1 extents:1 across:465844k
[   29.592000] EXT3 FS on hda2, internal journal
[   29.736000] NET: Registered protocol family 10
[   29.736000] lo: Disabled Privacy Extensions
[   29.964000] NTFS driver 2.1.28 [Flags: R/O MODULE].
[   30.040000] NTFS volume version 3.1.
[   31.956000] No dock devices found.
[   32.132000] input: Power Button (FF) as /class/input/input5
[   32.140000] ACPI: Power Button (FF) [PWRF]
[   32.204000] input: Power Button (CM) as /class/input/input6
[   32.216000] ACPI: Power Button (CM) [PWRB]
[   32.276000] input: Lid Switch as /class/input/input7
[   32.284000] ACPI: Lid Switch [LID]
[   32.360000] Using specific hotkey driver
[   32.416000] ACPI: Video Device [VGA] (multi-head: yes  rom: yes  post: no)
[   32.472000] ACPI: AC Adapter [ADP1] (on-line)
[   32.512000] toshiba_acpi: Toshiba Laptop ACPI Extras version 0.19a-dev
[   32.512000] toshiba_acpi:     HCI method: \_SB_.VALD.GHCI
[   32.520000] toshiba_acpi: Toshiba hotkeys are sent as ACPI events
[   32.520000] toshiba_acpi: ktoshkeyd will check 2 times per second
[   32.524000] toshiba_acpi: Dropped 0 keys from the queue on startup
[   32.556000] ibm_acpi: ec object not found
[   32.608000] ACPI: Battery Slot [BAT1] (battery present)
[   32.684000] pcc_acpi: loading...
[   37.868000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   37.940000] eth1: New link status: Disconnected (0002)
[   38.860000] ppdev: user-space parallel port driver
[   40.864000] apm: BIOS not found.
[   41.084000] Bluetooth: Core ver 2.11
[   41.084000] NET: Registered protocol family 31
[   41.084000] Bluetooth: HCI device and connection manager initialized
[   41.084000] Bluetooth: HCI socket layer initialized
[   41.104000] Bluetooth: L2CAP ver 2.8
[   41.104000] Bluetooth: L2CAP socket layer initialized
[   41.288000] Bluetooth: RFCOMM socket layer initialized
[   41.288000] Bluetooth: RFCOMM TTY layer initialized
[   41.288000] Bluetooth: RFCOMM ver 1.8
[   45.180000] wifi0: hardware error; resetting
[   46.152000] wifi0: hardware error; resetting
[   46.816000] wifi0: hardware error; resetting
[   49.480000] wifi0: hardware error; resetting
[   50.524000] wifi0: hardware error; resetting
[   51.116000] wifi0: hardware error; resetting
[   53.780000] wifi0: hardware error; resetting
[   64.280000] BUG: soft lockup detected on CPU#0!
[   64.280000]  [<c015354c>] softlockup_tick+0x9c/0xf0
[   64.280000]  [<c0130643>] update_process_times+0x33/0x80
[   64.280000]  [<c0106c45>] timer_interrupt+0x85/0xb0
[   64.280000]  [<c01538d0>] handle_IRQ_event+0x30/0x60
[   64.280000]  [<c015517d>] handle_level_irq+0x8d/0x120
[   64.280000]  [<c0105b70>] do_IRQ+0x40/0x80
[   64.280000]  [<c0104233>] common_interrupt+0x23/0x30
[   64.280000]  [<df863748>] e100_intr+0x28/0xc0 [e100]
[   64.280000]  [<c01538d0>] handle_IRQ_event+0x30/0x60
[   64.280000]  [<c015517d>] handle_level_irq+0x8d/0x120
[   64.280000]  [<c0105b70>] do_IRQ+0x40/0x80
[   64.280000]  [<c0104233>] common_interrupt+0x23/0x30
[   64.280000]  [<c012b3fb>] __do_softirq+0x5b/0x100
[   64.280000]  [<c012b4f5>] do_softirq+0x55/0x60
[   64.280000]  [<c0105b75>] do_IRQ+0x45/0x80
[   64.280000]  [<c0219e3e>] acpi_hw_register_write+0x154/0x187
[   64.280000]  [<c0104233>] common_interrupt+0x23/0x30
[   64.280000]  [<df82f7e2>] acpi_processor_idle+0x225/0x3f7 [processor]
[   64.280000]  [<c0101409>] cpu_idle+0x49/0xd0
[   64.280000]  [<c03d97f5>] start_kernel+0x365/0x420
[   64.280000]  [<c03d9230>] unknown_bootoption+0x0/0x260
[   64.280000]  =======================
[  194.436000] wifi0: rx FIFO overrun; resetting
[  194.440000] SysRq : Show Memory
[  194.440000] Mem-info:
[  194.440000] DMA per-cpu:
[  194.440000] CPU    0: Hot: hi:    0, btch:   1 usd:   0   Cold: hi:    0, btch:   1 usd:   0
[  194.440000] Normal per-cpu:
[  194.440000] CPU    0: Hot: hi:  186, btch:  31 usd: 150   Cold: hi:   62, btch:  15 usd:   5
[  194.440000] Active:16753 inactive:25079 dirty:455 writeback:0 unstable:0 free:78635 slab:2891 mapped:3534 pagetables:146
[  194.440000] DMA free:12684kB min:88kB low:108kB high:132kB active:0kB inactive:0kB present:16256kB pages_scanned:0 all_unreclaimable? no
[  194.440000] lowmem_reserve[]: 0 476 476
[  194.440000] Normal free:301856kB min:2744kB low:3428kB high:4116kB active:67012kB inactive:100316kB present:487620kB pages_scanned:0 all_unreclaimable? no
[  194.440000] lowmem_reserve[]: 0 0 0
[  194.440000] DMA: 3*4kB 6*8kB 1*16kB 4*32kB 3*64kB 4*128kB 2*256kB 0*512kB 1*1024kB 1*2048kB 2*4096kB = 12684kB
[  194.440000] Normal: 12*4kB 10*8kB 6*16kB 2*32kB 0*64kB 0*128kB 0*256kB 1*512kB 0*1024kB 1*2048kB 73*4096kB = 301856kB
[  194.440000] Swap cache: add 0, delete 0, find 0/0, race 0+0
[  194.440000] Free swap  = 465844kB
[  194.440000] Total swap = 465844kB
[  194.440000] Free swap:       465844kB
[  194.440000] 126960 pages of RAM
[  194.440000] 0 pages of HIGHMEM
[  194.440000] 2046 reserved pages
[  194.440000] 12379 pages shared
[  194.440000] 0 pages swap cached
[  194.440000] 455 pages dirty
[  194.440000] 0 pages writeback
[  194.440000] 3534 pages mapped
[  194.440000] 2891 pages slab
[  194.440000] 146 pages pagetables
[  194.456000] wifi0: ath_reset: unable to reset hardware: 'Hardware didn't respond as expected' (HAL status 3)
[  194.456000] wifi0: hardware error; resetting
-------------------------------------------------------------------

Notes:
The log continues and I have it if needed. I have not installed any other drivers.
Rarely, I regain control but the freezes continue until the card is removed. It is not clear if this is the same bug as reported in the link above. Is this more general than just a Dapper bug? Thanks for any help.

---

