---
title: "No sound in hp pavilion dv4 series"
date: 2009-10-13
forum: New to Ubuntu
---

### Post by lapputappu on 2009-10-13
HI i m a new user for ubuntu. My frnd first tym made me introduced with the graphics of ubuntu and i became quite interested in it ,so i ordered a new pack of UBUNTU 9.04 ,ND MADE A FRESH INSTALL. After installation AND  downloading the all packages i used the graphics it was really very appreciable but wen i played the sound it was ZERO. I went through the COMPREHENSIVE SOUND PROBLEM SOLUTIONS GUIDE but i got the following error.................................. I m using HP PAVILIO



HI I jst installed ubuntu 9.04 over vista home premium .after installation wen it finished downloading the packages , i tried to play a song .Video was running very nicely but with no audio output .I checked for the ALSA DRIVER as per the instructions in COMPREHENSIVE SOUND PROBLEM SOLUTIONS GUIDE .
STEP 1:- aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

STEP 2:- lspci -v

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
    Subsystem: Hewlett-Packard Company Device 30f7
    Flags: bus master, fast devsel, latency 0, IRQ 22
    Memory at df300000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

after this i went through the alternatives steps described there means uninstalling and reinstalling with compiling the alsamixer .After this process wen i returned bck to the 

step 4:- sudo modprobe snd-hda-intel              I GOT DIS AS  d error msg 
 

