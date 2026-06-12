---
title: "linksys (acx111) not working anymore"
date: 2006-11-09
forum: Networking &amp; Wireless
---

### Post by phreakshew on 2006-11-09
OK- I HAD my wireless card workig fine in Dapper, using my Linksys WPC54Gver.2 card in my old HP Pavillion lappy.

Then, mysteriously, it stopped working!  The card workd fine in another (windows) machine and this Pavillion could get onto the net via cable, but no more WIFI!

Sooooo, because there were some weird issues [(see this thread)]("http://ubuntuforums.org/showthread.php?t=280878") I decided to remove ndiswrapper and try the ACX driver, following [this howto]("https://help.ubuntu.com/community/WifiDocs/Driver/acx111?action=show&amp;redirect=WifiDocs%2FDevice%2FAcx111#head-1aaa70f54b4b3014b2c72a71d8da22ec02ba3bbb") verbatim.

Now, my card does not show up at all and I am extremely upset. GRRRRRRRRRRRRRRRRRRRRRR

Any and all help is greatly appreciated!

thanx

---

### Post by wieman01 on 2006-11-09
Can you tell me what chipset your card has?

---

### Post by phreakshew on 2006-11-10
my chipset is the Texas Instruments ACX 111

---

### Post by wieman01 on 2006-11-10
According to this Wiki, you ought to use "ndiswrapper":

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/List")

It's also a Broadcom chipset. Have you tried "ndiswrapper" before?

[http://www.ubuntuforums.org/showthread.php?t=25683&highlight=Broadcom+4301]("http://www.ubuntuforums.org/showthread.php?t=25683&highlight=Broadcom+4301")

---

### Post by phreakshew on 2006-11-10
Actually, it's not a Broadcom chipset, per the [ndiswrapper wiki's card list]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/List")

Card: Linksys #[WPC54G v2], 54Mbps -- [link here|List#WPC54G v2]

    * Chipset: Texas Instruments ACX 111
    * pciid: 104c:9066
    * Driver: Linksys 

Mine is ver.2; ver. 1 and 3 are Broadcom.

Yes, as I stated in [this thread]("http://ubuntuforums.org/showthread.php?t=280878")

I used ndiswrapper and it worked, but,

when I typed "sudo ndiswrapper -l" in a terminal, I got: 
Installed ndis drivers:
lsbcmnds invalid driver!
lstinds invalid driver!

What's more, going to System / Administration / Windows Wireless Drivers
shows lsbcmnds and lstinds, but they both say "Hardware present: No."

Nobody could tell me why my WIFI card was working when my system says that the drivers are invalid and that my hardware is not present.

ANYWAY, it suddenly STOPPED working the other day for no apparant reason.

