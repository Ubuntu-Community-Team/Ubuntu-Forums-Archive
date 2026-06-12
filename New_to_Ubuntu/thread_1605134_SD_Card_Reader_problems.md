---
title: "SD Card Reader problems"
date: 2010-10-24
forum: New to Ubuntu
---

### Post by Kolfinna on 2010-10-24
Hello!

I am using a Sony Vaio VGN-P530H netbook which until recently had EasyPeasy installed on it; I have now upgraded to Ubuntu 10.04 and have encountered some issues regarding my SD card reader.

When I insert the card, the light next to the port flashes once, but it does not mount. I have used mountpy, but it's not picking up the interface to mount.

At this rate, I suspect it's a driver issue, but I wanted to clarify here and figure out what specifically I need to download/change to resolve the issue.

Here is the outpost of lsmod:
```
Module                  Size  Used by
tifm_sd                 8035  0 
tifm_core               6089  1 tifm_sd
isofs                  30022  0 
msdos                   6436  0 
vfat                    9201  0 
fat                    48240  2 msdos,vfat
aes_i586                7280  1 
aes_generic            26875  1 aes_i586
binfmt_misc             6599  1 
rfcomm                 33811  4 
sco                     7998  2 
bnep                    9542  2 
l2cap                  37008  16 rfcomm,bnep
parport_pc             26058  0 
ppdev                   5556  0 
dm_crypt               11385  0 
snd_hda_codec_realtek   217980  1 
arc4                    1165  2 
snd_hda_intel          22107  2 
snd_hda_codec          87552  2 snd_hda_codec_realtek,snd_hda_intel
ath9k                  88756  0 
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
ath9k_common            5982  1 ath9k
snd_seq_midi            4588  0 
ath9k_hw              292297  2 ath9k,ath9k_common
snd_rawmidi            17783  1 snd_seq_midi
ath                     8153  2 ath9k,ath9k_hw
mac80211              231541  2 ath9k,ath9k_common
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
btusb                  10969  2 
cfg80211              144470  4 ath9k,ath9k_common,ath,mac80211
i2c_isch                3086  0 
bluetooth              50500  9 rfcomm,sco,bnep,l2cap,btusb
sony_laptop            29088  0 
psmouse                59033  0 
snd                    49006  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw               4022  0 
led_class               2633  1 ath9k
soundcore                880  1 snd
lpc_sch                 1761  0 
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
dm_raid45              81721  0 
xor                    15136  1 dm_raid45
sky2                   45127  0 
video                  18712  0 
pata_sch                1975  5 
output                  1883  1 video

```

and lspci:
```
00:00.0 Host bridge: Intel Corporation System Controller Hub (SCH Poulsbo) (rev 06)
00:02.0 VGA compatible controller: Intel Corporation System Controller Hub (SCH Poulsbo) Graphics Controller (rev 06)
00:1b.0 Audio device: Intel Corporation System Controller Hub (SCH Poulsbo) HD Audio Controller (rev 06)
00:1c.0 PCI bridge: Intel Corporation System Controller Hub (SCH Poulsbo) PCI Express Port 1 (rev 06)
00:1c.1 PCI bridge: Intel Corporation System Controller Hub (SCH Poulsbo) PCI Express Port 2 (rev 06)
00:1d.0 USB Controller: Intel Corporation System Controller Hub (SCH Poulsbo) USB UHCI #1 (rev 06)
00:1d.1 USB Controller: Intel Corporation System Controller Hub (SCH Poulsbo) USB UHCI #2 (rev 06)
00:1d.2 USB Controller: Intel Corporation System Controller Hub (SCH Poulsbo) USB UHCI #3 (rev 06)
00:1d.7 USB Controller: Intel Corporation System Controller Hub (SCH Poulsbo) USB EHCI #1 (rev 06)
00:1f.0 ISA bridge: Intel Corporation System Controller Hub (SCH Poulsbo) LPC Bridge (rev 06)
00:1f.1 IDE interface: Intel Corporation System Controller Hub (SCH Poulsbo) IDE Controller (rev 06)
01:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8057 PCI-E Gigabit Ethernet Controller (rev 10)
02:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
```

Finally, dmesg with the card in:

