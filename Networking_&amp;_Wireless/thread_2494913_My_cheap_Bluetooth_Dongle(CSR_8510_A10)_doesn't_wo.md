---
title: "My cheap Bluetooth Dongle(CSR 8510 A10) doesn't work on Ubuntu new versions"
date: 2024-01-31
forum: Networking &amp; Wireless
---

### Post by ahmermanzoor on 2024-01-31
Hi! I am Ahmer, if I provide less info sorry, because it is my first time on the linux forums. I have a Dell Optiplex 3010 pc, I run Ubuntu-23.10  release when I plugged the Cambridge Silicon Usb Dongle it shows up in  the settings but doesn't turn on, It has no brand but shows as cambridge  silicon chip in the terminal. It actually worked on Ubuntu-20.04 as it  had old kernel with the patches from this link:
[https://bugzilla.kernel.org/show_bug.cgi?id=60824#c155](https://bugzilla.kernel.org/show_bug.cgi?id=60824#c155)
But, this patch is in kernel 6.0.0 and later but doesn't work. I have  tried to manually patch the kernel as some extra files had been added to  newer kernels and then compiled. But it didn't work, I have already  been to the post you told me. But none of them work with the newer  kernels. Please help me. Here is more information about the usb dongle:
"inxi -Eaz" output:
Bluetooth:
Device-1: Cambridge Silicon Radio Bluetooth Dongle (HCI mode) driver: btusb
v: 0.8 type: USB rev: 2.0 speed: 12 Mb/s lanes: 1 mode: 1.1 bus-ID: 2-1.4:4
chip-ID: 0a12:0001 class-ID: e001
Report: hciconfig ID: hci0 rfk-id: 1 state: down bt-service: disabled
rfk-block: hardware: no software: no address: <filter>
Info: acl-mtu: 0:0 sco-mtu: 0:0 link-mode: peripheral accept

"hciconfig -a" output:
hci0: Type: Primary Bus: USB
BD Address: 00:00:00:00:00:00 ACL MTU: 0:0 SCO MTU: 0:0
DOWN 
RX bytes:14 acl:0 sco:0 events:1 errors:0
TX bytes:3 acl:0 sco:0 commands:2 errors:1
Features: 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00
Packet type: DM1 DH1 HV1 
Link policy: 
Link mode: PERIPHERAL ACCEPT 
"lsusb -vv -d 0a12:0001" output:
Bus 002 Device 004: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Couldn't open device, some information will be missing
Device Descriptor:
bLength 18
bDescriptorType 1
bcdUSB 2.00
bDeviceClass 224 Wireless
bDeviceSubClass 1 Radio Frequency
bDeviceProtocol 1 Bluetooth
bMaxPacketSize0 64
idVendor 0x0a12 Cambridge Silicon Radio, Ltd
idProduct 0x0001 Bluetooth Dongle (HCI mode)
bcdDevice 25.20
iManufacturer 0 
iProduct 2 CSR8510 A10
iSerial 0 
bNumConfigurations 1
Configuration Descriptor:
bLength 9
bDescriptorType 2
wTotalLength 0x00b1
bNumInterfaces 2
bConfigurationValue 1
iConfiguration 0 
bmAttributes 0xa0
(Bus Powered)
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
bEndpointAddress 0x83 EP 3 IN
bmAttributes 3
Transfer Type Interrupt
Synch Type None
Usage Type Data
wMaxPacketSize 0x0010 1x 16 bytes
bInterval 1
Endpoint Descriptor:
bLength 7
bDescriptorType 5
bEndpointAddress 0x01 EP 1 OUT
bmAttributes 2
Transfer Type Bulk
Synch Type None
Usage Type Data
wMaxPacketSize 0x0040 1x 64 bytes
bInterval 1
Endpoint Descriptor:
bLength 7
bDescriptorType 5
bEndpointAddress 0x81 EP 1 IN
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
bEndpointAddress 0x02 EP 2 OUT
bmAttributes 1
Transfer Type Isochronous
Synch Type None
Usage Type Data
wMaxPacketSize 0x0000 1x 0 bytes
bInterval 1
Endpoint Descriptor:
bLength 7
bDescriptorType 5
bEndpointAddress 0x82 EP 2 IN
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
bEndpointAddress 0x02 EP 2 OUT
bmAttributes 1
Transfer Type Isochronous
Synch Type None
Usage Type Data
wMaxPacketSize 0x0009 1x 9 bytes
bInterval 1
Endpoint Descriptor:
bLength 7
bDescriptorType 5
bEndpointAddress 0x82 EP 2 IN
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
bEndpointAddress 0x02 EP 2 OUT
bmAttributes 1
Transfer Type Isochronous
Synch Type None
Usage Type Data
wMaxPacketSize 0x0011 1x 17 bytes
bInterval 1
Endpoint Descriptor:
bLength 7
bDescriptorType 5
bEndpointAddress 0x82 EP 2 IN
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
bEndpointAddress 0x02 EP 2 OUT
bmAttributes 1
Transfer Type Isochronous
Synch Type None
Usage Type Data
wMaxPacketSize 0x0019 1x 25 bytes
bInterval 1
Endpoint Descriptor:
bLength 7
bDescriptorType 5
bEndpointAddress 0x82 EP 2 IN
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
bEndpointAddress 0x02 EP 2 OUT
bmAttributes 1
Transfer Type Isochronous
Synch Type None
Usage Type Data
wMaxPacketSize 0x0021 1x 33 bytes
bInterval 1
Endpoint Descriptor:
bLength 7
bDescriptorType 5
bEndpointAddress 0x82 EP 2 IN
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
bEndpointAddress 0x02 EP 2 OUT
bmAttributes 1
Transfer Type Isochronous
Synch Type None
Usage Type Data
wMaxPacketSize 0x0031 1x 49 bytes
bInterval 1
Endpoint Descriptor:
bLength 7
bDescriptorType 5
bEndpointAddress 0x82 EP 2 IN
bmAttributes 1
Transfer Type Isochronous
Synch Type None
Usage Type Data
wMaxPacketSize 0x0031 1x 49 bytes
bInterval 1

Please, tell me if you need any more info.

---

