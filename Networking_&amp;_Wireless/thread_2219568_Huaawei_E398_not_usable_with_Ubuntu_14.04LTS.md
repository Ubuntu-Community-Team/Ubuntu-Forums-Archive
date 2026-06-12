---
title: "Huaawei E398 not usable with Ubuntu 14.04LTS"
date: 2014-04-24
forum: Networking &amp; Wireless
---

### Post by strsljen on 2014-04-24
Hi!

Huawei mobile internet adapter that works properly on my old laptop (Ubuntu 12.04LTS) is not being properly initialized on my new laptop (Lenovo L540) with Ubuntu 14.04LTS.

lsusb -v states:
```
Bus 003 Device 006: ID 12d1:1505 Huawei Technologies Co., Ltd. E398 LTE/UMTS/GSM Modem/Networkcard
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x12d1 Huawei Technologies Co., Ltd.
  idProduct          0x1505 E398 LTE/UMTS/GSM Modem/Networkcard
  bcdDevice            0.00
  iManufacturer           3 Huawei Technologies
  iProduct                2 HUAWEI Mobile
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          1 Huawei Configuration
    bmAttributes         0xc0
      Self Powered
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      6 SCSI
      bInterfaceProtocol     80 Bulk-Only
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0000
  (Bus Powered)

```


When inserted, I see in dmesg:
```
[ 3450.255431] usb 3-3: new high-speed USB device number 6 using xhci_hcd
[ 3450.275221] usb 3-3: New USB device found, idVendor=12d1, idProduct=1505
[ 3450.275231] usb 3-3: New USB device strings: Mfr=3, Product=2, SerialNumber=0
[ 3450.275236] usb 3-3: Product: HUAWEI Mobile
[ 3450.275240] usb 3-3: Manufacturer: Huawei Technologies
[ 3450.276838] usb-storage 3-3:1.0: USB Mass Storage device detected
[ 3450.277019] scsi6 : usb-storage 3-3:1.0
[ 3451.277690] scsi 6:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 0
[ 3451.309639] sr0: scsi-1 drive
[ 3451.309644] cdrom: Uniform CD-ROM driver Revision: 3.20
[ 3451.309755] sr 6:0:0:0: Attached scsi CD-ROM sr0
[ 3451.309828] sr 6:0:0:0: Attached scsi generic sg1 type 5
[ 3451.332436] scsi 6:0:0:0: rejecting I/O to offline device
[ 3451.332442] scsi 6:0:0:0: killing request
[ 3451.345965] systemd-udevd[10054]: Failed to apply ACL on /dev/sr0: No such file or directory
[ 3451.345973] systemd-udevd[10054]: Failed to apply ACL on /dev/sr0: No such file or directory
[ 3451.348308] systemd-udevd[10036]: Failed to apply ACL on /dev/sr0: No such file or directory
[ 3451.348314] systemd-udevd[10036]: Failed to apply ACL on /dev/sr0: No such file or directory
[ 4746.201877] ACPI: \_SB_.PCI0: Bus check notify on hotplug_event_root
[ 4746.584117] ACPI: \_SB_.PCI0: Bus check notify on hotplug_event_root
[ 4747.247789] ACPI: \_SB_.PCI0: Bus check notify on hotplug_event_root
[ 4747.664123] usb 3-3: USB disconnect, device number 6
[ 8096.196710] ACPI: \_SB_.PCI0: Bus check notify on hotplug_event_root
[ 8554.293489] ACPI: \_SB_.PCI0: Bus check notify on hotplug_event_root
[ 9223.057183] ACPI: \_SB_.PCI0: Bus check notify on hotplug_event_root
[ 9873.431084] usb 3-3: new high-speed USB device number 7 using xhci_hcd
[ 9873.450263] usb 3-3: New USB device found, idVendor=12d1, idProduct=1505
[ 9873.450277] usb 3-3: New USB device strings: Mfr=3, Product=2, SerialNumber=0
[ 9873.450285] usb 3-3: Product: HUAWEI Mobile
[ 9873.450291] usb 3-3: Manufacturer: Huawei Technologies
[ 9873.451877] usb-storage 3-3:1.0: USB Mass Storage device detected
[ 9873.452026] scsi7 : usb-storage 3-3:1.0
[ 9874.453546] scsi 7:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 0
[ 9874.493434] sr0: scsi-1 drive
[ 9874.493536] sr 7:0:0:0: Attached scsi CD-ROM sr0
[ 9874.493592] sr 7:0:0:0: Attached scsi generic sg1 type 5
[ 9874.516429] systemd-udevd[10548]: Failed to apply ACL on /dev/sr0: No such file or directory
[ 9874.516437] systemd-udevd[10548]: Failed to apply ACL on /dev/sr0: No such file or directory
[ 9874.519822] systemd-udevd[10526]: Failed to apply ACL on /dev/sr0: No such file or directory
[ 9874.519830] systemd-udevd[10526]: Failed to apply ACL on /dev/sr0: No such file or directory

```