WARNING: Error inserting snd_page_alloc (/lib/modules/2.6.28-15-generic/updates/alsa/acore/snd-page-alloc.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_timer (/lib/modules/2.6.28-15-generic/updates/alsa/acore/snd-timer.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_pcm (/lib/modules/2.6.28-15-generic/updates/alsa/acore/snd-pcm.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_hda_intel (/lib/modules/2.6.28-15-generic/updates/alsa/pci/hda/snd-hda-intel.ko): Unknown symbol in module, or unknown parameter (see dmesg)

  AND still no sound output 

plz sort dis problem i m just fed up with dis problem after installing ubuntu 9.04 .




but after rebooting again i typed 
sudo modprobe snd-hda-intel 
and d o/p was 

rajeev@rajeev-laptop:~$ sudo modprobe snd-hda-intel
rajeev@rajeev-laptop:~$ 
 means dere was no output .........
after going through some more pages i did dis one , typed dmesg and output was


[    1.005404] pci 0000:00:1c.2:   IO window: 0x5000-0x5fff
[    1.005410] pci 0000:00:1c.2:   MEM window: 0xdc200000-0xdd2fffff
[    1.005415] pci 0000:00:1c.2:   PREFETCH window: 0x000000d5000000-0x000000d5ffffff
[    1.005424] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:05
[    1.005427] pci 0000:00:1c.3:   IO window: 0x3000-0x4fff
[    1.005433] pci 0000:00:1c.3:   MEM window: 0xdb200000-0xdc1fffff
[    1.005438] pci 0000:00:1c.3:   PREFETCH window: 0x000000d6000000-0x000000d70fffff
[    1.005447] pci 0000:00:1c.4: PCI bridge, secondary bus 0000:06
[    1.005450] pci 0000:00:1c.4:   IO window: 0x2000-0x2fff
[    1.005457] pci 0000:00:1c.4:   MEM window: 0xda100000-0xdb1fffff
[    1.005462] pci 0000:00:1c.4:   PREFETCH window: 0x000000d7100000-0x000000d80fffff
[    1.005470] pci 0000:00:1c.5: PCI bridge, secondary bus 0000:07
[    1.005474] pci 0000:00:1c.5:   IO window: 0x1000-0x1fff
[    1.005480] pci 0000:00:1c.5:   MEM window: 0xd9100000-0xda0fffff
[    1.005485] pci 0000:00:1c.5:   PREFETCH window: 0x000000d8100000-0x000000d90fffff
[    1.005493] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:0a
[    1.005495] pci 0000:00:1e.0:   IO window: disabled
[    1.005502] pci 0000:00:1e.0:   MEM window: disabled
[    1.005506] pci 0000:00:1e.0:   PREFETCH window: disabled
[    1.005521] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.005525] pci 0000:00:01.0: setting latency timer to 64
[    1.005533] pci 0000:00:1c.0: enabling device (0000 -> 0003)
[    1.005537] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.005543] pci 0000:00:1c.0: setting latency timer to 64
[    1.005552] pci 0000:00:1c.1: enabling device (0000 -> 0003)
[    1.005556] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.005562] pci 0000:00:1c.1: setting latency timer to 64
[    1.005572] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.005577] pci 0000:00:1c.2: setting latency timer to 64
[    1.005586] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    1.005590] pci 0000:00:1c.3: setting latency timer to 64
[    1.005599] pci 0000:00:1c.4: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.005604] pci 0000:00:1c.4: setting latency timer to 64
[    1.005612] pci 0000:00:1c.5: enabling device (0000 -> 0003)
[    1.005616] pci 0000:00:1c.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.005622] pci 0000:00:1c.5: setting latency timer to 64
[    1.005630] pci 0000:00:1e.0: setting latency timer to 64
[    1.005634] bus: 00 index 0 io port: [0x00-0xffff]
[    1.005637] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    1.005639] bus: 01 index 0 io port: [0x8000-0x8fff]
[    1.005641] bus: 01 index 1 mmio: [0xd0000000-0xd2ffffff]
[    1.005643] bus: 01 index 2 mmio: [0xc0000000-0xcfffffff]
[    1.005645] bus: 01 index 3 mmio: [0x0-0x0]
[    1.005647] bus: 02 index 0 io port: [0x7000-0x7fff]
[    1.005649] bus: 02 index 1 mmio: [0xde300000-0xdf2fffff]
[    1.005651] bus: 02 index 2 mmio: [0xd3000000-0xd3ffffff]
[    1.005653] bus: 02 index 3 mmio: [0x0-0x0]
[    1.005655] bus: 03 index 0 io port: [0x6000-0x6fff]
[    1.005657] bus: 03 index 1 mmio: [0xdd300000-0xde2fffff]
[    1.005659] bus: 03 index 2 mmio: [0xd4000000-0xd4ffffff]
[    1.005661] bus: 03 index 3 mmio: [0x0-0x0]
[    1.005663] bus: 04 index 0 io port: [0x5000-0x5fff]
[    1.005665] bus: 04 index 1 mmio: [0xdc200000-0xdd2fffff]
[    1.005667] bus: 04 index 2 mmio: [0xd5000000-0xd5ffffff]
[    1.005669] bus: 04 index 3 mmio: [0x0-0x0]
[    1.005671] bus: 05 index 0 io port: [0x3000-0x4fff]
[    1.005673] bus: 05 index 1 mmio: [0xdb200000-0xdc1fffff]
[    1.005675] bus: 05 index 2 mmio: [0xd6000000-0xd70fffff]
[    1.005677] bus: 05 index 3 mmio: [0x0-0x0]
[    1.005679] bus: 06 index 0 io port: [0x2000-0x2fff]
[    1.005681] bus: 06 index 1 mmio: [0xda100000-0xdb1fffff]
[    1.005683] bus: 06 index 2 mmio: [0xd7100000-0xd80fffff]
[    1.005685] bus: 06 index 3 mmio: [0x0-0x0]
[    1.005687] bus: 07 index 0 io port: [0x1000-0x1fff]
[    1.005689] bus: 07 index 1 mmio: [0xd9100000-0xda0fffff]
[    1.005691] bus: 07 index 2 mmio: [0xd8100000-0xd90fffff]
[    1.005693] bus: 07 index 3 mmio: [0x0-0x0]
[    1.005695] bus: 0a index 0 mmio: [0x0-0x0]
[    1.005697] bus: 0a index 1 mmio: [0x0-0x0]
[    1.005698] bus: 0a index 2 mmio: [0x0-0x0]
[    1.005700] bus: 0a index 3 io port: [0x00-0xffff]
[    1.005702] bus: 0a index 4 mmio: [0x000000-0xffffffff]
[    1.005710] NET: Registered protocol family 2
[    1.020053] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    1.020285] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    1.020618] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    1.020798] TCP: Hash tables configured (established 131072 bind 65536)
[    1.020800] TCP reno registered
[    1.028077] NET: Registered protocol family 1
[    1.028189] checking if image is initramfs... it is
[    1.630291] Freeing initrd memory: 7377k freed
[    1.630327] Simple Boot Flag value 0x5 read from CMOS RAM was invalid
[    1.630330] Simple Boot Flag at 0x44 set to 0x1
[    1.630492] cpufreq: No nForce2 chipset.
[    1.630618] audit: initializing netlink socket (disabled)
[    1.630634] type=2000 audit(1253885273.628:1): initialized
[    1.637741] highmem bounce pool size: 64 pages
[    1.637746] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.639037] VFS: Disk quotas dquot_6.5.1
[    1.639096] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.639685] fuse init (API version 7.10)
[    1.639762] msgmni has been set to 1671
[    1.639927] alg: No test for stdrng (krng)
[    1.639936] io scheduler noop registered
[    1.639938] io scheduler anticipatory registered
[    1.639940] io scheduler deadline registered
[    1.639953] io scheduler cfq registered (default)
[    9.640007] pci 0000:00:1a.7: EHCI: BIOS handoff failed (BIOS bug?) 01010001
[   17.640007] pci 0000:00:1d.7: EHCI: BIOS handoff failed (BIOS bug?) 01010001
[   17.640151] pci 0000:01:00.0: Boot video device
[   17.877433] pcieport-driver 0000:00:01.0: setting latency timer to 64
[   17.877472] pcieport-driver 0000:00:01.0: found MSI capability
[   17.877497] pcieport-driver 0000:00:01.0: irq 2303 for MSI/MSI-X
[   17.877507] pci_express 0000:00:01.0cie00: allocate port service
[   17.877520] pci_express 0000:00:01.0cie02: allocate port service
[   17.877532] pci_express 0000:00:01.0cie03: allocate port service
[   17.877585] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[   17.877636] pcieport-driver 0000:00:1c.0: found MSI capability
[   17.877671] pcieport-driver 0000:00:1c.0: irq 2302 for MSI/MSI-X
[   17.877687] pci_express 0000:00:1c.0cie00: allocate port service
[   17.877699] pci_express 0000:00:1c.0cie02: allocate port service
[   17.877710] pci_express 0000:00:1c.0cie03: allocate port service
[   17.877786] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[   17.877837] pcieport-driver 0000:00:1c.1: found MSI capability
[   17.877871] pcieport-driver 0000:00:1c.1: irq 2301 for MSI/MSI-X
[   17.877888] pci_express 0000:00:1c.1cie00: allocate port service
[   17.877901] pci_express 0000:00:1c.1cie02: allocate port service
[   17.877913] pci_express 0000:00:1c.1cie03: allocate port service
[   17.877988] pcieport-driver 0000:00:1c.2: setting latency timer to 64
[   17.878040] pcieport-driver 0000:00:1c.2: found MSI capability
[   17.878074] pcieport-driver 0000:00:1c.2: irq 2300 for MSI/MSI-X
[   17.878090] pci_express 0000:00:1c.2cie00: allocate port service
[   17.878107] pci_express 0000:00:1c.2cie02: allocate port service
[   17.878119] pci_express 0000:00:1c.2cie03: allocate port service
[   17.878195] pcieport-driver 0000:00:1c.3: setting latency timer to 64
[   17.878246] pcieport-driver 0000:00:1c.3: found MSI capability
[   17.878281] pcieport-driver 0000:00:1c.3: irq 2299 for MSI/MSI-X
[   17.878297] pci_express 0000:00:1c.3cie00: allocate port service
[   17.878309] pci_express 0000:00:1c.3cie02: allocate port service
[   17.878321] pci_express 0000:00:1c.3cie03: allocate port service
[   17.878396] pcieport-driver 0000:00:1c.4: setting latency timer to 64
[   17.878447] pcieport-driver 0000:00:1c.4: found MSI capability
[   17.878482] pcieport-driver 0000:00:1c.4: irq 2298 for MSI/MSI-X
[   17.878498] pci_express 0000:00:1c.4cie00: allocate port service
[   17.878510] pci_express 0000:00:1c.4cie02: allocate port service
[   17.878522] pci_express 0000:00:1c.4cie03: allocate port service
[   17.878598] pcieport-driver 0000:00:1c.5: setting latency timer to 64
[   17.878650] pcieport-driver 0000:00:1c.5: found MSI capability
[   17.878684] pcieport-driver 0000:00:1c.5: irq 2297 for MSI/MSI-X
[   17.878701] pci_express 0000:00:1c.5cie00: allocate port service
[   17.878713] pci_express 0000:00:1c.5cie02: allocate port service
[   17.878725] pci_express 0000:00:1c.5cie03: allocate port service
[   17.878809] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   17.879106] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[   18.008088] ACPI: AC Adapter [AC] (off-line)
[   18.233505] ACPI: Battery Slot [BAT0] (battery present)
[   18.233584] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[   18.233587] ACPI: Power Button (FF) [PWRF]
[   18.233629] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[   18.233632] ACPI: Power Button (CM) [PWRB]
[   18.233673] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input2
[   18.233751] ACPI: Lid Switch [LID0]
[   18.233794] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input3
[   18.233804] ACPI: Sleep Button (CM) [SLPB]
[   18.249799] fan PNP0C0B:00: registered as cooling_device0
[   18.249804] ACPI: Fan [FAN] (off)
[   18.250586] ACPI: SSDT BFC77C18, 0265 (r1  PmRef  Cpu0Ist     3000 INTL 20060912)
[   18.251139] ACPI: SSDT BFC75618, 0594 (r1  PmRef  Cpu0Cst     3001 INTL 20060912)
[   18.251752] Monitor-Mwait will be used to enter C-1 state
[   18.251755] Monitor-Mwait will be used to enter C-2 state
[   18.251758] Monitor-Mwait will be used to enter C-3 state
[   18.251771] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   18.251790] processor ACPI_CPU:00: registered as cooling_device1
[   18.251794] ACPI: Processor [CPU0] (supports 8 throttling states)
[   18.252283] ACPI: SSDT BFC76E18, 01CF (r1  PmRef    ApIst     3000 INTL 20060912)
[   18.252854] ACPI: SSDT BFC77F18, 008D (r1  PmRef    ApCst     3000 INTL 20060912)
[   18.253559] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[   18.253577] processor ACPI_CPU:01: registered as cooling_device2
[   18.253581] ACPI: Processor [CPU1] (supports 8 throttling states)
[   18.384665] thermal LNXTHERM:01: registered as thermal_zone0
[   18.441261] ACPI: Thermal Zone [THRM] (53 C)
[   18.441318] isapnp: Scanning for PnP cards...
[   18.797096] isapnp: No Plug & Play device found
[   18.808739] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[   18.809758] brd: module loaded
[   18.810062] loop: module loaded
[   18.810123] Fixed MDIO Bus: probed
[   18.810128] PPP generic driver version 2.4.2
[   18.810182] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[   18.810209] Driver 'sd' needs updating - please use bus_type methods
[   18.810218] Driver 'sr' needs updating - please use bus_type methods
[   18.810255] ahci 0000:00:1f.2: version 3.0
[   18.810270] ahci 0000:00:1f.2: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[   18.810308] ahci 0000:00:1f.2: irq 2296 for MSI/MSI-X
[   18.810398] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 4 ports 3 Gbps 0x33 impl SATA mode
[   18.810401] ahci 0000:00:1f.2: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part ems 
[   18.810407] ahci 0000:00:1f.2: setting latency timer to 64
[   18.810678] scsi0 : ahci
[   18.810760] scsi1 : ahci
[   18.810812] scsi2 : ahci
[   18.810863] scsi3 : ahci
[   18.810917] scsi4 : ahci
[   18.810967] scsi5 : ahci
[   18.811140] ata1: SATA max UDMA/133 abar m2048@0xdf304000 port 0xdf304100 irq 2296
[   18.811144] ata2: SATA max UDMA/133 abar m2048@0xdf304000 port 0xdf304180 irq 2296
[   18.811146] ata3: DUMMY
[   18.811147] ata4: DUMMY
[   18.811150] ata5: SATA max UDMA/133 abar m2048@0xdf304000 port 0xdf304300 irq 2296
[   18.811153] ata6: SATA max UDMA/133 abar m2048@0xdf304000 port 0xdf304380 irq 2296
[   19.292016] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   19.292904] ata1.00: ACPI cmd 00/00:00:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[   19.293001] ata1.00: ACPI cmd ef/10:01:00:00:00:a0 succeeded
[   19.293093] ata1.00: ACPI cmd ef/10:02:00:00:00:a0 succeeded
[   19.293096] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[   19.293188] ata1.00: ACPI cmd ef/10:04:00:00:00:a0 succeeded
[   19.293279] ata1.00: ACPI cmd ef/10:05:00:00:00:a0 succeeded
[   19.293625] ata1.00: ATA-8: FUJITSU MHZ2250BH G2, 8909, max UDMA/100
[   19.293628] ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[   19.294550] ata1.00: ACPI cmd 00/00:00:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[   19.294647] ata1.00: ACPI cmd ef/10:01:00:00:00:a0 succeeded
[   19.294650] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[   19.294743] ata1.00: ACPI cmd ef/10:04:00:00:00:a0 succeeded
[   19.294834] ata1.00: ACPI cmd ef/10:05:00:00:00:a0 succeeded
[   19.295201] ata1.00: configured for UDMA/100
[   20.196015] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   20.209376] ata2.00: ACPI cmd 00/00:00:00:00:00:b0 succeeded
[   20.209687] ata2.00: ACPI cmd ef/10:01:00:00:00:b0 rejected by device (Stat=0x51 Err=0x04)
[   20.209952] ata2.00: ACPI cmd ef/10:02:00:00:00:b0 rejected by device (Stat=0x51 Err=0x04)
[   20.209955] ata2.00: ACPI cmd ef/10:03:00:00:00:b0 filtered out
[   20.210217] ata2.00: ACPI cmd ef/10:04:00:00:00:b0 rejected by device (Stat=0x51 Err=0x04)
[   20.210730] ata2.00: ACPI cmd ef/10:05:00:00:00:b0 rejected by device (Stat=0x51 Err=0x04)
[   20.223423] ata2.00: ATAPI: Optiarc DVD RW AD-7561S, AH03, max UDMA/100
[   20.237600] ata2.00: ACPI cmd 00/00:00:00:00:00:b0 succeeded
[   20.237908] ata2.00: ACPI cmd ef/10:01:00:00:00:b0 rejected by device (Stat=0x51 Err=0x04)
[   20.238175] ata2.00: ACPI cmd ef/10:02:00:00:00:b0 rejected by device (Stat=0x51 Err=0x04)
[   20.238178] ata2.00: ACPI cmd ef/10:03:00:00:00:b0 filtered out
[   20.238440] ata2.00: ACPI cmd ef/10:04:00:00:00:b0 rejected by device (Stat=0x51 Err=0x04)
[   20.238703] ata2.00: ACPI cmd ef/10:05:00:00:00:b0 rejected by device (Stat=0x51 Err=0x04)
[   20.251348] ata2.00: configured for UDMA/100
[   20.584017] ata5: SATA link down (SStatus 0 SControl 300)
[   20.920016] ata6: SATA link down (SStatus 0 SControl 300)
[   20.936099] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHZ2250B 8909 PQ: 0 ANSI: 5
[   20.936188] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors: (250 GB/232 GiB)
[   20.936204] sd 0:0:0:0: [sda] Write Protect is off
[   20.936206] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   20.936231] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   20.936289] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors: (250 GB/232 GiB)
[   20.936303] sd 0:0:0:0: [sda] Write Protect is off
[   20.936305] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   20.936328] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   20.936331]  sda: sda1 sda2 < sda5 sda6 > sda3 sda4
[   21.333898] sd 0:0:0:0: [sda] Attached SCSI disk
[   21.333938] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   21.334860] scsi 1:0:0:0: CD-ROM            Optiarc  DVD RW AD-7561S  AH03 PQ: 0 ANSI: 5
[   21.340217] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[   21.340220] Uniform CD-ROM driver Revision: 3.20
[   21.340304] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   21.340338] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   21.341059] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[   21.341079] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[   21.341093] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[   21.341096] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[   21.341150] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[   21.345059] ehci_hcd 0000:00:1a.7: debug port 1
[   21.345066] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[   21.345080] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xdf304c00
[   21.360009] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[   21.360070] usb usb1: configuration #1 chosen from 1 choice
[   21.360095] hub 1-0:1.0: USB hub found
[   21.360102] hub 1-0:1.0: 4 ports detected
[   21.360207] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[   21.360218] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[   21.360221] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   21.360272] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[   21.364192] ehci_hcd 0000:00:1d.7: debug port 1
[   21.364199] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[   21.364211] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xdf304800
[   21.376009] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[   21.376070] usb usb2: configuration #1 chosen from 1 choice
[   21.376094] hub 2-0:1.0: USB hub found
[   21.376100] hub 2-0:1.0: 8 ports detected
[   21.376201] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[   21.376218] uhci_hcd: USB Universal Host Controller Interface driver
[   21.376238] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   21.376244] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[   21.376248] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[   21.376285] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[   21.376320] uhci_hcd 0000:00:1a.0: irq 16, io base 0x000090e0
[   21.376392] usb usb3: configuration #1 chosen from 1 choice
[   21.376415] hub 3-0:1.0: USB hub found
[   21.376421] hub 3-0:1.0: 2 ports detected
[   21.376508] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   21.376515] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[   21.376518] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[   21.376560] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[   21.376595] uhci_hcd 0000:00:1a.1: irq 17, io base 0x000090c0
[   21.376665] usb usb4: configuration #1 chosen from 1 choice
[   21.376689] hub 4-0:1.0: USB hub found
[   21.376695] hub 4-0:1.0: 2 ports detected
[   21.376776] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[   21.376783] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[   21.376786] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   21.376824] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[   21.376850] uhci_hcd 0000:00:1d.0: irq 20, io base 0x000090a0
[   21.376917] usb usb5: configuration #1 chosen from 1 choice
[   21.376942] hub 5-0:1.0: USB hub found
[   21.376948] hub 5-0:1.0: 2 ports detected
[   21.377027] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 22 (level, low) -> IRQ 22
[   21.377033] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[   21.377036] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   21.377078] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[   21.377112] uhci_hcd 0000:00:1d.1: irq 22, io base 0x00009080
[   21.377184] usb usb6: configuration #1 chosen from 1 choice
[   21.377207] hub 6-0:1.0: USB hub found
[   21.377214] hub 6-0:1.0: 2 ports detected
[   21.377293] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[   21.377300] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[   21.377303] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   21.377350] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[   21.377376] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00009060
[   21.377445] usb usb7: configuration #1 chosen from 1 choice
[   21.377469] hub 7-0:1.0: USB hub found
[   21.377475] hub 7-0:1.0: 2 ports detected
[   21.377555] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[   21.377562] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[   21.377565] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   21.377605] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 8
[   21.377640] uhci_hcd 0000:00:1d.3: irq 19, io base 0x00009040
[   21.377709] usb usb8: configuration #1 chosen from 1 choice
[   21.377734] hub 8-0:1.0: USB hub found
[   21.377740] hub 8-0:1.0: 2 ports detected
[   21.377872] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:MOUE] at 0x60,0x64 irq 1,12
[   21.422867] serio: i8042 KBD port at 0x60,0x64 irq 1
[   21.422872] serio: i8042 AUX port at 0x60,0x64 irq 12
[   21.424039] mice: PS/2 mouse device common for all mice
[   21.444071] rtc_cmos 00:03: RTC can wake from S4
[   21.444103] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[   21.444136] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[   21.444198] device-mapper: uevent: version 1.0.3
[   21.444277] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[   21.444344] device-mapper: multipath: version 1.0.5 loaded
[   21.444346] device-mapper: multipath round-robin: version 1.0.0 loaded
[   21.444418] EISA: Probing bus 0 at eisa.0
[   21.444425] Cannot allocate resource for EISA slot 1
[   21.444427] Cannot allocate resource for EISA slot 2
[   21.444429] Cannot allocate resource for EISA slot 3
[   21.444431] Cannot allocate resource for EISA slot 4
[   21.444433] Cannot allocate resource for EISA slot 5
[   21.444435] Cannot allocate resource for EISA slot 6
[   21.444438] Cannot allocate resource for EISA slot 7
[   21.444440] Cannot allocate resource for EISA slot 8
[   21.444441] EISA: Detected 0 cards.
[   21.444548] cpuidle: using governor ladder
[   21.444659] cpuidle: using governor menu
[   21.445149] TCP cubic registered
[   21.445240] NET: Registered protocol family 10
[   21.445659] lo: Disabled Privacy Extensions
[   21.445986] NET: Registered protocol family 17
[   21.446001] Bluetooth: L2CAP ver 2.11
[   21.446003] Bluetooth: L2CAP socket layer initialized
[   21.446006] Bluetooth: SCO (Voice Link) ver 0.6
[   21.446008] Bluetooth: SCO socket layer initialized
[   21.446039] Bluetooth: RFCOMM socket layer initialized
[   21.446046] Bluetooth: RFCOMM TTY layer initialized
[   21.446047] Bluetooth: RFCOMM ver 1.10
[   21.446073] Marking TSC unstable due to TSC halts in idle
[   21.446621] Using IPI No-Shortcut mode
[   21.446683] registered taskstats version 1
[   21.446820]   Magic number: 9:202:484
[   21.446906] rtc_cmos 00:03: setting system clock to 2009-09-25 13:28:13 UTC (1253885293)
[   21.446910] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   21.446911] EDD information not available.
[   21.447179] Freeing unused kernel memory: 532k freed
[   21.447329] Write protecting the kernel text: 4116k
[   21.447387] Write protecting the kernel read-only data: 1528k
[   21.477719] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[   21.776756] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[   21.776780] r8169 0000:05:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   21.776802] r8169 0000:05:00.0: setting latency timer to 64
[   21.776971] r8169 0000:05:00.0: irq 2295 for MSI/MSI-X
[   21.777613] eth0: RTL8168c/8111c at 0xf7c6e000, 00:1e:ec:a7:6a:84, XID 3c4000c0 IRQ 2295
[   21.788525] usb 2-5: new high speed USB device using ehci_hcd and address 2
[   21.949203] usb 2-5: configuration #1 chosen from 1 choice
[   22.300520] usb 3-2: new full speed USB device using uhci_hcd and address 2
[   22.462555] usb 3-2: configuration #1 chosen from 1 choice
[   22.519274] PM: Starting manual resume from disk
[   22.519277] PM: Resume from partition 8:5
[   22.519279] PM: Checking hibernation image.
[   22.519434] PM: Resume from disk failed.
[   22.542689] kjournald starting.  Commit interval 5 seconds
[   22.542700] EXT3-fs: mounted filesystem with ordered data mode.
[   23.000052] Clocksource tsc unstable (delta = -150783895 ns)
[   27.634063] udev: starting version 141
[   27.817524] lis3lv02d: laptop model unknown, using default axes configuration
[   27.829521] input: ST LIS3LV02DL Accelerometer as /devices/platform/lis3lv02d/input/input6
[   27.838166] lis3lv02d driver loaded.
[   27.867136] acpi device:09: registered as cooling_device3
[   27.867512] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:07/device:08/input/input7
[   27.874194] Linux agpgart interface v0.103
[   27.893625] ACPI: Video Device [EVGA] (multi-head: yes  rom: no  post: no)
[   27.987767] leds-hp-disk driver loaded.
[   28.005048] iTCO_vendor_support: vendor-support=0
[   28.018639] ieee80211_crypt: registered algorithm 'NULL'
[   28.021914] wl: module license 'MIXED/Proprietary' taints kernel.
[   28.023927] wl 0000:04:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   28.023941] wl 0000:04:00.0: setting latency timer to 64
[   28.950710] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
[   28.950915] iTCO_wdt: Found a ICH9M TCO device (Version=2, TCOBASE=0x0460)
[   28.951000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   28.967663] sdhci: Secure Digital Host Controller Interface driver
[   28.967665] sdhci: Copyright(c) Pierre Ossman
[   28.969120] sdhci-pci 0000:06:00.0: SDHCI controller found [197b:2382] (rev 0)
[   28.969142] sdhci-pci 0000:06:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   28.969184] sdhci-pci 0000:06:00.0: setting latency timer to 64
[   28.969251] mmc0: SDHCI controller on PCI [0000:06:00.0] using ADMA
[   28.969261] sdhci-pci 0000:06:00.2: SDHCI controller found [197b:2381] (rev 0)
[   28.969278] sdhci-pci 0000:06:00.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   28.969285] sdhci-pci 0000:06:00.2: Refusing to bind to secondary interface.
[   28.969293] sdhci-pci 0000:06:00.2: PCI INT A disabled
[   28.985780] input: PC Speaker as /devices/platform/pcspkr/input/input8
[   29.008439] ieee80211_crypt: registered algorithm 'TKIP'
[   29.008653] eth1: Broadcom BCM4315 802.11 Wireless Controller 5.10.91.9
[   29.046565] Linux video capture interface: v2.00
[   29.153249] uvcvideo: Found UVC 1.00 device HP Webcam  (046d:09b
[   29.153850] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   29.153866] nvidia 0000:01:00.0: setting latency timer to 64
[   29.154054] NVRM: loading NVIDIA UNIX x86 Kernel Module  180.44  Mon Mar 23 14:59:10 PST 2009
[   29.157464] input: HP Webcam  as /devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5:1.0/input/input9
[   29.169502] usbcore: registered new interface driver uvcvideo
[   29.169529] USB Video Class driver (v0.1.0)
[   29.287849] HDA Intel 0000:00:1b.0: power state changed by ACPI to D0
[   29.287860] HDA Intel 0000:00:1b.0: PCI INT B -> GSI 22 (level, low) -> IRQ 22
[   29.287955] HDA Intel 0000:00:1b.0: setting latency timer to 64
[ 29.287961] ALSA /usr/src/modules/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/hda_intel.c:2130: chipset global capabilities = 0x4401
[   29.316558] ALSA /usr/src/modules/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/hda_intel.c:771: codec_mask = 0x7
[   29.330999] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   30.284982] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input10
[ 30.320508] ALSA /usr/src/modules/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/hda_intel.c:618: hda_intel: azx_get_response timeout, switching to polling mode: last cmd=0x000f0000
[ 30.322051] ALSA /usr/src/modules/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/patch_sigmatel.c:4508: hda_codec: Unknown model for STAC92HD71BXX, using BIOS defaults
[ 30.322091] ALSA /usr/src/modules/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/patch_sigmatel.c:2203: hda_codec: pin nid 0a bios pin config 0221201f
[ 30.322130] ALSA /usr/src/modules/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/patch_sigmatel.c:2203: hda_codec: pin nid 0b bios pin config 02a12020
[ 30.322169] ALSA /usr/src/modules/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/patch_sigmatel.c:2203: hda_codec: pin nid 0c bios pin config 40f100f8
[ 30.322208] ALSA /usr/src/modules/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/patch_sigmatel.c:2203: hda_codec: pin nid 0d bios pin config 90170110
[ 30.322258] ALSA /usr/src/modules/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/patch_sigmatel.c:2203: hda_codec: pin nid 0e bios pin config 40f100f1
[ 30.322298] ALSA /usr/src/modules/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/patch_sigmatel.c:2203: hda_codec: pin nid 0f bios pin config 40f100f0
[ 30.322336] ALSA /usr/src/modules/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/patch_sigmatel.c:2203: hda_codec: pin nid 14 bios pin config 40f100f2
[ 30.322375] ALSA /usr/src/modules/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/patch_sigmatel.c:2203: hda_codec: pin nid 18 bios pin config 95a6912e
[ 30.322426] ALSA /usr/src/modules/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/patch_sigmatel.c:2203: hda_codec: pin nid 19 bios pin config 40f000f5
[ 30.322464] ALSA /usr/src/modules/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/patch_sigmatel.c:2203: hda_codec: pin nid 1e bios pin config 40f000f3
[ 30.322503] ALSA /usr/src/modules/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/patch_sigmatel.c:2203: hda_codec: pin nid 1f bios pin config 40f000f6
[   30.322964] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:3267: autoconfig: line_outs=1 (0xd/0x0/0x0/0x0/0x0)
[   30.322968] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:3271:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   30.322971] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:3275:    hp_outs=1 (0xa/0x0/0x0/0x0/0x0)
[   30.322975] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:3276:    mono: mono_out=0x0
[ 30.322977] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:3284: inputs: mic=0xb, fmic=0x0, line=0x0, fline=0x0, cd=0x0, aux=0x0
[ 30.322982] ALSA /usr/src/modules/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/patch_sigmatel.c:2655: stac92xx_add_dyn_out_pins: total dac count=2
[   30.323113] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input11
[ 30.335191] ALSA /usr/src/modules/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/hda_generic.c:679: hda_generic: no proper input path found
[ 30.335196] ALSA /usr/src/modules/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/hda_generic.c:427: hda_generic: no proper output path found
[   30.335587] ALSA /usr/src/modules/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/hda_generic.c:1026: hda_generic: no PCM found
[   30.371298] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input12
[   30.372152] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:1255: Cannot find slave Surround Playback Volume, skipped
[   30.372156] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:1255: Cannot find slave Center Playback Volume, skipped
[   30.372160] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:1255: Cannot find slave LFE Playback Volume, skipped
[   30.372163] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:1255: Cannot find slave Side Playback Volume, skipped
[   30.372169] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:1255: Cannot find slave Speaker Playback Volume, skipped
[ 30.372172] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:1255: Cannot find slave External Speaker Playback Volume, skipped
[   30.372176] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:1255: Cannot find slave Speaker2 Playback Volume, skipped
[   30.372183] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:1255: Cannot find slave Surround Playback Switch, skipped
[   30.372187] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:1255: Cannot find slave Center Playback Switch, skipped
[   30.372190] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:1255: Cannot find slave LFE Playback Switch, skipped
[   30.372194] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:1255: Cannot find slave Side Playback Switch, skipped
[   30.372199] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:1255: Cannot find slave Speaker Playback Switch, skipped
[ 30.372203] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:1255: Cannot find slave External Speaker Playback Switch, skipped
[   30.372207] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:1255: Cannot find slave Speaker2 Playback Switch, skipped
[   30.372211] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:1255: Cannot find slave IEC958 Playback Switch, skipped
[   30.436199] input: HDA Intel at 0xdf300000 irq 22 Mic at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/input/input13
[   30.436673] input: HDA Intel at 0xdf300000 irq 22 HP Out at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/input/input14
[   30.605193] lp: driver loaded but no devices found
[   30.674010] Adding 4996172k swap on /dev/sda5.  Priority:-1 extents:1 across:4996172k
[   30.691014] EXT3 FS on sda6, internal journal
[ 31.059473] type=1505 audit(1253865503.109:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2167
[   31.103623] type=1505 audit(1253865503.153:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2171
[   31.103722] type=1505 audit(1253865503.153:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2171
[ 31.103763] type=1505 audit(1253865503.153:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2171
[ 31.103799] type=1505 audit(1253865503.153:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2171
[ 31.226243] type=1505 audit(1253865503.277:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2176
[   31.226406] type=1505 audit(1253865503.277:: operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2176
[   31.252749] type=1505 audit(1253865503.305:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2180
[   33.700709] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   33.700712] Bluetooth: BNEP filters: protocol multicast
[   33.719796] Bridge firewalling registered
[   35.149389] ppdev: user-space parallel port driver
[   38.948451] r8169: eth0: link up
[   38.948454] r8169: eth0: link up
[ 42.636891] ALSA /usr/src/modules/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/hda_intel.c:1434: azx_pcm_prepare: bufsize=0x10000, format=0x31
[ 42.636912] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:822: hda_codec_setup_stream: NID=0x10, stream=0x5, channel=0, format=0x31
[ 42.644555] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:822: hda_codec_setup_stream: NID=0x11, stream=0x5, channel=0, format=0x31
[   44.172044] eth1: no IPv6 routers present
[   49.220042] eth0: no IPv6 routers present
[ 53.153342] ALSA /usr/src/modules/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/hda_intel.c:1434: azx_pcm_prepare: bufsize=0x3800, format=0x4011
[ 53.196063] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:822: hda_codec_setup_stream: NID=0x12, stream=0x1, channel=0, format=0x4011
[ 53.204494] ALSA /usr/src/modules/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/hda_intel.c:1434: azx_pcm_prepare: bufsize=0x3800, format=0x4011
[ 53.248061] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:822: hda_codec_setup_stream: NID=0x12, stream=0x1, channel=0, format=0x4011
[   58.260705] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:834: hda_codec_cleanup_stream: NID=0x12
[   58.260729] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:834: hda_codec_cleanup_stream: NID=0x12
[   58.278614] CPU0 attaching NULL sched-domain.
[   58.278619] CPU1 attaching NULL sched-domain.
[   58.292580] CPU0 attaching sched-domain:
[   58.292582]  domain 0: span 0-1 level MC
[   58.292585]   groups: 0 1
[   58.292589]   domain 1: span 0-1 level CPU
[   58.292592]    groups: 0-1
[   58.292596] CPU1 attaching sched-domain:
[   58.292598]  domain 0: span 0-1 level MC
[   58.292600]   groups: 1 0
[   58.292604]   domain 1: span 0-1 level CPU
[   58.292606]    groups: 0-1
[ 3479.012009] CE: hpet increasing min_delta_ns to 15000 nsec
rajeev@rajeev-laptop:~$ 

dis whole o/p is out of my getting level ............
still i hv no output of sound plz help me ............
i hv been f***ed after installing ubuntu ..........
:sad:

---

### Post by Xander {MP} on 2009-10-13
install beta and you get sound I have the same model hp pavilion dv4 with an intel proc and intel audio card. the only that needs work is the system beep which is more like a buzz then a beep. so far everything is running stable so I recommend you go to the beta of karmic koala.

---

### Post by mhgsys on 2009-10-13
Hey

I noticed you are using a intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)

To get sound working you need to add; 
```

options snd-hda-intel model=3stack-dig
options snd-hda-intel enable_msi=1
options snd-hda-intel single_cmd=1

```

to /etc/modprobe.d/alsa-base.conf

so; open up a terminal ; 
typ;
```

sudo gedit /etc/modprobe.d/alsa-base.conf

```

and copy paste the options from above in it at the bottom of the file; save your file, reboot and all should be working.
 
info from here; 
[http://ubuntuforums.org/showthread.php?t=940689&page=3](http://ubuntuforums.org/showthread.php?t=940689&page=3)

ps; please put codetags around your dmesg output, it's taking a whole page now. 
use [ code ] textyouwanttoputincodetags [ /code ] without the space in it to do so.

---

