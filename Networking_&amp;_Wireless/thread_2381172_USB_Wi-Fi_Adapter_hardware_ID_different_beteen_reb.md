---
title: "USB Wi-Fi Adapter hardware ID different beteen reboot and unplug/replug"
date: 2017-12-27
forum: Networking &amp; Wireless
---

### Post by constantinoflouras on 2017-12-27
Hi all,

I'm having an issue with my Linksys AE1200 802.11bgn Wireless Adapter, or the Broadcom BCM43235, on my Ubuntu 16.04 LTS (i386) install. During the install, the Ubuntu Installer recognized my wireless adapter, and allowed me to connect to a Wi-Fi network during the installation without an issue. However, upon first boot, Ubuntu did not find the USB wireless adapter driver. After running lsusb, I get the following output:

> Bus 001 Device 004: ID 13b1:0bdc Linksys 
Bus 001 Device 003: ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 413c:3200 Dell Computer Corp. Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

However, if I unplug and replug the USB wireless adapter, it successfully works, and I am able to connect to a Wi-Fi network without an issue. Running lsusb again gives me the following output:

> Bus 001 Device 003: ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer
Bus 001 Device 005: ID 13b1:0039 Linksys AE1200 802.11bgn Wireless Adapter [Broadcom BCM43235]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 413c:3200 Dell Computer Corp. Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

While this works for the time being, I must unplug/replug upon every reboot. Otherwise, I am back to the other device ID and no connection.

I'm not sure why the device IDs would be different-- coming from a Windows background, I imagine this is why Ubuntu is struggling to find a device driver. Does anyone have any suggestions to resolve this issue? Thanks in advance.

EDIT: Ran some other commands to get some more insight....

grep | usbcore
> [    0.355083] usbcore: registered new interface driver usbfs
[    0.355114] usbcore: registered new interface driver hub
[    0.355165] usbcore: registered new device driver usb
[    4.478206] usbcore: registered new interface driver usbhid
[    4.884329] usbcore: registered new interface driver usb-storage
[    4.895298] usbcore: registered new interface driver uas

grep | usb
> [    0.355083] usbcore: registered new interface driver usbfs
[    0.355114] usbcore: registered new interface driver hub
[    0.355165] usbcore: registered new device driver usb
[    3.186869] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    3.186873] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    3.186876] usb usb1: Product: EHCI Host Controller
[    3.186880] usb usb1: Manufacturer: Linux 4.10.0-28-generic ehci_hcd
[    3.186883] usb usb1: SerialNumber: 0000:00:02.1
[    3.248824] usb usb2: New USB device found, idVendor=1d6b, idProduct=0001
[    3.248828] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    3.248831] usb usb2: Product: OHCI PCI host controller
[    3.248835] usb usb2: Manufacturer: Linux 4.10.0-28-generic ohci_hcd
[    3.248838] usb usb2: SerialNumber: 0000:00:02.0
[    3.522515] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    3.681891] usb 1-1: New USB device found, idVendor=13b1, idProduct=0bdc
[    3.681897] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    3.681901] usb 1-1: Product: Linksys AE1200
[    3.681905] usb 1-1: Manufacturer: Cisco
[    3.681908] usb 1-1: SerialNumber: 43235
[    4.203903] usb 2-3: new low-speed USB device number 2 using ohci-pci
[    4.433793] usb 2-3: New USB device found, idVendor=413c, idProduct=3200
[    4.433800] usb 2-3: New USB device strings: Mfr=2, Product=1, SerialNumber=0
[    4.433805] usb 2-3: Product: Dell USB Mouse
[    4.433808] usb 2-3: Manufacturer: Dell
[    4.478206] usbcore: registered new interface driver usbhid
[    4.478207] usbhid: USB HID core driver
[    4.488843] input: Dell Dell USB Mouse as /devices/pci0000:00/0000:00:02.0/usb2/2-3/2-3:1.0/0003:413C:3200.0001/input/input3
[    4.489128] hid-generic 0003:413C:3200.0001: input,hidraw0: USB HID v1.10 Mouse [Dell Dell USB Mouse] on usb-0000:00:02.0-3/input0
[    4.563762] usb 1-5: new high-speed USB device number 4 using ehci-pci
[    4.717270] usb 1-5: New USB device found, idVendor=058f, idProduct=6362
[    4.717277] usb 1-5: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    4.717281] usb 1-5: Product: Mass Storage Device
[    4.717285] usb 1-5: Manufacturer: Generic
[    4.717288] usb 1-5: SerialNumber: 058F312D81B
[    4.883863] usb-storage 1-5:1.0: USB Mass Storage device detected
[    4.884107] scsi host4: usb-storage 1-5:1.0
[    4.884329] usbcore: registered new interface driver usb-storage
[    4.895298] usbcore: registered new interface driver uas
[   20.566268] audit: type=1400 audit(1514412647.685:11): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/ippusbxd" pid=501 comm="apparmor_parser"