And that's about it. No initialization for mobile internet, nothing relevant in network listing...

How to correctly use this adapter with Ubuntu 14.04LTS?

Any help is more than welcomed.

Best regards,

--
Strs.

---

### Post by strsljen on 2014-04-24
UPDATE: on my old laptop (HP EliteBook 6930p), the same Huawei USB adapter works properly.

When inserted, dmesg shows:
```
[54180.300087] usb 2-1: new high-speed USB device number 3 using ehci_hcd
[54180.434644] usb 2-1: New USB device found, idVendor=12d1, idProduct=1505
[54180.434655] usb 2-1: New USB device strings: Mfr=3, Product=2, SerialNumber=0
[54180.434662] usb 2-1: Product: HUAWEI Mobile
[54180.434668] usb 2-1: Manufacturer: Huawei Technologies
[54180.436794] scsi10 : usb-storage 2-1:1.0
[54181.437483] scsi 10:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 0
[54181.450448] sr1: scsi-1 drive
[54181.451223] sr 10:0:0:0: Attached scsi CD-ROM sr1
[54181.454941] sr 10:0:0:0: Attached scsi generic sg2 type 5
[54181.859194] usb 2-1: USB disconnect, device number 3
[54193.196094] usb 2-1: new high-speed USB device number 4 using ehci_hcd
[54193.330885] usb 2-1: New USB device found, idVendor=12d1, idProduct=1506
[54193.330896] usb 2-1: New USB device strings: Mfr=4, Product=3, SerialNumber=0
[54193.330903] usb 2-1: Product: HUAWEI Mobile
[54193.330909] usb 2-1: Manufacturer: Huawei Technologies
[54193.335997] scsi11 : usb-storage 2-1:1.5
[54193.336668] scsi12 : usb-storage 2-1:1.6
[54193.376762] usbcore: registered new interface driver usbserial
[54193.377356] usbcore: registered new interface driver usbserial_generic
[54193.377422] USB Serial support registered for generic
[54193.377443] usbserial: USB Serial Driver core
[54193.381145] cdc_wdm 2-1:1.3: Ignoring extra header, type 15, length 13
[54193.381156] cdc_wdm 2-1:1.3: Ignoring extra header, type 6, length 5
[54193.382595] cdc_wdm 2-1:1.3: cdc-wdm0: USB WDM device
[54193.385648] usbcore: registered new interface driver cdc_wdm
[54193.388400] usbcore: registered new interface driver option
[54193.392494] USB Serial support registered for GSM modem (1-port)
[54193.393371] option 2-1:1.0: GSM modem (1-port) converter detected
[54193.397663] usb 2-1: GSM modem (1-port) converter now attached to ttyUSB0
[54193.397738] option 2-1:1.1: GSM modem (1-port) converter detected
[54193.398392] usb 2-1: GSM modem (1-port) converter now attached to ttyUSB1
[54193.398655] option 2-1:1.2: GSM modem (1-port) converter detected
[54193.399021] usb 2-1: GSM modem (1-port) converter now attached to ttyUSB2
[54193.406598] qmi_wwan 2-1:1.4: Use "cdc_wdm" for QMI interface 2-1:1.3
[54193.408858] qmi_wwan 2-1:1.4: wwan0: register 'qmi_wwan' at usb-0000:00:1d.7-1, QMI speaking wwan device, 00:a0:c6:00:00:00
[54193.409291] usbcore: registered new interface driver qmi_wwan
[54194.340464] scsi 11:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 0
[54194.340561] scsi 12:0:0:0: Direct-Access     HUAWEI   SD Storage       2.31 PQ: 0 ANSI: 2
[54194.361944] sr1: scsi-1 drive
[54194.365933] sr 11:0:0:0: Attached scsi CD-ROM sr1
[54194.367873] sr 11:0:0:0: Attached scsi generic sg2 type 5
[54194.370487] sd 12:0:0:0: Attached scsi generic sg3 type 0
[54194.374173] sd 12:0:0:0: [sdb] Attached SCSI removable disk
[54196.870028] ISO 9660 Extensions: Microsoft Joliet Level 1
[54196.871905] ISOFS: changing to secondary root

```

