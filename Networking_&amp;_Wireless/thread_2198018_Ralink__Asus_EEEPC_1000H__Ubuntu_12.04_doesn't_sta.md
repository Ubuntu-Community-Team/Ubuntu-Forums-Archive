---
title: "Ralink / Asus EEEPC 1000H / Ubuntu 12.04 doesn't stay connected to wifi"
date: 2014-01-06
forum: Networking &amp; Wireless
---

### Post by wkcchampion on 2014-01-06
Hello,
the Asus EEEPC 1000H doesn't stay connected o my home wifi MysteryStyle. The network is detected and Ubuntu says "connected", but it stops loading web ages after a few seconds. 
If I disconnect and reconnect or disable/re-enable the wifi using the FN+F2 keys, it behaves the same.
Here is the result of the commands coming from the Sticky thread. Thanks for your help!
Marco

```
1)Asus EEEPC 1000H
Wifi device: Ralink corp. RT2790 Wireless 802.11n


2)marco@marco-1000H:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GSE Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GSE Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7-M Family) SATA Controller [IDE mode] (rev 02)
01:00.0 Network controller: Ralink corp. RT2790 Wireless 802.11n 1T/2R PCIe
03:00.0 Ethernet controller: Atheros Communications Inc. AR8121/AR8113/AR8114 Gigabit or Fast Ethernet (rev b0)
marco@marco-1000H:~$ lsusb
Bus 001 Device 003: ID 058f:6335 Alcor Micro Corp. SD/MMC Card Reader
Bus 001 Device 004: ID 04f2:b071 Chicony Electronics Co., Ltd 2.0M UVC Webcam / CNF7129
Bus 003 Device 002: ID 046d:c016 Logitech, Inc. Optical Wheel Mouse
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


marco@marco-1000H:~$ lspci -nn | grep 'Ralink'
01:00.0 Network controller [0280]: Ralink corp. RT2790 Wireless 802.11n 1T/2R PCIe [1814:0781]




3)marco@marco-1000H:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:23:54:63:8a:8e  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:2
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:406 errors:0 dropped:0 overruns:0 frame:0
          TX packets:406 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:66712 (66.7 KB)  TX bytes:66712 (66.7 KB)


wlan0     Link encap:Ethernet  HWaddr 00:22:43:24:94:f8  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::222:43ff:fe24:94f8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7348 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5758 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8823026 (8.8 MB)  TX bytes:880700 (880.7 KB)


marco@marco-1000H:~$ iwconfig
wlan0     IEEE 802.11bgn  ESSID:"MysteryStyle"  
          Mode:Managed  Frequency:2.472 GHz  Access Point: 64:70:02:9F:92:48   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=62/70  Signal level=-48 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:25  Invalid misc:65   Missed beacon:0


lo        no wireless extensions.


eth0      no wireless extensions.




4)marco@marco-1000H:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12617  1 
bnep                   17852  2 
rfcomm                 38400  0 
bluetooth             211435  10 bnep,rfcomm
parport_pc             27612  0 
ppdev                  12849  0 
arc4                   12509  2 
snd_hda_codec_realtek    65004  1 
rt2800pci              18371  0 
joydev                 17329  0 
snd_hda_intel          38819  3 
rt2800lib              61785  1 rt2800pci
snd_hda_codec         118613  2 snd_hda_codec_realtek,snd_hda_intel
crc_ccitt              12627  1 rt2800lib
rt2x00pci              14237  1 rt2800pci
uvcvideo               72250  0 
rt2x00lib              49096  3 rt2800pci,rt2800lib,rt2x00pci
videobuf2_core         39385  1 uvcvideo
snd_hwdep              13276  1 snd_hda_codec
videodev               96131  2 uvcvideo,videobuf2_core
coretemp               13324  0 
snd_pcm                85934  2 snd_hda_intel,snd_hda_codec
videobuf2_vmalloc      12920  1 uvcvideo
mac80211              541819  3 rt2800lib,rt2x00pci,rt2x00lib
i915                  550346  3 
videobuf2_memops       13042  1 videobuf2_vmalloc
snd_seq_midi           13132  0 
snd_rawmidi            25157  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51593  2 snd_seq_midi,snd_seq_midi_event
cfg80211              453853  2 rt2x00lib,mac80211
snd_timer              28931  2 snd_pcm,snd_seq
drm_kms_helper         47749  1 i915
snd_seq_device         14137  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                82769  0 
drm                   233935  4 i915,drm_kms_helper
microcode              18433  0 
snd                    57014  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              13031  0 
eeepc_laptop           19469  0 
lpc_ich                17048  0 
soundcore              12600  1 snd
snd_page_alloc         18398  2 snd_hda_intel,snd_pcm
eeprom_93cx6           13168  1 rt2800pci
i2c_algo_bit           13316  1 i915
sparse_keymap          13658  1 eeepc_laptop
mac_hid                13077  0 
video                  19116  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
hid_generic            12484  0 
usbhid                 46125  0 
hid                    83037  2 hid_generic,usbhid
usb_storage            48053  1 
atl1e                  32727  0 


5)dmesg
[    1.050373] brd: module loaded
[    1.053071] loop: module loaded
[    1.053556] ata_piix 0000:00:1f.2: version 2.13
[    1.053591] ata_piix 0000:00:1f.2: MAP [
[    1.053596]  P0 P2 IDE IDE ]
[    1.053685] ata_piix 0000:00:1f.2: setting latency timer to 64
[    1.054488] scsi0 : ata_piix
[    1.056562] scsi1 : ata_piix
[    1.058125] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    1.058134] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    1.059413] libphy: Fixed MDIO Bus: probed
[    1.059759] tun: Universal TUN/TAP device driver, 1.6
[    1.059765] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.059940] PPP generic driver version 2.4.2
[    1.060156] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.060163] ehci-pci: EHCI PCI platform driver
[    1.060243] ehci-pci 0000:00:1d.7: setting latency timer to 64
[    1.060254] ehci-pci 0000:00:1d.7: EHCI Host Controller
[    1.060273] ehci-pci 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    1.060306] ehci-pci 0000:00:1d.7: debug port 1
[    1.064255] ehci-pci 0000:00:1d.7: cache line size of 32 is not supported
[    1.064313] ehci-pci 0000:00:1d.7: irq 23, io mem 0xf7eb7c00
[    1.076072] ehci-pci 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.076167] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    1.076202] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.076233] usb usb1: Product: EHCI Host Controller
[    1.076262] usb usb1: Manufacturer: Linux 3.8.0-29-generic ehci_hcd
[    1.076270] usb usb1: SerialNumber: 0000:00:1d.7
[    1.076604] hub 1-0:1.0: USB hub found
[    1.076622] hub 1-0:1.0: 8 ports detected
[    1.077061] ehci-platform: EHCI generic platform driver
[    1.077102] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.077170] uhci_hcd: USB Universal Host Controller Interface driver
[    1.077232] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.077243] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.077261] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.077319] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000d400
[    1.077432] usb usb2: New USB device found, idVendor=1d6b, idProduct=0001
[    1.077441] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.077449] usb usb2: Product: UHCI Host Controller
[    1.077457] usb usb2: Manufacturer: Linux 3.8.0-29-generic uhci_hcd
[    1.077464] usb usb2: SerialNumber: 0000:00:1d.0
[    1.077850] hub 2-0:1.0: USB hub found
[    1.077867] hub 2-0:1.0: 2 ports detected
[    1.078096] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.078107] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.078124] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    1.078197] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000d480
[    1.078301] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
[    1.078310] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.078318] usb usb3: Product: UHCI Host Controller
[    1.078326] usb usb3: Manufacturer: Linux 3.8.0-29-generic uhci_hcd
[    1.078334] usb usb3: SerialNumber: 0000:00:1d.1
[    1.078624] hub 3-0:1.0: USB hub found
[    1.078645] hub 3-0:1.0: 2 ports detected
[    1.078866] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.078877] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.078894] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    1.078968] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000d800
[    1.079088] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
[    1.079097] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.079105] usb usb4: Product: UHCI Host Controller
[    1.079113] usb usb4: Manufacturer: Linux 3.8.0-29-generic uhci_hcd
[    1.079120] usb usb4: SerialNumber: 0000:00:1d.2
[    1.079403] hub 4-0:1.0: USB hub found
[    1.079419] hub 4-0:1.0: 2 ports detected
[    1.079634] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    1.079645] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    1.079662] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    1.079729] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000d880
[    1.079831] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
[    1.079841] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.079848] usb usb5: Product: UHCI Host Controller
[    1.079856] usb usb5: Manufacturer: Linux 3.8.0-29-generic uhci_hcd
[    1.079864] usb usb5: SerialNumber: 0000:00:1d.3
[    1.080209] hub 5-0:1.0: USB hub found
[    1.080225] hub 5-0:1.0: 2 ports detected
[    1.080855] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.111320] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.111342] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.111743] mousedev: PS/2 mouse device common for all mice
[    1.112917] rtc_cmos 00:02: RTC can wake from S4
[    1.113174] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    1.113226] rtc0: alarms up to one month, 114 bytes nvram, hpet irqs
[    1.113635] device-mapper: uevent: version 1.0.3
[    1.113838] device-mapper: ioctl: 4.23.1-ioctl (2012-12-18) initialised: dm-devel@redhat.com
[    1.113905] EISA: Probing bus 0 at eisa.0
[    1.113913] EISA: Cannot allocate resource for mainboard
[    1.113921] Cannot allocate resource for EISA slot 1
[    1.113928] Cannot allocate resource for EISA slot 2
[    1.113935] Cannot allocate resource for EISA slot 3
[    1.113942] Cannot allocate resource for EISA slot 4
[    1.113949] Cannot allocate resource for EISA slot 5
[    1.113956] Cannot allocate resource for EISA slot 6
[    1.113963] Cannot allocate resource for EISA slot 7
[    1.113970] Cannot allocate resource for EISA slot 8
[    1.113975] EISA: Detected 0 cards.
[    1.113999] cpufreq-nforce2: No nForce2 chipset.
[    1.114129] cpuidle: using governor ladder
[    1.114293] cpuidle: using governor menu
[    1.114304] ledtrig-cpu: registered to indicate activity on CPUs
[    1.114310] EFI Variables Facility v0.08 2004-May-17
[    1.114913] ashmem: initialized
[    1.115303] TCP: cubic registered
[    1.115658] NET: Registered protocol family 10
[    1.116240] NET: Registered protocol family 17
[    1.116285] Key type dns_resolver registered
[    1.116771] Using IPI No-Shortcut mode
[    1.117035] Loading module verification certificates
[    1.131545] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: 760b08a5a1de9684ced1bfd52640b05fe41b6ca5'
[    1.131581] registered taskstats version 1
[    1.138449] Key type trusted registered
[    1.145388] Key type encrypted registered
[    1.152902] rtc_cmos 00:02: setting system clock to 2014-01-06 17:25:16 UTC (1389029116)
[    1.153851] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.153858] EDD information not available.
[    1.164274] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.228666] ata1.00: ATA-8: ST9160310AS, 0303, max UDMA/133
[    1.228677] ata1.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.244625] ata1.00: configured for UDMA/133
[    1.266202] ACPI: Battery Slot [BAT0] (battery present)
[    1.393693] isapnp: No Plug & Play device found
[    1.394021] scsi 0:0:0:0: Direct-Access     ATA      ST9160310AS      0303 PQ: 0 ANSI: 5
[    1.394380] sd 0:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    1.394487] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.394598] sd 0:0:0:0: [sda] Write Protect is off
[    1.394611] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.394720] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.444162] usb 1-5: new high-speed USB device number 3 using ehci-pci
[    1.578196] usb 1-5: New USB device found, idVendor=058f, idProduct=6335
[    1.578215] usb 1-5: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    1.578239] usb 1-5: Product: Mass Storage Device
[    1.578246] usb 1-5: Manufacturer: Generic
[    1.578252] usb 1-5: SerialNumber: 058F63356336
[    1.688136] usb 1-8: new high-speed USB device number 4 using ehci-pci
[    1.695712]  sda: sda1 sda2 < sda5 >
[    1.696915] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.697086] Freeing unused kernel memory: 796k freed
[    1.697749] Write protecting the kernel text: 6360k
[    1.697895] Write protecting the kernel read-only data: 2496k
[    1.697901] NX-protecting the kernel data: 3880k
[    1.745506] udevd[101]: starting version 175
[    1.864902] usb 1-8: New USB device found, idVendor=04f2, idProduct=b071
[    1.864916] usb 1-8: New USB device strings: Mfr=2, Product=1, SerialNumber=3
[    1.864925] usb 1-8: Product: CNF7129
[    1.864934] usb 1-8: Manufacturer: Chicony Electronics Co., Ltd.
[    1.864942] usb 1-8: SerialNumber: SN0001
[    2.026454] Disabling lock debugging due to kernel taint
[    2.045969] Initializing USB Mass Storage driver...
[    2.048241] scsi2 : usb-storage 1-5:1.0
[    2.048626] usbcore: registered new interface driver usb-storage
[    2.048635] USB Mass Storage support registered.
[    2.108093] usb 3-2: new low-speed USB device number 2 using uhci_hcd
[    2.283514] usb 3-2: New USB device found, idVendor=046d, idProduct=c016
[    2.283541] usb 3-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.283566] usb 3-2: Product: Optical USB Mouse
[    2.283575] usb 3-2: Manufacturer: Logitech
[    2.309484] usbcore: registered new interface driver usbhid
[    2.309493] usbhid: USB HID core driver
[    2.316795] input: Logitech Optical USB Mouse as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.0/input/input5
[    2.317370] hid-generic 0003:046D:C016.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:1d.1-2/input0
[    2.529431] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    3.049172] scsi 2:0:0:0: Direct-Access     Single   Flash Reader     1.00 PQ: 0 ANSI: 0
[    3.051112] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    3.457245] sd 2:0:0:0: [sdb] 7835648 512-byte logical blocks: (4.01 GB/3.73 GiB)
[    3.458566] sd 2:0:0:0: [sdb] Write Protect is off
[    3.458578] sd 2:0:0:0: [sdb] Mode Sense: 03 00 00 00
[    3.459667] sd 2:0:0:0: [sdb] No Caching mode page present
[    3.459675] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    3.464173] sd 2:0:0:0: [sdb] No Caching mode page present
[    3.464182] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    3.466437]  sdb: sdb1
[    3.469664] sd 2:0:0:0: [sdb] No Caching mode page present
[    3.469673] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    3.470416] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[    4.000593] init: ureadahead main process (249) terminated with status 5
[    5.232094] Adding 1038332k swap on /dev/sda5.  Priority:-1 extents:1 across:1038332k 
[    6.396218] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    6.947434] udevd[325]: starting version 175
[    7.589039] lp: driver loaded but no devices found
[    7.826969] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[    8.236581] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[    8.236976] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input6
[    8.427039] intel_rng: FWH not detected
[    8.540573] ACPI Warning: 0x00000828-0x0000082f SystemIO conflicts with Region \PMIO 1 (20121018/utaddress-251)
[    8.540597] ACPI Warning: 0x00000828-0x0000082f SystemIO conflicts with Region \_SB_.PCI0.SBRG.PMS0 2 (20121018/utaddress-251)
[    8.540613] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    8.540625] ACPI Warning: 0x000004b0-0x000004bf SystemIO conflicts with Region \_SB_.PCI0.SBRG.GPBX 1 (20121018/utaddress-251)
[    8.540638] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    8.540645] ACPI Warning: 0x00000480-0x000004af SystemIO conflicts with Region \_SB_.PCI0.SBRG.GPBX 1 (20121018/utaddress-251)
[    8.540659] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    8.540665] lpc_ich: Resource conflict(s) found affecting gpio_ich
[    8.556435] eeepc_laptop: Eee PC Hotkey Driver
[    8.556463] eeepc_laptop: Hotkey init flags 0x41
[    8.585723] eeepc_laptop: TYPE (2000000) not reported by BIOS, enabling anyway
[    8.590949] eeepc_laptop: PANELPOWER (4000000) not reported by BIOS, enabling anyway
[    8.590967] eeepc_laptop: Get control methods supported: 0x6101713
[    8.604876] input: Asus EeePC extra buttons as /devices/platform/eeepc/input/input7
[    8.641413] leds_ss4200: no LED devices found
[    8.739015] microcode: CPU0 sig=0x106c2, pf=0x4, revision=0x212
[    8.776114] [drm] Initialized drm 1.1.0 20060810
[    8.984132] cfg80211: Calling CRDA to update world regulatory domain
[    9.314543] microcode: CPU1 sig=0x106c2, pf=0x4, revision=0x212
[    9.321326] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    9.429208] i915 0000:00:02.0: setting latency timer to 64
[    9.432275] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    9.432285] [drm] Driver supports precise vblank timestamp query.
[    9.434903] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    9.584126] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 207
[    9.584155] Raw EDID:
[    9.584171]  	00 ff ff ff ff ff ff 00 22 64 e9 03 c9 06 00 00
[    9.584188]  	12 12 01 03 80 16 0d 78 0a 86 26 94 57 51 90 27
[    9.584205]  	21 4f 54 00 00 00 01 01 01 01 01 01 01 01 01 01
[    9.584221]  	01 01 01 01 01 01 94 11 00 b0 40 58 19 20 35 23
[    9.584237]  	45 00 dc 81 00 00 00 19 16 14 00 d8 40 58 26 20
[    9.584254]  	5d 23 15 04 dc 81 00 00 00 00 00 00 00 fe 00 00
[    9.584270]  	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 fe
[    9.584286]  	00 00 00 00 00 00 00 00 00 01 00 00 00 00 00 c8
[    9.638794] Linux video capture interface: v2.00
[    9.720087] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 207
[    9.720104] Raw EDID:
[    9.720113]  	00 ff ff ff ff ff ff 00 22 64 e9 03 c9 06 00 00
[    9.720121]  	12 12 01 03 80 16 0d 78 0a 86 26 94 57 51 90 27
[    9.720129]  	21 4f 54 00 00 00 01 01 01 01 01 01 01 01 01 01
[    9.720137]  	01 01 01 01 01 01 94 11 00 b0 40 58 19 20 35 23
[    9.720145]  	45 00 dc 81 00 00 00 19 16 14 00 d8 40 58 26 20
[    9.720154]  	5d 23 15 04 dc 81 00 00 00 00 00 00 00 fe 00 00
[    9.720162]  	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 fe
[    9.720170]  	00 00 00 00 00 00 00 00 00 01 00 00 00 00 00 c8
[    9.864084] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 207
[    9.864105] Raw EDID:
[    9.864122]  	00 ff ff ff ff ff ff 00 22 64 e9 03 c9 06 00 00
[    9.864139]  	12 12 01 03 80 16 0d 78 0a 86 26 94 57 51 90 27
[    9.864155]  	21 4f 54 00 00 00 01 01 01 01 01 01 01 01 01 01
[    9.864171]  	01 01 01 01 01 01 94 11 00 b0 40 58 19 20 35 23
[    9.864187]  	45 00 dc 81 00 00 00 19 16 14 00 d8 40 58 26 20
[    9.864204]  	5d 23 15 04 dc 81 00 00 00 00 00 00 00 fe 00 00
[    9.864217]  	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 fe
[    9.864227]  	00 00 00 00 00 00 00 00 00 01 00 00 00 00 00 c8
[    9.976660] uvcvideo: Found UVC 1.00 device CNF7129 (04f2:b071)
[    9.993810] input: CNF7129 as /devices/pci0000:00/0000:00:1d.7/usb1/1-8/1-8:1.0/input/input8
[    9.994437] usbcore: registered new interface driver uvcvideo
[    9.994447] USB Video Class driver (1.1.1)
[   10.000108] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 207
[   10.000137] Raw EDID:
[   10.000153]  	00 ff ff ff ff ff ff 00 22 64 e9 03 c9 06 00 00
[   10.000171]  	12 12 01 03 80 16 0d 78 0a 86 26 94 57 51 90 27
[   10.000188]  	21 4f 54 00 00 00 01 01 01 01 01 01 01 01 01 01
[   10.000205]  	01 01 01 01 01 01 94 11 00 b0 40 58 19 20 35 23
[   10.000222]  	45 00 dc 81 00 00 00 19 16 14 00 d8 40 58 26 20
[   10.000238]  	5d 23 15 04 dc 81 00 00 00 00 00 00 00 fe 00 00
[   10.000256]  	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 fe
[   10.000272]  	00 00 00 00 00 00 00 00 00 01 00 00 00 00 00 c8
[   10.000298] i915 0000:00:02.0: LVDS-1: EDID block 0 invalid.
[   10.001819] psmouse serio1: elantech: assuming hardware version 2 (with firmware version 0x020030)
[   10.003785] [drm] initialized overlay support
[   10.074268] psmouse serio1: elantech: Synaptics capabilities query result 0x00, 0x02, 0x64.
[   10.296379] input: ETPS/2 Elantech Touchpad as /devices/platform/i8042/serio1/input/input9
[   10.326027] fbcon: inteldrmfb (fb0) is primary device
[   10.757224] Console: switching to colour frame buffer device 128x37
[   10.764754] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[   10.764760] i915 0000:00:02.0: registered panic notifier
[   10.764778] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   10.765202] snd_hda_intel 0000:00:1b.0: irq 43 for MSI/MSI-X
[   10.890376] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   10.891004] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   11.009748] eeepc_laptop: Unable to find port
[   11.335506] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   11.682259] type=1400 audit(1389029127.023:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=593 comm="apparmor_parser"
[   11.682285] type=1400 audit(1389029127.023:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=592 comm="apparmor_parser"
[   11.683385] type=1400 audit(1389029127.023:4): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=686 comm="apparmor_parser"
[   11.683922] type=1400 audit(1389029127.023:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=593 comm="apparmor_parser"
[   11.685030] type=1400 audit(1389029127.027:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=593 comm="apparmor_parser"
[   11.685154] type=1400 audit(1389029127.027:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=686 comm="apparmor_parser"
[   11.686145] type=1400 audit(1389029127.027:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=686 comm="apparmor_parser"
[   11.690595] type=1400 audit(1389029127.031:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=592 comm="apparmor_parser"
[   11.691553] type=1400 audit(1389029127.031:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=592 comm="apparmor_parser"
[   12.569692] init: failsafe main process (701) killed by TERM signal
[   14.459979] ppdev: user-space parallel port driver
[   15.088134] Bluetooth: Core ver 2.16
[   15.088208] NET: Registered protocol family 31
[   15.088217] Bluetooth: HCI device and connection manager initialized
[   15.088241] Bluetooth: HCI socket layer initialized
[   15.088253] Bluetooth: L2CAP socket layer initialized
[   15.088276] Bluetooth: SCO socket layer initialized
[   15.187198] Bluetooth: RFCOMM TTY layer initialized
[   15.187234] Bluetooth: RFCOMM socket layer initialized
[   15.187242] Bluetooth: RFCOMM ver 1.11
[   15.284379] type=1400 audit(1389029130.627:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=802 comm="apparmor_parser"
[   15.362532] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   15.362545] Bluetooth: BNEP filters: protocol multicast
[   15.362754] Bluetooth: BNEP socket layer initialized
[   17.996506] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   17.997890] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   18.010268] audit_printk_skb: 3 callbacks suppressed
[   18.010277] type=1400 audit(1389029133.351:13): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=869 comm="apparmor_parser"
[   18.011498] type=1400 audit(1389029133.351:14): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=869 comm="apparmor_parser"
[   18.012312] type=1400 audit(1389029133.355:15): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=869 comm="apparmor_parser"
[   18.060778] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   18.061609] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   18.067816] type=1400 audit(1389029133.407:16): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=868 comm="apparmor_parser"
[   18.069624] type=1400 audit(1389029133.411:17): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper//chromium_browser" pid=868 comm="apparmor_parser"
[   18.156733] type=1400 audit(1389029133.499:18): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=875 comm="apparmor_parser"
[   18.158533] type=1400 audit(1389029133.499:19): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=875 comm="apparmor_parser"
[   18.172806] type=1400 audit(1389029133.515:20): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=876 comm="apparmor_parser"
[   18.174250] type=1400 audit(1389029133.515:21): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=876 comm="apparmor_parser"
[   18.229306] type=1400 audit(1389029133.571:22): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=878 comm="apparmor_parser"
[   20.225877] init: anacron main process (937) killed by TERM signal
[   21.533835] wlan0: authenticate with 64:70:02:9f:92:48
[   21.552570] wlan0: send auth to 64:70:02:9f:92:48 (try 1/3)
[   21.554363] wlan0: authenticated
[   21.556629] wlan0: associate with 64:70:02:9f:92:48 (try 1/3)
[   21.560800] wlan0: RX AssocResp from 64:70:02:9f:92:48 (capab=0x411 status=0 aid=3)
[   21.561279] wlan0: associated
[   21.561308] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   53.745905] wlan0: deauthenticating from 64:70:02:9f:92:48 by local choice (reason=3)
[   53.776839] cfg80211: Calling CRDA for country: IT
[   55.371561] init: anacron main process (1670) killed by TERM signal
[   56.462522] PM: Syncing filesystems ... done.
[   56.502024] Freezing user space processes ... (elapsed 0.01 seconds) done.
[   56.516175] Freezing remaining freezable tasks ... (elapsed 0.01 seconds) done.
[   56.532437] Suspending console(s) (use no_console_suspend to debug)
[   56.533015] sd 0:0:0:0: [sda] Synchronizing SCSI cache
[   56.760951] sd 0:0:0:0: [sda] Stopping disk
[   57.108247] PM: suspend of devices complete after 575.537 msecs
[   57.108669] PM: late suspend of devices complete after 0.408 msecs
[   57.124418] PM: noirq suspend of devices complete after 15.739 msecs
[   57.124469] ACPI: Preparing to enter system sleep state S3
[   57.151648] PM: Saving platform NVS memory
[   57.152862] Disabling non-boot CPUs ...
[   57.153316] Broke affinity for irq 14
[   57.256129] smpboot: CPU 1 is now offline
[   57.256733] ACPI: Low-level resume complete
[   57.256733] PM: Restoring platform NVS memory
[   57.256733] Enabling non-boot CPUs ...
[   57.256733] smpboot: Booting Node 0 Processor 1 APIC 0x1
[   57.154407] Initializing CPU#1
[   57.154407] Disabled fast string operations
[   57.268891] CPU1 is up
[   57.269554] ACPI: Waking up from system sleep state S3
[   57.420269] PM: noirq resume of devices complete after 96.027 msecs
[   57.420542] PM: early resume of devices complete after 0.189 msecs
[   57.420639] i915 0000:00:02.0: setting latency timer to 64
[   57.420807] snd_hda_intel 0000:00:1b.0: irq 43 for MSI/MSI-X
[   57.421151] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[   57.421188] usb usb2: root hub lost power or was reset
[   57.421217] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[   57.421250] usb usb3: root hub lost power or was reset
[   57.421277] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[   57.421309] usb usb4: root hub lost power or was reset
[   57.421336] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[   57.421369] usb usb5: root hub lost power or was reset
[   57.421397] ehci-pci 0000:00:1d.7: setting latency timer to 64
[   57.421434] pci 0000:00:1e.0: setting latency timer to 64
[   57.421461] ata_piix 0000:00:1f.2: setting latency timer to 64
[   57.664216] usb 1-5: reset high-speed USB device number 3 using ehci-pci
[   57.908211] usb 1-8: reset high-speed USB device number 4 using ehci-pci
[   58.036419] ata1.00: ACPI cmd ef/03:45:00:00:00:a0 (SET FEATURES) filtered out
[   58.036425] ata1.00: ACPI cmd ef/03:0c:00:00:00:a0 (SET FEATURES) filtered out
[   58.036861] ata1.00: ACPI cmd c6/00:10:00:00:00:a0 (SET MULTIPLE MODE) succeeded
[   58.060882] ata1.00: configured for UDMA/133
[   58.061091] sd 0:0:0:0: [sda] Starting disk
[   58.300248] usb 3-2: reset low-speed USB device number 2 using uhci_hcd
[   58.617843] PM: resume of devices complete after 1197.283 msecs
[   58.619888] ------------[ cut here ]------------
[   58.619911] WARNING: at /build/buildd/linux-lts-raring-3.8.0/kernel/trace/ring_buffer.c:2413 rb_reserve_next_event+0x22e/0x240()
[   58.619917] Hardware name: 1000H
[   58.619927] Delta way too big! 18446744017624307285 ts=18446744061686237053 write stamp = 44061929768
[   58.619927] If you just came from a suspend/resume,
[   58.619927] please switch to the trace global clock:
[   58.619927]   echo global > /sys/kernel/debug/tracing/trace_clock
[   58.618320] Restarting tasks ... 
[   58.619939] Modules linked in: bnep(F) rfcomm(F) bluetooth(F) parport_pc(F) ppdev(F) arc4(F) snd_hda_codec_realtek(F) rt2800pci(F) joydev(F) snd_hda_intel(F) rt2800lib(F) snd_hda_codec(F) crc_ccitt(F) rt2x00pci(F) uvcvideo(F) rt2x00lib(F) videobuf2_core(F) snd_hwdep(F) videodev(F) coretemp(F) snd_pcm(F) videobuf2_vmalloc(F) mac80211(F) i915(F) videobuf2_memops(F) snd_seq_midi(F) snd_rawmidi(F) snd_seq_midi_event(F) snd_seq(F) cfg80211(F) snd_timer(F) drm_kms_helper(F) snd_seq_device(F) psmouse(F) drm(F) microcode(F) snd(F) serio_raw(F) eeepc_laptop(F) lpc_ich(F) soundcore(F) snd_page_alloc(F) eeprom_93cx6(F) i2c_algo_bit(F) sparse_keymap(F) mac_hid(F) video(F) lp(F) parport(F) hid_generic(F) usbhid(F) hid(F) usb_storage(F) atl1e(F)
[   58.620160] Pid: 325, comm: udevd Tainted: GF            3.8.0-29-generic #42~precise1-Ubuntu
[   58.620167] Call Trace:
[   58.620186]  [<c104b7f2>] warn_slowpath_common+0x72/0xa0
[   58.620200]  [<c10e5b9e>] ? rb_reserve_next_event+0x22e/0x240
[   58.620213]  [<c10e5b9e>] ? rb_reserve_next_event+0x22e/0x240
[   58.620225]  [<c104b8c3>] warn_slowpath_fmt+0x33/0x40
[   58.620251]  [<c10e5b9e>] rb_reserve_next_event+0x22e/0x240
[   58.620273]  [<c10e5c15>] ring_buffer_lock_reserve+0x65/0xc0
[   58.620286]  [<c10eaea8>] trace_buffer_lock_reserve+0x18/0x50
[   58.620298]  [<c10eaf03>] trace_current_buffer_lock_reserve+0x23/0x30
[   58.620313]  [<c1161f25>] ftrace_raw_event_do_sys_open+0x55/0xd0
[   58.620327]  [<c1161ed0>] ? ftrace_raw_event_open_exec+0xc0/0xc0
[   58.620340]  [<c1163a33>] do_sys_open+0x1e3/0x220
[   58.620354]  [<c1163aa2>] sys_open+0x32/0x40
[   58.620369]  [<c163490d>] sysenter_do_call+0x12/0x28
[   58.620379] ---[ end trace 19ef1511be9bb4a6 ]---
[   58.639015] done.
[   58.639414] video LNXVIDEO:00: Restoring backlight state
[   59.050488] sd 2:0:0:0: [sdb] No Caching mode page present
[   59.050502] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   59.055609] sd 2:0:0:0: [sdb] No Caching mode page present
[   59.055623] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   59.058363]  sdb: sdb1
[   59.755280] init: anacron main process (2021) killed by TERM signal
[   59.960418] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   60.002589] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   63.033199] wlan0: authenticate with 64:70:02:9f:92:48
[   63.048648] wlan0: send auth to 64:70:02:9f:92:48 (try 1/3)
[   63.050149] wlan0: authenticated
[   63.052189] wlan0: associate with 64:70:02:9f:92:48 (try 1/3)
[   63.055946] wlan0: RX AssocResp from 64:70:02:9f:92:48 (capab=0x411 status=0 aid=3)
[   63.056454] wlan0: associated
[   63.056489] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   83.889206] audit_printk_skb: 24 callbacks suppressed
[   83.889220] type=1400 audit(1389029235.564:31): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/telepathy/mission-control-5" name="/usr/share/gvfs/remote-volume-monitors/" pid=2574 comm="mission-control" requested_mask="r" denied_mask="r" fsuid=100


6)[    1.050373] brd: module loaded
[    1.053071] loop: module loaded
[    1.053556] ata_piix 0000:00:1f.2: version 2.13
[    1.053591] ata_piix 0000:00:1f.2: MAP [
[    1.053596]  P0 P2 IDE IDE ]
[    1.053685] ata_piix 0000:00:1f.2: setting latency timer to 64
[    1.054488] scsi0 : ata_piix
[    1.056562] scsi1 : ata_piix
[    1.058125] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    1.058134] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    1.059413] libphy: Fixed MDIO Bus: probed
[    1.059759] tun: Universal TUN/TAP device driver, 1.6
[    1.059765] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.059940] PPP generic driver version 2.4.2
[    1.060156] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.060163] ehci-pci: EHCI PCI platform driver
[    1.060243] ehci-pci 0000:00:1d.7: setting latency timer to 64
[    1.060254] ehci-pci 0000:00:1d.7: EHCI Host Controller
[    1.060273] ehci-pci 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    1.060306] ehci-pci 0000:00:1d.7: debug port 1
[    1.064255] ehci-pci 0000:00:1d.7: cache line size of 32 is not supported
[    1.064313] ehci-pci 0000:00:1d.7: irq 23, io mem 0xf7eb7c00
[    1.076072] ehci-pci 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.076167] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    1.076202] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.076233] usb usb1: Product: EHCI Host Controller
[    1.076262] usb usb1: Manufacturer: Linux 3.8.0-29-generic ehci_hcd
[    1.076270] usb usb1: SerialNumber: 0000:00:1d.7
[    1.076604] hub 1-0:1.0: USB hub found
[    1.076622] hub 1-0:1.0: 8 ports detected
[    1.077061] ehci-platform: EHCI generic platform driver
[    1.077102] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.077170] uhci_hcd: USB Universal Host Controller Interface driver
[    1.077232] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.077243] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.077261] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.077319] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000d400
[    1.077432] usb usb2: New USB device found, idVendor=1d6b, idProduct=0001
[    1.077441] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.077449] usb usb2: Product: UHCI Host Controller
[    1.077457] usb usb2: Manufacturer: Linux 3.8.0-29-generic uhci_hcd
[    1.077464] usb usb2: SerialNumber: 0000:00:1d.0
[    1.077850] hub 2-0:1.0: USB hub found
[    1.077867] hub 2-0:1.0: 2 ports detected
[    1.078096] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.078107] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.078124] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    1.078197] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000d480
[    1.078301] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
[    1.078310] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.078318] usb usb3: Product: UHCI Host Controller
[    1.078326] usb usb3: Manufacturer: Linux 3.8.0-29-generic uhci_hcd
[    1.078334] usb usb3: SerialNumber: 0000:00:1d.1
[    1.078624] hub 3-0:1.0: USB hub found
[    1.078645] hub 3-0:1.0: 2 ports detected
[    1.078866] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.078877] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.078894] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    1.078968] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000d800
[    1.079088] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
[    1.079097] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.079105] usb usb4: Product: UHCI Host Controller
[    1.079113] usb usb4: Manufacturer: Linux 3.8.0-29-generic uhci_hcd
[    1.079120] usb usb4: SerialNumber: 0000:00:1d.2
[    1.079403] hub 4-0:1.0: USB hub found
[    1.079419] hub 4-0:1.0: 2 ports detected
[    1.079634] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    1.079645] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    1.079662] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    1.079729] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000d880
[    1.079831] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
[    1.079841] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.079848] usb usb5: Product: UHCI Host Controller
[    1.079856] usb usb5: Manufacturer: Linux 3.8.0-29-generic uhci_hcd
[    1.079864] usb usb5: SerialNumber: 0000:00:1d.3
[    1.080209] hub 5-0:1.0: USB hub found
[    1.080225] hub 5-0:1.0: 2 ports detected
[    1.080855] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.111320] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.111342] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.111743] mousedev: PS/2 mouse device common for all mice
[    1.112917] rtc_cmos 00:02: RTC can wake from S4
[    1.113174] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    1.113226] rtc0: alarms up to one month, 114 bytes nvram, hpet irqs
[    1.113635] device-mapper: uevent: version 1.0.3
[    1.113838] device-mapper: ioctl: 4.23.1-ioctl (2012-12-18) initialised: dm-devel@redhat.com
[    1.113905] EISA: Probing bus 0 at eisa.0
[    1.113913] EISA: Cannot allocate resource for mainboard
[    1.113921] Cannot allocate resource for EISA slot 1
[    1.113928] Cannot allocate resource for EISA slot 2
[    1.113935] Cannot allocate resource for EISA slot 3
[    1.113942] Cannot allocate resource for EISA slot 4
[    1.113949] Cannot allocate resource for EISA slot 5
[    1.113956] Cannot allocate resource for EISA slot 6
[    1.113963] Cannot allocate resource for EISA slot 7
[    1.113970] Cannot allocate resource for EISA slot 8
[    1.113975] EISA: Detected 0 cards.
[    1.113999] cpufreq-nforce2: No nForce2 chipset.
[    1.114129] cpuidle: using governor ladder
[    1.114293] cpuidle: using governor menu
[    1.114304] ledtrig-cpu: registered to indicate activity on CPUs
[    1.114310] EFI Variables Facility v0.08 2004-May-17
[    1.114913] ashmem: initialized
[    1.115303] TCP: cubic registered
[    1.115658] NET: Registered protocol family 10
[    1.116240] NET: Registered protocol family 17
[    1.116285] Key type dns_resolver registered
[    1.116771] Using IPI No-Shortcut mode
[    1.117035] Loading module verification certificates
[    1.131545] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: 760b08a5a1de9684ced1bfd52640b05fe41b6ca5'
[    1.131581] registered taskstats version 1
[    1.138449] Key type trusted registered
[    1.145388] Key type encrypted registered
[    1.152902] rtc_cmos 00:02: setting system clock to 2014-01-06 17:25:16 UTC (1389029116)
[    1.153851] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.153858] EDD information not available.
[    1.164274] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.228666] ata1.00: ATA-8: ST9160310AS, 0303, max UDMA/133
[    1.228677] ata1.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.244625] ata1.00: configured for UDMA/133
[    1.266202] ACPI: Battery Slot [BAT0] (battery present)
[    1.393693] isapnp: No Plug & Play device found
[    1.394021] scsi 0:0:0:0: Direct-Access     ATA      ST9160310AS      0303 PQ: 0 ANSI: 5
[    1.394380] sd 0:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    1.394487] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.394598] sd 0:0:0:0: [sda] Write Protect is off
[    1.394611] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.394720] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.444162] usb 1-5: new high-speed USB device number 3 using ehci-pci
[    1.578196] usb 1-5: New USB device found, idVendor=058f, idProduct=6335
[    1.578215] usb 1-5: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    1.578239] usb 1-5: Product: Mass Storage Device
[    1.578246] usb 1-5: Manufacturer: Generic
[    1.578252] usb 1-5: SerialNumber: 058F63356336
[    1.688136] usb 1-8: new high-speed USB device number 4 using ehci-pci
[    1.695712]  sda: sda1 sda2 < sda5 >
[    1.696915] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.697086] Freeing unused kernel memory: 796k freed
[    1.697749] Write protecting the kernel text: 6360k
[    1.697895] Write protecting the kernel read-only data: 2496k
[    1.697901] NX-protecting the kernel data: 3880k
[    1.745506] udevd[101]: starting version 175
[    1.864902] usb 1-8: New USB device found, idVendor=04f2, idProduct=b071
[    1.864916] usb 1-8: New USB device strings: Mfr=2, Product=1, SerialNumber=3
[    1.864925] usb 1-8: Product: CNF7129
[    1.864934] usb 1-8: Manufacturer: Chicony Electronics Co., Ltd.
[    1.864942] usb 1-8: SerialNumber: SN0001
[    2.026454] Disabling lock debugging due to kernel taint
[    2.045969] Initializing USB Mass Storage driver...
[    2.048241] scsi2 : usb-storage 1-5:1.0
[    2.048626] usbcore: registered new interface driver usb-storage
[    2.048635] USB Mass Storage support registered.
[    2.108093] usb 3-2: new low-speed USB device number 2 using uhci_hcd
[    2.283514] usb 3-2: New USB device found, idVendor=046d, idProduct=c016
[    2.283541] usb 3-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.283566] usb 3-2: Product: Optical USB Mouse
[    2.283575] usb 3-2: Manufacturer: Logitech
[    2.309484] usbcore: registered new interface driver usbhid
[    2.309493] usbhid: USB HID core driver
[    2.316795] input: Logitech Optical USB Mouse as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.0/input/input5
[    2.317370] hid-generic 0003:046D:C016.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:1d.1-2/input0
[    2.529431] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    3.049172] scsi 2:0:0:0: Direct-Access     Single   Flash Reader     1.00 PQ: 0 ANSI: 0
[    3.051112] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    3.457245] sd 2:0:0:0: [sdb] 7835648 512-byte logical blocks: (4.01 GB/3.73 GiB)
[    3.458566] sd 2:0:0:0: [sdb] Write Protect is off
[    3.458578] sd 2:0:0:0: [sdb] Mode Sense: 03 00 00 00
[    3.459667] sd 2:0:0:0: [sdb] No Caching mode page present
[    3.459675] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    3.464173] sd 2:0:0:0: [sdb] No Caching mode page present
[    3.464182] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    3.466437]  sdb: sdb1
[    3.469664] sd 2:0:0:0: [sdb] No Caching mode page present
[    3.469673] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    3.470416] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[    4.000593] init: ureadahead main process (249) terminated with status 5
[    5.232094] Adding 1038332k swap on /dev/sda5.  Priority:-1 extents:1 across:1038332k 
[    6.396218] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    6.947434] udevd[325]: starting version 175
[    7.589039] lp: driver loaded but no devices found
[    7.826969] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[    8.236581] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[    8.236976] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input6
[    8.427039] intel_rng: FWH not detected
[    8.540573] ACPI Warning: 0x00000828-0x0000082f SystemIO conflicts with Region \PMIO 1 (20121018/utaddress-251)
[    8.540597] ACPI Warning: 0x00000828-0x0000082f SystemIO conflicts with Region \_SB_.PCI0.SBRG.PMS0 2 (20121018/utaddress-251)
[    8.540613] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    8.540625] ACPI Warning: 0x000004b0-0x000004bf SystemIO conflicts with Region \_SB_.PCI0.SBRG.GPBX 1 (20121018/utaddress-251)
[    8.540638] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    8.540645] ACPI Warning: 0x00000480-0x000004af SystemIO conflicts with Region \_SB_.PCI0.SBRG.GPBX 1 (20121018/utaddress-251)
[    8.540659] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    8.540665] lpc_ich: Resource conflict(s) found affecting gpio_ich
[    8.556435] eeepc_laptop: Eee PC Hotkey Driver
[    8.556463] eeepc_laptop: Hotkey init flags 0x41
[    8.585723] eeepc_laptop: TYPE (2000000) not reported by BIOS, enabling anyway
[    8.590949] eeepc_laptop: PANELPOWER (4000000) not reported by BIOS, enabling anyway
[    8.590967] eeepc_laptop: Get control methods supported: 0x6101713
[    8.604876] input: Asus EeePC extra buttons as /devices/platform/eeepc/input/input7
[    8.641413] leds_ss4200: no LED devices found
[    8.739015] microcode: CPU0 sig=0x106c2, pf=0x4, revision=0x212
[    8.776114] [drm] Initialized drm 1.1.0 20060810
[    8.984132] cfg80211: Calling CRDA to update world regulatory domain
[    9.314543] microcode: CPU1 sig=0x106c2, pf=0x4, revision=0x212
[    9.321326] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    9.429208] i915 0000:00:02.0: setting latency timer to 64
[    9.432275] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    9.432285] [drm] Driver supports precise vblank timestamp query.
[    9.434903] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    9.584126] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 207
[    9.584155] Raw EDID:
[    9.584171]  	00 ff ff ff ff ff ff 00 22 64 e9 03 c9 06 00 00
[    9.584188]  	12 12 01 03 80 16 0d 78 0a 86 26 94 57 51 90 27
[    9.584205]  	21 4f 54 00 00 00 01 01 01 01 01 01 01 01 01 01
[    9.584221]  	01 01 01 01 01 01 94 11 00 b0 40 58 19 20 35 23
[    9.584237]  	45 00 dc 81 00 00 00 19 16 14 00 d8 40 58 26 20
[    9.584254]  	5d 23 15 04 dc 81 00 00 00 00 00 00 00 fe 00 00
[    9.584270]  	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 fe
[    9.584286]  	00 00 00 00 00 00 00 00 00 01 00 00 00 00 00 c8
[    9.638794] Linux video capture interface: v2.00
[    9.720087] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 207
[    9.720104] Raw EDID:
[    9.720113]  	00 ff ff ff ff ff ff 00 22 64 e9 03 c9 06 00 00
[    9.720121]  	12 12 01 03 80 16 0d 78 0a 86 26 94 57 51 90 27
[    9.720129]  	21 4f 54 00 00 00 01 01 01 01 01 01 01 01 01 01
[    9.720137]  	01 01 01 01 01 01 94 11 00 b0 40 58 19 20 35 23
[    9.720145]  	45 00 dc 81 00 00 00 19 16 14 00 d8 40 58 26 20
[    9.720154]  	5d 23 15 04 dc 81 00 00 00 00 00 00 00 fe 00 00
[    9.720162]  	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 fe
[    9.720170]  	00 00 00 00 00 00 00 00 00 01 00 00 00 00 00 c8
[    9.864084] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 207
[    9.864105] Raw EDID:
[    9.864122]  	00 ff ff ff ff ff ff 00 22 64 e9 03 c9 06 00 00
[    9.864139]  	12 12 01 03 80 16 0d 78 0a 86 26 94 57 51 90 27
[    9.864155]  	21 4f 54 00 00 00 01 01 01 01 01 01 01 01 01 01
[    9.864171]  	01 01 01 01 01 01 94 11 00 b0 40 58 19 20 35 23
[    9.864187]  	45 00 dc 81 00 00 00 19 16 14 00 d8 40 58 26 20
[    9.864204]  	5d 23 15 04 dc 81 00 00 00 00 00 00 00 fe 00 00
[    9.864217]  	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 fe
[    9.864227]  	00 00 00 00 00 00 00 00 00 01 00 00 00 00 00 c8
[    9.976660] uvcvideo: Found UVC 1.00 device CNF7129 (04f2:b071)
[    9.993810] input: CNF7129 as /devices/pci0000:00/0000:00:1d.7/usb1/1-8/1-8:1.0/input/input8
[    9.994437] usbcore: registered new interface driver uvcvideo
[    9.994447] USB Video Class driver (1.1.1)
[   10.000108] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 207
[   10.000137] Raw EDID:
[   10.000153]  	00 ff ff ff ff ff ff 00 22 64 e9 03 c9 06 00 00
[   10.000171]  	12 12 01 03 80 16 0d 78 0a 86 26 94 57 51 90 27
[   10.000188]  	21 4f 54 00 00 00 01 01 01 01 01 01 01 01 01 01
[   10.000205]  	01 01 01 01 01 01 94 11 00 b0 40 58 19 20 35 23
[   10.000222]  	45 00 dc 81 00 00 00 19 16 14 00 d8 40 58 26 20
[   10.000238]  	5d 23 15 04 dc 81 00 00 00 00 00 00 00 fe 00 00
[   10.000256]  	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 fe
[   10.000272]  	00 00 00 00 00 00 00 00 00 01 00 00 00 00 00 c8
[   10.000298] i915 0000:00:02.0: LVDS-1: EDID block 0 invalid.
[   10.001819] psmouse serio1: elantech: assuming hardware version 2 (with firmware version 0x020030)
[   10.003785] [drm] initialized overlay support
[   10.074268] psmouse serio1: elantech: Synaptics capabilities query result 0x00, 0x02, 0x64.
[   10.296379] input: ETPS/2 Elantech Touchpad as /devices/platform/i8042/serio1/input/input9
[   10.326027] fbcon: inteldrmfb (fb0) is primary device
[   10.757224] Console: switching to colour frame buffer device 128x37
[   10.764754] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[   10.764760] i915 0000:00:02.0: registered panic notifier
[   10.764778] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   10.765202] snd_hda_intel 0000:00:1b.0: irq 43 for MSI/MSI-X
[   10.890376] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   10.891004] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   11.009748] eeepc_laptop: Unable to find port
[   11.335506] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   11.682259] type=1400 audit(1389029127.023:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=593 comm="apparmor_parser"
[   11.682285] type=1400 audit(1389029127.023:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=592 comm="apparmor_parser"
[   11.683385] type=1400 audit(1389029127.023:4): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=686 comm="apparmor_parser"
[   11.683922] type=1400 audit(1389029127.023:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=593 comm="apparmor_parser"
[   11.685030] type=1400 audit(1389029127.027:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=593 comm="apparmor_parser"
[   11.685154] type=1400 audit(1389029127.027:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=686 comm="apparmor_parser"
[   11.686145] type=1400 audit(1389029127.027:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=686 comm="apparmor_parser"
[   11.690595] type=1400 audit(1389029127.031:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=592 comm="apparmor_parser"
[   11.691553] type=1400 audit(1389029127.031:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=592 comm="apparmor_parser"
[   12.569692] init: failsafe main process (701) killed by TERM signal
[   14.459979] ppdev: user-space parallel port driver
[   15.088134] Bluetooth: Core ver 2.16
[   15.088208] NET: Registered protocol family 31
[   15.088217] Bluetooth: HCI device and connection manager initialized
[   15.088241] Bluetooth: HCI socket layer initialized
[   15.088253] Bluetooth: L2CAP socket layer initialized
[   15.088276] Bluetooth: SCO socket layer initialized
[   15.187198] Bluetooth: RFCOMM TTY layer initialized
[   15.187234] Bluetooth: RFCOMM socket layer initialized
[   15.187242] Bluetooth: RFCOMM ver 1.11
[   15.284379] type=1400 audit(1389029130.627:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=802 comm="apparmor_parser"
[   15.362532] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   15.362545] Bluetooth: BNEP filters: protocol multicast
[   15.362754] Bluetooth: BNEP socket layer initialized
[   17.996506] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   17.997890] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   18.010268] audit_printk_skb: 3 callbacks suppressed
[   18.010277] type=1400 audit(1389029133.351:13): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=869 comm="apparmor_parser"
[   18.011498] type=1400 audit(1389029133.351:14): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=869 comm="apparmor_parser"
[   18.012312] type=1400 audit(1389029133.355:15): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=869 comm="apparmor_parser"
[   18.060778] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   18.061609] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   18.067816] type=1400 audit(1389029133.407:16): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=868 comm="apparmor_parser"
[   18.069624] type=1400 audit(1389029133.411:17): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper//chromium_browser" pid=868 comm="apparmor_parser"
[   18.156733] type=1400 audit(1389029133.499:18): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=875 comm="apparmor_parser"
[   18.158533] type=1400 audit(1389029133.499:19): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=875 comm="apparmor_parser"
[   18.172806] type=1400 audit(1389029133.515:20): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=876 comm="apparmor_parser"
[   18.174250] type=1400 audit(1389029133.515:21): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=876 comm="apparmor_parser"
[   18.229306] type=1400 audit(1389029133.571:22): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=878 comm="apparmor_parser"
[   20.225877] init: anacron main process (937) killed by TERM signal
[   21.533835] wlan0: authenticate with 64:70:02:9f:92:48
[   21.552570] wlan0: send auth to 64:70:02:9f:92:48 (try 1/3)
[   21.554363] wlan0: authenticated
[   21.556629] wlan0: associate with 64:70:02:9f:92:48 (try 1/3)
[   21.560800] wlan0: RX AssocResp from 64:70:02:9f:92:48 (capab=0x411 status=0 aid=3)
[   21.561279] wlan0: associated
[   21.561308] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   53.745905] wlan0: deauthenticating from 64:70:02:9f:92:48 by local choice (reason=3)
[   53.776839] cfg80211: Calling CRDA for country: IT
[   55.371561] init: anacron main process (1670) killed by TERM signal
[   56.462522] PM: Syncing filesystems ... done.
[   56.502024] Freezing user space processes ... (elapsed 0.01 seconds) done.
[   56.516175] Freezing remaining freezable tasks ... (elapsed 0.01 seconds) done.
[   56.532437] Suspending console(s) (use no_console_suspend to debug)
[   56.533015] sd 0:0:0:0: [sda] Synchronizing SCSI cache
[   56.760951] sd 0:0:0:0: [sda] Stopping disk
[   57.108247] PM: suspend of devices complete after 575.537 msecs
[   57.108669] PM: late suspend of devices complete after 0.408 msecs
[   57.124418] PM: noirq suspend of devices complete after 15.739 msecs
[   57.124469] ACPI: Preparing to enter system sleep state S3
[   57.151648] PM: Saving platform NVS memory
[   57.152862] Disabling non-boot CPUs ...
[   57.153316] Broke affinity for irq 14
[   57.256129] smpboot: CPU 1 is now offline
[   57.256733] ACPI: Low-level resume complete
[   57.256733] PM: Restoring platform NVS memory
[   57.256733] Enabling non-boot CPUs ...
[   57.256733] smpboot: Booting Node 0 Processor 1 APIC 0x1
[   57.154407] Initializing CPU#1
[   57.154407] Disabled fast string operations
[   57.268891] CPU1 is up
[   57.269554] ACPI: Waking up from system sleep state S3
[   57.420269] PM: noirq resume of devices complete after 96.027 msecs
[   57.420542] PM: early resume of devices complete after 0.189 msecs
[   57.420639] i915 0000:00:02.0: setting latency timer to 64
[   57.420807] snd_hda_intel 0000:00:1b.0: irq 43 for MSI/MSI-X
[   57.421151] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[   57.421188] usb usb2: root hub lost power or was reset
[   57.421217] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[   57.421250] usb usb3: root hub lost power or was reset
[   57.421277] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[   57.421309] usb usb4: root hub lost power or was reset
[   57.421336] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[   57.421369] usb usb5: root hub lost power or was reset
[   57.421397] ehci-pci 0000:00:1d.7: setting latency timer to 64
[   57.421434] pci 0000:00:1e.0: setting latency timer to 64
[   57.421461] ata_piix 0000:00:1f.2: setting latency timer to 64
[   57.664216] usb 1-5: reset high-speed USB device number 3 using ehci-pci
[   57.908211] usb 1-8: reset high-speed USB device number 4 using ehci-pci
[   58.036419] ata1.00: ACPI cmd ef/03:45:00:00:00:a0 (SET FEATURES) filtered out
[   58.036425] ata1.00: ACPI cmd ef/03:0c:00:00:00:a0 (SET FEATURES) filtered out
[   58.036861] ata1.00: ACPI cmd c6/00:10:00:00:00:a0 (SET MULTIPLE MODE) succeeded
[   58.060882] ata1.00: configured for UDMA/133
[   58.061091] sd 0:0:0:0: [sda] Starting disk
[   58.300248] usb 3-2: reset low-speed USB device number 2 using uhci_hcd
[   58.617843] PM: resume of devices complete after 1197.283 msecs
[   58.619888] ------------[ cut here ]------------
[   58.619911] WARNING: at /build/buildd/linux-lts-raring-3.8.0/kernel/trace/ring_buffer.c:2413 rb_reserve_next_event+0x22e/0x240()
[   58.619917] Hardware name: 1000H
[   58.619927] Delta way too big! 18446744017624307285 ts=18446744061686237053 write stamp = 44061929768
[   58.619927] If you just came from a suspend/resume,
[   58.619927] please switch to the trace global clock:
[   58.619927]   echo global > /sys/kernel/debug/tracing/trace_clock
[   58.618320] Restarting tasks ... 
[   58.619939] Modules linked in: bnep(F) rfcomm(F) bluetooth(F) parport_pc(F) ppdev(F) arc4(F) snd_hda_codec_realtek(F) rt2800pci(F) joydev(F) snd_hda_intel(F) rt2800lib(F) snd_hda_codec(F) crc_ccitt(F) rt2x00pci(F) uvcvideo(F) rt2x00lib(F) videobuf2_core(F) snd_hwdep(F) videodev(F) coretemp(F) snd_pcm(F) videobuf2_vmalloc(F) mac80211(F) i915(F) videobuf2_memops(F) snd_seq_midi(F) snd_rawmidi(F) snd_seq_midi_event(F) snd_seq(F) cfg80211(F) snd_timer(F) drm_kms_helper(F) snd_seq_device(F) psmouse(F) drm(F) microcode(F) snd(F) serio_raw(F) eeepc_laptop(F) lpc_ich(F) soundcore(F) snd_page_alloc(F) eeprom_93cx6(F) i2c_algo_bit(F) sparse_keymap(F) mac_hid(F) video(F) lp(F) parport(F) hid_generic(F) usbhid(F) hid(F) usb_storage(F) atl1e(F)
[   58.620160] Pid: 325, comm: udevd Tainted: GF            3.8.0-29-generic #42~precise1-Ubuntu
[   58.620167] Call Trace:
[   58.620186]  [<c104b7f2>] warn_slowpath_common+0x72/0xa0
[   58.620200]  [<c10e5b9e>] ? rb_reserve_next_event+0x22e/0x240
[   58.620213]  [<c10e5b9e>] ? rb_reserve_next_event+0x22e/0x240
[   58.620225]  [<c104b8c3>] warn_slowpath_fmt+0x33/0x40
[   58.620251]  [<c10e5b9e>] rb_reserve_next_event+0x22e/0x240
[   58.620273]  [<c10e5c15>] ring_buffer_lock_reserve+0x65/0xc0
[   58.620286]  [<c10eaea8>] trace_buffer_lock_reserve+0x18/0x50
[   58.620298]  [<c10eaf03>] trace_current_buffer_lock_reserve+0x23/0x30
[   58.620313]  [<c1161f25>] ftrace_raw_event_do_sys_open+0x55/0xd0
[   58.620327]  [<c1161ed0>] ? ftrace_raw_event_open_exec+0xc0/0xc0
[   58.620340]  [<c1163a33>] do_sys_open+0x1e3/0x220
[   58.620354]  [<c1163aa2>] sys_open+0x32/0x40
[   58.620369]  [<c163490d>] sysenter_do_call+0x12/0x28
[   58.620379] ---[ end trace 19ef1511be9bb4a6 ]---
[   58.639015] done.
[   58.639414] video LNXVIDEO:00: Restoring backlight state
[   59.050488] sd 2:0:0:0: [sdb] No Caching mode page present
[   59.050502] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   59.055609] sd 2:0:0:0: [sdb] No Caching mode page present
[   59.055623] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   59.058363]  sdb: sdb1
[   59.755280] init: anacron main process (2021) killed by TERM signal
[   59.960418] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   60.002589] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   63.033199] wlan0: authenticate with 64:70:02:9f:92:48
[   63.048648] wlan0: send auth to 64:70:02:9f:92:48 (try 1/3)
[   63.050149] wlan0: authenticated
[   63.052189] wlan0: associate with 64:70:02:9f:92:48 (try 1/3)
[   63.055946] wlan0: RX AssocResp from 64:70:02:9f:92:48 (capab=0x411 status=0 aid=3)
[   63.056454] wlan0: associated
[   63.056489] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   83.889206] audit_printk_skb: 24 callbacks suppressed
[   83.889220] type=1400 audit(1389029235.564:31): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/telepathy/mission-control-5" name="/usr/share/gvfs/remote-volume-monitors/" pid=2574 comm="mission-control" requested_mask="r" denied_mask="r" fsuid=100


7)marco@marco-1000H:~$ iwlist scan
wlan0     Scan completed :
          Cell 01 - Address: 64:70:02:9F:92:48
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=64/70  Signal level=-46 dBm  
                    Encryption key:on
                    ESSID:"MysteryStyle"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000010daf19617a
                    Extra: Last beacon: 90664ms ago
                    IE: Unknown: 000C4D7973746572795374796C65
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010D
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1AEE1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D160D000600000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: DD07000C4304000000
                    IE: Unknown: 0706495400010D10
                    IE: Unknown: DD9D0050F204104A0001001044000102103B00010310470010BC329E001DD811B286016470029F92481021001852616C696E6B20546563686E6F6C6F67792C20436F72702E1023001C52616C696E6B20576972656C6573732041636365737320506F696E74102400065254323836301042000831323334353637381054000800060050F20400011011000952616C696E6B415053100800020004103C000100


lo        Interface doesn't support scanning.


eth0      Interface doesn't support scanning.




8) marco@marco-1000H:~$ lsb_release -d
Description:	Ubuntu 12.04.3 LTS




9)marco@marco-1000H:~$ uname -mr
3.8.0-29-generic i686


10) marco@marco-1000H:~$ sudo service networking restart
stop: Unknown instance: 
networking stop/waiting







```

---

### Post by wkcchampion on 2014-01-07
Bump

---

### Post by praseodym on 2014-01-07
Deactivate the power management:
```

sudo iwconfig wlan0 power off
```
Check the encryption mode of your router: Mixed TKIP/CCMP looks weird, change to pure WPA2-AES (CCMP)

---

### Post by Bucky Ball on 2014-01-07
Could be related to this bug related specifically to 12.04 and that chipset:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/989473](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/989473)

You could try installing a newer kernel. Apparently that bug has been fixed in more recent kernels (from 3.4).

---

### Post by wkcchampion on 2014-01-08
> **praseodym said:**
> Deactivate the power management:
```

sudo iwconfig wlan0 power off
```
Check the encryption mode of your router:  Mixed TKIP/CCMP looks weird, change to pure WPA2-AES (CCMP)


Thanks!!! These two suggestions solved it! I've been testing it since yesterday afternoon and it seems to work perfectly!
Thread is solved.

---