Also, I found this:
Ndiswrapper is not needed. In Ubuntu Dapper (and probably in other Linux distributions as well) this card is supported natively with the acx driver. See [http://ubuntuforums.org/showthread.php?t=75448](http://ubuntuforums.org/showthread.php?t=75448) --neu or [http://ubuntuforums.org/showpost.php?p=1114757&postcount=31](http://ubuntuforums.org/showpost.php?p=1114757&postcount=31) for a summary of the fix --GigaClon

which led me to believe maybe I should try the ACX driver instead.  That did not work either, so last night I decided to start all the way over and reinstall my OS hoping that the native driver would recognize it.  It does sort of; the lights are on, it lists my card under networking, but no internet, no ping [www.anything](www.anything).

phooey.

---

### Post by FrodoB on 2006-11-10
Post your outputs from the following utilities for the group to see:

iwconfig

ifconfig

dmesg

a copy of the file /etc/networks/interfaces

---

### Post by phreakshew on 2006-11-10
welllllll, this is how it went:

I reinstalled my OS (Ubuntu-Dapper 6.06) and while it was loading from the CD I made sure my Linksys card was plugged in.  

Then, I opened up sudo gedit /etc/modprobe.d/options and added the following 2 lines:

#Ensure a working version of the acx111 firmware is used.
options acx firmware_ver=1.2.1.34

Even though the lights on my card were on, I could not connect to the net.  So then I unplugged that card and inserted my PCMCIA ethernet card which allowed me to connect and download ALL the updates.  

Of course, I did sudo gedit /etc/apt/sources.list and uncommented lines first, then sudo apt/get/update to update the repositories before I installed the updates. 

Restarted the system, and during the process I switched out the Ethernet card for my WIFI card.

Ubuntu loaded up, went to System/Administration/Networking, and highlighted my card, making sure it was active and the default gateway was set to wlan0.  I checked properties, and found my Belkin54g router was listed under ESSID.  CLicked OK all the way out, and now I'm online and typing this very message from the computer in quesiton.  Whew!

Although it's a moot point now, here's my outputs:

$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11b+/g+  ESSID:"belkin54g"  Nickname:"acx v0.3.21"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:30:BD:9A:39:96
          Bit Rate:54 Mb/s   Tx-Power=15 dBm   Sensitivity=1/3
          Retry min limit:7   RTS thr:off
          Power Management:off
          Link Quality=44/100  Signal level=22/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.


$ ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:15 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:772 (772.0 b)  TX bytes:772 (772.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:12:17:B1:46:CE
          inet addr:192.168.2.5  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::212:17ff:feb1:46ce/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3202 errors:6 dropped:0 overruns:0 frame:0
          TX packets:3194 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3061840 (2.9 MiB)  TX bytes:449511 (438.9 KiB)
          Interrupt:11


$ dmesg
[17179569.184000] Linux version 2.6.15-27-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Sat Sep 16 01:51:59 UTC 2006
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 00000000177f0000 (usable)
[17179569.184000]  BIOS-e820: 00000000177f0000 - 00000000177fffc0 (ACPI data)
[17179569.184000]  BIOS-e820: 00000000177fffc0 - 0000000017800000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 375MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 96240
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   DMA32 zone: 0 pages, LIFO batch:0
[17179569.184000]   Normal zone: 92144 pages, LIFO batch:31
[17179569.184000]   HighMem zone: 0 pages, LIFO batch:0
[17179569.184000] DMI 2.2 present.
[17179569.184000] ACPI: RSDP (v000 OID_00                                ) @ 0x000e4010
[17179569.184000] ACPI: RSDT (v001 OID_00 RSDT_000 0x30303030 &#65533;& 0x00010000) @ 0x177ffbd0
[17179569.184000] ACPI: FADT (v001 SYSSFT FACP_000 0x00000100 &#65533;& 0x00010000) @ 0x177ffb20
[17179569.184000] ACPI: BOOT (v001 SYSSFT SYS_BOOT 0x00000100 &#65533;& 0x00010000) @ 0x177ffba0
[17179569.184000] ACPI: DSDT (v001 LTLVIA INSYDESW 0x00001001 MSFT 0x0100000c) @ 0x00000000
[17179569.184000] ACPI: BIOS age (1999) fails cutoff (2000), acpi=force is required to enable ACPI
[17179569.184000] ACPI: Disabling ACPI support
[17179569.184000] Allocating PCI resources starting at 20000000 (gap: 17800000:e8780000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda1 ro quiet splash
[17179569.184000] No local APIC present or hardware disabled
[17179569.184000] mapped APIC to ffffd000 (012f2000)
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 2048 (order: 11, 32768 bytes)
[    0.000000] Detected 477.364 MHz processor.
[ 3927.701402] Using tsc for high-res timesource
[ 3927.702989] Console: colour VGA+ 80x25
[ 3927.706282] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[ 3927.709053] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[ 3927.777100] Memory: 371124k/384960k available (1976k kernel code, 13336k reserved, 606k data, 288k init, 0k highmem)
[ 3927.777117] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[ 3927.853593] Calibrating delay using timer specific routine.. 956.26 BogoMIPS (lpj=1912536)
[ 3927.853774] Security Framework v1.0.0 initialized
[ 3927.853815] SELinux:  Disabled at boot.
[ 3927.853897] Mount-cache hash table entries: 512
[ 3927.854564] CPU: After generic identify, caps: 008021bf 808029bf 00000000 00000000 00000000 00000000 00000000
[ 3927.854604] CPU: After vendor identify, caps: 008021bf 808029bf 00000000 00000000 00000000 00000000 00000000
[ 3927.854638] CPU: L1 I Cache: 32K (32 bytes/line), D cache 32K (32 bytes/line)[ 3927.854650] CPU: After all inits, caps: 008021bf 808029bf 00000000 00000002 00000000 00000000 00000000
[ 3927.854744] mtrr: v2.0 (20020519)
[ 3927.854756] CPU: AMD-K6(tm) 3D processor stepping 0c
[ 3927.854779] Checking 'hlt' instruction... OK.
[ 3927.870327] checking if image is initramfs... it is
[ 3931.231927] Freeing initrd memory: 6616k freed
[ 3931.310142] NET: Registered protocol family 16
[ 3931.310313] EISA bus registered
[ 3931.310732] PCI: PCI BIOS revision 2.10 entry at 0xeb800, last bus=1
[ 3931.310756] PCI: Using configuration type 1
[ 3931.312857] ACPI: Subsystem revision 20051216
[ 3931.312869] ACPI: Interpreter disabled.
[ 3931.312881] Linux Plug and Play Support v0.97 (c) Adam Belay
[ 3931.312927] pnp: PnP ACPI: disabled
[ 3931.312988] PnPBIOS: Scanning system for PnP BIOS support...
[ 3931.313639] PnPBIOS: Found PnP BIOS installation structure at 0xc00ff020
[ 3931.313660] PnPBIOS: PnP BIOS version 1.0, entry 0xec000:0x3128, dseg 0xec000[ 3931.320224] PnPBIOS: 15 nodes reported by PnP BIOS; 15 recorded by driver
[ 3931.320319] PCI: Probing PCI hardware
[ 3931.320336] PCI: Probing PCI hardware (bus 00)
[ 3931.320981] PCI quirk: region 1600-167f claimed by vt82c686 HW-mon
[ 3931.320997] PCI quirk: region 1400-140f claimed by vt82c686 SMB
[ 3931.321509] Boot video device is 0000:01:00.0
[ 3931.325204] PCI: Using IRQ router VIA [1106/0686] at 0000:00:07.0
[ 3931.330683] pnp: 00:01: ioport range 0x4d0-0x4d1 has been reserved
[ 3931.330702] pnp: 00:01: ioport range 0x1000-0x107f has been reserved
[ 3931.330717] pnp: 00:01: ioport range 0x1600-0x167f has been reserved
[ 3931.330730] pnp: 00:01: ioport range 0x1400-0x140f has been reserved
[ 3931.332527] PCI: Bridge: 0000:00:01.0
[ 3931.332543]   IO window: a000-afff
[ 3931.332555]   MEM window: 40000000-470fffff
[ 3931.332566]   PREFETCH window: 48000000-4f0fffff
[ 3931.332580] PCI: Bus 2, cardbus bridge: 0000:00:0a.0
[ 3931.332590]   IO window: 00001800-000018ff
[ 3931.332602]   IO window: 00001c00-00001cff
[ 3931.332614]   PREFETCH window: 24000000-25ffffff
[ 3931.332626]   MEM window: 26000000-27ffffff
[ 3931.332650] PCI: Setting latency timer of device 0000:00:01.0 to 64
[ 3931.332681] PCI: Found IRQ 11 for device 0000:00:0a.0
[ 3931.333158] Simple Boot Flag at 0x37 set to 0x1
[ 3931.336446] audit: initializing netlink socket (disabled)
[ 3931.336498] audit(1163197833.920:1): initialized
[ 3931.337278] VFS: Disk quotas dquot_6.5.1
[ 3931.337420] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[ 3931.337734] Initializing Cryptographic API
[ 3931.337757] io scheduler noop registered
[ 3931.337807] io scheduler anticipatory registered
[ 3931.337842] io scheduler deadline registered
[ 3931.337907] io scheduler cfq registered
[ 3931.337932] PCI: Disabling Via external APIC routing
[ 3931.338969] isapnp: Scanning for PnP cards...
[ 3931.693663] isapnp: No Plug & Play device found
[ 3931.870253] PNP: PS/2 Controller [PNP0303,PNP0f13] at 0x60,0x64 irq 1,12
[ 3931.895311] serio: i8042 AUX port at 0x60,0x64 irq 12
[ 3931.897864] serio: i8042 KBD port at 0x60,0x64 irq 1
[ 3931.898145] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[ 3931.898645] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[ 3931.921455] 00:0d: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[ 3931.925485] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[ 3931.925802] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[ 3931.925821] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[ 3931.926675] mice: PS/2 mouse device common for all mice
[ 3931.930425] EISA: Probing bus 0 at eisa.0
[ 3931.930452] Cannot allocate resource for EISA slot 1
[ 3931.930472] Cannot allocate resource for EISA slot 3
[ 3931.930516] EISA: Detected 0 cards.
[ 3931.930755] NET: Registered protocol family 2
[ 3931.965132] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[ 3931.966133] TCP established hash table entries: 16384 (order: 4, 65536 bytes)[ 3931.966833] TCP bind hash table entries: 16384 (order: 4, 65536 bytes)
[ 3931.967568] TCP: Hash tables configured (established 16384 bind 16384)
[ 3931.967581] TCP reno registered
[ 3931.968046] TCP bic registered
[ 3931.968094] NET: Registered protocol family 1
[ 3931.968131] NET: Registered protocol family 8
[ 3931.968139] NET: Registered protocol family 20
[ 3931.968244] Using IPI Shortcut mode
[ 3931.968402] Freeing unused kernel memory: 288k freed
[ 3931.981803] input: AT Translated Set 2 keyboard as /class/input/input0
[ 3932.314534] vga16fb: initializing
[ 3932.314568] vga16fb: mapped to 0xc00a0000
[ 3932.375611] Console: switching to colour frame buffer device 80x25
[ 3932.375639] fb0: VGA16 VGA frame buffer device
[ 3933.547245] Capability LSM initialized
[ 3937.161605] VP_IDE: IDE controller at PCI slot 0000:00:07.1
[ 3937.161653] PCI: Via IRQ fixup for 0000:00:07.1, from 255 to 0
[ 3937.161696] VP_IDE: chipset revision 6
[ 3937.161706] VP_IDE: not 100% native mode: will probe irqs later
[ 3937.161742] VP_IDE: VIA vt82c686a (rev 1b) IDE UDMA66 controller on pci0000:00:07.1
[ 3937.161773]     ide0: BM-DMA at 0x1100-0x1107, BIOS settings: hda:DMA, hdb:pio
[ 3937.161843]     ide1: BM-DMA at 0x1108-0x110f, BIOS settings: hdc:DMA, hdd:pio
[ 3937.161902] Probing IDE interface ide0...
[ 3937.575885] hda: FUJITSU MHK2120AT, ATA DISK drive
[ 3938.258716] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[ 3938.259504] Probing IDE interface ide1...
[ 3939.123571] hdc: TOSHIBA DVD-ROM SD-C2402, ATAPI CD/DVD-ROM drive
[ 3939.482813] ide1 at 0x170-0x177,0x376 on irq 15
[ 3939.523725] hda: max request size: 128KiB
[ 3939.603696] hda: 23579136 sectors (12072 MB) w/512KiB Cache, CHS=23392/16/63, UDMA(66)
[ 3939.603733] hda: cache flushes not supported
[ 3939.604505]  hda: hda1 hda2 < hda5 >
[ 3939.675407] hdc: ATAPI 24X DVD-ROM drive, 128kB Cache, DMA
[ 3939.675447] Uniform CD-ROM driver Revision: 3.20
[ 3940.397557] usbcore: registered new driver usbfs
[ 3940.399682] usbcore: registered new driver hub
[ 3940.409876] USB Universal Host Controller Interface driver v2.3
[ 3940.412231] PCI: Found IRQ 10 for device 0000:00:07.2
[ 3940.412299] uhci_hcd 0000:00:07.2: UHCI Host Controller
[ 3940.414645] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
[ 3940.414684] uhci_hcd 0000:00:07.2: irq 10, io base 0x00003000
[ 3940.416548] hub 1-0:1.0: USB hub found
[ 3940.416639] hub 1-0:1.0: 2 ports detected
[ 3940.826799] Attempting manual resume
[ 3940.962822] EXT3-fs: mounted filesystem with ordered data mode.
[ 3940.967263] kjournald starting.  Commit interval 5 seconds
[ 3969.790516] Linux agpgart interface v0.101 (c) Dave Jones
[ 3969.808654] agpgart: Detected VIA Apollo MVP4 chipset
[ 3969.811243] agpgart: AGP aperture is 32M @ 0x20000000
[ 3970.339216] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[ 3970.354849] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[ 3970.532356] parport_pc: VIA 686A/8231 detected
[ 3970.532376] parport_pc: probing current configuration
[ 3970.532404] parport_pc: Current parallel port base: 0x378
[ 3970.532501] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
[ 3970.629795] parport_pc: VIA parallel port: io=0x378, irq=7
[ 3971.885016] PCI: Found IRQ 11 for device 0000:00:0a.0
[ 3971.885095] Yenta: CardBus bridge found at 0000:00:0a.0 [103c:000f]
[ 3971.885129] Yenta O2: res at 0x94/0xD4: 00/e0
[ 3971.885139] Yenta O2: old bridge, disabling read prefetch/write burst
[ 3972.070150] Yenta: ISA IRQ mask 0x0008, PCI irq 11
[ 3972.070168] Socket status: 30000821
[ 3973.589074] pccard: CardBus card inserted into slot 0
[ 3973.829974] Synaptics Touchpad, model: 1, fw: 4.6, id: 0x135eb1, caps: 0x804713/0x0
[ 3973.921395] input: SynPS/2 Synaptics TouchPad as /class/input/input1
[ 3974.602894] Real Time Clock Driver v1.12
[ 3974.887077] input: PC Speaker as /class/input/input2
[ 3975.586233] PCI: Found IRQ 5 for device 0000:00:0d.0
[ 3975.903226] Floppy drive(s): fd0 is 1.44M
[ 3976.015699] FDC 0 is a post-1991 82077
[ 3976.992104] cs: IO port probe 0x100-0x3af: excluding 0x200-0x207
[ 3976.994820] cs: IO port probe 0x3e0-0x4ff: clean.
[ 3976.996008] cs: IO port probe 0x820-0x8ff: clean.
[ 3976.997126] cs: IO port probe 0xc00-0xcf7: clean.
[ 3976.998928] cs: IO port probe 0xa00-0xaff: clean.
[ 3977.229195] acx: Loaded combined PCI/USB driver, firmware_ver=1.2.1.34
[ 3977.229221] acx: compiled to use 32bit I/O access. I/O timing issues might occur, such as non-working firmware upload. Report them
[ 3977.231964] PCI: Enabling device 0000:02:00.0 (0000 -> 0002)
[ 3977.231995] PCI: Setting latency timer of device 0000:02:00.0 to 64
[ 3977.232071] acx: found ACX111-based wireless network card at 0000:02:00.0, irq:11, phymem1:0x26020000, phymem2:0x26000000, mem1:0xd8190000, mem1_size:8192, mem2:0xd8280000, mem2_size:131072
[ 3977.721031] ts: Compaq touchscreen protocol output
[ 3978.400276] acx: form factor 0x01 ((mini-)PCI / CardBus), radio type 0x16 (Radia), EEPROM version 0x05, uploaded firmware 'Rev 1.2.1.34' (0x03010101)
[ 3978.401547] acx v0.3.21: net device wlan0, driver compiled against wireless extensions 19 and Linux 2.6.15-27-386
[ 3978.404005] usbcore: registered new driver acx_usb
[ 3980.234106] lp0: using parport0 (interrupt-driven).
[ 3980.617389] Adding 514040k swap on /dev/hda5.  Priority:-1 extents:1 across:514040k
[ 3980.984565] EXT3 FS on hda1, internal journal
[ 3981.048580] NET: Registered protocol family 17
[ 3981.861492] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[ 3981.861513] md: bitmap version 4.39
[ 3983.472670] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[ 3984.885736] cdrom: open failed.
[ 4015.704968] ppdev: user-space parallel port driver
[ 4017.549298] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[ 4021.584553] wlan0 (WE) : Driver using old /proc/net/wireless support, please fix driver !
[ 4024.438279] hdc: drive_cmd: status=0x51 { DriveReady SeekComplete Error }
[ 4024.438316] hdc: drive_cmd: error=0x04 { AbortedCommand }
[ 4024.438331] ide: failed opcode was: 0xec
[ 4033.046295] Bluetooth: Core ver 2.8
[ 4033.046329] NET: Registered protocol family 31
[ 4033.046340] Bluetooth: HCI device and connection manager initialized
[ 4033.046403] Bluetooth: HCI socket layer initialized
[ 4033.112912] Bluetooth: L2CAP ver 2.8
[ 4033.112944] Bluetooth: L2CAP socket layer initialized
[ 4033.179445] Bluetooth: RFCOMM socket layer initialized
[ 4033.179536] Bluetooth: RFCOMM TTY layer initialized
[ 4033.179547] Bluetooth: RFCOMM ver 1.7
[ 4057.329672] NET: Registered protocol family 10
[ 4057.330304] lo: Disabled Privacy Extensions
[ 4057.330625] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4057.330795] IPv6 over IPv4 tunneling driver
[ 4186.729864] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4187.253629] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 4187.748064] wlan0: duplicate address detected!
[ 4202.776522] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4204.530348] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 4205.255459] wlan0: duplicate address detected!


/etc/network/interfaces:
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid belkin54g

---

### Post by DougInKY on 2006-11-20
Phreakshew, have you got roaming working yet? I used your method to get my wpc54g v2 card running (am using the wireless as I type this - YEAH!). I have  Gnome Network Manager running but it doesn't show my connection. The Network Monitor doesn't show the connection either. Any ideas?

---

### Post by FrodoB on 2006-11-20
Phreakshew;

Good job, this chipset is working for me out of the box on Edgy as well. Good to know that Dapper works as well.

FrodoB

---

### Post by phreakshew on 2006-11-22
not sure exactly what u mean- In 6.06 Dapper, I just go to system / administration / networking which opens up network settings.  Do not know Gnome network manager or network monitor- Still a noob, just learning on this distro-


> **DougInKY said:**
> Phreakshew, have you got roaming working yet? I used your method to get my wpc54g v2 card running (am using the wireless as I type this - YEAH!). I have  Gnome Network Manager running but it doesn't show my connection. The Network Monitor doesn't show the connection either. Any ideas?

---

### Post by phreakshew on 2006-11-25
so, I was experimenting with different hard drives (long story) and ended up reinstalling my OS- this time, after doing all the upates and getting my WIFI card working again, there was an extra little icon in the top toolbar that said "no network connection" Hmmmmmmmm I wondered- I WAS on, but this thingy said I wasn't- so I clicked on it and told it to find my connection- it could not, and then after that I could not get onto the net anymore! Crickey! So, I right clicked on that little bugger and disabled it and removed it from the toolbar, then went back into Networking and reconfigured my card- Voila! It works again- must be some sort of software conflict.....

---

### Post by lattemonster on 2007-07-17
Hello,

Finally got my Linksys Wireless-G Notebook Adapter WPC54G ver. 2.0 (WPC54G v2, wpc54g v2, wpc54gv2, WPC54Gv2) to work.  I used native Ubuntu 7.04 without any need for NDIS or the Microsoft drivers.

Here were my steps.

Installed latest, greatest Ubuntu 7.04.

In Desktop clicked on System / Administration / Network and configured my network (WEP key etc.) and saved it.

Went to Applications / Accessories / Terminal and typed the following:

uname -r

[Note:  Replace <kernel> with what gets outputted when you run uname -r in the following]

cd /lib/firmware/<kernel>/acx/default/  
sudo mv tiacx111c16 tiacx111c16.old
sudo ln -s ../1.2.0.30/tiacx111c16 tiacx111c16
sudo rmmod acx
sudo modprobe acx

sudo gedit /etc/modprobe.d/options and added the following 2 lines:

#Ensure a working version of the acx111 firmware is used.
options acx firmware_ver=1.2.1.34

Save, exit.

After that, I didn't even need to re-boot, went to Firefox and was on-line!

Yippeee!!  Thanks for the posting.  The key was editing the modprobe.d/options file for me

---

### Post by lattemonster on 2007-07-18
OK -- this is weird.  I'm on the Internet and all happy.  But now, my Network Manager does not show that I have a wireless connection.  Normally, under Network Manager in my system tray should show the wireless network listed but it is not showing.

Also, I'm trying to set-up a VPN connection using Network Manager but those options don't appear.  I have the latest versions of the Network Manager software, I've restarted -- can't figure it out.

Thanks for your help.

---