Then the mobile network is shown in Network tab in Unity (upper right corner in tray) and can be used.

lsusb -v  shows:
```
Bus 006 Device 002: ID 12d1:1506 Huawei Technologies Co., Ltd. E398 LTE/UMTS/GSM Modem/Networkcard
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x12d1 Huawei Technologies Co., Ltd.
  idProduct          0x1506 E398 LTE/UMTS/GSM Modem/Networkcard
  bcdDevice            0.00
  iManufacturer           4 
  iProduct                3 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength          193
    bNumInterfaces          7
    bConfigurationValue     1
    iConfiguration          2 
    bmAttributes         0xc0
      Self Powered
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           3
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      1 
      bInterfaceProtocol      1 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               5
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval              32
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval              32
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      1 
      bInterfaceProtocol      2 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval              32
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval              32
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        2
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      1 
      bInterfaceProtocol      3 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval              32
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval              32
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        3
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      1 
      bInterfaceProtocol      9 
      iInterface              0 
      ** UNRECOGNIZED:  05 24 00 10 01
      ** UNRECOGNIZED:  0d 24 0f 01 00 00 00 00 08 06 01 00 00
      ** UNRECOGNIZED:  05 24 06 03 04
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x85  EP 5 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               5
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        4
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      1 
      bInterfaceProtocol      8 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x86  EP 6 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval              32
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x04  EP 4 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval              32
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        5
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      6 SCSI
      bInterfaceProtocol     80 Bulk-Only
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x87  EP 7 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x05  EP 5 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        6
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      6 SCSI
      bInterfaceProtocol     80 Bulk-Only
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x06  EP 6 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x88  EP 8 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0

```

Now, I'm quite positive I never installed any driver on Ubuntu 12.04LTS in order for Huawei to work.

Still, on 14.04LTS it doesn't ge properly initialized, while on 12.04LTS it works like a charm.

---

### Post by strsljen on 2014-04-25
Hi!

Another update: it seems Ubuntu 14.04 implemented systemd-udevd. According to some info I managed to find, ACL should not be set when systemd-udevd is used.

In my case, systemd-udevd can't make /dev/sr0 device. Then it stops. 
This Huawei device also provides virtual CD (fir driver installation on windows). Ubuntu gets stuck on it and it doesn't go any further.
 
I can't exactly find how to fix it.

---

### Post by jacek6 on 2014-09-23
Hi,

I seem to have same problem, did you manage to find a solution for this?

---

### Post by ccooi on 2014-11-30
I got the similar problem solved.
Try to manually switch the usb mode twice; by running the following commands two times sudo usb_modeswitch -v <vendorID> -p <productID> -c /etc/usb_modeswitch.d/<new config file specifying target IDs>.  E.g. sudo usb_modeswitch -v 0x19d2 -p 0x2000 -c /etc/usb_modeswitch.d/19d2\:2000
Example contents of config file:
# ZTE MF190 (Variant) and others


TargetVendor=  0x19d2
TargetProductList="0017,0117"


MessageContent="5553424312345678000000000000061e000000000000000000000000000000"
MessageContent2="5553424312345679000000000000061b000000020000000000000000000000"
NeedResponse=1

Once it works, you can automate the process during reboot.
You might want to check if the driver/module is loaded via the following command:
 lsmod | grep option

---

### Post by 0-tobias on 2015-10-15
If someone still faces similiar problems: I made a .deb package with modified udev rules that at least for me works perfectly (Ubuntu 14.04,14.10 and 15.0 tested)

[http://www.die-schrages.de/tobias/blog/en/2015/10/14/t-mobile-lte-stick-huawei-e-398/](http://www.die-schrages.de/tobias/blog/en/2015/10/14/t-mobile-lte-stick-huawei-e-398/)

---

