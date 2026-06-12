---
title: "Netgear wg111 and kubuntu"
date: 2006-08-15
forum: Networking &amp; Wireless
---

### Post by kdotsky on 2006-08-15
Hello,
I'm running a virgin install of Kubuntu Dapper on a PC and am trying to get a Netgear WG111 wirless USB stick to work.  The install automatically detected the stick and the device showed up in iwconfig and ifconfig.  I set the essid via the gui, but the internet did not work.

I then followed the instructions [here]("http://www.ubuntuforums.org/showthread.php?t=212365"), to disable the native drivers and use ndiswrapper, but was still unsuccessful.  When doing rmmod bcm43xx, it said bcm43xx does not exist in /proc/modules.  The same happened for ndiswrapper.  After following the instructions, I am not able to change the essid with iwconfig.

Is there something different with my installation (perhaps being kubuntu?) that results in the previous instructions not working for me?

ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 00:11:11:44:99:99  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:35 errors:0 dropped:0 overruns:0 frame:0
          TX packets:35 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2540 (2.4 KiB)  TX bytes:2540 (2.4 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:14:6C:6C:8F:90  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


```

iwconfig:
```
wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  
          RTS thr:2432 B   Fragment thr:2432 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

lsmod:
```
Module                  Size  Used by
i915                   20608  1 
drm                    73236  2 i915
rfcomm                 40216  0 
l2cap                  26244  5 rfcomm
bluetooth              49892  4 rfcomm,l2cap
ppdev                   9220  0 
speedstep_lib           4484  0 
cpufreq_userspace       4696  0 
cpufreq_stats           5636  0 
freq_table              4740  1 cpufreq_stats
cpufreq_powersave       1920  0 
cpufreq_ondemand        6428  0 
cpufreq_conservative     7332  0 
video                  16260  0 
tc1100_wmi              6916  0 
sony_acpi               5644  0 
pcc_acpi               12416  0 
hotkey                 11556  0 
dev_acpi               11140  0 
container               4608  0 
button                  6672  0 
acpi_sbs               19980  0 
battery                 9988  1 acpi_sbs
i2c_acpi_ec             5120  1 acpi_sbs
i2c_core               21904  1 i2c_acpi_ec
ac                      5252  1 acpi_sbs
ndiswrapper           177364  0 
sg                     37920  0 
sd_mod                 19984  0 
af_packet              22920  4 
dm_mod                 58936  1 
md_mod                 72532  0 
lp                     11844  0 
tsdev                   8000  0 
e100                   40580  0 
mii                     5888  1 e100
usb_storage            74176  0 
scsi_mod              139496  3 sg,sd_mod,usb_storage
psmouse                36228  0 
serio_raw               7300  0 
snd_intel8x0           33692  1 
snd_ac97_codec         92704  1 snd_intel8x0
snd_ac97_bus            2304  1 snd_ac97_codec
shpchp                 45632  0 
snd_pcm_oss            53664  0 
snd_mixer_oss          18688  1 snd_pcm_oss
pci_hotplug            29236  1 shpchp
snd_pcm                89864  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25220  1 snd_pcm
snd                    55268  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10208  1 snd
snd_page_alloc         10632  2 snd_intel8x0,snd_pcm
parport_pc             35780  1 
pcspkr                  2180  0 
parport                36296  3 ppdev,lp,parport_pc
rtc                    13492  0 
intel_agp              22940  1 
agpgart                34888  3 drm,intel_agp
evdev                   9856  1 
ext3                  135688  1 
jbd                    58772  1 ext3
ide_generic             1536  0 
ehci_hcd               32008  0 
uhci_hcd               33680  0 
usbcore               129668  5 ndiswrapper,usb_storage,ehci_hcd,uhci_hcd
ide_cd                 33028  0 
cdrom                  38560  1 ide_cd
ide_disk               17664  3 
piix                   11012  1 
generic                 5124  0 
thermal                13576  0 
processor              23360  1 thermal
fan                     4868  0 
capability              5000  0 
commoncap               7296  1 capability
vga16fb                13704  1 
vgastate               10368  1 vga16fb
fbcon                  42784  72 
tileblit                2816  1 fbcon
font                    8320  1 fbcon
bitblit                 6272  1 fbcon
softcursor              2304  1 bitblit

```

dmesg:
```
[4294667.296000] Linux version 2.6.15-23-386 (buildd@rothera) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Tue May 23 13:49:40 UTC 2006
[4294667.296000] BIOS-provided physical RAM map:
[4294667.296000]  BIOS-e820: 0000000000000000 - 00000000000a0000 (usable)
[4294667.296000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[4294667.296000]  BIOS-e820: 0000000000100000 - 000000001fe70000 (usable)
[4294667.296000]  BIOS-e820: 000000001fe70000 - 000000001fe72000 (ACPI NVS)
[4294667.296000]  BIOS-e820: 000000001fe72000 - 000000001fe93000 (ACPI data)
[4294667.296000]  BIOS-e820: 000000001fe93000 - 000000001ff00000 (reserved)
[4294667.296000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[4294667.296000]  BIOS-e820: 00000000fecf0000 - 00000000fecf1000 (reserved)
[4294667.296000]  BIOS-e820: 00000000fed20000 - 00000000fed90000 (reserved)
[4294667.296000]  BIOS-e820: 00000000fee00000 - 00000000fee10000 (reserved)
[4294667.296000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[4294667.296000] 0MB HIGHMEM available.
[4294667.296000] 510MB LOWMEM available.
[4294667.296000] found SMP MP-table at 000fe710
[4294667.296000] On node 0 totalpages: 130672
[4294667.296000]   DMA zone: 4096 pages, LIFO batch:0
[4294667.296000]   DMA32 zone: 0 pages, LIFO batch:0
[4294667.296000]   Normal zone: 126576 pages, LIFO batch:31
[4294667.296000]   HighMem zone: 0 pages, LIFO batch:0
[4294667.296000] DMI 2.3 present.
[4294667.296000] ACPI: RSDP (v000 DELL                                  ) @ 0x000feb90
[4294667.296000] ACPI: RSDT (v001 DELL    3000    0x00000007 ASL  0x00000061) @ 0x000fd28b
[4294667.296000] ACPI: FADT (v001 DELL    3000    0x00000007 ASL  0x00000061) @ 0x000fd2bf
[4294667.296000] ACPI: SSDT (v001   DELL    st_ex 0x00001000 MSFT 0x0100000d) @ 0xfffd1a9a
[4294667.296000] ACPI: MADT (v001 DELL    3000    0x00000007 ASL  0x00000061) @ 0x000fd333
[4294667.296000] ACPI: BOOT (v001 DELL    3000    0x00000007 ASL  0x00000061) @ 0x000fd39f
[4294667.296000] ACPI: DSDT (v001   DELL    dt_ex 0x00001000 MSFT 0x0100000d) @ 0x00000000
[4294667.296000] ACPI: PM-Timer IO Port: 0x808
[4294667.296000] ACPI: Local APIC address 0xfee00000
[4294667.296000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[4294667.296000] Processor #0 15:3 APIC version 20
[4294667.296000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] disabled)
[4294667.296000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x01] disabled)
[4294667.296000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] disabled)
[4294667.296000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[4294667.296000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[4294667.296000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[4294667.296000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[4294667.296000] ACPI: IRQ0 used by override.
[4294667.296000] ACPI: IRQ2 used by override.
[4294667.296000] ACPI: IRQ9 used by override.
[4294667.296000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[4294667.296000] Using ACPI (MADT) for SMP configuration information
[4294667.296000] Allocating PCI resources starting at 20000000 (gap: 1ff00000:ded00000)
[4294667.296000] Built 1 zonelists
[4294667.296000] Kernel command line: root=/dev/hda1 ro quiet splash
[4294667.296000] mapped APIC to ffffd000 (fee00000)
[4294667.296000] mapped IOAPIC to ffffc000 (fec00000)
[4294667.296000] Initializing CPU#0
[4294667.296000] PID hash table entries: 2048 (order: 11, 32768 bytes)
[4294667.296000] Detected 2793.970 MHz processor.
[4294667.296000] Using pmtmr for high-res timesource
[4294667.296000] Console: colour VGA+ 80x25
[4294669.438000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[4294669.438000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[4294669.446000] Memory: 507444k/522688k available (1976k kernel code, 14628k reserved, 606k data, 288k init, 0k highmem)
[4294669.446000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[4294669.506000] Calibrating delay using timer specific routine.. 5589.45 BogoMIPS (lpj=2794726)
[4294669.506000] Security Framework v1.0.0 initialized
[4294669.506000] SELinux:  Disabled at boot.
[4294669.506000] Mount-cache hash table entries: 512
[4294669.506000] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 0000441d 00000000 00000000
[4294669.506000] CPU: After vendor identify, caps: bfebfbff 00000000 00000000 00000000 0000441d 00000000 00000000
[4294669.506000] monitor/mwait feature present.
[4294669.506000] using mwait in idle threads.
[4294669.506000] CPU: Trace cache: 12K uops, L1 D cache: 16K
[4294669.506000] CPU: L2 cache: 1024K
[4294669.506000] CPU: After all inits, caps: bfebfbff 00000000 00000000 00000080 0000441d 00000000 00000000
[4294669.506000] mtrr: v2.0 (20020519)
[4294669.506000] CPU: Intel(R) Pentium(R) 4 CPU 2.80GHz stepping 04
[4294669.506000] Enabling fast FPU save and restore... done.
[4294669.506000] Enabling unmasked SIMD FPU exception support... done.
[4294669.506000] Checking 'hlt' instruction... OK.
[4294669.510000] checking if image is initramfs... it is
[4294670.078000] Freeing initrd memory: 6834k freed
[4294670.084000] ACPI: Looking for DSDT ... not found!
[4294670.108000] ENABLING IO-APIC IRQs
[4294670.108000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[4294670.219000] NET: Registered protocol family 16
[4294670.219000] EISA bus registered
[4294670.219000] ACPI: bus type pci registered
[4294670.219000] PCI: PCI BIOS revision 2.10 entry at 0xfbbf8, last bus=1
[4294670.219000] PCI: Using configuration type 1
[4294670.219000] ACPI: Subsystem revision 20051216
[4294670.246000] ACPI: Interpreter enabled
[4294670.246000] ACPI: Using IOAPIC for interrupt routing
[4294670.251000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[4294670.251000] PCI: Probing PCI hardware (bus 00)
[4294670.251000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[4294670.266000] Boot video device is 0000:00:02.0
[4294670.266000] PCI quirk: region 0800-087f claimed by ICH4 ACPI/GPIO/TCO
[4294670.266000] PCI quirk: region 0880-08bf claimed by ICH4 GPIO
[4294670.266000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
[4294670.267000] PCI: Transparent bridge - 0000:00:1e.0
[4294670.267000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[4294670.419000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[4294670.435000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 15)
[4294670.436000] ACPI: PCI Interrupt Link [LNKB] (IRQs *3 4 5 6 7 9 10 11 12 15)
[4294670.437000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 9 10 11 12 15)
[4294670.438000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 *10 11 12 15)
[4294670.438000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 *9 10 11 12 15)
[4294670.439000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
[4294670.440000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 *10 11 12 15)
[4294670.441000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *9 10 11 12 15)
[4294670.441000] Linux Plug and Play Support v0.97 (c) Adam Belay
[4294670.441000] pnp: PnP ACPI init
[4294670.468000] pnp: PnP ACPI: found 10 devices
[4294670.468000] PnPBIOS: Disabled by ACPI PNP
[4294670.468000] PCI: Using ACPI for IRQ routing
[4294670.468000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[4294670.480000] pnp: 00:09: ioport range 0x800-0x85f could not be reserved
[4294670.480000] pnp: 00:09: ioport range 0xc00-0xc7f has been reserved
[4294670.480000] pnp: 00:09: ioport range 0x860-0x8ff could not be reserved
[4294670.480000] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
[4294670.480000] PCI: Bridge: 0000:00:1e.0
[4294670.480000]   IO window: d000-dfff
[4294670.480000]   MEM window: fea00000-feafffff
[4294670.480000]   PREFETCH window: disabled.
[4294670.480000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[4294670.480000] Simple Boot Flag value 0x87 read from CMOS RAM was invalid
[4294670.480000] Simple Boot Flag at 0x7a set to 0x1
[4294670.481000] audit: initializing netlink socket (disabled)
[4294670.481000] audit(1155667957.480:1): initialized
[4294670.481000] VFS: Disk quotas dquot_6.5.1
[4294670.481000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[4294670.481000] Initializing Cryptographic API
[4294670.481000] io scheduler noop registered
[4294670.481000] io scheduler anticipatory registered
[4294670.481000] io scheduler deadline registered
[4294670.481000] io scheduler cfq registered
[4294670.481000] isapnp: Scanning for PnP cards...
[4294670.836000] isapnp: No Plug & Play device found
[4294670.853000] PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
[4294670.857000] serio: i8042 AUX port at 0x60,0x64 irq 12
[4294670.858000] serio: i8042 KBD port at 0x60,0x64 irq 1
[4294670.858000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[4294670.858000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294670.860000] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294670.861000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[4294670.861000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294670.861000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[4294670.861000] mice: PS/2 mouse device common for all mice
[4294670.861000] EISA: Probing bus 0 at eisa.0
[4294670.861000] EISA: Detected 0 cards.
[4294670.862000] NET: Registered protocol family 2
[4294670.871000] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[4294670.871000] TCP established hash table entries: 16384 (order: 4, 65536 bytes)
[4294670.871000] TCP bind hash table entries: 16384 (order: 4, 65536 bytes)
[4294670.871000] TCP: Hash tables configured (established 16384 bind 16384)
[4294670.871000] TCP reno registered
[4294670.871000] TCP bic registered
[4294670.871000] NET: Registered protocol family 1
[4294670.871000] NET: Registered protocol family 8
[4294670.871000] NET: Registered protocol family 20
[4294670.871000] Using IPI Shortcut mode
[4294670.871000] ACPI wakeup devices: 
[4294670.871000] VBTN PCI0 USB0 USB1 USB2 USB3 PCI1  KBD 
[4294670.871000] ACPI: (supports S0 S1 S3 S4 S5)
[4294670.871000] Freeing unused kernel memory: 288k freed
[4294670.888000] input: AT Translated Set 2 keyboard as /class/input/input0
[4294670.917000] vga16fb: initializing
[4294670.917000] vga16fb: mapped to 0xc00a0000
[4294671.034000] Console: switching to colour frame buffer device 80x25
[4294671.034000] fb0: VGA16 VGA frame buffer device
[4294672.127000] Capability LSM initialized
[4294672.591000] ICH5: IDE controller at PCI slot 0000:00:1f.1
[4294672.591000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 169
[4294672.591000] ICH5: chipset revision 2
[4294672.591000] ICH5: not 100% native mode: will probe irqs later
[4294672.591000]     ide0: BM-DMA at 0xffa0-0xffa7, BIOS settings: hda:DMA, hdb:pio
[4294672.591000]     ide1: BM-DMA at 0xffa8-0xffaf, BIOS settings: hdc:DMA, hdd:pio
[4294672.591000] Probing IDE interface ide0...
[4294672.855000] hda: WDC WD400BB-75FJA1, ATA DISK drive
[4294673.467000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294673.471000] Probing IDE interface ide1...
[4294675.265000] hdc: Philips DVD+RW DVD8601, ATAPI CD/DVD-ROM drive
[4294675.877000] ide1 at 0x170-0x177,0x376 on irq 15
[4294675.887000] hda: max request size: 128KiB
[4294675.906000] hda: 78125000 sectors (40000 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(100)
[4294675.906000] hda: cache flushes supported
[4294675.906000]  hda: hda1 hda2 < hda5 >
[4294675.960000] hdc: ATAPI 40X DVD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
[4294675.960000] Uniform CD-ROM driver Revision: 3.20
[4294676.216000] usbcore: registered new driver usbfs
[4294676.217000] usbcore: registered new driver hub
[4294676.218000] USB Universal Host Controller Interface driver v2.3
[4294676.218000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 177
[4294676.218000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[4294676.218000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[4294676.219000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[4294676.219000] uhci_hcd 0000:00:1d.0: irq 177, io base 0x0000ff80
[4294676.219000] hub 1-0:1.0: USB hub found
[4294676.219000] hub 1-0:1.0: 2 ports detected
[4294676.320000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 185
[4294676.320000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[4294676.320000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[4294676.320000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[4294676.320000] uhci_hcd 0000:00:1d.1: irq 185, io base 0x0000ff60
[4294676.320000] hub 2-0:1.0: USB hub found
[4294676.320000] hub 2-0:1.0: 2 ports detected
[4294676.421000] ACPI: PCI Interrupt 0000:00:1d.3[A] -> GSI 16 (level, low) -> IRQ 177
[4294676.421000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[4294676.421000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[4294676.421000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 3
[4294676.421000] uhci_hcd 0000:00:1d.3: irq 177, io base 0x0000ff20
[4294676.421000] hub 3-0:1.0: USB hub found
[4294676.421000] hub 3-0:1.0: 2 ports detected
[4294676.523000] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 193
[4294676.523000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[4294676.523000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[4294676.523000] ehci_hcd 0000:00:1d.7: debug port 1
[4294676.523000] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[4294676.523000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[4294676.523000] ehci_hcd 0000:00:1d.7: irq 193, io mem 0xffa80800
[4294676.526000] usb 1-1: new full speed USB device using uhci_hcd and address 2
[4294676.527000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[4294676.528000] hub 4-0:1.0: USB hub found
[4294676.528000] hub 4-0:1.0: 8 ports detected
[4294676.694000] Attempting manual resume
[4294676.763000] EXT3-fs: mounted filesystem with ordered data mode.
[4294676.779000] kjournald starting.  Commit interval 5 seconds
[4294676.893000] usb 4-1: new high speed USB device using ehci_hcd and address 2
[4294677.219000] usb 4-7: new high speed USB device using ehci_hcd and address 3
[4294686.795000] Linux agpgart interface v0.101 (c) Dave Jones
[4294686.807000] agpgart: Detected an Intel 865 Chipset.
[4294686.808000] agpgart: Detected 892K stolen memory.
[4294686.823000] agpgart: AGP aperture is 128M @ 0xe8000000
[4294687.046000] Real Time Clock Driver v1.12
[4294687.107000] input: PC Speaker as /class/input/input1
[4294687.150000] parport: PnPBIOS parport detected.
[4294687.150000] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
[4294687.339000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294687.360000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[4294687.380000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 201
[4294687.380000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[4294687.399000] hw_random: RNG not detected
[4294687.690000] SCSI subsystem initialized
[4294687.694000] intel8x0_measure_ac97_clock: measured 50628 usecs
[4294687.694000] intel8x0: clocking to 48000
[4294687.705000] Initializing USB Mass Storage driver...
[4294687.706000] scsi0 : SCSI emulation for USB Mass Storage devices
[4294687.706000] usb-storage: device found at 3
[4294687.706000] usb-storage: waiting for device to settle before scanning
[4294687.706000] usbcore: registered new driver usb-storage
[4294687.706000] USB Mass Storage support registered.
[4294687.777000] e100: Intel(R) PRO/100 Network Driver, 3.4.14-k4-NAPI
[4294687.777000] e100: Copyright(c) 1999-2005 Intel Corporation
[4294687.777000] ACPI: PCI Interrupt 0000:01:08.0[A] -> GSI 20 (level, low) -> IRQ 209
[4294687.798000] e100: eth0: e100_probe: addr 0xfeaef000, irq 209, MAC addr 00:11:11:44:99:99
[4294687.893000] logips2pp: Detected unknown logitech mouse model 85
[4294688.003000] input: ImPS/2 Logitech Wheel Mouse as /class/input/input2
[4294688.113000] ts: Compaq touchscreen protocol output
[4294688.209000] lp0: using parport0 (interrupt-driven).
[4294688.259000] Adding 1502036k swap on /dev/hda5.  Priority:-1 extents:1 across:1502036k
[4294688.382000] EXT3 FS on hda1, internal journal
[4294688.525000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294688.525000] md: bitmap version 4.39
[4294688.973000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[4294689.443000] NET: Registered protocol family 17
[4294692.706000]   Vendor: SMART G2  Model: Dell Memory Key   Rev: 1.04
[4294692.706000]   Type:   Direct-Access                      ANSI SCSI revision: 01 CCS
[4294692.707000] usb-storage: device scan complete
[4294692.743000] Driver 'sd' needs updating - please use bus_type methods
[4294692.744000] SCSI device sda: 251904 512-byte hdwr sectors (129 MB)
[4294692.745000] sda: Write Protect is off
[4294692.745000] sda: Mode Sense: 23 00 00 00
[4294692.745000] sda: assuming drive cache: write through
[4294692.748000] SCSI device sda: 251904 512-byte hdwr sectors (129 MB)
[4294692.749000] sda: Write Protect is off
[4294692.749000] sda: Mode Sense: 23 00 00 00
[4294692.749000] sda: assuming drive cache: write through
[4294692.749000]  sda: unknown partition table
[4294692.752000] sd 0:0:0:0: Attached scsi removable disk sda
[4294692.760000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[4294694.087000] ndiswrapper version 1.8 loaded (preempt=yes,smp=no)
[4294694.172000] ndiswrapper: driver net111v2 (NETGEAR Inc.,3/16/2006,5.1213.06.0316) loaded
[4294697.871000] wlan0: vendor: 'Realtek RTL8187 Wireless LAN USB NIC                                     '
[4294697.871000] wlan0: ndiswrapper ethernet device 00:14:6c:6c:8f:90 using driver net111v2, 0846:6A00.F.conf
[4294697.871000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[4294697.871000] usbcore: registered new driver ndiswrapper
[4294760.799000] ACPI: Power Button (FF) [PWRF]
[4294760.799000] ACPI: Power Button (CM) [VBTN]
[4294760.913000] ibm_acpi: ec object not found
[4294760.932000] pcc_acpi: loading...
[4294762.847000] ppdev: user-space parallel port driver
[4294763.145000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[4294763.145000] apm: overridden by ACPI.
[4294767.353000] Bluetooth: Core ver 2.8
[4294767.353000] NET: Registered protocol family 31
[4294767.353000] Bluetooth: HCI device and connection manager initialized
[4294767.353000] Bluetooth: HCI socket layer initialized
[4294767.412000] Bluetooth: L2CAP ver 2.8
[4294767.412000] Bluetooth: L2CAP socket layer initialized
[4294767.436000] Bluetooth: RFCOMM socket layer initialized
[4294767.436000] Bluetooth: RFCOMM TTY layer initialized
[4294767.436000] Bluetooth: RFCOMM ver 1.7
[4294769.676000] [drm] Initialized drm 1.0.1 20051102
[4294769.679000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 177
[4294769.679000] [drm] Initialized i915 1.4.0 20060119 on minor 0

```
Thanks.

---

### Post by Darkhack on 2006-08-15
I would try using the native drivers first and ndiswrapper as a last resort.  Assuming Ubuntu detects your card you should be able to configure it with the GUI.  Make sure you have your WEP or WPA key entered or else it won't be able to connect.  Also make sure you activate the device and deactive eth0 or whatever ethernet card you are not using in place of the wireless.  If you can, try to be more specific as to why the native drivers aren't working.

---

### Post by kdotsky on 2006-08-16
From related threads I've gathered that the native drivers are experimental and do not work properly.  In addition, pretty much every other thread regarding this device involves ndiswrapper.

Anyway, when I initially tried using the native drivers I think it was a similar result... all I did was change the ESSID in the gui (which if I remember correctly worked) but there was no internet connectivity.  I don't think I could do a scan either.

Thanks.

---

### Post by kdotsky on 2006-08-16
Bump.

---

### Post by kdotsky on 2006-08-16
I think ndiswrapper and the drivers are all set up properly at this point, and everything looks fine with iwconfig/ifconfig.  I think the main symptom right now is that I cannot change my ESSID (through iwconfig or the kubuntu gui) or do "iwlist scan" (no scan results).

---

