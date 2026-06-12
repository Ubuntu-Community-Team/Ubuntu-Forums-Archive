---
title: "Wireless Networking Issue"
date: 2009-12-05
forum: New to Ubuntu
---

### Post by mydisguise09 on 2009-12-05
[COLOR=black]Every time I can connect to this wireless network with no problems, it's just 90% of the time I have to click the Network thing up top in the right hand corner and click the wireless network before I click a link or else the page doesn't even load.

I thought I should have done a re-install so that it would "restore" everything back to it's original setting but I made a thread a couple weeks ago and someone said:
[/COLOR]if wireless was working sounds like it would be easier just to make the wireless work
can you find and run a terminal ? if so, try these commands to see whats up :

ifconfig
iwconfig
dmesg

you may need to do a man on these to see how/why they work.

so I did and this is what I got:
[COLOR=black]
mydisguise09@Nano:~$ su
Password: 
root@Nano:/home/mydisguise09# ifconfig
eth1      Link encap:Ethernet  HWaddr 00:14:0b:45:ad:b7  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Base address:0x5000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:107 errors:0 dropped:0 overruns:0 frame:0
          TX packets:107 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7016 (7.0 KB)  TX bytes:7016 (7.0 KB)

wlan0     Link encap:Ethernet  HWaddr 00:15:af:4d:ea:ae  
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::215:afff:fe4d:eaae/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4529 errors:0 dropped:0 overruns:0 frame:0

root@Nano:/home/mydisguise09# iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"dlink"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1E:58:3D:DA:A1   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Encryption key:off
          Link Quality=56/64  Signal level=20/65  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