```
[    0.507072] NET: Registered protocol family 1
[    0.507161] pci 0000:00:02.0: Boot video device
[    0.507329] PCI: CLS 0 bytes, default 64
[    0.507457] Simple Boot Flag at 0x44 set to 0x1
[    0.508604] cpufreq-nforce2: No nForce2 chipset.
[    0.508811] Scanning for low memory corruption every 60 seconds
[    0.509660] audit: initializing netlink socket (disabled)
[    0.509713] type=2000 audit(1287910592.504:1): initialized
[    0.557927] highmem bounce pool size: 64 pages
[    0.557961] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.568922] VFS: Disk quotas dquot_6.5.2
[    0.569334] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.573690] fuse init (API version 7.14)
[    0.574364] msgmni has been set to 1671
[    0.576647] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.576667] io scheduler noop registered
[    0.576680] io scheduler deadline registered
[    0.576785] io scheduler cfq registered (default)
[    0.577334] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.577710] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.578225] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.578778] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.579435] intel_idle: MWAIT substates: 0x3020220
[    0.579451] intel_idle: v0.4 model 0x1C
[    0.579463] intel_idle: lapic_timer_reliable_states 0x6
[    0.579501] Marking TSC unstable due to TSC halts in idle states deeper than C2
[    0.581531] ACPI: AC Adapter [AC] (on-line)
[    0.581999] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    0.583509] ACPI: Lid Switch [LID0]
[    0.583583] Switching to clocksource hpet
[    0.584035] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
[    0.584064] ACPI: Power Button [PWRB]
[    0.585222] ACPI: acpi_idle yielding to intel_idle
[    0.609548] thermal LNXTHERM:01: registered as thermal_zone0
[    0.609606] ACPI: Thermal Zone [ATF0] (60 C)
[    0.610107] ERST: Table is not found!
[    0.611124] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.621296] brd: module loaded
[    0.625539] loop: module loaded
[    0.627198] pata_acpi 0000:00:1f.1: setting latency timer to 64
[    0.629986] isapnp: Scanning for PnP cards...
[    0.658384] ACPI: Battery Slot [BAT0] (battery present)
[    0.679340] Fixed MDIO Bus: probed
[    0.679679] PPP generic driver version 2.4.2
[    0.680008] tun: Universal TUN/TAP device driver, 1.6
[    0.680021] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.680555] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.680650] ehci_hcd 0000:00:1d.7: enabling device (0000 -> 0002)
[    0.680680]   alloc irq_desc for 20 on node -1
[    0.680693]   alloc kstat_irqs on node -1
[    0.680726] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 20 (level, low) -> IRQ 20
[    0.680802] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.680821] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.681132] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.683874] ehci_hcd 0000:00:1d.7: can't setup
[    0.683895] ehci_hcd 0000:00:1d.7: USB bus 1 deregistered
[    0.684187] ehci_hcd 0000:00:1d.7: PCI INT D disabled
[    0.684206] ehci_hcd 0000:00:1d.7: init 0000:00:1d.7 fail, -110
[    0.684232] ehci_hcd: probe of 0000:00:1d.7 failed with error -110
[    0.684349] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.684453] uhci_hcd: USB Universal Host Controller Interface driver
[    0.684596]   alloc irq_desc for 21 on node -1
[    0.684610]   alloc kstat_irqs on node -1
[    0.684642] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    0.684676] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.684693] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.684945] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    0.685101] uhci_hcd 0000:00:1d.0: irq 21, io base 0x00006040
[    0.685925] hub 1-0:1.0: USB hub found
[    0.685969] hub 1-0:1.0: 2 ports detected
[    0.686291]   alloc irq_desc for 22 on node -1
[    0.686306]   alloc kstat_irqs on node -1
[    0.686336] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 22 (level, low) -> IRQ 22
[    0.686369] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.686386] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.686635] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[    0.686741] uhci_hcd 0000:00:1d.1: irq 22, io base 0x00006020
[    0.687521] hub 2-0:1.0: USB hub found
[    0.687551] hub 2-0:1.0: 2 ports detected
[    0.687867]   alloc irq_desc for 23 on node -1
[    0.687882]   alloc kstat_irqs on node -1
[    0.687912] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 23 (level, low) -> IRQ 23
[    0.687945] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.687963] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.688231] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[    0.688348] uhci_hcd 0000:00:1d.2: irq 23, io base 0x00006000
[    0.689213] hub 3-0:1.0: USB hub found
[    0.689243] hub 3-0:1.0: 2 ports detected
[    0.689882] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.692872] i8042.c: Detected active multiplexing controller, rev 1.1.
[    0.695800] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.695849] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    0.696058] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    0.696237] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    0.696413] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    0.697257] mice: PS/2 mouse device common for all mice
[    0.698043] rtc_cmos 00:05: RTC can wake from S4
[    0.698288] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    0.698360] rtc0: alarms up to one day, 242 bytes nvram, hpet irqs
[    0.699137] device-mapper: uevent: version 1.0.3
[    0.708709] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: dm-devel@redhat.com
[    0.797194] device-mapper: multipath: version 1.1.1 loaded
[    0.797213] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.798020] EISA: Probing bus 0 at eisa.0
[    0.798038] EISA: Cannot allocate resource for mainboard
[    0.798056] Cannot allocate resource for EISA slot 1
[    0.798072] Cannot allocate resource for EISA slot 2
[    0.798087] Cannot allocate resource for EISA slot 3
[    0.798103] Cannot allocate resource for EISA slot 4
[    0.798118] Cannot allocate resource for EISA slot 5
[    0.798134] Cannot allocate resource for EISA slot 6
[    0.798149] Cannot allocate resource for EISA slot 7
[    0.798165] Cannot allocate resource for EISA slot 8
[    0.798177] EISA: Detected 0 cards.
[    0.817546] cpuidle: using governor ladder
[    0.818351] cpuidle: using governor menu
[    0.820117] TCP cubic registered
[    0.821033] NET: Registered protocol family 10
[    0.823038] lo: Disabled Privacy Extensions
[    0.824373] NET: Registered protocol family 17
[    0.826782] Using IPI No-Shortcut mode
[    0.827322] PM: Resume from disk failed.
[    0.827376] registered taskstats version 1
[    0.828100]   Magic number: 14:565:928
[    0.828291] rtc_cmos 00:05: setting system clock to 2010-10-24 08:56:33 UTC (1287910593)
[    0.828310] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.828321] EDD information not available.
[    0.962498] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    1.006657] isapnp: No Plug & Play device found
[    1.061126] usb 2-2: new full speed USB device using uhci_hcd and address 2
[    1.962960] Freeing initrd memory: 15756k freed
[    1.987142] Freeing unused kernel memory: 684k freed
[    1.988499] Write protecting the kernel text: 4932k
[    1.988651] Write protecting the kernel read-only data: 1976k
[    2.073157] udev[79]: starting version 163
[    2.658408] pata_sch 0000:00:1f.1: version 0.2
[    2.658578] pata_sch 0000:00:1f.1: setting latency timer to 64
[    2.666239] scsi0 : pata_sch
[    2.668103] sky2: driver version 1.28
[    2.668241] sky2 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.668282] sky2 0000:01:00.0: setting latency timer to 64
[    2.668402] sky2 0000:01:00.0: Yukon-2 UL 2 chip revision 0
[    2.668626]   alloc irq_desc for 40 on node -1
[    2.668643]   alloc kstat_irqs on node -1
[    2.668690] sky2 0000:01:00.0: irq 40 for MSI/MSI-X
[    2.668876] scsi1 : pata_sch
[    2.671843] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x6060 irq 14
[    2.671867] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x6068 irq 15
[    2.675723] sky2 0000:01:00.0: eth0: addr 00:1d:ba:6b:e5:bf
[    2.884253] ata1.00: ATA-7: TOSHIBA MK6028GAL, BN101A, max UDMA/100
[    2.884271] ata1.00: 117210240 sectors, multi 16: LBA48 
[    2.884363] ata1.00: limited to UDMA/33 due to 40-wire cable
[    2.900946] ata1.00: configured for UDMA/33
[    2.901530] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK6028GA BN10 PQ: 0 ANSI: 5
[    2.902527] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.903130] sd 0:0:0:0: [sda] 117210240 512-byte logical blocks: (60.0 GB/55.8 GiB)
[    2.903462] sd 0:0:0:0: [sda] Write Protect is off
[    2.903478] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.903619] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.904473]  sda: sda1 sda2 < sda5 sda6 >
[    2.967205] sd 0:0:0:0: [sda] Attached SCSI disk
[    4.188445] xor: automatically using best checksumming function: pIII_sse
[    4.208023]    pIII_sse  :  2427.000 MB/sec
[    4.208042] xor: using function: pIII_sse (2427.000 MB/sec)
[    4.224048] device-mapper: dm-raid45: initialized v0.2594b
[    4.603090] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[   24.139140] Adding 4881404k swap on /dev/sda6.  Priority:-1 extents:1 across:4881404k 
[   24.287372] udev[350]: starting version 163
[   24.570375] lp: driver loaded but no devices found
[   24.823870] ACPI: resource (null) [io  0x0500-0x053f] conflicts with ACPI region GPIO [??? 0x00000500-0x0000053f flags 0x4f]
[   24.823895] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   24.953261] lpc_sch: probe of 0000:00:1f.0 failed with error -16
[   25.249876] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
[   25.921666] sony-laptop: Sony Programmable IO Control Driver v0.6.
[   25.921726] sony-laptop: detected Type2 model
[   25.940027] input: Sony Vaio Keys as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:16/SNY6001:00/input/input3
[   25.941208] input: Sony Vaio Jogdial as /devices/virtual/input/input4
[   25.942751] sony-laptop: device allocated minor is 55
[   26.031520] sony-laptop: Sony Notebook Control Driver v0.6.
[   26.070995] psmouse serio2: ID: 42 02 0a
[   26.275819] Bluetooth: Core ver 2.15
[   26.276128] NET: Registered protocol family 31
[   26.276143] Bluetooth: HCI device and connection manager initialized
[   26.276159] Bluetooth: HCI socket layer initialized
[   26.367871] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   26.395725] usbcore: registered new interface driver btusb
[   26.449071] type=1400 audit(1287928619.116:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=588 comm="apparmor_parser"
[   26.451404] type=1400 audit(1287928619.116:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=588 comm="apparmor_parser"
[   26.452440] type=1400 audit(1287928619.120:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=588 comm="apparmor_parser"
[   26.517628] cfg80211: Calling CRDA to update world regulatory domain
[   26.572596] sony-laptop: brightness ignored, must be controlled by ACPI video driver
[   26.715994] input: PS/2 Generic Mouse as /devices/platform/i8042/serio2/input/input5
[   26.765394] cfg80211: World regulatory domain updated:
[   26.765412]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   26.765434]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   26.765453]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   26.765473]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   26.765492]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   26.765511]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   27.864120] ath9k 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   27.864160] ath9k 0000:02:00.0: setting latency timer to 64
[   28.106220] sky2 0000:01:00.0: eth0: enabling interface
[   28.113679] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   28.208306] type=1400 audit(1287928620.876:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=779 comm="apparmor_parser"
[   28.210544] type=1400 audit(1287928620.876:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=779 comm="apparmor_parser"
[   28.211526] type=1400 audit(1287928620.876:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=779 comm="apparmor_parser"
[   28.282728] type=1400 audit(1287928620.948:8): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=787 comm="apparmor_parser"
[   28.360555] HDA Intel 0000:00:1b.0: power state changed by ACPI to D0
[   28.379200] type=1400 audit(1287928621.044:9): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=787 comm="apparmor_parser"
[   28.380458] HDA Intel 0000:00:1b.0: power state changed by ACPI to D0
[   28.380500]   alloc irq_desc for 19 on node -1
[   28.380515]   alloc kstat_irqs on node -1
[   28.380552] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   28.380745] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   28.411649] type=1400 audit(1287928621.076:10): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-thumbnailer" pid=787 comm="apparmor_parser"
[   28.512407] ath: EEPROM regdomain: 0x65
[   28.512425] ath: EEPROM indicates we should expect a direct regpair map
[   28.512447] ath: Country alpha2 being used: 00
[   28.512462] ath: Regpair used: 0x65
[   28.516591] type=1400 audit(1287928621.184:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=802 comm="apparmor_parser"
[   28.638992] phy0: Selected rate control algorithm 'ath9k_rate_control'
[   28.645112] Registered led device: ath9k-phy0::radio
[   28.645477] Registered led device: ath9k-phy0::assoc
[   28.645808] Registered led device: ath9k-phy0::tx
[   28.646136] Registered led device: ath9k-phy0::rx
[   28.646175] phy0: Atheros AR9280 Rev:2 mem=0xf84c0000, irq=17
[   28.697488] hda_codec: ALC262: SKU not ready 0x411111f0
[   28.697586] hda_codec: ALC262: BIOS auto-probing.
[   28.927136] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   29.225104] ppdev: user-space parallel port driver
[   30.361611] Bluetooth: L2CAP ver 2.14
[   30.361629] Bluetooth: L2CAP socket layer initialized
[   30.478481] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   30.478501] Bluetooth: BNEP filters: protocol multicast
[   30.556420] Bluetooth: SCO (Voice Link) ver 0.6
[   30.556437] Bluetooth: SCO socket layer initialized
[   30.743843] Bluetooth: RFCOMM TTY layer initialized
[   30.743877] Bluetooth: RFCOMM socket layer initialized
[   30.743891] Bluetooth: RFCOMM ver 1.11
[   31.768090] wlan0: authenticate with 00:25:9c:ec:eb:55 (try 1)
[   31.770245] wlan0: authenticated
[   31.784087] wlan0: associate with 00:25:9c:ec:eb:55 (try 1)
[   31.811451] wlan0: RX AssocResp from 00:25:9c:ec:eb:55 (capab=0x431 status=0 aid=1)
[   31.811473] wlan0: associated
[   31.813388] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   32.607530] padlock: VIA PadLock not detected.
[   33.810458] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0
[   40.276860] hda-intel: Invalid position buffer, using LPIB read method instead.
[   40.279615] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
[   42.224060] wlan0: no IPv6 routers present
[   44.080241] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0
[13086.341836] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=600
[13088.634842] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0
[13090.509087] No probe response from AP 00:25:9c:ec:eb:55 after 500ms, disconnecting.
[13090.564240] cfg80211: All devices are disconnected, going to restore regulatory settings
[13090.564258] cfg80211: Restoring regulatory settings
[13090.564270] cfg80211: Calling CRDA to update world regulatory domain
[13090.580164] cfg80211: World regulatory domain updated:
[13090.580177]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[13090.580191]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[13090.580203]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[13090.580214]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[13090.580226]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[13090.580238]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[13090.980223] sky2 0000:01:00.0: eth0: disabling interface
[13094.079900] PM: Marking nosave pages: 0000000000002000 - 0000000000010000
[13094.079910] PM: Marking nosave pages: 000000000009f000 - 0000000000100000
[13094.079919] PM: Basic memory bitmaps created
[13094.079924] PM: Syncing filesystems ... done.
[13094.270104] Freezing user space processes ... (elapsed 0.01 seconds) done.
[13094.284280] Freezing remaining freezable tasks ... (elapsed 0.01 seconds) done.
[13094.300347] PM: Preallocating image memory... done (allocated 106460 pages)
[13094.523716] PM: Allocated 425840 kbytes in 0.22 seconds (1935.63 MB/s)
[13094.523723] Suspending console(s) (use no_console_suspend to debug)
[13094.540623] sd 0:0:0:0: [sda] Synchronizing SCSI cache
[13094.541376] ACPI handle has no context!
[13094.541549] ath9k 0000:02:00.0: PCI INT A disabled
[13094.542664] btusb_intr_complete: hci0 urb f4a8bb00 failed to resubmit (1)
[13094.543722] btusb_bulk_complete: hci0 urb f4674500 failed to resubmit (1)
[13094.544770] btusb_bulk_complete: hci0 urb f4a8ba80 failed to resubmit (1)
[13094.645105] HDA Intel 0000:00:1b.0: PCI INT A disabled
[13094.660274] HDA Intel 0000:00:1b.0: power state changed by ACPI to D3
[13094.660299] PM: freeze of drv:HDA Intel dev:0000:00:1b.0 complete after 118.283 msecs
[13094.696178] PM: freeze of drv:sky2 dev:0000:01:00.0 complete after 154.590 msecs
[13094.696250] PM: freeze of drv:pcieport dev:0000:00:1c.0 complete after 154.267 msecs
[13094.696300] PM: freeze of drv: dev:pci0000:00 complete after 154.046 msecs
[13094.696329] PM: freeze of devices complete after 172.256 msecs
[13094.696998] PM: late freeze of devices complete after 0.651 msecs
[13094.697041] ACPI: Preparing to enter system sleep state S4
[13094.724436] PM: Saving platform NVS memory
[13094.734953] PM: Saving platform NVS memory
[13094.745206] Disabling non-boot CPUs ...
[13094.848130] CPU 1 is now offline
[13094.848143] SMP alternatives: switching to UP code
[13094.856436] PM: Creating hibernation image:
[13094.860017] PM: Need to copy 106142 pages
[13094.860017] PM: Normal pages needed: 31300 + 1024, available pages: 195879
[13094.860017] PM: Restoring platform NVS memory
[13094.860017] Enabling non-boot CPUs ...
[13094.860017] SMP alternatives: switching to SMP code
[13094.863752] Booting Node 0 Processor 1 APIC 0x1
[13094.855173] Initializing CPU#1
[13094.855173] Atom PSE erratum detected, BIOS microcode update recommended
[13094.981061] CPU1 is up
[13094.981651] ACPI: Waking up from system sleep state S4
[13095.060855] HDA Intel 0000:00:1b.0: restoring config space at offset 0x1 (was 0x100006, writing 0x100002)
[13095.061158] pata_sch 0000:00:1f.1: restoring config space at offset 0x1 (was 0x1, writing 0x5)
[13095.061319] ath9k 0000:02:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[13095.061650] PM: early restore of devices complete after 0.983 msecs
[13095.161661] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[13095.161708] usb usb1: root hub lost power or was reset
[13095.161743] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[13095.161772] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[13095.161785] usb usb2: root hub lost power or was reset
[13095.161815] usb usb3: root hub lost power or was reset
[13095.161835] pata_sch 0000:00:1f.1: setting latency timer to 64
[13095.161906] ath9k 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[13095.162389] sd 0:0:0:0: [sda] Starting disk
[13095.163456] HDA Intel 0000:00:1b.0: power state changed by ACPI to D0
[13095.184403] HDA Intel 0000:00:1b.0: power state changed by ACPI to D0
[13095.201350] HDA Intel 0000:00:1b.0: power state changed by ACPI to D0
[13095.221454] HDA Intel 0000:00:1b.0: power state changed by ACPI to D0
[13095.221492] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[13095.221535] HDA Intel 0000:00:1b.0: setting latency timer to 64
[13095.305260] PM: restore of drv:usb dev:usb1 complete after 143.300 msecs
[13095.305279] PM: restore of drv:usb dev:usb3 complete after 143.273 msecs
[13095.305337] PM: restore of drv:hub dev:1-0:1.0 complete after 143.387 msecs
[13095.305354] PM: restore of drv:hub dev:3-0:1.0 complete after 143.350 msecs
[13095.333609] ata1.00: ACPI cmd ef/03:0c:00:00:00:a0 (SET FEATURES) filtered out
[13095.333622] ata1.00: ACPI cmd ef/03:45:00:00:00:a0 (SET FEATURES) filtered out
[13095.341860] ata1.00: configured for UDMA/33
[13095.369728] PM: restore of drv:sd dev:0:0:0:0 complete after 207.337 msecs
[13095.369796] PM: restore of drv:scsi_device dev:0:0:0:0 complete after 207.254 msecs
[13095.408159] PM: restore of drv:usb dev:usb2 complete after 246.195 msecs
[13095.408213] PM: restore of drv:hub dev:2-0:1.0 complete after 246.244 msecs
[13095.408256] PM: restore of drv: dev:ep_81 complete after 102.773 msecs
[13095.520217] usb 2-2: reset full speed USB device using uhci_hcd and address 2
[13095.673224] btusb 2-2:1.0: no reset_resume for driver btusb?
[13095.673242] btusb 2-2:1.1: no reset_resume for driver btusb?
[13095.924696] PM: restore of drv:usb dev:2-2 complete after 762.704 msecs
[13095.924758] PM: restore of drv:usb dev:2-2:1.0 complete after 762.765 msecs
[13095.924767] PM: restore of drv:usb dev:2-2:1.3 complete after 762.476 msecs
[13095.924783] PM: restore of drv:usb dev:2-2:1.1 complete after 762.602 msecs
[13095.924801] PM: restore of drv:usb dev:2-2:1.2 complete after 762.516 msecs
[13095.924811] PM: restore of drv: dev:ep_81 complete after 512.117 msecs
[13095.947739] PM: restore of devices complete after 786.585 msecs
[13096.032657] PM: Image restored successfully.
[13096.032670] Restarting tasks ... done.
[13096.033929] PM: Basic memory bitmaps freed
[13096.464965] psmouse.c: Failed to reset mouse on isa0060/serio2
[13096.687208] psmouse serio2: ID: 42 02 0a
[13096.837421] sky2 0000:01:00.0: eth0: enabling interface
[13096.838254] ADDRCONF(NETDEV_UP): eth0: link is not ready
[13096.902197] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[13100.569123] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0
[13101.517935] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0
[13108.118488] wlan0: authenticate with 00:25:9c:ec:eb:55 (try 1)
[13108.120573] wlan0: authenticated
[13108.120648] wlan0: associate with 00:25:9c:ec:eb:55 (try 1)
[13108.136243] wlan0: RX AssocResp from 00:25:9c:ec:eb:55 (capab=0x431 status=0 aid=3)
[13108.136256] wlan0: associated
[13108.137112] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[13118.816127] wlan0: no IPv6 routers present
[13470.198515] lo: Disabled Privacy Extensions
[14516.516153] No probe response from AP 00:25:9c:ec:eb:55 after 500ms, disconnecting.
[14516.553144] cfg80211: All devices are disconnected, going to restore regulatory settings
[14516.553170] cfg80211: Restoring regulatory settings
[14516.553190] cfg80211: Calling CRDA to update world regulatory domain
[14516.572574] cfg80211: World regulatory domain updated:
[14516.572589]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[14516.572605]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[14516.572619]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[14516.572632]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[14516.572646]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[14516.572659]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[14529.867062] wlan0: authenticate with 00:25:9c:ec:eb:55 (try 1)
[14529.879799] wlan0: authenticated
[14529.879942] wlan0: associate with 00:25:9c:ec:eb:55 (try 1)
[14529.904669] wlan0: RX AssocResp from 00:25:9c:ec:eb:55 (capab=0x431 status=0 aid=3)
[14529.904688] wlan0: associated
[15540.516164] No probe response from AP 00:25:9c:ec:eb:55 after 500ms, disconnecting.
[15540.553181] cfg80211: All devices are disconnected, going to restore regulatory settings
[15540.553205] cfg80211: Restoring regulatory settings
[15540.553225] cfg80211: Calling CRDA to update world regulatory domain
[15540.571382] cfg80211: World regulatory domain updated:
[15540.571397]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[15540.571413]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[15540.571427]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[15540.571440]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[15540.571454]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[15540.571467]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[15547.811520] wlan0: authenticate with 00:25:9c:ec:eb:55 (try 1)
[15547.814425] wlan0: authenticated
[15547.814505] wlan0: associate with 00:25:9c:ec:eb:55 (try 1)
[15547.830221] wlan0: RX AssocResp from 00:25:9c:ec:eb:55 (capab=0x431 status=0 aid=2)
[15547.830240] wlan0: associated
[15920.760238] No probe response from AP 00:25:9c:ec:eb:55 after 500ms, disconnecting.
[15920.792775] cfg80211: All devices are disconnected, going to restore regulatory settings
[15920.792800] cfg80211: Restoring regulatory settings
[15920.792819] cfg80211: Calling CRDA to update world regulatory domain
[15920.810686] cfg80211: World regulatory domain updated:
[15920.810701]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[15920.810718]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[15920.810732]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[15920.810745]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[15920.810758]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[15920.810772]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[15928.045134] wlan0: authenticate with 00:25:9c:ec:eb:55 (try 1)
[15928.048836] wlan0: authenticated
[15928.048913] wlan0: associate with 00:25:9c:ec:eb:55 (try 1)
[15928.064622] wlan0: RX AssocResp from 00:25:9c:ec:eb:55 (capab=0x431 status=0 aid=2)
[15928.064641] wlan0: associated
[16702.564209] No probe response from AP 00:25:9c:ec:eb:55 after 500ms, disconnecting.
[16702.604007] cfg80211: All devices are disconnected, going to restore regulatory settings
[16702.604033] cfg80211: Restoring regulatory settings
[16702.604051] cfg80211: Calling CRDA to update world regulatory domain
[16702.622446] cfg80211: World regulatory domain updated:
[16702.622461]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[16702.622478]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[16702.622491]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[16702.622505]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[16702.622518]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[16702.622531]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[16703.793798] wlan0: authenticate with 00:25:9c:ec:eb:55 (try 1)
[16703.797857] wlan0: authenticated
[16703.797941] wlan0: associate with 00:25:9c:ec:eb:55 (try 1)
[16703.822894] wlan0: RX AssocResp from 00:25:9c:ec:eb:55 (capab=0x431 status=0 aid=2)
[16703.822913] wlan0: associated
[17337.084151] FAT: invalid media value (0x12)
[17337.084162] VFS: Can't find a valid FAT filesystem on dev sda2.
[17337.096148] FAT: Unrecognized mount option "utf8" or missing value
[17337.113415] attempt to access beyond end of device
[17337.113431] sda2: rw=0, want=66, limit=2
[17337.113444] isofs_fill_super: bread failed, dev=sda2, iso_blknum=16, block=32
[17337.148899] FAT: invalid media value (0x12)
[17337.148911] VFS: Can't find a valid FAT filesystem on dev sda2.
[17337.181770] FAT: bogus number of reserved sectors
[17337.181785] VFS: Can't find a valid FAT filesystem on dev sda1.
[17337.208197] FAT: Unrecognized mount option "utf8" or missing value
[17337.270459] ISOFS: Unable to identify CD-ROM format.
[41240.752221] No probe response from AP 00:25:9c:ec:eb:55 after 500ms, disconnecting.
[41240.792004] cfg80211: All devices are disconnected, going to restore regulatory settings
[41240.792029] cfg80211: Restoring regulatory settings
[41240.792049] cfg80211: Calling CRDA to update world regulatory domain
[41240.810304] cfg80211: World regulatory domain updated:
[41240.810320]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[41240.810336]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[41240.810349]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[41240.810363]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[41240.810376]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[41240.810390]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[41241.985067] wlan0: authenticate with 00:25:9c:ec:eb:55 (try 1)
[41242.184252] wlan0: authenticate with 00:25:9c:ec:eb:55 (try 2)
[41242.384183] wlan0: authenticate with 00:25:9c:ec:eb:55 (try 3)
[41242.431928] wlan0: authenticated
[41242.432223] wlan0: associate with 00:25:9c:ec:eb:55 (try 1)
[41242.457618] wlan0: RX AssocResp from 00:25:9c:ec:eb:55 (capab=0x431 status=0 aid=2)
[41242.457638] wlan0: associated
[41276.580215] No probe response from AP 00:25:9c:ec:eb:55 after 500ms, disconnecting.
[41276.617181] cfg80211: All devices are disconnected, going to restore regulatory settings
[41276.617206] cfg80211: Restoring regulatory settings
[41276.617225] cfg80211: Calling CRDA to update world regulatory domain
[41276.635755] cfg80211: World regulatory domain updated:
[41276.635770]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[41276.635787]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[41276.635800]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[41276.635814]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[41276.635827]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[41276.635841]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[41289.947249] wlan0: authenticate with 00:25:9c:ec:eb:55 (try 1)
[41290.144252] wlan0: authenticate with 00:25:9c:ec:eb:55 (try 2)
[41290.152280] wlan0: authenticated
[41290.152409] wlan0: associate with 00:25:9c:ec:eb:55 (try 1)
[41290.186204] wlan0: RX AssocResp from 00:25:9c:ec:eb:55 (capab=0x431 status=0 aid=2)
[41290.186224] wlan0: associated
[42714.532247] No probe response from AP 00:25:9c:ec:eb:55 after 500ms, disconnecting.
[42714.576741] cfg80211: All devices are disconnected, going to restore regulatory settings
[42714.576766] cfg80211: Restoring regulatory settings
[42714.576787] cfg80211: Calling CRDA to update world regulatory domain
[42714.595220] cfg80211: World regulatory domain updated:
[42714.595236]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[42714.595252]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[42714.595266]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[42714.595279]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[42714.595292]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[42714.595306]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[42715.766377] wlan0: authenticate with 00:25:9c:ec:eb:55 (try 1)
[42715.907551] wlan0: authenticated
[42715.907680] wlan0: associate with 00:25:9c:ec:eb:55 (try 1)
[42715.941286] wlan0: RX AssocResp from 00:25:9c:ec:eb:55 (capab=0x431 status=0 aid=2)
[42715.941306] wlan0: associated
[42769.572243] No probe response from AP 00:25:9c:ec:eb:55 after 500ms, disconnecting.
[42769.609164] cfg80211: All devices are disconnected, going to restore regulatory settings
[42769.609189] cfg80211: Restoring regulatory settings
[42769.609208] cfg80211: Calling CRDA to update world regulatory domain
[42769.627292] cfg80211: World regulatory domain updated:
[42769.627308]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[42769.627324]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[42769.627338]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[42769.627351]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[42769.627365]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[42769.627378]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[42782.927637] wlan0: direct probe to 00:25:9c:ec:eb:55 (try 1)
[42783.124160] wlan0: direct probe to 00:25:9c:ec:eb:55 (try 2)
[42783.324157] wlan0: direct probe to 00:25:9c:ec:eb:55 (try 3)
[42783.524244] wlan0: direct probe to 00:25:9c:ec:eb:55 timed out
[42792.722484] wlan0: authenticate with 00:25:9c:ec:eb:55 (try 1)
[42792.726300] wlan0: authenticated
[42792.726377] wlan0: associate with 00:25:9c:ec:eb:55 (try 1)
[42792.742081] wlan0: RX AssocResp from 00:25:9c:ec:eb:55 (capab=0x431 status=0 aid=3)
[42792.742100] wlan0: associated

```

Please let me know if there's anything else I can do. 

Thanks!

~Kolfinna

---

