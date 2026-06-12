---
title: "interntal sd card reader"
date: 2009-03-05
forum: New to Ubuntu
---

### Post by trinidadflores on 2009-03-05
I have a Hp DV6500 Pavilion notebook which has a internal sd card reader.  When running the live cd my card reader works, but when restart and load ubuntu it dont work.  How can i correct this issue?

trinidad

---

### Post by brdmb on 2009-03-05
could you open a terminal (Applications->Accessories->Terminal) and type in
```
lspci
```
and post the output?

This helps us know if your computer can "see" the cardreader.

Thanks!

---

### Post by trinidadflores on 2009-03-05
> **brdmb said:**
> could you open a terminal (Applications->Accessories->Terminal) and type in
```
lspci
```
and post the output?

This helps us know if your computer can "see" the cardreader.

Thanks!
trinidad@ubuntu-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M GS (rev a1)
02:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
[B]09:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
09:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
09:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
09:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
09:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)[/B]
trinidad@ubuntu-laptop:~$

---

### Post by brdmb on 2009-03-06
Ok, that looks good!  Try putting an SD (or other format) card into the card reader and then post the results of

```
dmesg
```

I have the same card reader in my Pavilion, so I have a feeling we'll be able to figure this one out!

---

### Post by trinidadflores on 2009-03-06
[   11.861111] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input4
[   11.890316] Linux agpgart interface v0.103
[   11.893019] ACPI: Sleep Button (CM) [SLPB]
[   11.895180] ACPI: AC Adapter [ACAD] (on-line)
[   11.895228] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input5
[   11.897099] ACPI: Lid Switch [LID]
[   12.062835] ACPI: Battery Slot [BAT0] (battery present)
[   12.062990] ACPI: WMI: Mapper loaded
[   12.147681] acpi device:06: registered as cooling_device2
[   12.147807] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02/device:03/input/input6
[   12.172018] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   12.172626] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:08/input/input7
[   12.204017] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   12.561842] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27ks
[   12.561845] iwlagn: Copyright(c) 2003-2008 Intel Corporation
[   12.562350] iwlagn 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   12.562359] iwlagn 0000:02:00.0: setting latency timer to 64
[   12.562383] iwlagn: Detected Intel Wireless WiFi Link 4965AGN REV=0x4
[   12.608284] iwlagn: Tunable channels: 11 802.11bg, 13 802.11a channels
[   12.608543] iwlagn 0000:02:00.0: PCI INT A disabled
[   12.608858] phy0: Selected rate control algorithm 'iwl-agn-rs'
[   12.633734] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   12.633760] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   12.658845] Bluetooth: Core ver 2.13
[   12.658985] NET: Registered protocol family 31
[   12.658987] Bluetooth: HCI device and connection manager initialized
[   12.658990] Bluetooth: HCI socket layer initialized
[   12.711634] Bluetooth: Generic Bluetooth USB driver ver 0.3
[   12.711715] usbcore: registered new interface driver btusb
[   12.844073] iTCO_vendor_support: vendor-support=0
[   12.892437] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008)
[   12.892740] iTCO_wdt: Found a ICH8M TCO device (Version=2, TCOBASE=0x1060)
[   12.892828] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   12.954124] Linux video capture interface: v2.00
[   12.957577] sdhci: Secure Digital Host Controller Interface driver
[   12.957579] sdhci: Copyright(c) Pierre Ossman
[   12.982522] ricoh-mmc: Ricoh MMC Controller disabling driver
[   12.982525] ricoh-mmc: Copyright(c) Philip Langdale
[   12.982557] ricoh-mmc: Ricoh MMC controller found at 0000:09:09.2 [1180:0843] (rev 12)
[   12.982576] ricoh-mmc: Controller is now disabled.
[   12.989478] sdhci-pci 0000:09:09.1: SDHCI controller found [1180:0822] (rev 22)
[   12.989494] sdhci-pci 0000:09:09.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[   12.990502] sdhci-pci 0000:09:09.1: Will use DMA mode even though HW doesn't fully claim to support it.
[   12.992720] mmc0: SDHCI controller on PCI [0000:09:09.1] using DMA
[   13.064735] input: PC Speaker as /devices/platform/pcspkr/input/input8
[   13.075888] uvcvideo: Found UVC 1.00 device HP Webcam (04f2:b015)
[   13.077033] input: HP Webcam as /devices/pci0000:00/0000:00:1d.7/usb7/7-4/7-4:1.0/input/input9
[   13.282226] usbcore: registered new interface driver uvcvideo
[   13.282231] USB Video Class driver (v0.1.0)
[   14.134351] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1a0b1, caps: 0xa04713/0x200000
[   14.244061] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input10
[   16.527098] lp: driver loaded but no devices found
[   16.628939] Adding 19816136k swap on /dev/sda6.  Priority:-1 extents:1 across:19816136k
[   17.158508] EXT3 FS on sda5, internal journal
[   18.117943] type=1505 audit(1236286418.714:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4349
[   18.240901] type=1505 audit(1236286418.838:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4354
[   18.241084] type=1505 audit(1236286418.838:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4354
[   18.378675] ip_tables: (C) 2000-2006 Netfilter Core Team
[   19.517332] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   19.555506] apm: BIOS not found.
[   19.713850] ppdev: user-space parallel port driver
[   22.009726] Bluetooth: L2CAP ver 2.11
[   22.009738] Bluetooth: L2CAP socket layer initialized
[   22.041684] Bluetooth: SCO (Voice Link) ver 0.6
[   22.041695] Bluetooth: SCO socket layer initialized
[   22.080130] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   22.080142] Bluetooth: BNEP filters: protocol multicast
[   22.139994] Bluetooth: RFCOMM socket layer initialized
[   22.140502] Bluetooth: RFCOMM TTY layer initialized
[   22.140512] Bluetooth: RFCOMM ver 1.10
[   22.157647] Bridge firewalling registered
[   24.097830] mtrr: base(0xd0000000) is not aligned on a size(0x7f00000) boundary
[   26.332312] r8169: eth0: link down
[   26.344699] iwlagn 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   26.344779] iwlagn 0000:02:00.0: restoring config space at offset 0x1 (was 0x40100102, writing 0x40100106)
[   26.345882] firmware: requesting iwlwifi-4965-2.ucode
[   26.595829] Registered led device: iwl-phy0:radio
[   26.596180] Registered led device: iwl-phy0:assoc
[   26.596492] Registered led device: iwl-phy0:RX
[   26.596781] Registered led device: iwl-phy0:TX
[   26.692130] NET: Registered protocol family 17
[   28.276712] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[   28.278642] wlan0: authenticated
[   28.278654] wlan0: associate with AP 00:1d:7e:f8:c4:c0
[   28.280994] wlan0: RX AssocResp from 00:1d:7e:f8:c4:c0 (capab=0x401 status=0 aid=2)
[   28.281008] wlan0: associated
[   28.288654] wlan0: disassociating by local choice (reason=3)
[   46.915602] UDF-fs: No VRS found
[   46.944358] ISO 9660 Extensions: Microsoft Joliet Level 3
[   47.009260] ISO 9660 Extensions: RRIP_1991A
[   54.011244] wlan0: associate with AP 00:1d:7e:f8:c4:c0
[   54.015857] wlan0: RX ReassocResp from 00:1d:7e:f8:c4:c0 (capab=0x401 status=0 aid=2)
[   54.015862] wlan0: associated
[   54.023085] wlan0: disassociating by local choice (reason=3)
[   55.186222] CPU0 attaching NULL sched-domain.
[   55.186240] CPU1 attaching NULL sched-domain.
[   55.189152] CPU0 attaching sched-domain:
[   55.189161]  domain 0: span 0-1 level MC
[   55.189168]   groups: 0 1
[   55.189182] CPU1 attaching sched-domain:
[   55.189187]  domain 0: span 0-1 level MC
[   55.189193]   groups: 1 0
[   80.544236] wlan0: associate with AP 00:1d:7e:f8:c4:c0
[   80.546549] wlan0: RX ReassocResp from 00:1d:7e:f8:c4:c0 (capab=0x401 status=0 aid=2)
[   80.546561] wlan0: associated
[   80.553220] wlan0: disassociating by local choice (reason=3)
[   99.889766] wlan0: associate with AP 00:1d:7e:f8:c4:c0
[   99.895150] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[   99.897208] wlan0: authenticated
[   99.897225] wlan0: associate with AP 00:1d:7e:f8:c4:c0
[   99.899581] wlan0: RX ReassocResp from 00:1d:7e:f8:c4:c0 (capab=0x401 status=0 aid=2)
[   99.899592] wlan0: associated
[  109.981905] NET: Registered protocol family 10
[  109.983161] lo: Disabled Privacy Extensions
[  109.984607] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  120.488068] wlan0: no IPv6 routers present
[  561.940118] CE: hpet increasing min_delta_ns to 15000 nsec
[ 2554.456201] usb 3-4: new high speed USB device using ehci_hcd and address 2
[ 2554.590060] usb 3-4: configuration #1 chosen from 1 choice
[ 2554.724693] usbcore: registered new interface driver libusual
[ 2554.759910] Initializing USB Mass Storage driver...
[ 2554.761219] scsi5 : SCSI emulation for USB Mass Storage devices
[ 2554.761819] usbcore: registered new interface driver usb-storage
[ 2554.762238] USB Mass Storage support registered.
[ 2554.762810] usb-storage: device found at 2
[ 2554.762819] usb-storage: waiting for device to settle before scanning
[ 2559.760343] usb-storage: device scan complete
[ 2559.760876] scsi 5:0:0:0: Direct-Access     Audiovox PEARL            3150 PQ: 0 ANSI: 4
[ 2559.764565] sd 5:0:0:0: [sdb] 476544 2048-byte hardware sectors (976 MB)
[ 2559.765064] sd 5:0:0:0: [sdb] Write Protect is off
[ 2559.765071] sd 5:0:0:0: [sdb] Mode Sense: 3e 00 00 00
[ 2559.765079] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 2559.767467] sd 5:0:0:0: [sdb] 476544 2048-byte hardware sectors (976 MB)
[ 2559.768073] sd 5:0:0:0: [sdb] Write Protect is off
[ 2559.768082] sd 5:0:0:0: [sdb] Mode Sense: 3e 00 00 00
[ 2559.768089] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 2559.768102]  sdb: sdb1
[ 2559.779997] sd 5:0:0:0: [sdb] Attached SCSI removable disk
[ 2559.780205] sd 5:0:0:0: Attached scsi generic sg2 type 0
[ 3125.197827] usb 3-4: USB disconnect, address 2
[ 4216.424432] wlan0: deauthenticated
[ 4217.424094] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[ 4217.624100] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[ 4217.690374] wlan0: authenticated
[ 4217.690390] wlan0: associate with AP 00:1d:7e:f8:c4:c0
[ 4217.888091] wlan0: associate with AP 00:1d:7e:f8:c4:c0
[ 4218.088088] wlan0: associate with AP 00:1d:7e:f8:c4:c0
[ 4218.288096] wlan0: association with AP 00:1d:7e:f8:c4:c0 timed out
[ 4226.348384] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[ 4226.548094] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[ 4226.752184] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[ 4226.948099] wlan0: authentication with AP 00:1d:7e:f8:c4:c0 timed out
[ 4231.652558] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[ 4231.852068] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[ 4232.052093] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[ 4232.252200] wlan0: authentication with AP 00:1d:7e:f8:c4:c0 timed out
[ 4266.258615] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[ 4266.262101] wlan0: authenticated
[ 4266.262117] wlan0: associate with AP 00:1d:7e:f8:c4:c0
[ 4266.266355] wlan0: RX AssocResp from 00:1d:7e:f8:c4:c0 (capab=0x401 status=0 aid=2)
[ 4266.266369] wlan0: associated
[ 4311.488704] wlan0: disassociating by local choice (reason=3)
[ 4311.490283] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[ 4311.494197] wlan0: authenticated
[ 4311.494212] wlan0: associate with AP 00:1d:7e:f8:c4:c0
[ 4311.692102] wlan0: associate with AP 00:1d:7e:f8:c4:c0
[ 4311.694307] wlan0: RX AssocResp from 00:1d:7e:f8:c4:c0 (capab=0x401 status=0 aid=2)
[ 4311.694319] wlan0: associated
[ 4311.702852] wlan0: disassociating by local choice (reason=3)
[ 4337.163763] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[ 4337.165736] wlan0: authenticated
[ 4337.165752] wlan0: associate with AP 00:1d:7e:f8:c4:c0
[ 4337.167358] wlan0: associate with AP 00:1d:7e:f8:c4:c0
[ 4337.211288] wlan0: RX ReassocResp from 00:1d:7e:f8:c4:c0 (capab=0x401 status=0 aid=2)
[ 4337.211301] wlan0: associated
[12609.154520] CPU0 attaching NULL sched-domain.
[12609.154536] CPU1 attaching NULL sched-domain.
[12609.174871] CPU0 attaching sched-domain:
[12609.174882]  domain 0: span 0-1 level MC
[12609.174889]   groups: 0 1
[12609.174900]   domain 1: span 0-1 level CPU
[12609.174906]    groups: 0-1
[12609.174917] CPU1 attaching sched-domain:
[12609.174922]  domain 0: span 0-1 level MC
[12609.174928]   groups: 1 0
[12609.174937]   domain 1: span 0-1 level CPU
[12609.174943]    groups: 0-1
[12618.876450] CPU0 attaching NULL sched-domain.
[12618.876467] CPU1 attaching NULL sched-domain.
[12618.881996] CPU0 attaching sched-domain:
[12618.882008]  domain 0: span 0-1 level MC
[12618.882015]   groups: 0 1
[12618.882029] CPU1 attaching sched-domain:
[12618.882035]  domain 0: span 0-1 level MC
[12618.882040]   groups: 1 0
[12629.632200] usb 3-4: new high speed USB device using ehci_hcd and address 3
[12629.767012] usb 3-4: configuration #1 chosen from 1 choice
[12629.767937] scsi6 : SCSI emulation for USB Mass Storage devices
[12629.768777] usb-storage: device found at 3
[12629.768783] usb-storage: waiting for device to settle before scanning
[12634.769736] usb-storage: device scan complete
[12634.770910] scsi 6:0:0:0: Direct-Access     Audiovox PEARL            3150 PQ: 0 ANSI: 4
[12634.775231] sd 6:0:0:0: [sdb] 476544 2048-byte hardware sectors (976 MB)
[12634.777271] sd 6:0:0:0: [sdb] Write Protect is off
[12634.777284] sd 6:0:0:0: [sdb] Mode Sense: 3e 00 00 00
[12634.777291] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[12634.781996] sd 6:0:0:0: [sdb] 476544 2048-byte hardware sectors (976 MB)
[12634.783871] sd 6:0:0:0: [sdb] Write Protect is off
[12634.783882] sd 6:0:0:0: [sdb] Mode Sense: 3e 00 00 00
[12634.783888] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[12634.787065]  sdb: sdb1
[12634.811015] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[12634.811639] sd 6:0:0:0: Attached scsi generic sg2 type 0
[14637.904769] usb 3-4: USB disconnect, address 3
[14778.792109] usb 3-4: new high speed USB device using ehci_hcd and address 4
[14778.938130] usb 3-4: configuration #1 chosen from 1 choice
[14778.938675] scsi7 : SCSI emulation for USB Mass Storage devices
[14778.938845] usb-storage: device found at 4
[14778.938850] usb-storage: waiting for device to settle before scanning
[14783.936609] usb-storage: device scan complete
[14783.937547] scsi 7:0:0:0: Direct-Access     Audiovox PEARL            3150 PQ: 0 ANSI: 4
[14783.940726] sd 7:0:0:0: [sdb] 476544 2048-byte hardware sectors (976 MB)
[14783.941378] sd 7:0:0:0: [sdb] Write Protect is off
[14783.941388] sd 7:0:0:0: [sdb] Mode Sense: 3e 00 00 00
[14783.941397] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[14783.943834] sd 7:0:0:0: [sdb] 476544 2048-byte hardware sectors (976 MB)
[14783.944444] sd 7:0:0:0: [sdb] Write Protect is off
[14783.944455] sd 7:0:0:0: [sdb] Mode Sense: 3e 00 00 00
[14783.944461] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[14783.944471]  sdb: sdb1
[14783.957265] sd 7:0:0:0: [sdb] Attached SCSI removable disk
[14783.958021] sd 7:0:0:0: Attached scsi generic sg2 type 0
[15264.533191] wlan0: No ProbeResp from current AP 00:1d:7e:f8:c4:c0 - assume out of range
[15279.758043] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[15279.957184] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[15280.156193] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[15280.356098] wlan0: authentication with AP 00:1d:7e:f8:c4:c0 timed out
[15292.833228] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[15292.837605] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[15292.837647] wlan0: authenticated
[15292.837654] wlan0: associate with AP 00:1d:7e:f8:c4:c0
[15292.842001] wlan0: RX AssocResp from 00:1d:7e:f8:c4:c0 (capab=0x401 status=0 aid=1)
[15292.842013] wlan0: associated
[15307.464870] wlan0: disassociating by local choice (reason=3)
[15307.466961] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[15307.468919] wlan0: authenticated
[15307.468934] wlan0: associate with AP 00:1d:7e:f8:c4:c0
[15307.471178] wlan0: RX AssocResp from 00:1d:7e:f8:c4:c0 (capab=0x401 status=0 aid=1)
[15307.471190] wlan0: associated
[15307.480046] wlan0: disassociating by local choice (reason=3)
[15314.591976] wlan0: associate with AP 00:1d:7e:f8:c4:c0
[15314.595106] wlan0: RX ReassocResp from 00:1d:7e:f8:c4:c0 (capab=0x401 status=0 aid=1)
[15314.595119] wlan0: associated
[15314.601821] wlan0: disassociating by local choice (reason=3)
[15317.895861] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[15317.897806] wlan0: authenticated
[15317.897818] wlan0: associate with AP 00:1d:7e:f8:c4:c0
[15317.899989] wlan0: RX AssocResp from 00:1d:7e:f8:c4:c0 (capab=0x401 status=0 aid=1)
[15317.900023] wlan0: associated
[15317.911627] wlan0: disassociating by local choice (reason=3)
[15326.873950] wlan0: associate with AP 00:1d:7e:f8:c4:c0
[15326.876191] wlan0: RX ReassocResp from 00:1d:7e:f8:c4:c0 (capab=0x401 status=0 aid=1)
[15326.876202] wlan0: associated
[15326.883218] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[15326.885691] wlan0: authenticated
[15326.885701] wlan0: associate with AP 00:1d:7e:f8:c4:c0
[15326.891452] wlan0: RX ReassocResp from 00:1d:7e:f8:c4:c0 (capab=0x401 status=0 aid=1)
[15326.891462] wlan0: associated
[15326.903595] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[15326.920814] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[15326.920853] wlan0: authenticated
[15326.920860] wlan0: associate with AP 00:1d:7e:f8:c4:c0
[15326.925708] wlan0: RX ReassocResp from 00:1d:7e:f8:c4:c0 (capab=0x401 status=0 aid=1)
[15326.925720] wlan0: associated
[15994.156248] wlan0: No ProbeResp from current AP 00:1d:7e:f8:c4:c0 - assume out of range
[16002.192359] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[16002.197413] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[16002.199372] wlan0: authenticated
[16002.199387] wlan0: associate with AP 00:1d:7e:f8:c4:c0
[16002.201695] wlan0: RX ReassocResp from 00:1d:7e:f8:c4:c0 (capab=0x401 status=0 aid=2)
[16002.201704] wlan0: associated
[16038.533724] wlan0: deauthenticated
[16039.532074] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[16039.534019] wlan0: authenticated
[16039.534033] wlan0: associate with AP 00:1d:7e:f8:c4:c0
[16039.536346] wlan0: RX ReassocResp from 00:1d:7e:f8:c4:c0 (capab=0x401 status=0 aid=1)
[16039.536355] wlan0: associated
[16080.528073] wlan0: deauthenticated
[16081.532068] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[16081.534006] wlan0: authenticated
[16081.534012] wlan0: associate with AP 00:1d:7e:f8:c4:c0
[16081.536254] wlan0: RX ReassocResp from 00:1d:7e:f8:c4:c0 (capab=0x401 status=0 aid=1)
[16081.536258] wlan0: associated
[16839.207153] usb 3-4: USB disconnect, address 4
[16979.206014] iwlagn: Can not allocate SKB buffers
[16980.583636] iwlagn: Can not allocate SKB buffers
[17110.069963] psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 4
[17110.072506] psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 1
[17110.086611] psmouse.c: TouchPad at isa0060/serio1/input0 - driver resynched.
[17500.312188] wlan0: No ProbeResp from current AP 00:1d:7e:f8:c4:c0 - assume out of range
[17502.750575] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[17502.948192] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[17503.148191] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[17503.348187] wlan0: authentication with AP 00:1d:7e:f8:c4:c0 timed out
[17514.504942] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[17514.508692] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[17514.508735] wlan0: authenticated
[17514.508743] wlan0: associate with AP 00:1d:7e:f8:c4:c0
[17514.513769] wlan0: RX ReassocResp from 00:1d:7e:f8:c4:c0 (capab=0x401 status=0 aid=1)
[17514.513781] wlan0: associated
[17548.524073] wlan0: No ProbeResp from current AP 00:1d:7e:f8:c4:c0 - assume out of range
[17551.148907] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[17551.153795] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[17551.352200] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[17551.552191] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[17551.752190] wlan0: authentication with AP 00:1d:7e:f8:c4:c0 timed out
[17562.816848] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[17562.820521] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[17562.820545] wlan0: authenticated
[17562.820552] wlan0: associate with AP 00:1d:7e:f8:c4:c0
[17562.825313] wlan0: RX ReassocResp from 00:1d:7e:f8:c4:c0 (capab=0x401 status=0 aid=1)
[17562.825324] wlan0: associated
[18090.529795] wlan0: deauthenticated
[18091.528183] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[18091.530076] wlan0: authenticated
[18091.530089] wlan0: associate with AP 00:1d:7e:f8:c4:c0
[18091.532407] wlan0: RX ReassocResp from 00:1d:7e:f8:c4:c0 (capab=0x401 status=0 aid=1)
[18091.532417] wlan0: associated
[18290.144057] wlan0: No ProbeResp from current AP 00:1d:7e:f8:c4:c0 - assume out of range
[18305.367859] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[18305.564099] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[18305.764092] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[18305.964190] wlan0: authentication with AP 00:1d:7e:f8:c4:c0 timed out
[18315.568150] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[18315.572155] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[18315.572195] wlan0: authenticated
[18315.572203] wlan0: associate with AP 00:1d:7e:f8:c4:c0
[18315.578913] wlan0: RX AssocResp from 00:1d:7e:f8:c4:c0 (capab=0x401 status=0 aid=2)
[18315.578926] wlan0: associated
[18335.584190] wlan0: No ProbeResp from current AP 00:1d:7e:f8:c4:c0 - assume out of range
[18343.393377] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[18343.400180] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[18343.400224] wlan0: authenticated
[18343.400232] wlan0: associate with AP 00:1d:7e:f8:c4:c0
[18343.404297] wlan0: RX ReassocResp from 00:1d:7e:f8:c4:c0 (capab=0x401 status=0 aid=2)
[18343.404309] wlan0: associated
[19564.329457] wlan0: deauthenticated
[19565.328189] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[19565.528198] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[19565.728189] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[19565.928200] wlan0: authentication with AP 00:1d:7e:f8:c4:c0 timed out
[19573.500494] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[19573.700184] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[19573.900183] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[19574.100185] wlan0: authentication with AP 00:1d:7e:f8:c4:c0 timed out
[19579.547059] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[19579.745057] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[19579.945188] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[19580.145192] wlan0: authentication with AP 00:1d:7e:f8:c4:c0 timed out
[19585.137380] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[19585.140370] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[19585.340190] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[19585.540200] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[19585.740198] wlan0: authentication with AP 00:1d:7e:f8:c4:c0 timed out
[19596.775114] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[19596.778064] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[19596.976192] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[19597.176194] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[19597.376114] wlan0: authentication with AP 00:1d:7e:f8:c4:c0 timed out
[19608.414034] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[19608.418076] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[19608.616190] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[19608.816190] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[19609.016190] wlan0: authentication with AP 00:1d:7e:f8:c4:c0 timed out
[19620.053008] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[19620.055884] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[19620.252200] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[19620.452090] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[19620.652203] wlan0: authentication with AP 00:1d:7e:f8:c4:c0 timed out
[19631.690457] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[19631.693335] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[19631.892191] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[19632.092191] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[19632.292185] wlan0: authentication with AP 00:1d:7e:f8:c4:c0 timed out
[19643.327669] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[19643.330540] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[19643.343400] wlan0: authenticated
[19643.343416] wlan0: associate with AP 00:1d:7e:f8:c4:c0
[19643.540199] wlan0: associate with AP 00:1d:7e:f8:c4:c0
[19643.740186] wlan0: associate with AP 00:1d:7e:f8:c4:c0
[19643.940199] wlan0: association with AP 00:1d:7e:f8:c4:c0 timed out
[19654.968864] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[19654.971831] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[19655.168186] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[19655.368190] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[19655.568087] wlan0: authentication with AP 00:1d:7e:f8:c4:c0 timed out
[19666.606341] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[19666.609261] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[19666.808196] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[19666.829414] wlan0: authenticated
[19666.829429] wlan0: associate with AP 00:1d:7e:f8:c4:c0
[19667.028185] wlan0: associate with AP 00:1d:7e:f8:c4:c0
[19667.228196] wlan0: associate with AP 00:1d:7e:f8:c4:c0
[19667.428189] wlan0: association with AP 00:1d:7e:f8:c4:c0 timed out
[19678.270554] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[19678.273482] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[19678.472219] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[19678.672196] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[19678.872192] wlan0: authentication with AP 00:1d:7e:f8:c4:c0 timed out
[19689.905354] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[19689.908384] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[19689.908425] wlan0: authenticated
[19689.908432] wlan0: associate with AP 00:1d:7e:f8:c4:c0
[19689.917851] wlan0: RX AssocResp from 00:1d:7e:f8:c4:c0 (capab=0x401 status=0 aid=2)
[19689.917863] wlan0: associated
[19717.324197] wlan0: No ProbeResp from current AP 00:1d:7e:f8:c4:c0 - assume out of range
[19725.137972] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[19725.143620] wlan0: authenticated
[19725.143636] wlan0: associate with AP 00:1d:7e:f8:c4:c0
[19725.340185] wlan0: associate with AP 00:1d:7e:f8:c4:c0
[19725.540113] wlan0: associate with AP 00:1d:7e:f8:c4:c0
[19725.740196] wlan0: association with AP 00:1d:7e:f8:c4:c0 timed out
[19736.807501] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[19736.810439] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[19737.008193] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[19737.014940] wlan0: authenticated
[19737.014956] wlan0: associate with AP 00:1d:7e:f8:c4:c0
[19737.212187] wlan0: associate with AP 00:1d:7e:f8:c4:c0
[19737.214568] wlan0: RX ReassocResp from 00:1d:7e:f8:c4:c0 (capab=0x401 status=0 aid=2)
[19737.214579] wlan0: associated
[20288.439989] wlan0: disassociating by local choice (reason=3)
[20296.117108] wlan0: associate with AP 00:1d:7e:f8:c4:c0
[20296.121670] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[20296.124436] wlan0: authenticated
[20296.124451] wlan0: associate with AP 00:1d:7e:f8:c4:c0
[20296.126794] wlan0: RX ReassocResp from 00:1d:7e:f8:c4:c0 (capab=0x401 status=0 aid=2)
[20296.126805] wlan0: associated
[21801.560196] wlan0: No ProbeResp from current AP 00:1d:7e:f8:c4:c0 - assume out of range
[21816.788213] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[21816.989106] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[21817.189104] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[21817.389087] wlan0: authentication with AP 00:1d:7e:f8:c4:c0 timed out
[21826.976623] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[21826.980835] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[21826.980884] wlan0: authenticated
[21826.980892] wlan0: associate with AP 00:1d:7e:f8:c4:c0
[21826.985044] wlan0: RX AssocResp from 00:1d:7e:f8:c4:c0 (capab=0x401 status=0 aid=2)
[21826.985057] wlan0: associated
[21858.989051] wlan0: No ProbeResp from current AP 00:1d:7e:f8:c4:c0 - assume out of range
[21874.218410] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[21874.416194] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[21874.616046] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[21874.824025] wlan0: authentication with AP 00:1d:7e:f8:c4:c0 timed out
[21886.255318] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[21886.258867] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[21886.258891] wlan0: authenticated
[21886.258898] wlan0: associate with AP 00:1d:7e:f8:c4:c0
[21886.281225] wlan0: RX AssocResp from 00:1d:7e:f8:c4:c0 (capab=0x401 status=0 aid=2)
[21886.281236] wlan0: associated
[25111.467836] wlan0: deauthenticated
[25112.464187] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[25112.664186] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[25112.699114] wlan0: authenticated
[25112.699130] wlan0: associate with AP 00:1d:7e:f8:c4:c0
[25112.896219] wlan0: associate with AP 00:1d:7e:f8:c4:c0
[25112.959820] wlan0: RX ReassocResp from 00:1d:7e:f8:c4:c0 (capab=0x401 status=0 aid=2)
[25112.959833] wlan0: associated
[25176.539300] wlan0: deauthenticated
[25177.536210] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[25177.736186] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[25177.936092] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[25178.136188] wlan0: authentication with AP 00:1d:7e:f8:c4:c0 timed out
[25185.844278] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[25185.849734] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[25185.854152] wlan0: authenticated
[25185.854168] wlan0: associate with AP 00:1d:7e:f8:c4:c0
[25186.052186] wlan0: associate with AP 00:1d:7e:f8:c4:c0
[25186.057232] wlan0: RX ReassocResp from 00:1d:7e:f8:c4:c0 (capab=0x401 status=0 aid=2)
[25186.057244] wlan0: associated
[25352.933417] wlan0: deauthenticated
[25353.932198] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[25353.934156] wlan0: authenticated
[25353.934171] wlan0: associate with AP 00:1d:7e:f8:c4:c0
[25354.132196] wlan0: associate with AP 00:1d:7e:f8:c4:c0
[25354.137336] wlan0: RX ReassocResp from 00:1d:7e:f8:c4:c0 (capab=0x401 status=0 aid=2)
[25354.137349] wlan0: associated
[25555.393040] wlan0: deauthenticated
[25555.393109] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[25555.592190] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[25555.792196] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[25555.992192] wlan0: authentication with AP 00:1d:7e:f8:c4:c0 timed out
[25556.018446] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[25556.024210] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[25556.224201] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[25556.424194] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[25556.624191] wlan0: authentication with AP 00:1d:7e:f8:c4:c0 timed out
[25567.661486] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[25567.664289] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[25567.864089] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[25568.064090] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[25568.264037] wlan0: authentication with AP 00:1d:7e:f8:c4:c0 timed out
[25570.624709] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[25570.820101] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[25571.020189] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[25571.220192] wlan0: authentication with AP 00:1d:7e:f8:c4:c0 timed out
[27409.614112] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[27409.616731] wlan0: authenticate with AP 00:1d:7e:f8:c4:c0
[27409.616770] wlan0: authenticated
[27409.616778] wlan0: associate with AP 00:1d:7e:f8:c4:c0
[27409.621428] wlan0: RX AssocResp from 00:1d:7e:f8:c4:c0 (capab=0x401 status=0 aid=1)
[27409.621441] wlan0: associated

---