dmesg | grep -i usb
> [    0.355029] ACPI: bus type USB registered
[    0.355083] usbcore: registered new interface driver usbfs
[    0.355114] usbcore: registered new interface driver hub
[    0.355165] usbcore: registered new device driver usb
[    3.173615] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    3.173989] ehci-pci 0000:00:02.1: new USB bus registered, assigned bus number 1
[    3.186766] ehci-pci 0000:00:02.1: USB 2.0 started, EHCI 1.00
[    3.186869] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    3.186873] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    3.186876] usb usb1: Product: EHCI Host Controller
[    3.186880] usb usb1: Manufacturer: Linux 4.10.0-28-generic ehci_hcd
[    3.186883] usb usb1: SerialNumber: 0000:00:02.1
[    3.187199] hub 1-0:1.0: USB hub found
[    3.187777] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    3.188028] ohci-pci 0000:00:02.0: new USB bus registered, assigned bus number 2
[    3.248824] usb usb2: New USB device found, idVendor=1d6b, idProduct=0001
[    3.248828] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    3.248831] usb usb2: Product: OHCI PCI host controller
[    3.248835] usb usb2: Manufacturer: Linux 4.10.0-28-generic ohci_hcd
[    3.248838] usb usb2: SerialNumber: 0000:00:02.0
[    3.249169] hub 2-0:1.0: USB hub found
[    3.249703] uhci_hcd: USB Universal Host Controller Interface driver
[    3.522515] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    3.681891] usb 1-1: New USB device found, idVendor=13b1, idProduct=0bdc
[    3.681897] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    3.681901] usb 1-1: Product: Linksys AE1200
[    3.681905] usb 1-1: Manufacturer: Cisco
[    3.681908] usb 1-1: SerialNumber: 43235
[    4.203903] usb 2-3: new low-speed USB device number 2 using ohci-pci
[    4.433793] usb 2-3: New USB device found, idVendor=413c, idProduct=3200
[    4.433800] usb 2-3: New USB device strings: Mfr=2, Product=1, SerialNumber=0
[    4.433805] usb 2-3: Product: Dell USB Mouse
[    4.433808] usb 2-3: Manufacturer: Dell
[    4.478206] usbcore: registered new interface driver usbhid
[    4.478207] usbhid: USB HID core driver
[    4.488843] input: Dell Dell USB Mouse as /devices/pci0000:00/0000:00:02.0/usb2/2-3/2-3:1.0/0003:413C:3200.0001/input/input3
[    4.489128] hid-generic 0003:413C:3200.0001: input,hidraw0: USB HID v1.10 Mouse [Dell Dell USB Mouse] on usb-0000:00:02.0-3/input0
[    4.563762] usb 1-5: new high-speed USB device number 4 using ehci-pci
[    4.717270] usb 1-5: New USB device found, idVendor=058f, idProduct=6362
[    4.717277] usb 1-5: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    4.717281] usb 1-5: Product: Mass Storage Device
[    4.717285] usb 1-5: Manufacturer: Generic
[    4.717288] usb 1-5: SerialNumber: 058F312D81B
[    4.883863] usb-storage 1-5:1.0: USB Mass Storage device detected
[    4.884107] scsi host4: usb-storage 1-5:1.0
[    4.884329] usbcore: registered new interface driver usb-storage
[    4.895298] usbcore: registered new interface driver uas
[    5.899808] scsi 4:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
[    5.900562] scsi 4:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
[    5.901281] scsi 4:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
[    5.901905] scsi 4:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
[   20.566268] audit: type=1400 audit(1514412647.685:11): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/ippusbxd" pid=501 comm="apparmor_parser"


---

### Post by praseodym on 2017-12-27
Hi,

I haven't seen this behaviour before, Search engine with "G" only finds this thread

[https://www.google.de/search?client=ubuntu&hs=oqh&channel=fs&dcr=0&ei=tiJEWtXLONLdwAK-k4jAAQ&q=%2213b1%3A0bdc%22+Linksys&oq=%2213b1%3A0bdc%22+Linksys&gs_l=psy-ab.12...16572.19530.0.20858.2.2.0.0.0.0.102.194.1j1.2.0....0...1c.1.64.psy-ab..0.0.0....0.nu6qly8__eE](https://www.google.de/search?client=ubuntu&hs=oqh&channel=fs&dcr=0&ei=tiJEWtXLONLdwAK-k4jAAQ&q=%2213b1%3A0bdc%22+Linksys&oq=%2213b1%3A0bdc%22+Linksys&gs_l=psy-ab.12...16572.19530.0.20858.2.2.0.0.0.0.102.194.1j1.2.0....0...1c.1.64.psy-ab..0.0.0....0.nu6qly8__eE)

The device ID is unknown. Please show for the first output
```

usb-devices
lsmod
```

---

