---
title: "Sierra Wireless 313U not connecting/wireless networks not connecting"
date: 2013-11-19
forum: Networking &amp; Wireless
---

### Post by mnmcintosh on 2013-11-19
Hello all,

I am new to Ubuntu (as of yesterday!) and I am having trouble connecting to the internet.  I have a USB data card (Sierra Wireless Aircard 313U/AT&T USB Connect Momentum) that works in Windows on my ASUS zenbook, but isn't working in Ubuntu.  I used the network manager to set it up, and it seems to detect it and even connect, but promptly afterwards it disconnects.  I also tried a wireless network at a local cafe. The network manager detected the connection and attempted to connect, but was caught in an endless loop of trying to connect. When I logged into Windows, I could connect to the wifi.  Could someone help me trouble shoot or point me to a forum where this was solved?  Thanks!

---

### Post by mnmcintosh on 2013-11-19
Here is the info I saw to give on another post-


    
   
        1 ) Machine Brand and Model (PC/Laptop): ASUS UX31E

        2 ) $ lspci

00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b5)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b5)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation QS67 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
02:00.0 Network controller: Atheros Communications Inc. AR9485 Wireless Network Adapter (rev 01)
03:00.0 USB controller: Fresco Logic Device 1009 (rev 02)


        $ lsusb


Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 0781:5575 SanDisk Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0f3d:68aa Airprime, Incorporated 
Bus 001 Device 004: ID 13d3:5719 IMC Networks 
Bus 001 Device 005: ID 0bda:0139 Realtek Semiconductor Corp. 
Bus 001 Device 007: ID 13d3:3375 IMC Networks 

        3 ) $ ifconfig

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:128 errors:0 dropped:0 overruns:0 frame:0
          TX packets:128 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9472 (9.4 KB)  TX bytes:9472 (9.4 KB)

wlan0     Link encap:Ethernet  HWaddr 00:08:ca:e7:58:ec  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


        $ iwconfig


wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
wwan0     no wireless extensions.

lo        no wireless extensions.

        4 ) $ lsmod

Module                  Size  Used by
nls_iso8859_1          12617  1 
joydev                 17329  0 
dm_crypt               22555  0 
coretemp               13324  0 
kvm_intel             127786  0 
kvm                   384557  1 kvm_intel
asus_nb_wmi            12734  0 
asus_wmi               23821  1 asus_nb_wmi
sparse_keymap          13658  1 asus_wmi
snd_hda_codec_hdmi     36583  1 
snd_hda_codec_realtek    65004  1 
snd_hda_intel          38819  3 
snd_hda_codec         118613  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                85934  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
microcode              18433  0 
rts5139               279817  0 
snd_seq_midi           13132  0 
snd_rawmidi            25157  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
sierra                 17857  0 
arc4                   12509  2 
snd_seq                51593  2 snd_seq_midi,snd_seq_midi_event
usbserial              27633  1 sierra
sierra_net             13397  0 
usbnet                 26644  1 sierra_net
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14137  3 snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               72250  0 
videobuf2_core         39385  1 uvcvideo
ath3k                  12832  0 
videodev               96131  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12920  1 uvcvideo
btusb                  17951  0 
videobuf2_memops       13042  1 videobuf2_vmalloc
ath9k                 136512  0 
psmouse                82769  0 
serio_raw              13031  0 
bnep                   17852  2 
rfcomm                 38400  12 
mac80211              541819  1 ath9k
bluetooth             211435  25 ath3k,btusb,bnep,rfcomm
ath9k_common           13781  1 ath9k
ath9k_hw              406597  2 ath9k,ath9k_common
lpc_ich                17048  0 
mac_hid                13077  0 
ath                    19435  3 ath9k,ath9k_common,ath9k_hw
parport_pc             27612  0 
ppdev                  12849  0 
cfg80211              453853  3 ath9k,mac80211,ath
lp                     17455  0 
snd                    57014  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
parport                40930  3 parport_pc,ppdev,lp
soundcore              12600  1 snd
snd_page_alloc         18398  2 snd_hda_intel,snd_pcm
mei                    36756  0 
usb_storage            48053  1 
aesni_intel            18196  104 
ablk_helper            13357  1 aesni_intel
cryptd                 19821  1 ablk_helper
lrw                    13127  1 aesni_intel
aes_i586               16995  1 aesni_intel
xts                    12778  1 aesni_intel
gf128mul               14503  2 lrw,xts
wmi                    18744  1 asus_wmi
i915                  550346  3 
ahci                   25631  1 
libahci                26336  1 ahci
drm_kms_helper         47749  1 i915
drm                   233935  4 i915,drm_kms_helper
i2c_algo_bit           13316  1 i915
video                  19116  2 asus_wmi,i915

        5 )  $ dmesg

