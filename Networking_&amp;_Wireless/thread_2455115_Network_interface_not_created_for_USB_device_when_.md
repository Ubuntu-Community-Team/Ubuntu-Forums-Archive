---
title: "Network interface not created for USB device when trying to tether phone"
date: 2020-12-12
forum: Networking &amp; Wireless
---

### Post by jbhtexas on 2020-12-12
Hello!

I am running Ubuntu 16.04.7 LTS and having difficulty tethering my LG G7 ThinQ running Android 9 to use the phone's Interent connection.  Tethering this phone works fine with various Windows 10 computers, so I don't think there are any problems on the phone side.

When I plug in the phone and turn on USB tethering, a USB device is created that appears to be an RNDIS network adapter.  From "sudo lsusb -v":

```
Bus 003 Device 032: ID 1004:62c4 LG Electronics, Inc. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.10
  bDeviceClass          239 Miscellaneous Device
  bDeviceSubClass         2 ?
  bDeviceProtocol         1 Interface Association
  bMaxPacketSize0        64
  idVendor           0x1004 LG Electronics, Inc.
  idProduct          0x62c4 
  bcdDevice            4.09
  iManufacturer           1 LGE
  iProduct                2 LM-G710VM
  iSerial                 3 LMG710VM2761e5e4
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength          187
    bNumInterfaces          6
    bConfigurationValue     1
    iConfiguration          4 rndis_acm_diag_adb
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              500mA
    Interface Association:
      bLength                 8
      bDescriptorType        11
      bFirstInterface         0
      bInterfaceCount         2
      bFunctionClass        239 Miscellaneous Device
      bFunctionSubClass       4 
      bFunctionProtocol       1 
      iFunction               7 RNDIS
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass       239 Miscellaneous Device
      bInterfaceSubClass      4 
      bInterfaceProtocol      1 
      iInterface              5 RNDIS Communications Control
      ** UNRECOGNIZED:  05 24 00 10 01
      ** UNRECOGNIZED:  05 24 01 00 01
      ** UNRECOGNIZED:  04 24 02 00
      ** UNRECOGNIZED:  05 24 06 00 01
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval               9
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass        10 CDC Data
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 
      iInterface              6 RNDIS Ethernet Data
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x8e  EP 14 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x0f  EP 15 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
    Interface Association:
      bLength                 8
      bDescriptorType        11
      bFirstInterface         2
      bInterfaceCount         2
      bFunctionClass          2 Communications
      bFunctionSubClass       2 Abstract (modem)
      bFunctionProtocol       1 AT-commands (v.25ter)
      iFunction              10 CDC Serial
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        2
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         2 Communications
      bInterfaceSubClass      2 Abstract (modem)
      bInterfaceProtocol      1 AT-commands (v.25ter)
      iInterface              8 CDC Abstract Control Model (ACM)
      CDC Header:
        bcdCDC               1.10
      CDC Call Management:
        bmCapabilities       0x00
        bDataInterface          3
      CDC ACM:
        bmCapabilities       0x02
          line coding and serial state
      CDC Union:
        bMasterInterface        2
        bSlaveInterface         3 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               9
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        3
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass        10 CDC Data
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 
      iInterface              9 CDC ACM Data
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
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
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        4
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol     48 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        5
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass     66 
      bInterfaceProtocol      1 
      iInterface             12 ADB Interface
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x85  EP 5 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
Binary Object Store Descriptor:
  bLength                 5
  bDescriptorType        15
  wTotalLength           22
  bNumDeviceCaps          2
  USB 2.0 Extension Device Capability:
    bLength                 7
    bDescriptorType        16
    bDevCapabilityType      2
    bmAttributes   0x00000006
      Link Power Management (LPM) Supported
  SuperSpeed USB Device Capability:
    bLength                10
    bDescriptorType        16
    bDevCapabilityType      3
    bmAttributes         0x00
    wSpeedsSupported   0x000f
      Device can operate at Low Speed (1Mbps)
      Device can operate at Full Speed (12Mbps)
      Device can operate at High Speed (480Mbps)
      Device can operate at SuperSpeed (5Gbps)
    bFunctionalitySupport   1
      Lowest fully-functional device speed is Full Speed (12Mbps)
    bU1DevExitLat           1 micro seconds
    bU2DevExitLat         500 micro seconds
Device Status:     0x0000
  (Bus Powered)

```

Interestingly, I have to issue the command "sudo lsusb -v", because if I issue only "lsusb -v", the command says "Couldn't open device, some information will be missing" for the LG phone, and indeed there is missing information relative to the "sudo lsusb -v" command.