```
[   45.928194] ACPI: Thermal Zone [THRM] (50 C)
[   48.534089] SCSI subsystem initialized
[   48.658172] usbcore: registered new interface driver usbfs
[   48.658251] usbcore: registered new interface driver hub
[   48.702073] usbcore: registered new device driver usb
[   49.141875] USB Universal Host Controller Interface driver v3.0
[   49.142091] ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 20 (level, low) -> IRQ 16
[   49.142126] PCI: Setting latency timer of device 0000:00:10.0 to 64
[   49.142141] uhci_hcd 0000:00:10.0: UHCI Host Controller
[   49.143010] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[   49.143071] uhci_hcd 0000:00:10.0: irq 16, io base 0x00004400
[   49.143583] usb usb1: configuration #1 chosen from 1 choice
[   49.143677] hub 1-0:1.0: USB hub found
[   49.143698] hub 1-0:1.0: 2 ports detected
[   49.246054] ACPI: PCI Interrupt 0000:00:10.1[B] -> GSI 22 (level, low) -> IRQ 17
[   49.246089] PCI: Setting latency timer of device 0000:00:10.1 to 64
[   49.246105] uhci_hcd 0000:00:10.1: UHCI Host Controller
[   49.246196] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[   49.246251] uhci_hcd 0000:00:10.1: irq 17, io base 0x00004420
[   49.246680] usb usb2: configuration #1 chosen from 1 choice
[   49.246771] hub 2-0:1.0: USB hub found
[   49.246792] hub 2-0:1.0: 2 ports detected
[   49.324314] libata version 3.00 loaded.
[   49.350007] ACPI: PCI Interrupt 0000:00:10.2[C] -> GSI 21 (level, low) -> IRQ 18
[   49.350042] PCI: Setting latency timer of device 0000:00:10.2 to 64
[   49.350058] uhci_hcd 0000:00:10.2: UHCI Host Controller
[   49.350143] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[   49.350196] uhci_hcd 0000:00:10.2: irq 18, io base 0x00004440
[   49.350631] usb usb3: configuration #1 chosen from 1 choice
[   49.350739] hub 3-0:1.0: USB hub found
[   49.350760] hub 3-0:1.0: 2 ports detected
[   49.454426] ACPI: PCI Interrupt 0000:00:10.4[D] -> GSI 23 (level, low) -> IRQ 19
[   49.454469] PCI: Setting latency timer of device 0000:00:10.4 to 64
[   49.454485] ehci_hcd 0000:00:10.4: EHCI Host Controller
[   49.454581] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 4
[   49.454672] ehci_hcd 0000:00:10.4: debug port 1
[   49.454706] ehci_hcd 0000:00:10.4: irq 19, io mem 0xd1400000
[   49.465656] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   49.466092] usb usb4: configuration #1 chosen from 1 choice
[   49.466187] hub 4-0:1.0: USB hub found
[   49.466210] hub 4-0:1.0: 6 ports detected
[   49.571031] PCI: Setting latency timer of device 0000:00:0f.0 to 64
[   49.769682] pata_via 0000:00:0f.0: version 0.3.3
[   49.805590] scsi0 : pata_via
[   49.857732] scsi1 : pata_via
[   49.860465] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x4460 irq 14
[   49.860483] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x4468 irq 15
[   49.860561] ata1: port disabled. ignoring.
[   50.021986] ata2.00: ATA-7: ST730212DE, 3.01, max UDMA/66
[   50.022005] ata2.00: 58605120 sectors, multi 16: LBA48 
[   50.022053] ata2.00: limited to UDMA/33 due to 40-wire cable
[   50.039590] ata2.00: configured for UDMA/33
[   50.039941] scsi 1:0:0:0: Direct-Access     ATA      ST730212DE       3.01 PQ: 0 ANSI: 5
[   50.533220] usb 4-4: new high speed USB device using ehci_hcd and address 3
[   50.673000] usb 4-4: configuration #1 chosen from 1 choice
[   50.913072] usb 4-5: new high speed USB device using ehci_hcd and address 4
[   51.289689] usb 4-5: configuration #1 chosen from 1 choice
[   51.502351] 8139too Fast Ethernet driver 0.9.28
[   51.502519] ACPI: PCI Interrupt 0000:03:09.0[A] -> GSI 16 (level, low) -> IRQ 20
[   51.502556] PCI: Setting latency timer of device 0000:03:09.0 to 64
[   51.503780] eth0: RealTek RTL8139 at 0x5000, 00:14:0b:45:ad:b7, IRQ 20
[   51.503794] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[   51.536795] usb 4-6: new high speed USB device using ehci_hcd and address 5
[   51.668840] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   51.685978] usb 4-6: configuration #1 chosen from 1 choice
[   51.924621] usb 1-2: new low speed USB device using uhci_hcd and address 2
[   52.100942] usb 1-2: configuration #1 chosen from 1 choice
[   54.093150] Driver 'sd' needs updating - please use bus_type methods
[   54.099749] sd 1:0:0:0: [sda] 58605120 512-byte hardware sectors (30006 MB)
[   54.099797] sd 1:0:0:0: [sda] Write Protect is off
[   54.099811] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   54.099875] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   54.100043] sd 1:0:0:0: [sda] 58605120 512-byte hardware sectors (30006 MB)
[   54.100082] sd 1:0:0:0: [sda] Write Protect is off
[   54.100095] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   54.100155] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   54.100175]  sda: sda1 sda2 sda3 sda4
[   54.152833] sd 1:0:0:0: [sda] Attached SCSI disk
[   54.183316] sd 1:0:0:0: Attached scsi generic sg0 type 0
[   54.633536] usbcore: registered new interface driver libusual
[   54.687819] Initializing USB Mass Storage driver...
[   54.700015] scsi2 : SCSI emulation for USB Mass Storage devices
[   54.711673] usbcore: registered new interface driver usb-storage
[   54.711695] USB Mass Storage support registered.
[   54.711712] usb-storage: device found at 5
[   54.711722] usb-storage: waiting for device to settle before scanning
[   54.738202] usbcore: registered new interface driver hiddev
[   54.753075] input:  USB OPTICAL MOUSE as /devices/pci0000:00/0000:00:10.0/usb1/1-2/1-2:1.0/input/input2
[   54.767656] input,hidraw0: USB HID v1.11 Mouse [ USB OPTICAL MOUSE] on usb-0000:00:10.0-2
[   54.767720] usbcore: registered new interface driver usbhid
[   54.767738] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   55.139242] Clocksource tsc unstable (delta = -1655946959 ns)
[   55.143235] Time: acpi_pm clocksource has been installed.
[   55.212129] Attempting manual resume
[   55.212144] swsusp: Resume From Partition 8:2
[   55.212154] PM: Checking swsusp image.
[   55.212707] PM: Resume from disk failed.
[   55.311632] kjournald starting.  Commit interval 5 seconds
[   55.311671] EXT3-fs: mounted filesystem with ordered data mode.
[   57.449223] usb-storage: device scan complete
[   57.455964] scsi 2:0:0:0: Direct-Access     Generic- Multi-Card       1.00 PQ: 0 ANSI: 0 CCS
[   57.458541] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[   57.458682] sd 2:0:0:0: Attached scsi generic sg1 type 0
[   67.056127] udev: starting version 141
[   68.263462] input: Power Button (FF) as /devices/virtual/input/input3
[   68.274847] ACPI: Power Button (FF) [PWRF]
[   68.275129] input: Power Button (CM) as /devices/virtual/input/input4
[   68.290837] ACPI: Power Button (CM) [PWRB]
[   68.291168] input: Lid Switch as /devices/virtual/input/input5
[   68.291336] ACPI: Lid Switch [LID]
[   68.312150] ACPI: AC Adapter [ACAD] (on-line)
[   68.743503] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:14/LNXVIDEO:00/input/input6
[   68.754651] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   69.053543] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   69.324123] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   69.361189] udev: renamed network interface eth0 to eth1
[   69.718631] ACPI: Battery Slot [BAT0] (battery present)
[   69.726802] input: PC Speaker as /devices/platform/pcspkr/input/input7
[   69.858496] Linux video capture interface: v2.00
[   69.944333] Linux agpgart interface v0.102
[   69.953796] agpgart: Detected VIA CX700 chipset
[   69.975808] agpgart: AGP aperture is 256M @ 0xc0000000
[   70.169097] uvcvideo: Found UVC 1.00 device USB2.0 Camera (5986:0101)
[   70.172701] input: USB2.0 Camera as /devices/pci0000:00/0000:00:10.4/usb4/4-5/4-5:1.0/input/input8
[   70.182241] usbcore: registered new interface driver uvcvideo
[   70.182262] USB Video Class driver (v0.1.0)
[   70.443296] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1c0b1, caps: 0xa04750/0x200000
[   70.495079] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input9
[   71.147542] phy0: Selected rate control algorithm 'simple'
[   71.347918] ACPI: PCI Interrupt 0000:02:01.0[A] -> GSI 17 (level, low) -> IRQ 21
[   71.347980] PCI: Setting latency timer of device 0000:02:01.0 to 64
[   71.437628] phy0: hwaddr 00:15:af:4d:ea:ae, rtl8187 V1 + rtl8225z2
[   71.437694] usbcore: registered new interface driver rtl8187
[   72.920130] lp: driver loaded but no devices found
[   73.248132] Adding 996020k swap on /dev/sda2.  Priority:-1 extents:1 across:996020k
[   73.632717] EXT3 FS on sda1, internal journal
[   74.790566] kjournald starting.  Commit interval 5 seconds
[   74.791043] EXT3 FS on sda4, internal journal
[   74.791060] EXT3-fs: mounted filesystem with ordered data mode.
[   75.608562] audit(1260046037.120:2): type=1505 operation="profile_load" info="unsupported interface version" pid=4277
[   75.946996] audit(1260046037.460:3): type=1505 operation="profile_load" info="unsupported interface version" pid=4283
[   76.930053] audit(1260046038.440:4): type=1505 operation="profile_load" info="unsupported interface version" pid=4290
[   77.110875] audit(1260046038.624:5): type=1505 operation="profile_load" info="unsupported interface version" pid=4296
[   78.609213] No dock devices found.
[   84.421012] Bluetooth: Core ver 2.11
[   84.423931] NET: Registered protocol family 31
[   84.423950] Bluetooth: HCI device and connection manager initialized
[   84.423966] Bluetooth: HCI socket layer initialized
[   84.490016] Bluetooth: L2CAP ver 2.9
[   84.490035] Bluetooth: L2CAP socket layer initialized
[   84.521978] Bluetooth: RFCOMM socket layer initialized
[   84.523638] Bluetooth: RFCOMM TTY layer initialized
[   84.523656] Bluetooth: RFCOMM ver 1.8
[   84.546768] Bluetooth: SCO (Voice Link) ver 0.6
[   84.546785] Bluetooth: SCO socket layer initialized
[   84.581263] Bluetooth: BNEP (Ethernet Emulation) ver 1.2
[   84.581282] Bluetooth: BNEP filters: protocol multicast
[   84.647701] Bridge firewalling registered
[   84.648155] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
[   87.168816] ppdev: user-space parallel port driver
[   87.997024] NET: Registered protocol family 10
[   87.999541] lo: Disabled Privacy Extensions
[   89.951039] eth1: link down
[   89.951833] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   96.717555] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   98.225140] NET: Registered protocol family 17
[   99.085425] wlan0: Initial auth_alg=0
[   99.085450] wlan0: authenticate with AP 00:1e:58:3d:da:a1
[   99.089354] wlan0: RX authentication from 00:1e:58:3d:da:a1 (alg=0 transaction=2 status=0)
[   99.089373] wlan0: authenticated
[   99.089387] wlan0: associate with AP 00:1e:58:3d:da:a1
[   99.091586] wlan0: RX AssocResp from 00:1e:58:3d:da:a1 (capab=0x421 status=0 aid=3)
[   99.091602] wlan0: associated
[   99.091620] wlan0: switched to short barker preamble (BSSID=00:1e:58:3d:da:a1)
[   99.092574] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   99.095150] wlan0: disassociate(reason=3)
[   99.099869] wlan0: RX deauthentication from 00:1e:58:3d:da:a1 (reason=7)
[   99.099885] wlan0: deauthenticated
[   99.683191] wlan0: RX deauthentication from 00:1e:58:3d:da:a1 (reason=7)
[  100.112296] wlan0: authenticate with AP 00:1e:58:3d:da:a1
[  100.114407] wlan0: RX authentication from 00:1e:58:3d:da:a1 (alg=0 transaction=2 status=0)
[  100.114425] wlan0: authenticated
[  100.114439] wlan0: associate with AP 00:1e:58:3d:da:a1
[  100.120901] wlan0: RX ReassocResp from 00:1e:58:3d:da:a1 (capab=0x421 status=0 aid=3)
[  100.120922] wlan0: associated
[  100.120947] wlan0: switched to short barker preamble (BSSID=00:1e:58:3d:da:a1)
[  100.123740] wlan0: disassociate(reason=3)
[  106.000556] wlan0: no IPv6 routers present
[  223.002489] hda-intel: Invalid position buffer, using LPIB read method instead.
[  280.624127] wlan0: Initial auth_alg=0
[  280.624154] wlan0: authenticate with AP 00:1e:58:3d:da:a1
[  280.627070] wlan0: RX authentication from 00:1e:58:3d:da:a1 (alg=0 transaction=2 status=0)
[  280.627092] wlan0: authenticated
[  280.627111] wlan0: associate with AP 00:1e:58:3d:da:a1
[  280.629815] wlan0: RX AssocResp from 00:1e:58:3d:da:a1 (capab=0x421 status=0 aid=5)
[  280.629836] wlan0: associated
[  280.629862] wlan0: switched to short barker preamble (BSSID=00:1e:58:3d:da:a1)
[  280.631365] wlan0: disassociate(reason=3)
[  287.201039] wlan0: Initial auth_alg=0
[  287.201066] wlan0: authenticate with AP 00:1e:58:3d:da:a1
[  287.203192] wlan0: Initial auth_alg=0
[  287.203218] wlan0: authenticate with AP 00:1e:58:3d:da:a1
[  287.204686] wlan0: RX authentication from 00:1e:58:3d:da:a1 (alg=0 transaction=2 status=0)
[  287.204707] wlan0: authenticated
[  287.204721] wlan0: associate with AP 00:1e:58:3d:da:a1
[  287.206564] wlan0: authentication frame received from 00:1e:58:3d:da:a1, but not in authenticate state - ignored
[  287.209081] wlan0: RX ReassocResp from 00:1e:58:3d:da:a1 (capab=0x421 status=0 aid=5)
[  287.209102] wlan0: associated
[  287.209123] wlan0: switched to short barker preamble (BSSID=00:1e:58:3d:da:a1)
[  836.550769] wlan0: disassociate(reason=3)
[  836.765238] wlan0: Initial auth_alg=0
[  836.765266] wlan0: authenticate with AP 00:1e:58:3d:da:a1
[  836.767185] wlan0: RX authentication from 00:1e:58:3d:da:a1 (alg=0 transaction=2 status=0)
[  836.767212] wlan0: authenticated
[  836.767226] wlan0: associate with AP 00:1e:58:3d:da:a1
[  836.769816] wlan0: RX AssocResp from 00:1e:58:3d:da:a1 (capab=0x421 status=0 aid=5)
[  836.769842] wlan0: associated
[  836.769863] wlan0: switched to short barker preamble (BSSID=00:1e:58:3d:da:a1)
[  839.318233] wlan0: Initial auth_alg=0
[  839.318268] wlan0: authenticate with AP 00:1e:58:3d:da:a1
[  839.320821] wlan0: Initial auth_alg=0
[  839.320847] wlan0: authenticate with AP 00:1e:58:3d:da:a1
[  839.322557] wlan0: RX authentication from 00:1e:58:3d:da:a1 (alg=0 transaction=2 status=0)
[  839.322584] wlan0: authenticated
[  839.322598] wlan0: associate with AP 00:1e:58:3d:da:a1
[  839.324538] wlan0: authentication frame received from 00:1e:58:3d:da:a1, but not in authenticate state - ignored
[  839.326923] wlan0: RX ReassocResp from 00:1e:58:3d:da:a1 (capab=0x421 status=0 aid=5)
[  839.326945] wlan0: associated
[  913.582852] wlan0: disassociate(reason=3)
[  913.882485] wlan0: Initial auth_alg=0
[  913.882512] wlan0: authenticate with AP 00:1e:58:3d:da:a1
[  913.884536] wlan0: RX authentication from 00:1e:58:3d:da:a1 (alg=0 transaction=2 status=0)
[  913.884554] wlan0: authenticated
[  913.884568] wlan0: associate with AP 00:1e:58:3d:da:a1
[  913.888144] wlan0: RX AssocResp from 00:1e:58:3d:da:a1 (capab=0x421 status=0 aid=5)
[  913.888160] wlan0: associated
[  913.888180] wlan0: switched to short barker preamble (BSSID=00:1e:58:3d:da:a1)
[  923.079853] wlan0: Initial auth_alg=0
[  923.079890] wlan0: authenticate with AP 00:1e:58:3d:da:a1
[  923.082157] wlan0: RX authentication from 00:1e:58:3d:da:a1 (alg=0 transaction=2 status=0)
[  923.082179] wlan0: authenticated
[  923.082193] wlan0: associate with AP 00:1e:58:3d:da:a1
[  923.087104] wlan0: Initial auth_alg=0
[  923.087130] wlan0: authenticate with AP 00:1e:58:3d:da:a1
[  923.090122] wlan0: RX deauthentication from 00:1e:58:3d:da:a1 (reason=6)
[  923.090141] wlan0: deauthenticated
[  923.092045] wlan0: RX authentication from 00:1e:58:3d:da:a1 (alg=0 transaction=2 status=0)
[  923.092066] wlan0: authenticated
[  923.092080] wlan0: associate with AP 00:1e:58:3d:da:a1
[  923.095422] wlan0: RX ReassocResp from 00:1e:58:3d:da:a1 (capab=0x421 status=0 aid=5)
[  923.095464] wlan0: associated
[ 1002.342121] wlan0: disassociate(reason=3)
[ 1002.588374] wlan0: Initial auth_alg=0
[ 1002.588401] wlan0: authenticate with AP 00:1e:58:3d:da:a1
[ 1002.613153] wlan0: RX authentication from 00:1e:58:3d:da:a1 (alg=0 transaction=2 status=0)
[ 1002.613176] wlan0: authenticated
[ 1002.613191] wlan0: associate with AP 00:1e:58:3d:da:a1
[ 1002.641595] wlan0: RX AssocResp from 00:1e:58:3d:da:a1 (capab=0x421 status=0 aid=5)
[ 1002.641617] wlan0: associated
[ 1002.641638] wlan0: switched to short barker preamble (BSSID=00:1e:58:3d:da:a1)
[ 1011.512002] wlan0: Initial auth_alg=0
[ 1011.512044] wlan0: authenticate with AP 00:1e:58:3d:da:a1
[ 1011.515107] wlan0: Initial auth_alg=0
[ 1011.515133] wlan0: authenticate with AP 00:1e:58:3d:da:a1
[ 1011.554562] wlan0: RX authentication from 00:1e:58:3d:da:a1 (alg=0 transaction=2 status=0)
[ 1011.554584] wlan0: authenticated
[ 1011.554599] wlan0: associate with AP 00:1e:58:3d:da:a1
[ 1011.556735] wlan0: authentication frame received from 00:1e:58:3d:da:a1, but not in authenticate state - ignored
[ 1011.558385] wlan0: RX ReassocResp from 00:1e:58:3d:da:a1 (capab=0x421 status=0 aid=5)
[ 1011.558407] wlan0: associated
[ 1143.529369] wlan0: disassociate(reason=3)
[ 1143.801615] wlan0: Initial auth_alg=0
[ 1143.801641] wlan0: authenticate with AP 00:1e:58:3d:da:a1
[ 1143.803680] wlan0: RX authentication from 00:1e:58:3d:da:a1 (alg=0 transaction=2 status=0)
[ 1143.803706] wlan0: authenticated
[ 1143.803721] wlan0: associate with AP 00:1e:58:3d:da:a1
[ 1143.809918] wlan0: RX AssocResp from 00:1e:58:3d:da:a1 (capab=0x421 status=0 aid=5)
[ 1143.809940] wlan0: associated
[ 1143.809964] wlan0: switched to short barker preamble (BSSID=00:1e:58:3d:da:a1)
[ 1146.110687] wlan0: Initial auth_alg=0
[ 1146.110722] wlan0: authenticate with AP 00:1e:58:3d:da:a1
[ 1146.113473] wlan0: Initial auth_alg=0
[ 1146.113499] wlan0: authenticate with AP 00:1e:58:3d:da:a1
[ 1146.117596] wlan0: RX authentication from 00:1e:58:3d:da:a1 (alg=0 transaction=2 status=0)
[ 1146.117616] wlan0: authenticated
[ 1146.117631] wlan0: associate with AP 00:1e:58:3d:da:a1
[ 1146.119104] wlan0: authentication frame received from 00:1e:58:3d:da:a1, but not in authenticate state - ignored
[ 1146.125232] wlan0: RX deauthentication from 00:1e:58:3d:da:a1 (reason=6)
[ 1146.125251] wlan0: deauthenticated
[ 1146.759331] wlan0: authenticate with AP 00:1e:58:3d:da:a1
[ 1146.760537] wlan0: RX authentication from 00:1e:58:3d:da:a1 (alg=0 transaction=2 status=0)
[ 1146.760557] wlan0: authenticated
[ 1146.760572] wlan0: associate with AP 00:1e:58:3d:da:a1
[ 1146.763451] wlan0: RX ReassocResp from 00:1e:58:3d:da:a1 (capab=0x421 status=0 aid=5)
[ 1146.763470] wlan0: associated
[ 1166.903485] wlan0: disassociate(reason=3)
[ 1167.170646] wlan0: Initial auth_alg=0
[ 1167.170674] wlan0: authenticate with AP 00:1e:58:3d:da:a1
[ 1167.178436] wlan0: RX authentication from 00:1e:58:3d:da:a1 (alg=0 transaction=2 status=0)
[ 1167.178459] wlan0: authenticated
[ 1167.178474] wlan0: associate with AP 00:1e:58:3d:da:a1
[ 1167.180937] wlan0: RX AssocResp from 00:1e:58:3d:da:a1 (capab=0x421 status=0 aid=3)
[ 1167.180953] wlan0: associated
[ 1167.180973] wlan0: switched to short barker preamble (BSSID=00:1e:58:3d:da:a1)
[ 1169.117129] wlan0: Initial auth_alg=0
[ 1169.117171] wlan0: authenticate with AP 00:1e:58:3d:da:a1
[ 1169.120005] wlan0: RX authentication from 00:1e:58:3d:da:a1 (alg=0 transaction=2 status=0)
[ 1169.120028] wlan0: authenticated
[ 1169.120042] wlan0: associate with AP 00:1e:58:3d:da:a1
[ 1169.120107] wlan0: Initial auth_alg=0
[ 1169.120122] wlan0: authenticate with AP 00:1e:58:3d:da:a1
[ 1169.123796] wlan0: association frame received from 00:1e:58:3d:da:a1, but not in associate state - ignored
[ 1169.124630] wlan0: RX authentication from 00:1e:58:3d:da:a1 (alg=0 transaction=2 status=0)
[ 1169.124649] wlan0: authenticated
[ 1169.124663] wlan0: associate with AP 00:1e:58:3d:da:a1
[ 1169.126550] wlan0: RX deauthentication from 00:1e:58:3d:da:a1 (reason=6)
[ 1169.126569] wlan0: deauthenticated
[ 1169.527750] wlan0: authenticate with AP 00:1e:58:3d:da:a1
[ 1169.529570] wlan0: RX authentication from 00:1e:58:3d:da:a1 (alg=0 transaction=2 status=0)
[ 1169.529591] wlan0: authenticated
[ 1169.529606] wlan0: associate with AP 00:1e:58:3d:da:a1
[ 1169.532198] wlan0: RX ReassocResp from 00:1e:58:3d:da:a1 (capab=0x421 status=0 aid=3)
[ 1169.532219] wlan0: associated
[ 1193.993378] wlan0: disassociate(reason=3)
[ 1194.234914] wlan0: Initial auth_alg=0
[ 1194.234941] wlan0: authenticate with AP 00:1e:58:3d:da:a1
[ 1194.237677] wlan0: RX authentication from 00:1e:58:3d:da:a1 (alg=0 transaction=2 status=0)
[ 1194.237697] wlan0: authenticated
[ 1194.237711] wlan0: associate with AP 00:1e:58:3d:da:a1
[ 1194.240048] wlan0: RX AssocResp from 00:1e:58:3d:da:a1 (capab=0x421 status=0 aid=3)
[ 1194.240063] wlan0: associated
[ 1194.240083] wlan0: switched to short barker preamble (BSSID=00:1e:58:3d:da:a1)
[ 1195.993952] wlan0: Initial auth_alg=0
[ 1195.993987] wlan0: authenticate with AP 00:1e:58:3d:da:a1
[ 1195.997161] wlan0: Initial auth_alg=0
[ 1195.997187] wlan0: authenticate with AP 00:1e:58:3d:da:a1
[ 1196.007813] wlan0: RX authentication from 00:1e:58:3d:da:a1 (alg=0 transaction=2 status=0)
[ 1196.007835] wlan0: authenticated
[ 1196.007849] wlan0: associate with AP 00:1e:58:3d:da:a1
[ 1196.009536] wlan0: authentication frame received from 00:1e:58:3d:da:a1, but not in authenticate state - ignored
[ 1196.010731] wlan0: RX deauthentication from 00:1e:58:3d:da:a1 (reason=6)
[ 1196.010748] wlan0: deauthenticated
[ 1196.373648] wlan0: authenticate with AP 00:1e:58:3d:da:a1
[ 1196.374760] wlan0: RX authentication from 00:1e:58:3d:da:a1 (alg=0 transaction=2 status=0)
[ 1196.374782] wlan0: authenticated
[ 1196.374796] wlan0: associate with AP 00:1e:58:3d:da:a1
[ 1196.379444] wlan0: RX ReassocResp from 00:1e:58:3d:da:a1 (capab=0x421 status=0 aid=3)
[ 1196.379463] wlan0: associated
[ 1225.447092] wlan0: disassociate(reason=3)
[ 1225.730059] wlan0: Initial auth_alg=0
[ 1225.730087] wlan0: authenticate with AP 00:1e:58:3d:da:a1
[ 1225.731880] wlan0: RX authentication from 00:1e:58:3d:da:a1 (alg=0 transaction=2 status=0)
[ 1225.731897] wlan0: authenticated
[ 1225.731911] wlan0: associate with AP 00:1e:58:3d:da:a1
[ 1225.738070] wlan0: RX AssocResp from 00:1e:58:3d:da:a1 (capab=0x421 status=0 aid=3)
[ 1225.738093] wlan0: associated
[ 1225.738115] wlan0: switched to short barker preamble (BSSID=00:1e:58:3d:da:a1)
[ 1227.536828] wlan0: Initial auth_alg=0
[ 1227.536862] wlan0: authenticate with AP 00:1e:58:3d:da:a1
[ 1227.542183] wlan0: Initial auth_alg=0
[ 1227.542209] wlan0: authenticate with AP 00:1e:58:3d:da:a1
[ 1227.551701] wlan0: RX authentication from 00:1e:58:3d:da:a1 (alg=0 transaction=2 status=0)
[ 1227.551722] wlan0: authenticated
[ 1227.551737] wlan0: associate with AP 00:1e:58:3d:da:a1
[ 1227.553283] wlan0: authentication frame received from 00:1e:58:3d:da:a1, but not in authenticate state - ignored
[ 1227.555506] wlan0: RX deauthentication from 00:1e:58:3d:da:a1 (reason=6)
[ 1227.555522] wlan0: deauthenticated
[ 1227.929426] wlan0: authenticate with AP 00:1e:58:3d:da:a1
[ 1227.930611] wlan0: RX authentication from 00:1e:58:3d:da:a1 (alg=0 transaction=2 status=0)
[ 1227.930631] wlan0: authenticated
[ 1227.930646] wlan0: associate with AP 00:1e:58:3d:da:a1
[ 1227.934276] wlan0: RX ReassocResp from 00:1e:58:3d:da:a1 (capab=0x421 status=0 aid=3)
[ 1227.934295] wlan0: associated
[ 1259.670591] wlan0: disassociate(reason=3)
[ 1259.920931] wlan0: Initial auth_alg=0
[ 1259.920957] wlan0: authenticate with AP 00:1e:58:3d:da:a1
[ 1259.923099] wlan0: RX authentication from 00:1e:58:3d:da:a1 (alg=0 transaction=2 status=0)
[ 1259.923117] wlan0: authenticated
[ 1259.923131] wlan0: associate with AP 00:1e:58:3d:da:a1
[ 1259.925738] wlan0: RX AssocResp from 00:1e:58:3d:da:a1 (capab=0x421 status=0 aid=3)
[ 1259.925756] wlan0: associated
[ 1259.925782] wlan0: switched to short barker preamble (BSSID=00:1e:58:3d:da:a1)
[ 1266.455830] wlan0: Initial auth_alg=0
[ 1266.455885] wlan0: authenticate with AP 00:1e:58:3d:da:a1
[ 1266.458554] wlan0: Initial auth_alg=0
[ 1266.458580] wlan0: authenticate with AP 00:1e:58:3d:da:a1
[ 1266.459673] wlan0: RX authentication from 00:1e:58:3d:da:a1 (alg=0 transaction=2 status=0)
[ 1266.459693] wlan0: authenticated
[ 1266.459707] wlan0: associate with AP 00:1e:58:3d:da:a1
[ 1266.462339] wlan0: authentication frame received from 00:1e:58:3d:da:a1, but not in authenticate state - ignored
[ 1266.466194] wlan0: RX ReassocResp from 00:1e:58:3d:da:a1 (capab=0x421 status=0 aid=3)
[ 1266.466213] wlan0: associated
[ 1336.694048] wlan0: disassociate(reason=3)
[ 1336.947562] wlan0: Initial auth_alg=0
[ 1336.947589] wlan0: authenticate with AP 00:1e:58:3d:da:a1
[ 1336.949385] wlan0: RX authentication from 00:1e:58:3d:da:a1 (alg=0 transaction=2 status=0)
[ 1336.949403] wlan0: authenticated
[ 1336.949422] wlan0: associate with AP 00:1e:58:3d:da:a1
[ 1336.952008] wlan0: RX AssocResp from 00:1e:58:3d:da:a1 (capab=0x421 status=0 aid=3)
[ 1336.952026] wlan0: associated
[ 1336.952050] wlan0: switched to short barker preamble (BSSID=00:1e:58:3d:da:a1)
[ 1338.914569] wlan0: Initial auth_alg=0
[ 1338.914604] wlan0: authenticate with AP 00:1e:58:3d:da:a1
[ 1338.919836] wlan0: Initial auth_alg=0
[ 1338.919861] wlan0: authenticate with AP 00:1e:58:3d:da:a1
[ 1338.920969] wlan0: RX authentication from 00:1e:58:3d:da:a1 (alg=0 transaction=2 status=0)
[ 1338.920989] wlan0: authenticated
[ 1338.921003] wlan0: associate with AP 00:1e:58:3d:da:a1
[ 1338.923132] wlan0: authentication frame received from 00:1e:58:3d:da:a1, but not in authenticate state - ignored
[ 1338.925606] wlan0: RX ReassocResp from 00:1e:58:3d:da:a1 (capab=0x421 status=0 aid=3)
[ 1338.925625] wlan0: associated
```

I didn't know what a "man" was but now I do but don't understand it at all. Is there something I can do in terminal so that I don't have to click the wireless network before clicking on a link? thanks for any help :)
[/COLOR]

---

### Post by cariboo on 2009-12-11
Have you got available to all users check in the Edit Connections window?

---