[    0.183693] PnPBIOS: Disabled by ACPI PNP
[    0.220011] pci 0000:00:1c.0: PCI bridge to [bus 01]
[    0.220016] pci 0000:00:1c.0:   bridge window [io  0xd000-0xdfff]
[    0.220023] pci 0000:00:1c.0:   bridge window [mem 0xdf400000-0xdfdfffff]
[    0.220028] pci 0000:00:1c.0:   bridge window [mem 0xd1600000-0xd1ffffff 64bit pref]
[    0.220036] pci 0000:00:1c.1: PCI bridge to [bus 02]
[    0.220040] pci 0000:00:1c.1:   bridge window [io  0xc000-0xcfff]
[    0.220046] pci 0000:00:1c.1:   bridge window [mem 0xdea00000-0xdf3fffff]
[    0.220051] pci 0000:00:1c.1:   bridge window [mem 0xd0b00000-0xd14fffff 64bit pref]
[    0.220058] pci 0000:00:1c.3: PCI bridge to [bus 03]
[    0.220062] pci 0000:00:1c.3:   bridge window [io  0xb000-0xbfff]
[    0.220068] pci 0000:00:1c.3:   bridge window [mem 0xde000000-0xde9fffff]
[    0.220073] pci 0000:00:1c.3:   bridge window [mem 0xd0000000-0xd09fffff 64bit pref]
[    0.220114] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.220116] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.220119] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.220121] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000d3fff]
[    0.220123] pci_bus 0000:00: resource 8 [mem 0x000d4000-0x000d7fff]
[    0.220125] pci_bus 0000:00: resource 9 [mem 0x000d8000-0x000dbfff]
[    0.220127] pci_bus 0000:00: resource 10 [mem 0x000dc000-0x000dffff]
[    0.220130] pci_bus 0000:00: resource 11 [mem 0x000e0000-0x000e3fff]
[    0.220132] pci_bus 0000:00: resource 12 [mem 0x000e4000-0x000e7fff]
[    0.220134] pci_bus 0000:00: resource 13 [mem 0xc0000000-0xfeafffff]
[    0.220136] pci_bus 0000:00: resource 14 [mem 0xfed40000-0xfed44fff]
[    0.220138] pci_bus 0000:01: resource 0 [io  0xd000-0xdfff]
[    0.220140] pci_bus 0000:01: resource 1 [mem 0xdf400000-0xdfdfffff]
[    0.220143] pci_bus 0000:01: resource 2 [mem 0xd1600000-0xd1ffffff 64bit pref]
[    0.220145] pci_bus 0000:02: resource 0 [io  0xc000-0xcfff]
[    0.220147] pci_bus 0000:02: resource 1 [mem 0xdea00000-0xdf3fffff]
[    0.220149] pci_bus 0000:02: resource 2 [mem 0xd0b00000-0xd14fffff 64bit pref]
[    0.220152] pci_bus 0000:03: resource 0 [io  0xb000-0xbfff]
[    0.220154] pci_bus 0000:03: resource 1 [mem 0xde000000-0xde9fffff]
[    0.220156] pci_bus 0000:03: resource 2 [mem 0xd0000000-0xd09fffff 64bit pref]
[    0.220189] NET: Registered protocol family 2
[    0.220331] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[    0.220350] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[    0.220365] TCP: Hash tables configured (established 8192 bind 8192)
[    0.220378] TCP: reno registered
[    0.220381] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.220386] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.220438] NET: Registered protocol family 1
[    0.220450] pci 0000:00:02.0: Boot video device
[    0.347670] PCI: CLS 64 bytes, default 64
[    0.347715] Trying to unpack rootfs image as initramfs...
[    0.820449] Freeing initrd memory: 21756k freed
[    0.824036] Initialise module verification
[    0.824079] audit: initializing netlink socket (disabled)
[    0.824094] type=2000 audit(1384878298.824:1): initialized
[    0.850503] bounce pool size: 64 pages
[    0.850518] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.852136] VFS: Disk quotas dquot_6.5.2
[    0.852186] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.852692] fuse init (API version 7.20)
[    0.852776] msgmni has been set to 1653
[    0.853208] Key type asymmetric registered
[    0.853211] Asymmetric key parser 'x509' registered
[    0.853245] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    0.853274] io scheduler noop registered
[    0.853277] io scheduler deadline registered (default)
[    0.853284] io scheduler cfq registered
[    0.853429] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[    0.853548] pcieport 0000:00:1c.1: irq 41 for MSI/MSI-X
[    0.853663] pcieport 0000:00:1c.3: irq 42 for MSI/MSI-X
[    0.853756] pcieport 0000:00:1c.0: Signaling PME through PCIe PME interrupt
[    0.853762] pcie_pme 0000:00:1c.0:pcie01: service driver pcie_pme loaded
[    0.853783] pcieport 0000:00:1c.1: Signaling PME through PCIe PME interrupt
[    0.853785] pci 0000:02:00.0: Signaling PME through PCIe PME interrupt
[    0.853791] pcie_pme 0000:00:1c.1:pcie01: service driver pcie_pme loaded
[    0.853810] pcieport 0000:00:1c.3: Signaling PME through PCIe PME interrupt
[    0.853812] pci 0000:03:00.0: Signaling PME through PCIe PME interrupt
[    0.853817] pcie_pme 0000:00:1c.3:pcie01: service driver pcie_pme loaded
[    0.853830] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.853845] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.853910] intel_idle: MWAIT substates: 0x21120
[    0.853912] intel_idle: v0.4 model 0x2A
[    0.853913] intel_idle: lapic_timer_reliable_states 0xffffffff
[    0.854010] ACPI: AC Adapter [AC0] (off-line)
[    0.854121] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    0.875377] ACPI: Lid Switch [LID]
[    0.875418] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
[    0.875422] ACPI: Power Button [PWRB]
[    0.875454] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2
[    0.875458] ACPI: Sleep Button [SLPB]
[    0.875529] ACPI: Requesting acpi_cpufreq
[    0.882062] thermal LNXTHERM:00: registered as thermal_zone0
[    0.882065] ACPI: Thermal Zone [THRM] (59 C)
[    0.882100] GHES: HEST is not enabled!
[    0.882165] isapnp: Scanning for PnP cards...
[    0.882216] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.886327] Linux agpgart interface v0.103
[    0.888335] brd: module loaded
[    0.890130] loop: module loaded
[    0.891329] libphy: Fixed MDIO Bus: probed
[    0.891554] tun: Universal TUN/TAP device driver, 1.6
[    0.891556] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.891630] PPP generic driver version 2.4.2
[    0.891777] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.891779] ehci-pci: EHCI PCI platform driver
[    0.891861] ehci-pci 0000:00:1d.0: setting latency timer to 64
[    0.891882] ehci-pci 0000:00:1d.0: EHCI Host Controller
[    0.891916] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    0.891935] ehci-pci 0000:00:1d.0: debug port 2
[    0.894436] ACPI: Battery Slot [BAT0] (battery present)
[    0.895867] ehci-pci 0000:00:1d.0: cache line size of 64 is not supported
[    0.895888] ehci-pci 0000:00:1d.0: irq 23, io mem 0xdfe07000
[    0.907168] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    0.907201] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.907205] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.907208] usb usb1: Product: EHCI Host Controller
[    0.907210] usb usb1: Manufacturer: Linux 3.8.0-29-generic ehci_hcd
[    0.907213] usb usb1: SerialNumber: 0000:00:1d.0
[    0.907350] hub 1-0:1.0: USB hub found
[    0.907356] hub 1-0:1.0: 2 ports detected
[    0.907468] ehci-platform: EHCI generic platform driver
[    0.907478] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.907497] uhci_hcd: USB Universal Host Controller Interface driver
[    0.907553] xhci_hcd 0000:03:00.0: xHCI Host Controller
[    0.907559] xhci_hcd 0000:03:00.0: new USB bus registered, assigned bus number 2
[    0.907781] xhci_hcd 0000:03:00.0: irq 43 for MSI/MSI-X
[    0.907790] xhci_hcd 0000:03:00.0: irq 44 for MSI/MSI-X
[    0.907799] xhci_hcd 0000:03:00.0: irq 45 for MSI/MSI-X
[    0.907808] xhci_hcd 0000:03:00.0: irq 46 for MSI/MSI-X
[    0.907817] xhci_hcd 0000:03:00.0: irq 47 for MSI/MSI-X
[    0.907937] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    0.907941] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.907944] usb usb2: Product: xHCI Host Controller
[    0.907946] usb usb2: Manufacturer: Linux 3.8.0-29-generic xhci_hcd
[    0.907949] usb usb2: SerialNumber: 0000:03:00.0
[    0.908041] xHCI xhci_add_endpoint called for root hub
[    0.908043] xHCI xhci_check_bandwidth called for root hub
[    0.908073] hub 2-0:1.0: USB hub found
[    0.908081] hub 2-0:1.0: 2 ports detected
[    0.908159] xhci_hcd 0000:03:00.0: xHCI Host Controller
[    0.908164] xhci_hcd 0000:03:00.0: new USB bus registered, assigned bus number 3
[    0.908194] usb usb3: New USB device found, idVendor=1d6b, idProduct=0003
[    0.908197] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.908200] usb usb3: Product: xHCI Host Controller
[    0.908203] usb usb3: Manufacturer: Linux 3.8.0-29-generic xhci_hcd
[    0.908206] usb usb3: SerialNumber: 0000:03:00.0
[    0.908283] xHCI xhci_add_endpoint called for root hub
[    0.908286] xHCI xhci_check_bandwidth called for root hub
[    0.908312] hub 3-0:1.0: USB hub found
[    0.908320] hub 3-0:1.0: 2 ports detected
[    1.218947] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    1.236780] isapnp: No Plug & Play device found
[    1.247077] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    1.248788] i8042: Detected active multiplexing controller, rev 1.1
[    1.249624] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.249631] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.249640] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.249642] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.249644] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.249770] mousedev: PS/2 mouse device common for all mice
[    1.249914] rtc_cmos 00:05: RTC can wake from S4
[    1.250041] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    1.250071] rtc0: alarms up to one year, y3k, 242 bytes nvram, hpet irqs
[    1.250163] device-mapper: uevent: version 1.0.3
[    1.250220] device-mapper: ioctl: 4.23.1-ioctl (2012-12-18) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    1.250235] EISA: Probing bus 0 at eisa.0
[    1.250237] EISA: Cannot allocate resource for mainboard
[    1.250238] Cannot allocate resource for EISA slot 1
[    1.250240] Cannot allocate resource for EISA slot 2
[    1.250241] Cannot allocate resource for EISA slot 3
[    1.250243] Cannot allocate resource for EISA slot 4
[    1.250244] Cannot allocate resource for EISA slot 5
[    1.250245] Cannot allocate resource for EISA slot 6
[    1.250247] Cannot allocate resource for EISA slot 7
[    1.250248] Cannot allocate resource for EISA slot 8
[    1.250250] EISA: Detected 0 cards.
[    1.250257] cpufreq-nforce2: No nForce2 chipset.
[    1.250344] cpuidle: using governor ladder
[    1.250460] cpuidle: using governor menu
[    1.250465] ledtrig-cpu: registered to indicate activity on CPUs
[    1.250467] EFI Variables Facility v0.08 2004-May-17
[    1.250640] ashmem: initialized
[    1.250772] TCP: cubic registered
[    1.250878] NET: Registered protocol family 10
[    1.251081] NET: Registered protocol family 17
[    1.251090] Key type dns_resolver registered
[    1.251279] Using IPI No-Shortcut mode
[    1.251450] Loading module verification certificates
[    1.255376] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: 760b08a5a1de9684ced1bfd52640b05fe41b6ca5'
[    1.255390] registered taskstats version 1
[    1.257712] Key type trusted registered
[    1.259638] Key type encrypted registered
[    1.261783] rtc_cmos 00:05: setting system clock to 2013-11-19 16:24:59 UTC (1384878299)
[    1.262604] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.262607] EDD information not available.
[    1.262779] Freeing unused kernel memory: 796k freed
[    1.262968] Write protecting the kernel text: 6360k
[    1.263038] Write protecting the kernel read-only data: 2496k
[    1.263040] NX-protecting the kernel data: 3880k
[    1.280503] udevd[112]: starting version 175
[    1.294974] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.308010] Disabling lock debugging due to kernel taint
[    1.311742] [drm] Initialized drm 1.1.0 20060810
[    1.313083] ahci 0000:00:1f.2: version 3.0
[    1.313168] ahci 0000:00:1f.2: irq 48 for MSI/MSI-X
[    1.313254] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x1 impl SATA mode
[    1.313261] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part ems apst 
[    1.313269] ahci 0000:00:1f.2: setting latency timer to 64
[    1.315242] scsi0 : ahci
[    1.315372] scsi1 : ahci
[    1.315504] scsi2 : ahci
[    1.315609] scsi3 : ahci
[    1.315700] scsi4 : ahci
[    1.315792] scsi5 : ahci
[    1.315913] ata1: SATA max UDMA/133 abar m2048@0xdfe06000 port 0xdfe06100 irq 48
[    1.315916] ata2: DUMMY
[    1.315918] ata3: DUMMY
[    1.315920] ata4: DUMMY
[    1.315922] ata5: DUMMY
[    1.315925] ata6: DUMMY
[    1.317438] [drm] Memory usable by graphics device = 2048M
[    1.317447] i915 0000:00:02.0: setting latency timer to 64
[    1.318013] i915 0000:00:02.0: irq 49 for MSI/MSI-X
[    1.318024] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    1.318025] [drm] Driver supports precise vblank timestamp query.
[    1.318061] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    1.321427] [drm:intel_dp_i2c_aux_ch] *ERROR* too many retries, giving up
[    1.324423] [drm:intel_dp_i2c_aux_ch] *ERROR* too many retries, giving up
[    1.329823] wmi: Mapper loaded
[    1.351238] usb 1-1: New USB device found, idVendor=8087, idProduct=0024
[    1.351245] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.352522] hub 1-1:1.0: USB hub found
[    1.352610] hub 1-1:1.0: 8 ports detected
[    1.424267] fbcon: inteldrmfb (fb0) is primary device
[    1.518849] usb 2-1: new high-speed USB device number 2 using xhci_hcd
[    1.535618] usb 2-1: New USB device found, idVendor=0781, idProduct=5575
[    1.535623] usb 2-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    1.535627] usb 2-1: Product: Cruzer Glide
[    1.535630] usb 2-1: Manufacturer: SanDisk
[    1.535633] usb 2-1: SerialNumber: 2005174023189CD28748
[    1.538340] Initializing USB Mass Storage driver...
[    1.538479] scsi6 : usb-storage 2-1:1.0
[    1.538578] usbcore: registered new interface driver usb-storage
[    1.538579] USB Mass Storage support registered.
[    1.623007] usb 1-1.2: new high-speed USB device number 3 using ehci-pci
[    1.634757] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    1.635168] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[    1.635204] ata1.00: ACPI cmd ef/10:06:00:00:00:a0 (SET FEATURES) succeeded
[    1.635263] ata1.00: ACPI cmd ef/90:03:00:00:00:a0 (SET FEATURES) succeeded
[    1.635602] ata1.00: ATA-9: SanDisk SSD U100 128GB, 10.01.02, max UDMA/133
[    1.635607] ata1.00: 250069680 sectors, multi 1: LBA48 NCQ (depth 31/32)
[    1.636033] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[    1.636095] ata1.00: ACPI cmd ef/10:06:00:00:00:a0 (SET FEATURES) succeeded
[    1.636127] ata1.00: ACPI cmd ef/90:03:00:00:00:a0 (SET FEATURES) succeeded
[    1.636236] ata1.00: configured for UDMA/133
[    1.636437] scsi 0:0:0:0: Direct-Access     ATA      SanDisk SSD U100 10.0 PQ: 0 ANSI: 5
[    1.636617] sd 0:0:0:0: [sda] 250069680 512-byte logical blocks: (128 GB/119 GiB)
[    1.636647] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.636736] sd 0:0:0:0: [sda] Write Protect is off
[    1.636739] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.636785] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.637944]  sda: sda1 sda2 < sda5 sda6 >
[    1.638403] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.716490] usb 1-1.2: config 1 has an invalid interface number: 9 but max is 6
[    1.716495] usb 1-1.2: config 1 has an invalid interface number: 7 but max is 6
[    1.716498] usb 1-1.2: config 1 has no interface number 5
[    1.716501] usb 1-1.2: config 1 has no interface number 6
[    1.718350] usb 1-1.2: New USB device found, idVendor=0f3d, idProduct=68aa
[    1.718352] usb 1-1.2: New USB device strings: Mfr=3, Product=2, SerialNumber=4
[    1.718354] usb 1-1.2: Product: AirCard 313U
[    1.718356] usb 1-1.2: Manufacturer: Sierra Wireless, Incorporated
[    1.718358] usb 1-1.2: SerialNumber: 012615001297630
[    1.722666] scsi7 : usb-storage 1-1.2:1.9
[    1.794675] usb 1-1.5: new high-speed USB device number 4 using ehci-pci
[    1.822595] tsc: Refined TSC clocksource calibration: 1596.373 MHz
[    1.822606] Switching to clocksource tsc
[    1.948901] usb 1-1.5: New USB device found, idVendor=13d3, idProduct=5719
[    1.948907] usb 1-1.5: New USB device strings: Mfr=3, Product=1, SerialNumber=2
[    1.948911] usb 1-1.5: Product: USB2.0 VGA Webcam
[    1.948914] usb 1-1.5: Manufacturer: Azurewave
[    1.948917] usb 1-1.5: SerialNumber: NULL
[    2.022523] usb 1-1.7: new high-speed USB device number 5 using ehci-pci
[    2.115466] usb 1-1.7: New USB device found, idVendor=0bda, idProduct=0139
[    2.115471] usb 1-1.7: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    2.115475] usb 1-1.7: Product: USB2.0-CRW
[    2.115478] usb 1-1.7: Manufacturer: Generic
[    2.115482] usb 1-1.7: SerialNumber: 20100201396000000
[    2.186411] usb 1-1.8: new full-speed USB device number 6 using ehci-pci
[    2.280521] usb 1-1.8: New USB device found, idVendor=13d3, idProduct=3375
[    2.280526] usb 1-1.8: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    2.280530] usb 1-1.8: Product: Bluetooth USB Host Controller
[    2.280534] usb 1-1.8: Manufacturer: Atheros Communications
[    2.280537] usb 1-1.8: SerialNumber: Alaska Day 2006
[    2.534563] scsi 6:0:0:0: Direct-Access     SanDisk  Cruzer Glide     1.26 PQ: 0 ANSI: 6
[    2.535548] sd 6:0:0:0: Attached scsi generic sg1 type 0
[    2.535695] sd 6:0:0:0: [sdb] 15633408 512-byte logical blocks: (8.00 GB/7.45 GiB)
[    2.535973] sd 6:0:0:0: [sdb] Write Protect is off
[    2.535976] sd 6:0:0:0: [sdb] Mode Sense: 43 00 00 00
[    2.536263] sd 6:0:0:0: [sdb] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[    2.538640]  sdb: sdb1
[    2.539976] sd 6:0:0:0: [sdb] Attached SCSI disk
[    2.723878] scsi 7:0:0:0: Direct-Access     SWI      SD Card          2.31 PQ: 0 ANSI: 2
[    2.724529] sd 7:0:0:0: Attached scsi generic sg2 type 0
[    2.727366] sd 7:0:0:0: [sdc] Attached SCSI removable disk
[    2.782095] [drm] Enabling RC6 states: RC6 on, RC6p off, RC6pp off
[    3.569408] Console: switching to colour frame buffer device 200x56
[    3.573965] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[    3.573966] i915 0000:00:02.0: registered panic notifier
[    3.580905] ACPI Warning: _BQC returned an invalid level (20121018/video-526)
[    3.581288] acpi device:32: registered as cooling_device4
[    3.581694] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    3.581762] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input4
[    3.581868] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    8.918593] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[    9.096028] init: ureadahead main process (371) terminated with status 5
[    9.241383] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
[    9.258988] udevd[453]: starting version 175
[    9.387931] mei 0000:00:16.0: setting latency timer to 64
[    9.388016] mei 0000:00:16.0: irq 50 for MSI/MSI-X
[    9.426152] lp: driver loaded but no devices found
[    9.435943] cfg80211: Calling CRDA to update world regulatory domain
[    9.440868] ppdev: user-space parallel port driver
[    9.454548] ACPI Warning: 0x00000428-0x0000042f SystemIO conflicts with Region \GPIS 1 (20121018/utaddress-251)
[    9.454557] ACPI Warning: 0x00000428-0x0000042f SystemIO conflicts with Region \PMIO 2 (20121018/utaddress-251)
[    9.454564] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    9.454569] ACPI Warning: 0x00000540-0x0000054f SystemIO conflicts with Region \GPIO 1 (20121018/utaddress-251)
[    9.454575] ACPI Warning: 0x00000540-0x0000054f SystemIO conflicts with Region \GP01 2 (20121018/utaddress-251)
[    9.454580] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    9.454583] ACPI Warning: 0x00000530-0x0000053f SystemIO conflicts with Region \GPIO 1 (20121018/utaddress-251)
[    9.454588] ACPI Warning: 0x00000530-0x0000053f SystemIO conflicts with Region \GP01 2 (20121018/utaddress-251)
[    9.454593] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    9.454595] ACPI Warning: 0x00000500-0x0000052f SystemIO conflicts with Region \GPIO 1 (20121018/utaddress-251)
[    9.454600] ACPI Warning: 0x00000500-0x0000052f SystemIO conflicts with Region \GP01 2 (20121018/utaddress-251)
[    9.454605] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    9.454607] lpc_ich: Resource conflict(s) found affecting gpio_ich
[    9.463219] Bluetooth: Core ver 2.16
[    9.463242] NET: Registered protocol family 31
[    9.463245] Bluetooth: HCI device and connection manager initialized
[    9.463253] Bluetooth: HCI socket layer initialized
[    9.463257] Bluetooth: L2CAP socket layer initialized
[    9.463265] Bluetooth: SCO socket layer initialized
[    9.475613] Bluetooth: RFCOMM TTY layer initialized
[    9.475626] Bluetooth: RFCOMM socket layer initialized
[    9.475629] Bluetooth: RFCOMM ver 1.11
[    9.476605] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    9.476609] Bluetooth: BNEP filters: protocol multicast
[    9.476616] Bluetooth: BNEP socket layer initialized
[    9.503256] usbcore: registered new interface driver btusb
[    9.505578] Linux video capture interface: v2.00
[    9.510624] uvcvideo: Found UVC 1.00 device USB2.0 VGA Webcam (13d3:5719)
[    9.517132] input: USB2.0 VGA Webcam as /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1.5/1-1.5:1.0/input/input5
[    9.517355] usbcore: registered new interface driver uvcvideo
[    9.517358] USB Video Class driver (1.1.1)
[    9.528436] ath: EEPROM regdomain: 0x60
[    9.528440] ath: EEPROM indicates we should expect a direct regpair map
[    9.528445] ath: Country alpha2 being used: 00
[    9.528447] ath: Regpair used: 0x60
[    9.530888] type=1400 audit(1384896307.770:2): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=699 comm="apparmor_parser"
[    9.531623] type=1400 audit(1384896307.770:3): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=699 comm="apparmor_parser"
[    9.538219] sierra_net 1-1.2:1.7 wwan0: register 'sierra_net' at usb-0000:00:1d.0-1.2, Sierra Wireless USB-to-WWAN Modem, 32:09:ce:b5:01:07
[    9.538384] usbcore: registered new interface driver sierra_net
[    9.549091] usbcore: registered new interface driver usbserial
[    9.549113] usbcore: registered new interface driver usbserial_generic
[    9.549130] usbserial: USB Serial support registered for generic
[    9.550811] usbcore: registered new interface driver sierra
[    9.550830] usbserial: USB Serial support registered for Sierra USB modem
[    9.550853] sierra 1-1.2:1.0: Sierra USB modem converter detected
[    9.551633] usb 1-1.2: Sierra USB modem converter now attached to ttyUSB0
[    9.551656] sierra 1-1.2:1.1: Sierra USB modem converter detected
[    9.552224] usb 1-1.2: Sierra USB modem converter now attached to ttyUSB1
[    9.552246] sierra 1-1.2:1.2: Sierra USB modem converter detected
[    9.552760] usb 1-1.2: Sierra USB modem converter now attached to ttyUSB2
[    9.552789] sierra 1-1.2:1.3: Sierra USB modem converter detected
[    9.553698] usb 1-1.2: Sierra USB modem converter now attached to ttyUSB3
[    9.553727] sierra 1-1.2:1.4: Sierra USB modem converter detected
[    9.554673] usb 1-1.2: Sierra USB modem converter now attached to ttyUSB4
[    9.559725] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[    9.560428] ieee80211 phy0: Atheros AR9485 Rev:1 mem=0xf9380000, irq=17
[    9.572547] rts5139: module is from the staging directory, the quality is unknown, you have been warned.
[    9.573187] usbcore: registered new interface driver ath3k
[    9.582471] microcode: CPU0 sig=0x206a7, pf=0x10, revision=0x1a
[    9.583447] scsi8 : SCSI emulation for RTS5139 USB card reader
[    9.583658] scsi 8:0:0:0: Direct-Access     Generic- xD/SD/M.S.       1.00 PQ: 0 ANSI: 0 CCS
[    9.584466] usbcore: registered new interface driver rts5139
[    9.584895] sd 8:0:0:0: Attached scsi generic sg3 type 0
[    9.587989] sd 8:0:0:0: [sdd] Attached SCSI removable disk
[    9.594966] usb 1-1.8: USB disconnect, device number 6
[    9.607216] snd_hda_intel 0000:00:1b.0: irq 51 for MSI/MSI-X
[    9.635657] type=1400 audit(1384896307.874:4): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=802 comm="apparmor_parser"
[    9.636255] type=1400 audit(1384896307.874:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=802 comm="apparmor_parser"
[    9.636617] type=1400 audit(1384896307.874:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=802 comm="apparmor_parser"
[    9.647903] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
[    9.656758] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[    9.657821] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[    9.696745] asus_wmi: ASUS WMI generic driver loaded
[    9.697536] asus_wmi: Initialization: 0x1asus_wmi: BIOS WMI version: 7.6
[    9.697656] asus_wmi: SFUN value: 0xa0877<6>[    9.699069] input: Asus WMI hotkeys as /devices/platform/asus-nb-wmi/input/input9
[    9.724965] init: failsafe main process (820) killed by TERM signal
[    9.769851] asus_wmi: Backlight controlled by ACPI video driver
[    9.785751] microcode: CPU1 sig=0x206a7, pf=0x10, revision=0x1a
[    9.793886] type=1400 audit(1384896308.034:7): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=963 comm="apparmor_parser"
[    9.794492] usb 1-1.8: new full-speed USB device number 7 using ehci-pci
[    9.799583] type=1400 audit(1384896308.038:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=962 comm="apparmor_parser"
[    9.799756] type=1400 audit(1384896308.038:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=963 comm="apparmor_parser"
[    9.800063] type=1400 audit(1384896308.038:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper//chromium_browser" pid=962 comm="apparmor_parser"
[    9.800090] type=1400 audit(1384896308.038:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=963 comm="apparmor_parser"
[    9.834924] microcode: CPU2 sig=0x206a7, pf=0x10, revision=0x1a
[    9.858645] microcode: CPU3 sig=0x206a7, pf=0x10, revision=0x1a
[    9.873787] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    9.927853] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    9.930982] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   10.382697] psmouse serio4: elantech: assuming hardware version 4 (with firmware version 0x361f00)
[   10.395088] psmouse serio4: elantech: Synaptics capabilities query result 0x20, 0x15, 0x0e.
[   10.457850] input: ETPS/2 Elantech Touchpad as /devices/platform/i8042/serio4/input/input10
[   14.884141] usb 1-1.8: New USB device found, idVendor=13d3, idProduct=3375
[   14.884152] usb 1-1.8: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[   14.884159] usb 1-1.8: Product: Bluetooth USB Host Controller
[   14.884165] usb 1-1.8: Manufacturer: Atheros Communications
[   14.884170] usb 1-1.8: SerialNumber: Alaska Day 2006
[   21.310858] CPU0: Package power limit notification (total events = 1)
[   21.310860] CPU2: Package power limit notification (total events = 1)
[   21.310863] CPU1: Package power limit notification (total events = 1)
[   21.310865] CPU3: Package power limit notification (total events = 1)
[   21.313581] CPU0: Package power limit normal
[   21.313583] CPU3: Package power limit normal
[   21.313585] CPU1: Package power limit normal
[   21.313587] CPU2: Package power limit normal
[   28.984173] IPv6: ADDRCONF(NETDEV_UP): wwan0: link is not ready
[   28.984366] IPv6: ADDRCONF(NETDEV_UP): wwan0: link is not ready
[   34.262565] audit_printk_skb: 39 callbacks suppressed
[   34.262569] type=1400 audit(1384896332.518:25): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/telepathy/mission-control-5" name="/usr/share/gvfs/remote-volume-monitors/" pid=2033 comm="mission-control" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0

        6 ) $ sudo lshw -C network

PCI (sysfs)  
  *-network               
       description: Wireless interface
       product: AR9485 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 00:08:ca:e7:58:ec
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.8.0-29-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:dea00000-dea7ffff memory:dea80000-dea8ffff
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: wwan0
       serial: 32:09:ce:b5:01:07
       capabilities: ethernet physical
       configuration: broadcast=yes driver=sierra_net driverversion=v.2.0 firmware=Sierra Wireless USB-to-WWAN Mod link=no multicast=yes


        7 )  $ iwlist scan

wlan0     No scan results

wwan0     Interface doesn't support scanning.

lo        Interface doesn't support scanning.

        8 ) Ubuntu Version:
 $ lsb_release -d
12.04.3 LTS

        9 ) Kernel/architecture (including 32 vs. 64 bit):
        $ uname -mr

3.8.0-29-generic i686
        10 ) Restarting the network:
        $ sudo service networking restart

stop: Unknown instance: 
networking stop/waiting

---

### Post by ken-zwn on 2014-01-07
I have been having trouble with my 313u (Sierra wireless momentum 4g, at&t) for a while now.

NetworkManager recognizes it and usb_modeswitch sets it to the right mode.... but if you watch syslog, DHCPDISCOVER keeps asking for an IP address and eventually gives up. The modem itself gets an IP... which you can find using minicom. There is some kind of a handoff issue with dhclient. This is a direct IP modem.

---

### Post by ken-zwn on 2014-01-07
FYI... I am on 13.10 with a 3.12 kernel.

---

