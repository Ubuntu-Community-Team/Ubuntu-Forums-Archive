---
title: "Huawei 3G stick not changing to modem mode"
date: 2014-10-28
forum: Networking &amp; Wireless
---

### Post by Alex22 on 2014-10-28
Hi Guys,

When turning on my laptop (hp ProBook 4540s) my 3G modem (Huawei E1750) stays in storage mode:
12d1:1446

Only after replugging (mostly one time is sufficient) it is being morphed into: 
```
Bus 003 Device 005: ID 12d1:1001 Huawei Technologies Co., Ltd. E169/E620/E800 HSDPA Modem
```

This is not only annoying but i am afraid that finally i will destroy the stick/usb socket. 
The same behaviour across all usb sockets.

**Kindly help to solve - but a software command emulating replugging would be highly appreciated as well!**


----------------------------


Ubuntu version:
Ubuntu 14.04.1
Linux mach-name 3.13.0-37-generic #64-Ubuntu SMP Mon Sep 22 21:28:38 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Bad behaviour log (on pc startup):
```
[    3.581206] usb 1-1.3: SerialNumber: PMX02
[    4.209065] Switched to clocksource tsc
[    4.212908] usb 3-3: new high-speed USB device number 3 using xhci_hcd
[    4.231207] usb 3-3: New USB device found, idVendor=12d1, idProduct=1446
[    4.231213] usb 3-3: New USB device strings: Mfr=3, Product=2, SerialNumber=0
[    4.231216] usb 3-3: Product: HUAWEI Mobile
[    4.231219] usb 3-3: Manufacturer: HUAWEI Technology
[    4.403241] random: nonblocking pool is initialized
```

Good behaviour log (on replugging event):
```

[   67.015816] [drm] Disabling audio 0 support
[  109.754536] usb 3-3: USB disconnect, device number 3
[  119.482960] usb 3-3: new high-speed USB device number 4 using xhci_hcd
[  119.501750] usb 3-3: New USB device found, idVendor=12d1, idProduct=1446
[  119.501757] usb 3-3: New USB device strings: Mfr=3, Product=2, SerialNumber=0
[  119.501761] usb 3-3: Product: HUAWEI Mobile
[  119.501764] usb 3-3: Manufacturer: HUAWEI Technology
[  119.503801] usb-storage 3-3:1.0: USB Mass Storage device detected
[  119.503947] scsi8 : usb-storage 3-3:1.0
[  119.504115] usb-storage 3-3:1.1: USB Mass Storage device detected
[  119.504191] scsi9 : usb-storage 3-3:1.1
[  120.505543] scsi 8:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
[  120.506073] scsi 9:0:0:0: Direct-Access     HUAWEI   SD Storage       2.31 PQ: 0 ANSI: 2
[  120.508150] sr1: scsi-1 drive
[  120.508400] sr 8:0:0:0: Attached scsi CD-ROM sr1
[  120.508563] sr 8:0:0:0: Attached scsi generic sg2 type 5
[  120.508917] sd 9:0:0:0: Attached scsi generic sg3 type 0
[  120.511743] sd 9:0:0:0: [sdb] Attached SCSI removable disk
[  120.565318] usb 3-3: USB disconnect, device number 4
[  120.566407] systemd-udevd[2768]: Failed to apply ACL on /dev/sr1: No such file or directory
[  120.566419] systemd-udevd[2768]: Failed to apply ACL on /dev/sr1: No such file or directory
[  124.603232] usb 3-3: new high-speed USB device number 5 using xhci_hcd
[  124.621517] usb 3-3: New USB device found, idVendor=12d1, idProduct=1001
[  124.621522] usb 3-3: New USB device strings: Mfr=3, Product=2, SerialNumber=0
[  124.621525] usb 3-3: Product: HUAWEI Mobile
[  124.621528] usb 3-3: Manufacturer: HUAWEI Technology
[  124.623680] usb-storage 3-3:1.0: USB Mass Storage device detected
[  124.623813] usb-storage 3-3:1.1: USB Mass Storage device detected
[  124.623926] usb-storage 3-3:1.2: USB Mass Storage device detected
[  124.624052] usb-storage 3-3:1.3: USB Mass Storage device detected
[  124.624503] scsi13 : usb-storage 3-3:1.3
[  124.624611] usb-storage 3-3:1.4: USB Mass Storage device detected
[  124.624909] scsi14 : usb-storage 3-3:1.4
[  124.677332] usbcore: registered new interface driver usbserial
[  124.677346] usbcore: registered new interface driver usbserial_generic
[  124.677358] usbserial: USB Serial support registered for generic
[  124.723294] usbcore: registered new interface driver option
[  124.723594] usbserial: USB Serial support registered for GSM modem (1-port)
[  124.723951] option 3-3:1.0: GSM modem (1-port) converter detected
[  124.724397] usb 3-3: GSM modem (1-port) converter now attached to ttyUSB0
[  124.724418] option 3-3:1.1: GSM modem (1-port) converter detected
[  124.724848] usb 3-3: GSM modem (1-port) converter now attached to ttyUSB1
[  124.724865] option 3-3:1.2: GSM modem (1-port) converter detected
[  124.725104] usb 3-3: GSM modem (1-port) converter now attached to ttyUSB2
[  125.625650] scsi 13:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
[  125.626336] scsi 14:0:0:0: Direct-Access     HUAWEI   SD Storage       2.31 PQ: 0 ANSI: 2
[  125.629105] sr1: scsi-1 drive
[  125.629307] sr 13:0:0:0: Attached scsi CD-ROM sr1
[  125.629435] sr 13:0:0:0: Attached scsi generic sg2 type 5
[  125.634669] sd 14:0:0:0: Attached scsi generic sg3 type 0
[  125.638760] sd 14:0:0:0: [sdb] Attached SCSI removable disk
[  311.049610] PPP BSD Compression module registered

```

---

### Post by Alex22 on 2014-10-30
Tried to software'ly replug the whole usb3 bus from pci

```

echo "00:1a.0" | sudo tee /sys/bus/pci/drivers/xhci_hcd/unbind
echo "00:1a.0" | sudo tee /sys/bus/pci/drivers/xhci_hcd/bind

```

but the stick returns as 1446 (storage)

---

### Post by Alex22 on 2015-01-04
Another method found here:
[https://wiki.archlinux.org/index.php/udev](https://wiki.archlinux.org/index.php/udev)

```

# udevadm trigger -v -t subsystems -c remove -s usb -a "idVendor=abcd"

```
*"This command will trigger a USB remove event on all USB devices with vendor ID abcd."*

It didn't take any effects (and no track in system log)

---

