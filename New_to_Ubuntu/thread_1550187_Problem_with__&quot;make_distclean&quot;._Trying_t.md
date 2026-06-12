---
title: "Problem with  &quot;make distclean&quot;. Trying to get online"
date: 2010-08-10
forum: New to Ubuntu
---

### Post by digital_nite on 2010-08-10
Hello everyone,
    I'm new to Ubuntu and am trying to get online. My card isn't supported by Ububntu's drivers so I need to use ndiswrapper. I found a handful of tutorials on the net and am currently following one that tells me to use the "make distclean" command. The only problem is it doesn't work. I know I'm doing something wrong. Here's what my screen looks like:

digitalnite@ubuntu:~$ cd /usr/src
digitalnite@ubuntu:/usr/src$ ls
linux-headers-2.6.32-21  linux-headers-2.6.32-21-generic
digitalnite@ubuntu:/usr/src$ [COLOR=Green]make distclean[/COLOR]
[COLOR=Red]make: *** No rule to make target `distclean'.  Stop.[/COLOR]
digitalnite@ubuntu:/usr/src$ 

Here's what the tutorial is telling me. Should I still follow it.

You may not need to see this part of the tutorial I'm following
****************************************************
NdisWrapper implements Windows kernel API and
NDIS API within Linux kernel.
NdisWrapper implements Windows kernel API and NDIS (Network
Driver Interface Specification) API within Linux kernel.
A Windows driver for wireless network card is then linked to this
implementation so that the driver runs natively, as though it is in
Windows, without binary emulation.
Requirements:
- You need a recent kernel at least 2.6.6 or 2.4.26 with source. Under
Red Hat or Mandrake, the sources can be installed using the package
kernel-source< kernel-version >.rpm. Make sure there is a link to the
kernel source from the modules directory. /lib/modules/VERSION/build
should be a link to the kernel source, where VERSION is the version of
the kernel you are running. If there is no link, you'll get an error at the make install step. To create a link, assuming the
kernel sources are present, use the command
ln -s /usr/src/linux-< kernel-version > /lib/modules/VERSION/build
- Make sure you have started compiling the kernel sources, so needed header files are present. Some vendors ship
ndiswrapper in their distributions. Either use it or make sure you remove it before installing ndiswrapper by yourself. Make
sure you have the Wireless Tools installed. Again, there is a package that comes along with Red Hat and Mandrake
distributions. If you are using Debian you can install the wireless-tools package from the mirror.
*************************************************************************r[COLOR=Red]
[COLOR=Black]These are the instructions I've been following.[/COLOR]
Installation:
Go to source-directory and do
make distclean
As root run
make
and then
make install

[COLOR=Black]I appreciate everyones time. I look forward to passing on the knowledge you'll share.

digital_nite
[/COLOR][/COLOR]

---

### Post by davidmohammed on 2010-08-10
Hi there,
  I presume you are trying to compile ndiswrapper?

Suggest you use synaptic manager and search for ndisgtk.  This install a graphical GUI and ndiswrapper.  You'll need then just to supply the windows driver and its .inf file for ndis to work.

I'm curious - what makes you think that your network card is not supported?

what is your network card?  Have you checked "dmesg" to see if there are any errors initialising your network card?

---

### Post by digital_nite on 2010-08-11
Thank you for the response David.
About my network card, I have a linksys wireless card, specifically a "wireless-G Notebook Adapter WPC54GV3".
 I decided to wait on the compiling  of ndiswrapper and instead ran the dmesg command you recommended.I got a few screenfulls of information.
I didn't know what was important and what wasn't so here's what I got.

[    0.201377] VFS: Disk quotas dquot_6.5.2
[    0.201440] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.202169] fuse init (API version 7.13)
[    0.202254] msgmni has been set to 1722
[    0.202478] alg: No test for stdrng (krng)
[    0.202541] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.202544] io scheduler noop registered
[    0.202546] io scheduler anticipatory registered
[    0.202549] io scheduler deadline registered
[    0.202587] io scheduler cfq registered (default)
[    0.209834] pcieport 0000:00:04.0: setting latency timer to 64
[    0.209944] pcieport 0000:00:05.0: setting latency timer to 64
[    0.210003] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.210028] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.210598] ACPI: AC Adapter [ACAD] (on-line)
[    0.210676] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    0.211087] ACPI: Lid Switch [LID]
[    0.211142] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
[    0.211145] ACPI: Sleep Button [SLPB]
[    0.211188] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input2
[    0.211191] ACPI: Power Button [PWRB]
[    0.211238] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.211241] ACPI: Power Button [PWRF]
[    0.211438] Marking TSC unstable due to TSC halts in idle
[    0.211526] processor LNXCPU:00: registered as cooling_device0
[    0.221727] Switching to clocksource acpi_pm
[    0.222984] thermal LNXTHERM:01: registered as thermal_zone0
[    0.222996] ACPI: Thermal Zone [THRM] (71 C)
[    0.224550] Linux agpgart interface v0.103
[    0.224589] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.225937] brd: module loaded
[    0.226444] loop: module loaded
[    0.226549] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    0.231624]   alloc irq_desc for 16 on node 0
[    0.231628]   alloc kstat_irqs on node 0
[    0.231638] pata_acpi 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.231713] pata_acpi 0000:00:14.1: setting latency timer to 64
[    0.232291] Fixed MDIO Bus: probed
[    0.232328] PPP generic driver version 2.4.2
[    0.232403] tun: Universal TUN/TAP device driver, 1.6
[    0.232405] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.232512] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.232604]   alloc irq_desc for 19 on node 0
[    0.232606]   alloc kstat_irqs on node 0
[    0.232613] ehci_hcd 0000:00:13.2: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.232657] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    0.232693] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 1
[    0.232805] ehci_hcd 0000:00:13.2: irq 19, io mem 0xc0006000
[    0.260132] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    0.260284] usb usb1: configuration #1 chosen from 1 choice
[    0.260322] hub 1-0:1.0: USB hub found
[    0.260333] hub 1-0:1.0: 8 ports detected
[    0.260463] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.260765] ACPI: Battery Slot [BAT1] (battery present)
[    0.270088] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.270116] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    0.270207] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 2
[    0.270234] ohci_hcd 0000:00:13.0: irq 19, io mem 0xc0004000
[    0.330319] usb usb2: configuration #1 chosen from 1 choice
[    0.330355] hub 2-0:1.0: USB hub found
[    0.330370] hub 2-0:1.0: 4 ports detected
[    0.340153] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.340182] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    0.340267] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 3
[    0.340294] ohci_hcd 0000:00:13.1: irq 19, io mem 0xc0005000
[    0.400330] usb usb3: configuration #1 chosen from 1 choice
[    0.400367] hub 3-0:1.0: USB hub found
[    0.400382] hub 3-0:1.0: 4 ports detected
[    0.400491] uhci_hcd: USB Universal Host Controller Interface driver
[    0.400581] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    0.402631] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.402638] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.402779] mice: PS/2 mouse device common for all mice
[    0.402963] rtc_cmos 00:04: RTC can wake from S4
[    0.403015] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    0.403043] rtc0: alarms up to one month, 114 bytes nvram
[    0.403190] device-mapper: uevent: version 1.0.3
[    0.405879] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
[    0.410167] device-mapper: multipath: version 1.1.0 loaded
[    0.410172] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.412067] cpuidle: using governor ladder
[    0.412120] cpuidle: using governor menu
[    0.412520] TCP cubic registered
[    0.412669] NET: Registered protocol family 10
[    0.413173] lo: Disabled Privacy Extensions
[    0.413494] NET: Registered protocol family 17
[    0.413535] powernow-k8: Found 1 AMD Turion(tm) 64 Mobile Technology MK-36 processors (1 cpu cores) (version 2.20.00)
[    0.413589] powernow-k8:    0 : fid 0xc (2000 MHz), vid 0x10
[    0.413591] powernow-k8:    1 : fid 0xa (1800 MHz), vid 0x12
[    0.413594] powernow-k8:    2 : fid 0x8 (1600 MHz), vid 0x14
[    0.413596] powernow-k8:    3 : fid 0x0 (800 MHz), vid 0x18
[    0.413745] PM: Resume from disk failed.
[    0.413766] registered taskstats version 1
[    0.414152]   Magic number: 6:707:396
[    0.414251] rtc_cmos 00:04: setting system clock to 2010-08-10 20:22:31 UTC (1281471751)
[    0.414254] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.414256] EDD information not available.
[    0.426916] Freeing initrd memory: 8447k freed
[    0.431739] Freeing unused kernel memory: 876k freed
[    0.432261] Write protecting the kernel read-only data: 7680k
[    0.434484] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    0.455660] udev: starting version 151
[    0.580093] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    0.687100] sky2 driver version 1.25
[    0.687212] sky2 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.687226] sky2 0000:02:00.0: setting latency timer to 64
[    0.687262] sky2 0000:02:00.0: Yukon-2 FE chip revision 1
[    0.688002] sky2 eth0: addr 00:e0:b8:b8:a6:5c
[    0.688374]   alloc irq_desc for 17 on node 0
[    0.688376]   alloc kstat_irqs on node 0
[    0.688383] b43-pci-bridge 0000:05:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.688391] b43-pci-bridge 0000:05:00.0: setting latency timer to 64
[    0.694589] scsi0 : pata_atiixp
[    0.694783] ohci1394 0000:08:09.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.694956] scsi1 : pata_atiixp
[    0.695743] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x8410 irq 14
[    0.695746] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x8418 irq 15
[    0.731775] usb 1-1: configuration #1 chosen from 1 choice
[    0.740447] Initializing USB Mass Storage driver...
[    0.740566] scsi2 : SCSI emulation for USB Mass Storage devices
[    0.740700] usbcore: registered new interface driver usb-storage
[    0.740703] USB Mass Storage support registered.
[    0.740787] usb-storage: device found at 2
[    0.740789] usb-storage: waiting for device to settle before scanning
[    0.750119] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[21]  MMIO=[c0405000-c04057ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    0.800123] ssb: Sonics Silicon Backplane found on PCI device 0000:05:00.0
[    0.890890] ata1.00: ATA-7: HTS421212H9AT00, HA4OA70S, max UDMA/100
[    0.890893] ata1.00: 234441648 sectors, multi 16: LBA48 
[    0.890923] ata1.01: ATAPI: HL-DT-ST DVD-RW GWA-4082N, CG03, max UDMA/33
[    0.930829] ata1.00: configured for UDMA/100
[    0.970552] ata1.01: configured for UDMA/33
[    0.972793] scsi 0:0:0:0: Direct-Access     ATA      HTS421212H9AT00  HA4O PQ: 0 ANSI: 5
[    0.972964] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    0.976590] scsi 0:0:1:0: CD-ROM            HL-DT-ST DVD-RW GWA-4082N CG03 PQ: 0 ANSI: 5
[    0.976962] sd 0:0:0:0: [sda] 234441648 512-byte logical blocks: (120 GB/111 GiB)
[    0.980405] sr0: scsi3-mmc drive: 31x/31x writer cd/rw xa/form2 cdda tray
[    0.980409] Uniform CD-ROM driver Revision: 3.20
[    0.980534] sr 0:0:1:0: Attached scsi CD-ROM sr0
[    0.980593] sr 0:0:1:0: Attached scsi generic sg1 type 5
[    0.981002] sd 0:0:0:0: [sda] Write Protect is off
[    0.981005] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.981028] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.981159]  sda: sda1 sda2
[    1.000117] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.250089] usb 3-1: new low speed USB device using ohci_hcd and address 2
[    1.473417] usb 3-1: configuration #1 chosen from 1 choice
[    1.487231] usbcore: registered new interface driver hiddev
[    1.492620] input: B16_b_02 USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:13.1/usb3/3-1/3-1:1.0/input/input6
[    1.492818] generic-usb 0003:046D:C024.0001: input,hidraw0: USB HID v1.10 Mouse [B16_b_02 USB-PS/2 Optical Mouse] on usb-0000:00:13.1-1/input0
[    1.492850] usbcore: registered new interface driver usbhid
[    1.492964] usbhid: v2.6:USB HID core driver
[    1.810045] usb 2-2: new full speed USB device using ohci_hcd and address 2
[    2.028301] usb 2-2: configuration #1 chosen from 1 choice
[    2.036297] input: Microsoft LifeChat LX-3000  as /devices/pci0000:00/0000:00:13.0/usb2/2-2/2-2:1.3/input/input7
[    2.036398] generic-usb 0003:045E:070F.0002: input,hidraw1: USB HID v1.00 Device [Microsoft LifeChat LX-3000 ] on usb-0000:00:13.0-2/input3
[    2.070183] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00e0b80367009566]
[    2.446401] EXT4-fs (loop0): mounted filesystem with ordered data mode
[    5.740276] usb-storage: device scan complete
[    5.741250] scsi 2:0:0:0: Direct-Access     WD       Ext HDD 1021     2002 PQ: 0 ANSI: 4
[    5.741678] sd 2:0:0:0: Attached scsi generic sg2 type 0
[    5.742353] sd 2:0:0:0: [sdb] 1953519616 512-byte logical blocks: (1.00 TB/931 GiB)
[    5.743354] sd 2:0:0:0: [sdb] Test WP failed, assume Write Enabled
[    5.743357] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    5.744974] sd 2:0:0:0: [sdb] Test WP failed, assume Write Enabled
[    5.744976] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    5.744979]  sdb: sdb1
[    5.747473] sd 2:0:0:0: [sdb] Test WP failed, assume Write Enabled
[    5.747475] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    5.747478] sd 2:0:0:0: [sdb] Attached SCSI disk
[   21.276842] udev: starting version 151
[   21.359780] lp: driver loaded but no devices found
[   21.439060] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   21.648633] type=1505 audit(1281496972.725:2):  operation="profile_load" pid=448 name="/sbin/dhclient3"
[   21.648924] type=1505 audit(1281496972.725:3):  operation="profile_load" pid=448 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   21.649086] type=1505 audit(1281496972.725:4):  operation="profile_load" pid=448 name="/usr/lib/connman/scripts/dhclient-script"
[   21.833895] [Firmware Bug]: ACPI: ACPI brightness control misses _BQC function
[   21.833933] [Firmware Bug]: _BCQ is used instead of _BQC
[   21.836594] cfg80211: Calling CRDA to update world regulatory domain
[   21.855400] acpi device:1a: registered as cooling_device1
[   21.855543] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/device:17/LNXVIDEO:00/input/input8
[   21.855612] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   21.857945] k8temp 0000:00:18.3: Temperature readouts might be wrong - check erratum #141
[   21.886668] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0x8400, revision 0
[   21.887746] EDAC MC: Ver: 2.1.0 Apr 16 2010
[   21.972353] tifm_7xx1 0000:08:09.2: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[   21.979392] yenta_cardbus 0000:08:09.0: CardBus bridge found [107b:0367]
[   21.979422] yenta_cardbus 0000:08:09.0: Using CSCINT to route CSC interrupts to PCI
[   21.979425] yenta_cardbus 0000:08:09.0: Routing CardBus interrupts to PCI
[   21.979432] yenta_cardbus 0000:08:09.0: TI: mfunc 0x01ac1b22, devctl 0x64
[   22.001084] cfg80211: World regulatory domain updated:
[   22.001088]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   22.001092]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   22.001095]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   22.001097]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   22.001100]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   22.001102]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   22.049267] [drm] Initialized drm 1.1.0 20060810
[   22.068643] EDAC amd64_edac:  Ver: 3.2.0 Apr 16 2010
[   22.072187] EDAC amd64: This node reports that Memory ECC is currently disabled, set F3x44[22] (0000:00:18.3).
[   22.072194] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
[   22.072195]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
[   22.072197]  (Note that use of the override may cause unknown side effects.)
[   22.072217] amd64_edac: probe of 0000:00:18.2 failed with error -22
[   22.084116] b43-phy0: Broadcom 4311 WLAN found (core revision 10)
[   22.203265] [drm] radeon defaulting to kernel modesetting.
[   22.203269] [drm] radeon kernel modesetting enabled.
[   22.208609] radeon 0000:01:05.0: power state changed by ACPI to D0
[   22.208622] radeon 0000:01:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   22.220972] yenta_cardbus 0000:08:09.0: ISA IRQ mask 0x0ef8, PCI irq 20
[   22.220978] yenta_cardbus 0000:08:09.0: Socket status: 30000868
[   22.220987] yenta_cardbus 0000:08:09.0: pcmcia: parent PCI bridge I/O window: 0x2000 - 0x2fff
[   22.220992] yenta_cardbus 0000:08:09.0: pcmcia: parent PCI bridge Memory window: 0xc0400000 - 0xc04fffff
[   22.220995] yenta_cardbus 0000:08:09.0: pcmcia: parent PCI bridge Memory window: 0x40000000 - 0x43ffffff
[   22.227211] [drm] radeon: Initializing kernel modesetting.
[   22.238270] [drm] register mmio base: 0xC0100000
[   22.238274] [drm] register mmio size: 65536
[   22.238568] [drm] GPU reset succeed (RBBM_STATUS=0x00000140)
[   22.238593] [drm:rs400_gart_adjust_size] *ERROR* Forcing to 32M GART size (because of ASIC bug ?)
[   22.238643] [drm] Generation 2 PCI interface, using max accessible memory
[   22.238646] [drm] radeon: VRAM 128M
[   22.238648] [drm] radeon: VRAM from 0x38000000 to 0x3FFFFFFF
[   22.238649] [drm] radeon: GTT 32M
[   22.238651] [drm] radeon: GTT from 0x40000000 to 0x41FFFFFF
[   22.238691] [drm] radeon: irq initialized.
[   22.238796] [drm] Detected VRAM RAM=128M, BAR=128M
[   22.238801] [drm] RAM width 128bits DDR
[   22.238905] [TTM] Zone  kernel: Available graphics memory: 445712 kiB.
[   22.238925] [drm] radeon: 128M of VRAM memory ready
[   22.238927] [drm] radeon: 32M of GTT memory ready.
[   22.238952] [drm] GART: num cpu pages 8192, num gpu pages 8192
[   22.239355] [drm] radeon: 1 quad pipes, 1 z pipes initialized.
[   22.239374] [drm] radeon: cp idle (0x10000C03)
[   22.239491] [drm] Loading R300 Microcode
[   22.239887] platform radeon_cp.0: firmware: requesting radeon/R300_cp.bin
[   22.246838] [drm] radeon: ring at 0x0000000040000000
[   22.246860] [drm] ring test succeeded in 2 usecs
[   22.246987] [drm] radeon: ib pool ready.
[   22.247537] [drm] ib test succeeded in 0 usecs
[   22.247583] [drm] Default TV standard: NTSC
[   22.247585] [drm] 14.318180000 MHz TV ref clk
[   22.248695] [drm] Panel ID String: SEC                     
[   22.248699] [drm] Panel Size 1280x800
[   22.249268] [drm] Default TV standard: NTSC
[   22.249271] [drm] 14.318180000 MHz TV ref clk
[   22.249332] [drm] Radeon Display Connectors
[   22.249334] [drm] Connector 0:
[   22.249336] [drm]   VGA
[   22.249338] [drm]   DDC: 0x68 0x68 0x68 0x68 0x68 0x68 0x68 0x68
[   22.249340] [drm]   Encoders:
[   22.249342] [drm]     CRT1: INTERNAL_DAC2
[   22.249343] [drm] Connector 1:
[   22.249344] [drm]   LVDS
[   22.249347] [drm]   DDC: 0x198 0x198 0x19c 0x19c 0x1a0 0x1a0 0x1a4 0x1a4
[   22.249348] [drm]   Encoders:
[   22.249350] [drm]     LCD1: INTERNAL_LVDS
[   22.249352] [drm] Connector 2:
[   22.249353] [drm]   S-video
[   22.249354] [drm]   Encoders:
[   22.249355] [drm]     TV1: INTERNAL_DAC2
[   22.342927] phy0: Selected rate control algorithm 'minstrel'
[   22.343663] Registered led device: b43-phy0::tx
[   22.343682] Registered led device: b43-phy0::rx
[   22.343702] Registered led device: b43-phy0::radio
[   22.343781] Broadcom 43xx driver loaded [ Features: PL, Firmware-ID: FW13 ]
[   22.578034] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   22.580233] [drm:edid_is_valid] *ERROR* EDID checksum is invalid, remainder is 13
[   22.580277] [drm:edid_is_valid] *ERROR* Raw EDID:
[   22.580318] <3>00 ff ff ff ff ff ff 00 5a 63 1f 70 01 01 01 01  ........Zc.p....
[   22.580321] <3>05 11 01 03 08 29 1a 78 2e 9b b6 a4 53 4b 9d 24  .....).x....SK.$
[   22.580323] <3>14 4f 54 bf ef 80 95 00 95 0f 81 80 81 40 71 4f  .OT..........@qO
[   22.580326] <3>01 01 01 01 01 01 9a 29 a0 d0 51 84 22 30 50 98  .......)..Q."0P.
[   22.580328] <3>36 00 98 ff 10 00 00 1c 00 00 00 ff 00 51 4a 30  6............QJ0
[   22.580330] <3>30 37 30 35 32 32 31 35 32 0a 00 00 00 fd 00 32  070522152......2
[   22.580333] <3>4b 18 52 1f ff ff ff ff ff ff ff ff ff ff ff ff  K.R.............
[   22.580335] <3>ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff  ................
[   22.580337] 
[   22.580385] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x23aeb3, caps: 0xa04713/0x10008
[   22.615031] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input9
[   22.643648] usbcore: registered new interface driver snd-usb-audio
[   22.710948] [drm:edid_is_valid] *ERROR* EDID checksum is invalid, remainder is 9
[   22.710992] [drm:edid_is_valid] *ERROR* Raw EDID:
[   22.711032] <3>00 ff ff ff ff ff ff 00 5a 63 1f 70 01 01 01 01  ........Zc.p....
[   22.711035] <3>05 11 01 03 08 29 1a 78 2e 9b b6 a4 53 4b 9d 24  .....).x....SK.$
[   22.711037] <3>14 4f 54 bf ef 80 95 00 95 0f 81 80 81 40 71 4f  .OT..........@qO
[   22.711040] <3>01 01 01 01 07 ff ff ff ff ff ff ff ff ff ff ff  ................
[   22.711042] <3>ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff  ................
[   22.711044] <3>ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff  ................
[   22.711046] <3>ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff  ................
[   22.711049] <3>ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff  ................
[   22.711050] 
[   22.800396] input: HDA ATI SB Mic at Ext Front Jack as /devices/pci0000:00/0000:00:14.2/sound/card0/input10
[   22.880056] pcmcia_socket pcmcia_socket0: pccard: CardBus card inserted into slot 0
[   22.880098] pci 0000:09:00.0: reg 10 32bit mmio: [0x000000-0x001fff]
[   22.890153] b43-pci-bridge 0000:09:00.0: enabling device (0000 -> 0002)
[   22.890166] b43-pci-bridge 0000:09:00.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[   22.890180] b43-pci-bridge 0000:09:00.0: setting latency timer to 64
[   23.009335] [drm] fb mappable at 0xC8040000
[   23.009339] [drm] vram apper at 0xC8000000
[   23.009341] [drm] size 5184000
[   23.009343] [drm] fb depth is 24
[   23.009344] [drm]    pitch is 5760
[   23.009884] fb0: radeondrmfb frame buffer device
[   23.009887] registered panic notifier
[   23.009894] [drm] Initialized radeon 2.0.0 20080528 for 0000:01:05.0 on minor 0
[   23.011991] vga16fb: initializing
[   23.011996] vga16fb: mapped to 0xffff8800000a0000
[   23.012003] vga16fb: not registering due to another framebuffer present
[   23.012372] b43-phy1: Broadcom 4318 WLAN found (core revision 9)
[   23.187402] Console: switching to colour frame buffer device 160x50
[   23.210872] phy1: Selected rate control algorithm 'minstrel'
[   23.211752] Registered led device: b43-phy1::tx
[   23.211771] Registered led device: b43-phy1::rx
[   23.211791] Registered led device: b43-phy1::radio
[   23.211800] ssb: Sonics Silicon Backplane found on PCI device 0000:09:00.0
[   27.230369] Adding 261112k swap on /host/ubuntu/disks/swap.disk.  Priority:-1 extents:1019 across:2182900k 
[   27.533906] type=1505 audit(1281496978.615:5):  operation="profile_load" pid=857 name="/usr/share/gdm/guest-session/Xsession"
[   27.536953] type=1505 audit(1281496978.615:6):  operation="profile_replace" pid=858 name="/sbin/dhclient3"
[   27.537255] type=1505 audit(1281496978.615:7):  operation="profile_replace" pid=858 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   27.537427] type=1505 audit(1281496978.615:8):  operation="profile_replace" pid=858 name="/usr/lib/connman/scripts/dhclient-script"
[   27.545766] type=1505 audit(1281496978.625:9):  operation="profile_load" pid=859 name="/usr/bin/evince"
[   27.569933] type=1505 audit(1281496978.645:10):  operation="profile_load" pid=859 name="/usr/bin/evince-previewer"
[   27.578357] type=1505 audit(1281496978.655:11):  operation="profile_load" pid=859 name="/usr/bin/evince-thumbnailer"
[   27.593795] type=1505 audit(1281496978.675:12):  operation="profile_load" pid=861 name="/usr/lib/cups/backend/cups-pdf"
[   27.594165] type=1505 audit(1281496978.675:13):  operation="profile_load" pid=861 name="/usr/sbin/cupsd"
[   27.601391] type=1505 audit(1281496978.685:14):  operation="profile_load" pid=862 name="/usr/sbin/tcpdump"
[   27.626722] sky2 eth0: enabling interface
[   27.626918] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   27.720122] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   27.725379] b43 ssb0:0: firmware: requesting b43-open/ucode5.fw
[   27.731664] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   27.731670] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   27.731673] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[   27.830132] b43 ssb1:0: firmware: requesting b43/ucode5.fw
[   27.840904] b43 ssb1:0: firmware: requesting b43-open/ucode5.fw
[   27.851443] b43-phy1 ERROR: Firmware file "b43/ucode5.fw" not found
[   27.851448] b43-phy1 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   27.851452] b43-phy1 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[   27.940315] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   27.952261] b43 ssb0:0: firmware: requesting b43-open/ucode5.fw
[   27.962144] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   27.962150] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   27.962153] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[   27.968573] ppdev: user-space parallel port driver
[   28.000069] b43 ssb1:0: firmware: requesting b43/ucode5.fw
[   28.006556] b43 ssb1:0: firmware: requesting b43-open/ucode5.fw
[   28.013060] b43-phy1 ERROR: Firmware file "b43/ucode5.fw" not found
[   28.013066] b43-phy1 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   28.013069] b43-phy1 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[   31.454490] sr 0:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   31.454497] sr 0:0:1:0: [sr0] Sense Key : Illegal Request [current] 
[   31.454502] sr 0:0:1:0: [sr0] Add. Sense: Read of scrambled sector without authentication
[   31.454513] sr 0:0:1:0: [sr0] CDB: Read(10): 28 00 00 3c b6 f0 00 00 02 00
[   31.454520] end_request: I/O error, dev sr0, sector 15915968
[   31.457281] sr 0:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   31.457284] sr 0:0:1:0: [sr0] Sense Key : Illegal Request [current] 
[   31.457287] sr 0:0:1:0: [sr0] Add. Sense: Read of scrambled sector without authentication
[   31.457292] sr 0:0:1:0: [sr0] CDB: Read(10): 28 00 00 3c b6 f0 00 00 02 00
[   31.457299] end_request: I/O error, dev sr0, sector 15915968
[   39.475545] [drm:edid_is_valid] *ERROR* EDID checksum is invalid, remainder is 140
[   39.475550] [drm:edid_is_valid] *ERROR* Raw EDID:
[   39.475554] <3>00 ff ff ff ff ff ff 00 5a 63 1f 70 01 01 01 01  ........Zc.p....
[   39.475557] <3>05 11 01 03 08 29 1a 78 2e 9b b6 a4 53 4b 9d 24  .....).x....SK.$
[   39.475559] <3>14 4f 54 bf ef 80 95 00 95 0f 81 80 81 40 71 4f  .OT..........@qO
[   39.475562] <3>01 01 01 01 01 01 9a 29 a0 d0 51 84 22 30 50 98  .......)..Q."0P.
[   39.475564] <3>36 03 ff ff ff ff ff ff ff ff ff ff ff ff ff ff  6...............
[   39.475566] <3>ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff  ................
[   39.475568] <3>ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff  ................
[   39.475571] <3>ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff  ................
[   39.475572] 
[   39.531293] [drm:edid_is_valid] *ERROR* EDID checksum is invalid, remainder is 54
[   39.531297] [drm:edid_is_valid] *ERROR* Raw EDID:
[   39.531301] <3>00 ff ff ff ff ff ff 00 5a 63 1f 70 01 01 01 01  ........Zc.p....
[   39.531303] <3>05 11 01 03 08 29 1a 78 2e 9b b6 a4 53 4b 9d 24  .....).x....SK.$
[   39.531306] <3>14 4f 54 bf ef 80 95 00 95 0f 81 80 81 40 71 4f  .OT..........@qO
[   39.531308] <3>01 01 01 01 01 01 9a 29 a0 d0 51 84 22 30 50 98  .......)..Q."0P.
[   39.531310] <3>36 00 98 ff 13 ff ff ff ff ff ff ff ff ff ff ff  6...............
[   39.531313] <3>ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff  ................
[   39.531315] <3>ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff  ................
[   39.531317] <3>ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff  ................
[   39.531319] 
[   39.610045] [drm:edid_is_valid] *ERROR* EDID checksum is invalid, remainder is 52
[   39.610051] [drm:edid_is_valid] *ERROR* Raw EDID:
[   39.610054] <3>00 ff ff ff ff ff ff 00 5a 63 1f 70 01 01 01 01  ........Zc.p....
[   39.610057] <3>05 11 01 03 08 29 1a 78 2e 9b b6 a4 53 4b 9d 24  .....).x....SK.$
[   39.610059] <3>14 4f 54 bf ef 80 95 00 95 0f 81 80 81 40 71 4f  .OT..........@qO
[   39.610062] <3>01 01 01 01 01 01 9a 29 a0 d0 51 84 22 30 50 98  .......)..Q."0P.
[   39.610064] <3>36 00 98 ff 10 00 ff ff ff ff ff ff ff ff ff ff  6...............
[   39.610066] <3>ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff  ................
[   39.610069] <3>ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff  ................
[   39.610071] <3>ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff  ................
[   39.610073] 
[   44.398158] UDF-fs: Partition marked readonly; forcing readonly mount
[   44.474290] UDF-fs INFO UDF: Mounting volume 'BEST_OF_COSBY', timestamp 2007/07/18 03:10 (1e5c)
digitalnite@ubuntu:~$ 

I look forward to seeing what you think I should do.

Thanks,
digital_nite

---

### Post by davidmohammed on 2010-08-11
you've got messages in the reply indicating that you've got a broadcom type device (look at the trace - various "b43") errors.

Assuming that this is the case - there should be a driver offered in "administration - hardware drivers".  If this is the case - just activate it.


n.b. I'm assuming you are using lucid 10.04 and not an earlier version of ubuntu.

---

