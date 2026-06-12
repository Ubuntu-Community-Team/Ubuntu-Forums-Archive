---
title: "bluetoothd consumes 100% CPU when scanning for devices, then system hangs"
date: 2015-11-02
forum: Networking &amp; Wireless
---

### Post by giacof on 2015-11-02
Hi, I'm trying to use the bluedevil wizard on Kubuntu 15.04 to add a new device (BT headset). The scan window opens but no device is found.
Meanwhile, both cpu and memory usage start to increase until memory is 100% full and the system hangs!

Then if I just kill bluedevil, I see dbus-daemon keeps using 100% cpu, the only way to lower the cpu load is by manually stopping the bluetooth service.
```
$ uname -a
Linux Home1 3.19.0-32-generic #37-Ubuntu SMP Wed Oct 21 10:23:06 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

```
```
$ hciconfig -a
hci0: Type: BR/EDR Bus: USB
        BD Address: 44:39:C4:19:43:C9 ACL MTU: 1022:8 SCO MTU: 183:5
        DOWN
        RX bytes:564 acl:0 sco:0 events:29 errors:0
        TX bytes:358 acl:0 sco:0 commands:29 errors:0
        Features: 0xff 0xfe 0x0d 0xfe 0xd8 0x7f 0x7b 0x8f
        Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3
        Link policy: RSWITCH HOLD SNIFF
        Link mode: SLAVE ACCEPT

```
```
$ rfkill list
1: dell-wifi: Wireless LAN
        Soft blocked: no
        Hard blocked: no
2: dell-bluetooth: Bluetooth
        Soft blocked: no
        Hard blocked: no
3: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no
4: hci0: Bluetooth
        Soft blocked: no
        Hard blocked: no

```
```
$ lsmod | grep blue
bluetooth 491520 23 bnep,ath3k,btusb,rfcomm
```
```
$ lsusb
Bus 004 Device 004: ID 0a5c:5800 Broadcom Corp. BCM5880 Secure Applications Processor
Bus 004 Device 005: ID 0cf3:817a Atheros Communications, Inc.
Bus 004 Device 002: ID 8087:8000 Intel Corp.
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 003: ID 0c45:649d Microdia
Bus 003 Device 002: ID 8087:8008 Intel Corp.
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```
```
$ lsusb -s 004:005 -v

Bus 004 Device 005: ID 0cf3:817a Atheros Communications, Inc.
Couldn't open device, some information will be missing
Device Descriptor:
  bLength 18
  bDescriptorType 1
  bcdUSB 1.10
  bDeviceClass 224 Wireless
  bDeviceSubClass 1 Radio Frequency
  bDeviceProtocol 1 Bluetooth
  bMaxPacketSize0 64
  idVendor 0x0cf3 Atheros Communications, Inc.
  idProduct 0x817a
  bcdDevice 0.02
  iManufacturer 1
  iProduct 2
  iSerial 3
  bNumConfigurations 1
  Configuration Descriptor:
    bLength 9
    bDescriptorType 2
    wTotalLength 177
    bNumInterfaces 2
    bConfigurationValue 1
    iConfiguration 4
    bmAttributes 0xe0
      Self Powered
      Remote Wakeup
    MaxPower 100mA
    Interface Descriptor:
      bLength 9
      bDescriptorType 4
      bInterfaceNumber 0
      bAlternateSetting 0
      bNumEndpoints 3
      bInterfaceClass 224 Wireless
      bInterfaceSubClass 1 Radio Frequency
      bInterfaceProtocol 1 Bluetooth
      iInterface 0
      Endpoint Descriptor:
        bLength 7
        bDescriptorType 5
        bEndpointAddress 0x81 EP 1 IN
        bmAttributes 3
          Transfer Type Interrupt
          Synch Type None
          Usage Type Data
        wMaxPacketSize 0x0010 1x 16 bytes
        bInterval 1
      Endpoint Descriptor:
        bLength 7
        bDescriptorType 5
        bEndpointAddress 0x82 EP 2 IN
        bmAttributes 2
          Transfer Type Bulk
          Synch Type None
          Usage Type Data
        wMaxPacketSize 0x0040 1x 64 bytes
        bInterval 1
      Endpoint Descriptor:
        bLength 7
        bDescriptorType 5
        bEndpointAddress 0x02 EP 2 OUT
        bmAttributes 2
          Transfer Type Bulk
          Synch Type None
          Usage Type Data
        wMaxPacketSize 0x0040 1x 64 bytes
        bInterval 1
    Interface Descriptor:
      bLength 9
      bDescriptorType 4
      bInterfaceNumber 1
      bAlternateSetting 0
      bNumEndpoints 2
      bInterfaceClass 224 Wireless
      bInterfaceSubClass 1 Radio Frequency
      bInterfaceProtocol 1 Bluetooth
      iInterface 0
      Endpoint Descriptor:
        bLength 7
        bDescriptorType 5
        bEndpointAddress 0x83 EP 3 IN
        bmAttributes 1
          Transfer Type Isochronous
          Synch Type None
          Usage Type Data
        wMaxPacketSize 0x0000 1x 0 bytes
        bInterval 1
      Endpoint Descriptor:
        bLength 7
        bDescriptorType 5
        bEndpointAddress 0x03 EP 3 OUT
        bmAttributes 1
          Transfer Type Isochronous
          Synch Type None
          Usage Type Data
        wMaxPacketSize 0x0000 1x 0 bytes
        bInterval 1
    Interface Descriptor:
      bLength 9
      bDescriptorType 4
      bInterfaceNumber 1
      bAlternateSetting 1
      bNumEndpoints 2
      bInterfaceClass 224 Wireless
      bInterfaceSubClass 1 Radio Frequency
      bInterfaceProtocol 1 Bluetooth
      iInterface 0
      Endpoint Descriptor:
        bLength 7
        bDescriptorType 5
        bEndpointAddress 0x83 EP 3 IN
        bmAttributes 1
          Transfer Type Isochronous
          Synch Type None
          Usage Type Data
        wMaxPacketSize 0x0009 1x 9 bytes
        bInterval 1
      Endpoint Descriptor:
        bLength 7
        bDescriptorType 5
        bEndpointAddress 0x03 EP 3 OUT
        bmAttributes 1
          Transfer Type Isochronous
          Synch Type None
          Usage Type Data
        wMaxPacketSize 0x0009 1x 9 bytes
        bInterval 1
    Interface Descriptor:
      bLength 9
      bDescriptorType 4
      bInterfaceNumber 1
      bAlternateSetting 2
      bNumEndpoints 2
      bInterfaceClass 224 Wireless
      bInterfaceSubClass 1 Radio Frequency
      bInterfaceProtocol 1 Bluetooth
      iInterface 0
      Endpoint Descriptor:
        bLength 7
        bDescriptorType 5
        bEndpointAddress 0x83 EP 3 IN
        bmAttributes 1
          Transfer Type Isochronous
          Synch Type None
          Usage Type Data
        wMaxPacketSize 0x0011 1x 17 bytes
        bInterval 1
      Endpoint Descriptor:
        bLength 7
        bDescriptorType 5
        bEndpointAddress 0x03 EP 3 OUT
        bmAttributes 1
          Transfer Type Isochronous
          Synch Type None
          Usage Type Data
        wMaxPacketSize 0x0011 1x 17 bytes
        bInterval 1
    Interface Descriptor:
      bLength 9
      bDescriptorType 4
      bInterfaceNumber 1
      bAlternateSetting 3
      bNumEndpoints 2
      bInterfaceClass 224 Wireless
      bInterfaceSubClass 1 Radio Frequency
      bInterfaceProtocol 1 Bluetooth
      iInterface 0
      Endpoint Descriptor:
        bLength 7
        bDescriptorType 5
        bEndpointAddress 0x83 EP 3 IN
        bmAttributes 1
          Transfer Type Isochronous
          Synch Type None
          Usage Type Data
        wMaxPacketSize 0x0019 1x 25 bytes
        bInterval 1
      Endpoint Descriptor:
        bLength 7
        bDescriptorType 5
        bEndpointAddress 0x03 EP 3 OUT
        bmAttributes 1
          Transfer Type Isochronous
          Synch Type None
          Usage Type Data
        wMaxPacketSize 0x0019 1x 25 bytes
        bInterval 1
    Interface Descriptor:
      bLength 9
      bDescriptorType 4
      bInterfaceNumber 1
      bAlternateSetting 4
      bNumEndpoints 2
      bInterfaceClass 224 Wireless
      bInterfaceSubClass 1 Radio Frequency
      bInterfaceProtocol 1 Bluetooth
      iInterface 0
      Endpoint Descriptor:
        bLength 7
        bDescriptorType 5
        bEndpointAddress 0x83 EP 3 IN
        bmAttributes 1
          Transfer Type Isochronous
          Synch Type None
          Usage Type Data
        wMaxPacketSize 0x0021 1x 33 bytes
        bInterval 1
      Endpoint Descriptor:
        bLength 7
        bDescriptorType 5
        bEndpointAddress 0x03 EP 3 OUT
        bmAttributes 1
          Transfer Type Isochronous
          Synch Type None
          Usage Type Data
        wMaxPacketSize 0x0021 1x 33 bytes
        bInterval 1
    Interface Descriptor:
      bLength 9
      bDescriptorType 4
      bInterfaceNumber 1
      bAlternateSetting 5
      bNumEndpoints 2
      bInterfaceClass 224 Wireless
      bInterfaceSubClass 1 Radio Frequency
      bInterfaceProtocol 1 Bluetooth
      iInterface 0
      Endpoint Descriptor:
        bLength 7
        bDescriptorType 5
        bEndpointAddress 0x83 EP 3 IN
        bmAttributes 1
          Transfer Type Isochronous
          Synch Type None
          Usage Type Data
        wMaxPacketSize 0x0031 1x 49 bytes
        bInterval 1
      Endpoint Descriptor:
        bLength 7
        bDescriptorType 5
        bEndpointAddress 0x03 EP 3 OUT
        bmAttributes 1
          Transfer Type Isochronous
          Synch Type None
          Usage Type Data
        wMaxPacketSize 0x0031 1x 49 bytes
        bInterval 1
```

Any help appreciated.

---

