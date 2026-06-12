---
title: "Wireless not working :("
date: 2007-10-15
forum: Networking &amp; Wireless
---

### Post by Atzu on 2007-10-15
Well I´m getting tired, my computer sometimes connect to internet then it disconnect... I just got d/ced (router Linksys model WRT54G) my comp is compaq nc6220 (Intel PRO/Wireless 2200BG 802.11b/g WLAN), my brother have same computer with Ubuntu and he dont have this problem :(


Help please!!

---

### Post by anubhavrocks on 2007-10-15
please provide the output of  following command when you face this problem
```
dmesg
```

---

### Post by Atzu on 2007-10-15
> **anubhavrocks said:**
> please provide the output of  following command when you face this problem
```
dmesg
```

Right now i dont have the problem -_-;; sometimes i hate this computer >_>

---

### Post by Atzu on 2007-10-16
> **anubhavrocks said:**
> please provide the output of  following command when you face this problem
```
dmesg
```

ok here's the output(which is very big):

```
[   21.496000] ACPI: PCI Interrupt 0000:00:1e.2[A] -> GSI 21 (level, low) -> IRQ 22
[   21.496000] PCI: Setting latency timer of device 0000:00:1e.2 to 64
[   22.316000] intel8x0_measure_ac97_clock: measured 55480 usecs
[   22.316000] intel8x0: clocking to 48000
[   22.476000] fuse init (API version 7.8)
[   22.496000] lp0: using parport0 (interrupt-driven).
[   22.516000] Adding 1485972k swap on /dev/disk/by-uuid/d4df4f4d-ab16-4dc7-bfb5-16d290ba14b4.  Priority:-1 extents:1 across:1485972k
[   22.660000] EXT3 FS on sda1, internal journal
[   23.368000] logips2pp: Detected unknown logitech mouse model 0
[   23.904000] NET: Registered protocol family 10
[   23.904000] lo: Disabled Privacy Extensions
[   23.904000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   26.196000] IBM TrackPoint firmware: 0x12, buttons: 0/0
[   26.472000] input: TPPS/2 IBM TrackPoint as /class/input/input5
[   28.960000] Using specific hotkey driver
[   29.004000] ibm_acpi: ec object not found
[   29.032000] ACPI: Video Device [C059] (multi-head: yes  rom: no  post: no)
[   29.048000] ACPI: AC Adapter [C16E] (on-line)
[   29.064000] No dock devices found.
[   29.108000] ACPI: Battery Slot [C170] (battery present)
[   29.108000] ACPI: Battery Slot [C16F] (battery absent)
[   29.240000] input: Power Button (FF) as /class/input/input6
[   29.244000] ACPI: Power Button (FF) [PWRF]
[   29.280000] input: Sleep Button (CM) as /class/input/input7
[   29.280000] ACPI: Sleep Button (CM) [C1E8]
[   29.316000] input: Lid Switch as /class/input/input8
[   29.320000] ACPI: Lid Switch [C1E9]
[   29.368000] wmi_add device=de39f800
[   29.368000] calling WQBA
[   29.404000] pcc_acpi: loading...
[   34.568000] eth1: no IPv6 routers present
[   39.264000] [drm] Initialized drm 1.1.0 20060810
[   39.268000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[   39.268000] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   39.992000] ppdev: user-space parallel port driver
[   40.836000] apm: BIOS not found.
[   45.376000] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
[   45.472000] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   45.472000] NFSD: starting 90-second grace period
[   47.024000] Bluetooth: L2CAP ver 2.8
[   47.024000] Bluetooth: L2CAP socket layer initialized
[   47.100000] Bluetooth: RFCOMM socket layer initialized
[   47.100000] Bluetooth: RFCOMM TTY layer initialized
[   47.100000] Bluetooth: RFCOMM ver 1.8
[  163.616000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[  183.948000] eth1: no IPv6 routers present
[ 1603.648000] ipw2200: Firmware error detected.  Restarting.
[ 1605.512000] ipw2200: Firmware error detected.  Restarting.
[ 2085.796000] ipw2200: Failed to send SCAN_ABORT: Command timed out.
[ 2086.284000] ipw2200: Firmware error detected.  Restarting.
[ 2088.148000] ipw2200: Firmware error detected.  Restarting.
[ 2291.156000] ip_tables: (C) 2000-2006 Netfilter Core Team
[ 2326.316000] ipw2200: Failed to send SCAN_ABORT: Command timed out.
[ 2326.760000] ipw2200: Firmware error detected.  Restarting.
[ 3047.676000] ipw2200: Failed to send SCAN_ABORT: Command timed out.
[ 3048.156000] ipw2200: Firmware error detected.  Restarting.
[ 3180.248000] usb 4-1: new high speed USB device using ehci_hcd and address 4
[ 3180.380000] usb 4-1: configuration #1 chosen from 2 choices
[ 3181.452000] usbcore: registered new interface driver libusual
[ 3181.532000] Initializing USB Mass Storage driver...
[ 3181.532000] scsi2 : SCSI emulation for USB Mass Storage devices
[ 3181.532000] usbcore: registered new interface driver usb-storage
[ 3181.532000] USB Mass Storage support registered.
[ 3181.532000] usb-storage: device found at 4
[ 3181.532000] usb-storage: waiting for device to settle before scanning
[ 3186.532000] usb-storage: device scan complete
[ 3186.532000] scsi 2:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[ 3186.536000] SCSI device sdb: 1982464 2048-byte hdwr sectors (4060 MB)
[ 3186.536000] sdb: Write Protect is off
[ 3186.536000] sdb: Mode Sense: 68 00 00 08
[ 3186.536000] sdb: assuming drive cache: write through
[ 3186.540000] SCSI device sdb: 1982464 2048-byte hdwr sectors (4060 MB)
[ 3186.540000] sdb: Write Protect is off
[ 3186.540000] sdb: Mode Sense: 68 00 00 08
[ 3186.540000] sdb: assuming drive cache: write through
[ 3186.540000]  sdb: sdb1 sdb2
[ 3186.544000] sd 2:0:0:0: Attached scsi removable disk sdb
[ 3186.544000] sd 2:0:0:0: Attached scsi generic sg2 type 0
[ 3316.592000] usb 4-1: USB disconnect, address 4
[ 3466.788000] usb 4-1: new high speed USB device using ehci_hcd and address 5
[ 3466.920000] usb 4-1: configuration #1 chosen from 2 choices
[ 3466.920000] scsi3 : SCSI emulation for USB Mass Storage devices
[ 3466.920000] usb-storage: device found at 5
[ 3466.920000] usb-storage: waiting for device to settle before scanning
[ 3471.920000] usb-storage: device scan complete
[ 3471.920000] scsi 3:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[ 3471.924000] SCSI device sdb: 1982464 2048-byte hdwr sectors (4060 MB)
[ 3471.924000] sdb: Write Protect is off
[ 3471.924000] sdb: Mode Sense: 68 00 00 08
[ 3471.924000] sdb: assuming drive cache: write through
[ 3471.928000] SCSI device sdb: 1982464 2048-byte hdwr sectors (4060 MB)
[ 3471.928000] sdb: Write Protect is off
[ 3471.928000] sdb: Mode Sense: 68 00 00 08
[ 3471.928000] sdb: assuming drive cache: write through
[ 3471.928000]  sdb: sdb1 sdb2
[ 3471.932000] sd 3:0:0:0: Attached scsi removable disk sdb
[ 3471.932000] sd 3:0:0:0: Attached scsi generic sg2 type 0
[ 3649.816000] ipw2200: Failed to send SCAN_ABORT: Command timed out.
[ 3650.264000] ipw2200: Firmware error detected.  Restarting.
[ 4011.468000] ipw2200: Failed to send SCAN_ABORT: Command timed out.
[ 4011.940000] ipw2200: Firmware error detected.  Restarting.
[ 4252.804000] ipw2200: Failed to send SCAN_ABORT: Command timed out.
[ 4253.308000] ipw2200: Firmware error detected.  Restarting.
[ 4373.936000] ipw2200: Failed to send SCAN_ABORT: Command timed out.
[ 4374.428000] ipw2200: Firmware error detected.  Restarting.
[ 4376.160000] ipw2200: Firmware error detected.  Restarting.
[ 4377.864000] ipw2200: Firmware error detected.  Restarting.
[ 4378.876000] ipw2200: Failed to send CARD_DISABLE: Command timed out.
[ 4380.764000] ipw2200: Firmware error detected.  Restarting.
[ 5249.196000] usb 4-1: USB disconnect, address 5
[ 5457.148000] ipw2200: Failed to send SCAN_ABORT: Command timed out.
[ 5457.652000] ipw2200: Firmware error detected.  Restarting.
[ 5483.404000] usb 4-1: new high speed USB device using ehci_hcd and address 6
[ 5483.536000] usb 4-1: configuration #1 chosen from 2 choices
[ 5483.536000] scsi4 : SCSI emulation for USB Mass Storage devices
[ 5483.536000] usb-storage: device found at 6
[ 5483.536000] usb-storage: waiting for device to settle before scanning
[ 5488.536000] usb-storage: device scan complete
[ 5488.540000] scsi 4:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[ 5488.552000] SCSI device sdb: 1982464 2048-byte hdwr sectors (4060 MB)
[ 5488.560000] sdb: Write Protect is off
[ 5488.560000] sdb: Mode Sense: 68 00 00 08
[ 5488.560000] sdb: assuming drive cache: write through
[ 5488.564000] SCSI device sdb: 1982464 2048-byte hdwr sectors (4060 MB)
[ 5488.564000] sdb: Write Protect is off
[ 5488.564000] sdb: Mode Sense: 68 00 00 08
[ 5488.564000] sdb: assuming drive cache: write through
[ 5488.564000]  sdb: sdb1 sdb2
[ 5488.568000] sd 4:0:0:0: Attached scsi removable disk sdb
[ 5488.568000] sd 4:0:0:0: Attached scsi generic sg2 type 0
[ 5938.996000] ipw2200: Failed to send SCAN_ABORT: Command timed out.
[ 5939.496000] ipw2200: Firmware error detected.  Restarting.
[ 5941.200000] ipw2200: Firmware error detected.  Restarting.
[ 5943.092000] ipw2200: Firmware error detected.  Restarting.
[ 5944.104000] ipw2200: Failed to send CARD_DISABLE: Command timed out.
[ 6180.332000] ipw2200: Failed to send SCAN_ABORT: Command timed out.
[ 6180.788000] ipw2200: Firmware error detected.  Restarting.
[ 6301.464000] ipw2200: Failed to send SCAN_ABORT: Command timed out.
[ 6301.908000] ipw2200: Firmware error detected.  Restarting.
[ 6303.336000] ipw2200: Failed to send SSID: Command timed out.
[ 6422.468000] ipw2200: Failed to send SCAN_REQUEST_EXT: Command timed out.
[ 6543.472000] ipw2200: Failed to send SCAN_REQUEST_EXT: Command timed out.
[ 6664.476000] ipw2200: Failed to send SCAN_REQUEST_EXT: Command timed out.
[ 6785.480000] ipw2200: Failed to send SCAN_REQUEST_EXT: Command timed out.
[ 6905.484000] ipw2200: No space for Tx
[ 6905.484000] ipw2200: Failed to send SCAN_REQUEST_EXT: Reason -16
[ 6921.968000] ipw2200: Firmware error detected.  Restarting.
[ 7147.124000] ipw2200: Failed to send SCAN_ABORT: Command timed out.
[ 7147.560000] ipw2200: Firmware error detected.  Restarting.
[ 7508.080000] ipw2200: Firmware error detected.  Restarting.
[ 7628.672000] ipw2200: Firmware error detected.  Restarting.
[ 7990.228000] ipw2200: Failed to send SCAN_ABORT: Command timed out.
[ 7990.700000] ipw2200: Firmware error detected.  Restarting.
[ 7992.500000] ipw2200: Firmware error detected.  Restarting.
[ 7994.300000] ipw2200: Firmware error detected.  Restarting.
[ 7995.308000] ipw2200: Failed to send CARD_DISABLE: Command timed out.
[ 8110.336000] ipw2200: Failed to send SCAN_ABORT: Command timed out.
[ 8110.848000] ipw2200: Firmware error detected.  Restarting.
[ 8112.584000] ipw2200: Firmware error detected.  Restarting.
[ 8114.352000] ipw2200: Firmware error detected.  Restarting.
[ 8115.364000] ipw2200: Failed to send CARD_DISABLE: Command timed out.
[ 8117.316000] ipw2200: Firmware error detected.  Restarting.
[ 8119.116000] ipw2200: Firmware error detected.  Restarting.
[ 8120.916000] ipw2200: Firmware error detected.  Restarting.
[ 8121.924000] ipw2200: Failed to send CARD_DISABLE: Command timed out.
[ 8592.296000] ipw2200: Failed to send SCAN_ABORT: Command timed out.
[ 8592.736000] ipw2200: Firmware error detected.  Restarting.
[ 8712.504000] ipw2200: Firmware error detected.  Restarting.
[ 8712.648000] ipw2200: Firmware error detected.  Restarting.
[ 8714.476000] ipw2200: Firmware error detected.  Restarting.
[ 9074.260000] ipw2200: Failed to send SCAN_ABORT: Command timed out.
[ 9074.716000] ipw2200: Firmware error detected.  Restarting.
[ 9435.108000] ipw2200: Firmware error detected.  Restarting.
[ 9676.536000] ipw2200: Failed to send SCAN_ABORT: Command timed out.
[ 9677.052000] ipw2200: Firmware error detected.  Restarting.
[10038.188000] ipw2200: Failed to send SCAN_ABORT: Command timed out.
[10038.696000] ipw2200: Firmware error detected.  Restarting.
[10040.592000] ipw2200: Firmware error detected.  Restarting.
[10520.148000] ipw2200: Failed to send SCAN_ABORT: Command timed out.
[10520.628000] ipw2200: Firmware error detected.  Restarting.
[10640.476000] ipw2200: Firmware error detected.  Restarting.
[10881.904000] ipw2200: Failed to send SCAN_ABORT: Command timed out.
[10882.388000] ipw2200: Firmware error detected.  Restarting.
[10884.252000] ipw2200: Firmware error detected.  Restarting.
[11123.344000] ipw2200: Failed to send SCAN_ABORT: Command timed out.
[11123.792000] ipw2200: Firmware error detected.  Restarting.
[11185.156000] usb 4-3: new high speed USB device using ehci_hcd and address 7
[11185.292000] usb 4-3: configuration #1 chosen from 1 choice
[11185.292000] scsi5 : SCSI emulation for USB Mass Storage devices
[11185.292000] usb-storage: device found at 7
[11185.292000] usb-storage: waiting for device to settle before scanning
[11190.292000] usb-storage: device scan complete
[11190.292000] scsi 5:0:0:0: Direct-Access     Kingston DataTravelerMini PMAP PQ: 0 ANSI: 0 CCS
[11190.680000] SCSI device sdc: 2015232 512-byte hdwr sectors (1032 MB)
[11190.680000] sdc: Write Protect is off
[11190.680000] sdc: Mode Sense: 23 00 00 00
[11190.680000] sdc: assuming drive cache: write through
[11190.684000] SCSI device sdc: 2015232 512-byte hdwr sectors (1032 MB)
[11190.684000] sdc: Write Protect is off
[11190.684000] sdc: Mode Sense: 23 00 00 00
[11190.684000] sdc: assuming drive cache: write through
[11190.684000]  sdc: sdc1
[11190.684000] sd 5:0:0:0: Attached scsi removable disk sdc
[11190.684000] sd 5:0:0:0: Attached scsi generic sg3 type 0
[11364.788000] ipw2200: Failed to send SCAN_ABORT: Command timed out.
[11365.256000] ipw2200: Firmware error detected.  Restarting.
[11366.988000] ipw2200: Firmware error detected.  Restarting.
[11486.020000] ipw2200: Failed to send SCAN_ABORT: Command timed out.
[11486.444000] ipw2200: Firmware error detected.  Restarting.
[11607.252000] ipw2200: Failed to send SCAN_ABORT: Command timed out.
[11607.724000] ipw2200: Firmware error detected.  Restarting.
[11728.384000] ipw2200: Failed to send SCAN_ABORT: Command timed out.
[11728.872000] ipw2200: Firmware error detected.  Restarting.
[11730.736000] ipw2200: Firmware error detected.  Restarting.
[11804.628000] usb 1-2: USB disconnect, address 3
[11815.924000] usb 4-3: USB disconnect, address 7
[11847.080000] usb 4-1: USB disconnect, address 6
[11847.128000] scsi 4:0:0:0: rejecting I/O to dead device
[11847.128000] scsi 4:0:0:0: rejecting I/O to dead device
[11847.128000] scsi 4:0:0:0: rejecting I/O to dead device
[11847.128000] scsi 4:0:0:0: rejecting I/O to dead device
[11847.128000] sdb : READ CAPACITY failed.
[11847.128000] sdb : status=0, message=00, host=1, driver=00 
[11847.128000] sdb : sense not available. 
[11847.128000] scsi 4:0:0:0: rejecting I/O to dead device
[11847.128000] sdb: Write Protect is off
[11847.128000] sdb: Mode Sense: 00 00 00 00
[11847.128000] sdb: assuming drive cache: write through
[11847.128000] scsi 4:0:0:0: rejecting I/O to dead device
[11847.128000] scsi 4:0:0:0: rejecting I/O to dead device
[11847.128000] scsi 4:0:0:0: rejecting I/O to dead device
[11847.128000] scsi 4:0:0:0: rejecting I/O to dead device
[11847.128000] sdb : READ CAPACITY failed.
[11847.128000] sdb : status=0, message=00, host=1, driver=00 
[11847.128000] sdb : sense not available. 
[11847.128000] scsi 4:0:0:0: rejecting I/O to dead device
[11847.128000] sdb: Write Protect is off
[11847.128000] sdb: Mode Sense: 00 00 00 00
[11847.128000] sdb: assuming drive cache: write through
[11847.296000] scsi 4:0:0:0: rejecting I/O to dead device
[11847.296000] scsi 4:0:0:0: rejecting I/O to dead device
[11847.296000] scsi 4:0:0:0: rejecting I/O to dead device
[11847.296000] scsi 4:0:0:0: rejecting I/O to dead device
[11847.316000] scsi 4:0:0:0: rejecting I/O to dead device
[11847.320000] scsi 4:0:0:0: rejecting I/O to dead device
[11847.320000] scsi 4:0:0:0: rejecting I/O to dead device
[11847.320000] sdb : READ CAPACITY failed.
[11847.320000] sdb : status=0, message=00, host=1, driver=00 
[11847.320000] sdb : sense not available. 
[11847.320000] scsi 4:0:0:0: rejecting I/O to dead device
[11847.320000] sdb: Write Protect is off
[11847.320000] sdb: Mode Sense: 00 00 00 00
[11847.320000] sdb: assuming drive cache: write through
[11847.320000] scsi 4:0:0:0: rejecting I/O to dead device
[11848.580000] ipw2200: Firmware error detected.  Restarting.
[11969.812000] ipw2200: Failed to send SCAN_ABORT: Command timed out.
[11970.308000] ipw2200: Firmware error detected.  Restarting.
[12211.356000] ipw2200: Failed to send SCAN_ABORT: Command timed out.
[12211.832000] ipw2200: Firmware error detected.  Restarting.
[12213.536000] ipw2200: Firmware error detected.  Restarting.
[12215.496000] ipw2200: Firmware error detected.  Restarting.
[12216.504000] ipw2200: Failed to send CARD_DISABLE: Command timed out.
[14079.904000] usb 1-2: new low speed USB device using uhci_hcd and address 4
[14080.132000] usb 1-2: configuration #1 chosen from 1 choice
[14080.148000] input: Genius NetScroll + Traveler as /class/input/input9
[14080.148000] input: USB HID v1.10 Mouse [Genius NetScroll + Traveler] on usb-0000:00:1d.0-2
[14080.424000] usb 1-2: USB disconnect, address 4
[14082.248000] usb 1-1: new low speed USB device using uhci_hcd and address 5
[14082.420000] usb 1-1: configuration #1 chosen from 1 choice
[14082.436000] input: Genius NetScroll + Traveler as /class/input/input10
[14082.436000] input: USB HID v1.10 Mouse [Genius NetScroll + Traveler] on usb-0000:00:1d.0-1
[14255.484000] ipw2200: Failed to send SCAN_ABORT: Command timed out.
[14255.928000] ipw2200: Firmware error detected.  Restarting.
[14375.692000] ipw2200: Firmware error detected.  Restarting.
[14497.028000] ipw2200: Failed to send SCAN_ABORT: Command timed out.
[14497.516000] ipw2200: Firmware error detected.  Restarting.
[14499.316000] ipw2200: Firmware error detected.  Restarting.
[14618.260000] ipw2200: Failed to send SCAN_ABORT: Command timed out.
[14618.736000] ipw2200: Firmware error detected.  Restarting.
[14692.360000] usb 4-2: new high speed USB device using ehci_hcd and address 11
[14692.496000] usb 4-2: configuration #1 chosen from 1 choice
[14692.496000] scsi6 : SCSI emulation for USB Mass Storage devices
[14692.496000] usb-storage: device found at 11
[14692.496000] usb-storage: waiting for device to settle before scanning
[14697.496000] usb-storage: device scan complete
[14697.496000] scsi 6:0:0:0: Direct-Access     Kingston DataTravelerMini PMAP PQ: 0 ANSI: 0 CCS
[14698.260000] SCSI device sdb: 2015232 512-byte hdwr sectors (1032 MB)
[14698.260000] sdb: Write Protect is off
[14698.260000] sdb: Mode Sense: 23 00 00 00
[14698.260000] sdb: assuming drive cache: write through
[14698.264000] SCSI device sdb: 2015232 512-byte hdwr sectors (1032 MB)
[14698.264000] sdb: Write Protect is off
[14698.264000] sdb: Mode Sense: 23 00 00 00
[14698.264000] sdb: assuming drive cache: write through
[14698.264000]  sdb: sdb1
[14698.264000] sd 6:0:0:0: Attached scsi removable disk sdb
[14698.264000] sd 6:0:0:0: Attached scsi generic sg2 type 0
[14719.576000] usb 4-3: new high speed USB device using ehci_hcd and address 12
[14719.708000] usb 4-3: configuration #1 chosen from 2 choices
[14719.708000] scsi7 : SCSI emulation for USB Mass Storage devices
[14719.708000] usb-storage: device found at 12
[14719.708000] usb-storage: waiting for device to settle before scanning
[14724.708000] usb-storage: device scan complete
[14724.712000] scsi 7:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[14724.724000] SCSI device sdc: 1982464 2048-byte hdwr sectors (4060 MB)
[14724.724000] sdc: Write Protect is off
[14724.724000] sdc: Mode Sense: 68 00 00 08
[14724.724000] sdc: assuming drive cache: write through
[14724.732000] SCSI device sdc: 1982464 2048-byte hdwr sectors (4060 MB)
[14724.732000] sdc: Write Protect is off
[14724.732000] sdc: Mode Sense: 68 00 00 08
[14724.732000] sdc: assuming drive cache: write through
[14724.732000]  sdc: sdc1 sdc2
[14724.736000] sd 7:0:0:0: Attached scsi removable disk sdc
[14724.736000] sd 7:0:0:0: Attached scsi generic sg3 type 0
[14979.904000] usb 4-2: USB disconnect, address 11
[14980.000000] ipw2200: Failed to send SCAN_ABORT: Command timed out.
[14980.496000] ipw2200: Firmware error detected.  Restarting.
[14982.356000] ipw2200: Firmware error detected.  Restarting.
[15024.252000] ipw2200: Firmware error detected.  Restarting.
[15101.132000] ipw2200: Failed to send SCAN_ABORT: Command timed out.
[15101.628000] ipw2200: Firmware error detected.  Restarting.
[15342.676000] ipw2200: Failed to send SCAN_ABORT: Command timed out.
[15343.124000] ipw2200: Firmware error detected.  Restarting.
[15346.220000] ipw2200: Failed to send SSID: Command timed out.
[15354.080000] ipw2200: Failed to send SSID: Command timed out.
[15354.080000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[15355.092000] ipw2200: Failed to send SSID: Command timed out.
[15366.092000] ipw2200: Failed to send SSID: Command timed out.
[15369.096000] ipw2200: Failed to send SSID: Command timed out.
[15376.096000] ipw2200: No space for Tx
[15376.096000] ipw2200: Failed to send SSID: Reason -16
[15384.096000] ipw2200: No space for Tx
[15384.096000] ipw2200: Failed to send SSID: Reason -16
[15392.096000] ipw2200: No space for Tx
[15392.096000] ipw2200: Failed to send SSID: Reason -16
[15400.096000] ipw2200: No space for Tx
[15400.096000] ipw2200: Failed to send SSID: Reason -16
[15408.096000] ipw2200: No space for Tx
[15408.096000] ipw2200: Failed to send SSID: Reason -16
[15415.192000] ipw2200: No space for Tx
[15415.192000] ipw2200: Failed to send SSID: Reason -16
[15461.640000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[15461.648000] ipw2200: No space for Tx
[15461.648000] ipw2200: Failed to send SSID: Reason -16
[15481.908000] ipw2200: No space for Tx
[15481.908000] ipw2200: Failed to send SSID: Reason -16
[15602.164000] ipw2200: No space for Tx
[15602.164000] ipw2200: Failed to send SSID: Reason -16
[15722.420000] ipw2200: No space for Tx
[15722.420000] ipw2200: Failed to send SSID: Reason -16
[15842.676000] ipw2200: No space for Tx
[15842.676000] ipw2200: Failed to send SSID: Reason -16
[15962.932000] ipw2200: No space for Tx
[15962.932000] ipw2200: Failed to send SSID: Reason -16
[15963.180000] ipw2200: Firmware error detected.  Restarting.
[15965.748000] ipw2200: Firmware error detected.  Restarting.
[15969.084000] ipw2200: Firmware error detected.  Restarting.
[15971.652000] ipw2200: Firmware error detected.  Restarting.
[15975.244000] ipw2200: Firmware error detected.  Restarting.
[15978.064000] ipw2200: Firmware error detected.  Restarting.
[15980.728000] ipw2200: Firmware error detected.  Restarting.
[15982.464000] ipw2200: Firmware error detected.  Restarting.
[15987.112000] ipw2200: Firmware error detected.  Restarting.
[15991.184000] ipw2200: Firmware error detected.  Restarting.
[15993.080000] ipw2200: Firmware error detected.  Restarting.
[15996.252000] ipw2200: Firmware error detected.  Restarting.
[15998.916000] ipw2200: Firmware error detected.  Restarting.
[16002.188000] ipw2200: Firmware error detected.  Restarting.
[16004.500000] ipw2200: Firmware error detected.  Restarting.
[16007.132000] ipw2200: Firmware error detected.  Restarting.
[16009.572000] ipw2200: Firmware error detected.  Restarting.
[16011.468000] ipw2200: Firmware error detected.  Restarting.
[16013.936000] ipw2200: Firmware error detected.  Restarting.
[16016.120000] ipw2200: Firmware error detected.  Restarting.
[16018.304000] ipw2200: Firmware error detected.  Restarting.
[16020.104000] ipw2200: Firmware error detected.  Restarting.
[16022.724000] ipw2200: Failed to send SCAN_REQUEST_EXT: Command timed out.
[16084.308000] ipw2200: Failed to send SCAN_REQUEST_EXT: Command timed out.
[16205.312000] ipw2200: Failed to send SCAN_REQUEST_EXT: Command timed out.
[16326.316000] ipw2200: Failed to send SCAN_REQUEST_EXT: Command timed out.
[16447.320000] ipw2200: Failed to send SCAN_REQUEST_EXT: Command timed out.
[16567.324000] ipw2200: No space for Tx
[16567.324000] ipw2200: Failed to send SCAN_REQUEST_EXT: Reason -16
[16640.164000] ipw2200: Firmware error detected.  Restarting.
[16642.088000] ipw2200: Firmware error detected.  Restarting.
[16645.008000] ipw2200: Firmware error detected.  Restarting.
[16647.608000] ipw2200: Firmware error detected.  Restarting.
[16655.648000] ipw2200: Firmware error detected.  Restarting.
[16660.168000] ipw2200: Firmware error detected.  Restarting.
[16662.000000] ipw2200: Firmware error detected.  Restarting.
[16663.892000] ipw2200: Firmware error detected.  Restarting.
[16664.904000] ipw2200: Failed to send CARD_DISABLE: Command timed out.
[16668.904000] ipw2200: Firmware error detected.  Restarting.
[16671.792000] ipw2200: Firmware error detected.  Restarting.
[16674.612000] ipw2200: Firmware error detected.  Restarting.
[16678.172000] ipw2200: Firmware error detected.  Restarting.
[16682.596000] ipw2200: Firmware error detected.  Restarting.
[16685.260000] ipw2200: Firmware error detected.  Restarting.
[16687.156000] ipw2200: Firmware error detected.  Restarting.
[16691.548000] ipw2200: Firmware error detected.  Restarting.
[16693.284000] ipw2200: Firmware error detected.  Restarting.
[16696.232000] ipw2200: Firmware error detected.  Restarting.
[16698.512000] ipw2200: Firmware error detected.  Restarting.
[16702.488000] ipw2200: Firmware error detected.  Restarting.
[16708.992000] ipw2200: Firmware error detected.  Restarting.
[16714.120000] ipw2200: Firmware error detected.  Restarting.
[16716.748000] ipw2200: Firmware error detected.  Restarting.
[16718.452000] ipw2200: Firmware error detected.  Restarting.
[16723.260000] ipw2200: Firmware error detected.  Restarting.
[16725.412000] ipw2200: Firmware error detected.  Restarting.
[16727.564000] ipw2200: Firmware error detected.  Restarting.
[16729.364000] ipw2200: Firmware error detected.  Restarting.
[16735.516000] ipw2200: Firmware error detected.  Restarting.
[16738.304000] ipw2200: Firmware error detected.  Restarting.
[16739.832000] ipw2200: Failed to send SCAN_REQUEST_EXT: Command timed out.
[16808.836000] ipw2200: Failed to send SCAN_REQUEST_EXT: Command timed out.
[16929.840000] ipw2200: Failed to send SCAN_REQUEST_EXT: Command timed out.
[17050.844000] ipw2200: Failed to send SCAN_REQUEST_EXT: Command timed out.
[17171.848000] ipw2200: Failed to send SCAN_REQUEST_EXT: Command timed out.
[17291.852000] ipw2200: No space for Tx
[17291.852000] ipw2200: Failed to send SCAN_REQUEST_EXT: Reason -16
[17358.364000] ipw2200: Firmware error detected.  Restarting.
[17360.804000] ipw2200: Firmware error detected.  Restarting.
[17364.076000] ipw2200: Firmware error detected.  Restarting.
[17366.516000] ipw2200: Firmware error detected.  Restarting.
[17370.424000] ipw2200: Firmware error detected.  Restarting.
[17372.960000] ipw2200: Firmware error detected.  Restarting.
[17374.888000] ipw2200: Firmware error detected.  Restarting.
[17376.688000] ipw2200: Firmware error detected.  Restarting.
[17377.696000] ipw2200: Failed to send CARD_DISABLE: Command timed out.
[17381.184000] ipw2200: Firmware error detected.  Restarting.
[17386.056000] ipw2200: Firmware error detected.  Restarting.
[17391.052000] ipw2200: Firmware error detected.  Restarting.
[17393.908000] ipw2200: Firmware error detected.  Restarting.
[17400.380000] ipw2200: Firmware error detected.  Restarting.
[17402.436000] ipw2200: Firmware error detected.  Restarting.
[17404.268000] ipw2200: Firmware error detected.  Restarting.
[17409.300000] ipw2200: Firmware error detected.  Restarting.
[17411.928000] ipw2200: Firmware error detected.  Restarting.
[17415.264000] ipw2200: Firmware error detected.  Restarting.
[17418.440000] ipw2200: Firmware error detected.  Restarting.
[17421.136000] ipw2200: Firmware error detected.  Restarting.
[17423.320000] ipw2200: Firmware error detected.  Restarting.
[17425.056000] ipw2200: Firmware error detected.  Restarting.
[17427.240000] ipw2200: Firmware error detected.  Restarting.
[17429.324000] ipw2200: Firmware error detected.  Restarting.
[17431.956000] ipw2200: Firmware error detected.  Restarting.
[17434.364000] ipw2200: Firmware error detected.  Restarting.
[17439.780000] ipw2200: Firmware error detected.  Restarting.
[17442.028000] ipw2200: Failed to send SSID: Command timed out.
[17533.364000] ipw2200: Failed to send SSID: Command timed out.
[17654.368000] ipw2200: Failed to send SSID: Command timed out.
[17775.372000] ipw2200: Failed to send SSID: Command timed out.
[17896.376000] ipw2200: Failed to send SSID: Command timed out.
[18016.380000] ipw2200: No space for Tx
[18016.380000] ipw2200: Failed to send SSID: Reason -16
[18059.840000] ipw2200: Firmware error detected.  Restarting.
[18063.748000] ipw2200: Firmware error detected.  Restarting.
[18066.988000] ipw2200: Firmware error detected.  Restarting.
[18073.620000] ipw2200: Firmware error detected.  Restarting.
[18079.324000] ipw2200: Firmware error detected.  Restarting.
[18082.180000] ipw2200: Firmware error detected.  Restarting.
[18085.004000] ipw2200: Firmware error detected.  Restarting.
[18088.976000] ipw2200: Firmware error detected.  Restarting.
[18091.256000] ipw2200: Firmware error detected.  Restarting.
[18093.728000] ipw2200: Firmware error detected.  Restarting.
[18099.176000] ipw2200: Firmware error detected.  Restarting.
[18102.896000] ipw2200: Failed to send SSID: Command timed out.
[18137.636000] ipw2200: Failed to send SSID: Command timed out.
[18258.640000] ipw2200: Failed to send SSID: Command timed out.
[18379.644000] ipw2200: Failed to send SSID: Command timed out.
[18500.648000] ipw2200: Failed to send SSID: Command timed out.
[18620.652000] ipw2200: No space for Tx
[18620.652000] ipw2200: Failed to send SSID: Reason -16
[18719.232000] ipw2200: Firmware error detected.  Restarting.
[18722.184000] ipw2200: Firmware error detected.  Restarting.
[18724.624000] ipw2200: Firmware error detected.  Restarting.
[18727.480000] ipw2200: Firmware error detected.  Restarting.
[18731.136000] ipw2200: Firmware error detected.  Restarting.
[18735.112000] ipw2200: Firmware error detected.  Restarting.
[18737.008000] ipw2200: Firmware error detected.  Restarting.
[18739.636000] ipw2200: Firmware error detected.  Restarting.
[18743.724000] ipw2200: Failed to send SCAN_REQUEST_EXT: Command timed out.
[18862.164000] ipw2200: Failed to send SCAN_REQUEST_EXT: Command timed out.
[18983.168000] ipw2200: Failed to send SCAN_REQUEST_EXT: Command timed out.
[19104.172000] ipw2200: Failed to send SCAN_REQUEST_EXT: Command timed out.
```

---

