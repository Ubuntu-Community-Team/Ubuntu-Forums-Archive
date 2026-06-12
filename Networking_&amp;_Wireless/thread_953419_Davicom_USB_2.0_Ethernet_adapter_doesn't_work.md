---
title: "Davicom USB 2.0 Ethernet adapter doesn't work"
date: 2008-10-20
forum: Networking &amp; Wireless
---

### Post by quadrispro on 2008-10-20
After the last kernel updates, my USB 2.0 ethernet adapter stops to work.


With 2.6.24-19-generic kernel there's no problem, with 2.6-24-21-generic it doesn't work (I'm using Hardy).


**lsusb**:

```
Bus 001 Device 002: ID 0a46:9601 Davicom Semiconductor, Inc.
```

**sudo lsusb -d 0a46:9601 -v**:

```
Bus 001 Device 002: ID 0a46:9601 Davicom Semiconductor, Inc.
Device Descriptor:
  bLength 18
  bDescriptorType 1
  bcdUSB 1.10
  bDeviceClass 0 (Defined at Interface level)
  bDeviceSubClass 0
  bDeviceProtocol 0
  bMaxPacketSize0 8
  idVendor 0x0a46 Davicom Semiconductor, Inc.
  idProduct 0x9601
  bcdDevice 1.01
  iManufacturer 1
  iProduct 2
  iSerial 3
  bNumConfigurations 1
  Configuration Descriptor:
    bLength 9
    bDescriptorType 2
    wTotalLength 39
    bNumInterfaces 1
    bConfigurationValue 1
    iConfiguration 0
    bmAttributes 0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower 120mA
    Interface Descriptor:
      bLength 9
      bDescriptorType 4
      bInterfaceNumber 0
      bAlternateSetting 0
      bNumEndpoints 3
      bInterfaceClass 0 (Defined at Interface level)
      bInterfaceSubClass 0
      bInterfaceProtocol 0
      iInterface 0
      Endpoint Descriptor:
        bLength 7
        bDescriptorType 5
        bEndpointAddress 0x81 EP 1 IN
        bmAttributes 2
          Transfer Type Bulk
          Synch Type None
          Usage Type Data
        wMaxPacketSize 0x0040 1x 64 bytes
        bInterval 0
      Endpoint Descriptor:
        bLength 7
        bDescriptorType 5
        bEndpointAddress 0x02 EP 2 OUT
        bmAttributes 2
          Transfer Type Bulk
          Synch Type None
          Usage Type Data
        wMaxPacketSize 0x0040 1x 64 bytes
        bInterval 0
      Endpoint Descriptor:
        bLength 7
        bDescriptorType 5
        bEndpointAddress 0x83 EP 3 IN
        bmAttributes 3
          Transfer Type Interrupt
          Synch Type None
          Usage Type Data
        wMaxPacketSize 0x0008 1x 8 bytes
        bInterval 1
Device Status: 0x0000
  (Bus Powered)
```

**uname -r**:

```
2.6.24-21-generic
```

When I try to plug the device, **dmesg** shows this:

```
[ 486.154104] usb 1-2: new full speed USB device using ohci_hcd and address 3
[ 486.266130] usb 1-2: configuration #1 chosen from 1 choice
[ 486.352146] dm9601: disagrees about version of symbol usbnet_set_msglevel
[ 486.352159] dm9601: Unknown symbol usbnet_set_msglevel
[ 486.352366] dm9601: disagrees about version of symbol usbnet_get_msglevel
[ 486.352370] dm9601: Unknown symbol usbnet_get_msglevel
[ 486.352503] dm9601: disagrees about version of symbol usbnet_get_settings
[ 486.352507] dm9601: Unknown symbol usbnet_get_settings
[ 486.352557] dm9601: disagrees about version of symbol usbnet_suspend
[ 486.352561] dm9601: Unknown symbol usbnet_suspend
[ 486.352608] dm9601: disagrees about version of symbol usbnet_get_drvinfo
[ 486.352612] dm9601: Unknown symbol usbnet_get_drvinfo
[ 486.352691] dm9601: disagrees about version of symbol usbnet_get_endpoints
[ 486.352695] dm9601: Unknown symbol usbnet_get_endpoints
[ 486.352805] dm9601: disagrees about version of symbol usbnet_nway_reset
[ 486.352810] dm9601: Unknown symbol usbnet_nway_reset
[ 486.352877] dm9601: disagrees about version of symbol usbnet_defer_kevent
[ 486.352881] dm9601: Unknown symbol usbnet_defer_kevent
[ 486.352943] dm9601: disagrees about version of symbol usbnet_disconnect
[ 486.352946] dm9601: Unknown symbol usbnet_disconnect
[ 486.352997] dm9601: disagrees about version of symbol usbnet_set_settings
[ 486.353001] dm9601: Unknown symbol usbnet_set_settings
[ 486.353032] dm9601: disagrees about version of symbol usbnet_probe
[ 486.353036] dm9601: Unknown symbol usbnet_probe
[ 486.353066] dm9601: disagrees about version of symbol usbnet_resume
[ 486.353070] dm9601: Unknown symbol usbnet_resume
```



EDIT: I've just reported a [bug on Launchpad]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/285552").

---