However, after the USB device is created, nothing else happens.  There should be an interface created when the phone is plugged in that I can see with "ifconfig -a" or "ip link show", but there isn't. The list of interfaces is the same as before the phone is plugged in.

Things I have tried:
1) Enabled USB debugging on the phone, but that doesn't change anything.
2) manually loading the driver rndis_host.ko with modprobe, but that makes no difference.
3) different USB ports on the PC.

Any suggestions?  I don't really know much about the internals of Ubuntu networking.  What mechanism is supposed to create the interface after the USB RDNIS adpater is created?  Is there a way to manually do this?  Is there a package that I might be missing that needs to be installed?  Are there any configuration files I can check for missing/incorrect entries?

Thanks!

Update 1:  found the following in the system log, which seems to indicate some problems:
```
Dec 12 13:52:55 t5610 kernel: [ 2600.812091] usb 3-2: new high-speed USB device number 5 using xhci_hcd
Dec 12 13:52:55 t5610 kernel: [ 2600.945898] usb 3-2: New USB device found, idVendor=1004, idProduct=62c4
Dec 12 13:52:55 t5610 kernel: [ 2600.945903] usb 3-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Dec 12 13:52:55 t5610 kernel: [ 2600.945907] usb 3-2: Product: LM-G710VM
Dec 12 13:52:55 t5610 kernel: [ 2600.945910] usb 3-2: Manufacturer: LGE
Dec 12 13:52:55 t5610 kernel: [ 2600.945912] usb 3-2: SerialNumber: LMG710VM2761e5e4
Dec 12 13:52:55 t5610 mtp-probe: checking bus 3, device 5: "/sys/devices/pci0000:00/0000:00:1c.0/0000:05:00.0/usb3/3-2"
Dec 12 13:52:55 t5610 mtp-probe: bus: 3, device: 5 was not an MTP device
Dec 12 13:52:55 t5610 kernel: [ 2601.016992] cdc_acm 3-2:1.2: ttyACM0: USB ACM device
Dec 12 13:52:55 t5610 kernel: [ 2601.017691] usbcore: registered new interface driver cdc_acm
Dec 12 13:52:55 t5610 kernel: [ 2601.017693] cdc_acm: USB Abstract Control Model driver for USB modems and ISDN adapters
Dec 12 13:52:55 t5610 snapd[1319]: hotplug.go:199: hotplug device add event ignored, enable experimental.hotplug
Dec 12 13:52:55 t5610 org.gtk.vfs.Daemon[2965]: Android device detected, assigning default bug flags
Dec 12 13:53:06 t5610 ModemManager[1190]: <warn>  (tty/ttyACM0) failed to parse QCDM version info command result: -5
Dec 12 13:53:06 t5610 ModemManager[1190]: <warn>  (tty/ttyACM0) failed to parse QCDM version info command result: -5
Dec 12 13:53:06 t5610 ModemManager[1190]: <info>  Creating modem with plugin 'Generic' and '1' ports
Dec 12 13:53:06 t5610 ModemManager[1190]: <warn>  Could not grab port (tty/ttyACM0): 'Cannot add port 'tty/ttyACM0', unhandled serial type'
Dec 12 13:53:06 t5610 ModemManager[1190]: <warn>  Couldn't create modem for device at '/sys/devices/pci0000:00/0000:00:1c.0/0000:05:00.0/usb3/3-2': Failed to find primary AT port
```

---

### Post by CelticWarrior on 2020-12-12
USB tethering in Ubuntu should be straightforward, it should "just work" from the moment you select that setting on the phone. It should immediately show a new (USB) Ethernet connection.

Having done that with many phones of different Android versions and brands with many different Ubuntu releases and always successful, no exceptions, I don't know what's happening with yours. 

I *suspect* Android 9 is too new for such an old release. Considering 16.04 has a few months left of support I wouldn't bother troubleshooting it. Please try with a modern Ubuntu in live session. If it works install it instead of the old 16.04.

---

### Post by morrownr on 2020-12-12
The first thing that came to mind is that you need to upgrade Ubuntu. If your computer can handle 20.04, go there. Android 9 and 10 work fine with 20.04.

---

### Post by jbhtexas on 2020-12-13
Thanks for the replies!  

Yes, upgrading to Ubuntu 20.04 LTS solved the problem, and tethering is working now.  I also checked after the first upgrade to 18.04 LTS, and tethering was working there as well.

---

