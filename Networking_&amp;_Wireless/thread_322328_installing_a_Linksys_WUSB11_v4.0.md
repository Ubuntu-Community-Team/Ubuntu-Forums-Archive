---
title: "installing a Linksys WUSB11 v4.0"
date: 2006-12-20
forum: Networking &amp; Wireless
---

### Post by vintendo on 2006-12-20
Hey, I have a Linksys WUSB11 v4.0 on my Ubuntu 6.10 and cannot get it to work :( When I do a ```
sudo lsusb -v
``` I get,
Bus 002 Device 001: ID 0000:0000
Device Descriptor:
bLength 18
bDescriptorType 1
bcdUSB 1.10
bDeviceClass 9 Hub
bDeviceSubClass 0 Unused
bDeviceProtocol 0
bMaxPacketSize0 64
idVendor 0x0000
idProduct 0x0000
bcdDevice 2.06
iManufacturer 3 Linux 2.6.17-10-generic uhci_hcd
iProduct 2 UHCI Host Controller
iSerial 1 0000:00:04.3
bNumConfigurations 1
Configuration Descriptor:
bLength 9
bDescriptorType 2
wTotalLength 25
bNumInterfaces 1
bConfigurationValue 1
iConfiguration 0
bmAttributes 0xe0
Self Powered
Remote Wakeup
MaxPower 0mA
Interface Descriptor:
bLength 9
bDescriptorType 4
bInterfaceNumber 0
bAlternateSetting 0
bNumEndpoints 1
bInterfaceClass 9 Hub
bInterfaceSubClass 0 Unused
bInterfaceProtocol 0
iInterface 0
Endpoint Descriptor:
bLength 7
bDescriptorType 5
bEndpointAddress 0x81 EP 1 IN
bmAttributes 3
Transfer Type Interrupt
Synch Type None
Usage Type Data
wMaxPacketSize 0x0002 1x 2 bytes
bInterval 255
Hub Descriptor:
bLength 9
bDescriptorType 41
nNbrPorts 2
wHubCharacteristic 0x000a
No power switching (usb 1.0)
Per-port overcurrent protection
bPwrOn2PwrGood 1 * 2 milli seconds
bHubContrCurrent 0 milli Ampere
DeviceRemovable 0x00
PortPwrCtrlMask 0xff
Hub Port Status:
Port 1: 0000.0100 power
Port 2: 0000.0100 power
Device Status: 0x0003
Self Powered
Remote Wakeup Enabled

Bus 001 Device 004: ID 0443:002e Gateway, Inc.
Device Descriptor:
bLength 18
bDescriptorType 1
bcdUSB 1.10
bDeviceClass 0 (Defined at Interface level)
bDeviceSubClass 0
bDeviceProtocol 0
bMaxPacketSize0 8
idVendor 0x0443 Gateway, Inc.
idProduct 0x002e
bcdDevice 1.00
iManufacturer 1 NMB
iProduct 2 Gateway USB Hub Keyboard
iSerial 0
bNumConfigurations 1
Configuration Descriptor:
bLength 9
bDescriptorType 2
wTotalLength 59
bNumInterfaces 2
bConfigurationValue 1
iConfiguration 2 Gateway USB Hub Keyboard
bmAttributes 0xe0
Self Powered
Remote Wakeup
MaxPower 0mA
Interface Descriptor:
bLength 9
bDescriptorType 4
bInterfaceNumber 0
bAlternateSetting 0
bNumEndpoints 1
bInterfaceClass 3 Human Interface Devices
bInterfaceSubClass 1 Boot Interface Subclass
bInterfaceProtocol 1 Keyboard
iInterface 2 Gateway USB Hub Keyboard
HID Device Descriptor:
bLength 9
bDescriptorType 33
bcdHID 1.10
bCountryCode 0 Not supported
bNumDescriptors 1
bDescriptorType 34 Report
wDescriptorLength 65
Report Descriptors:
** UNAVAILABLE **
Endpoint Descriptor:
bLength 7
bDescriptorType 5
bEndpointAddress 0x81 EP 1 IN
bmAttributes 3
Transfer Type Interrupt
Synch Type None
Usage Type Data
wMaxPacketSize 0x0008 1x 8 bytes
bInterval 24
Interface Descriptor:
bLength 9
bDescriptorType 4
bInterfaceNumber 1
bAlternateSetting 0
bNumEndpoints 1
bInterfaceClass 3 Human Interface Devices
bInterfaceSubClass 0 No Subclass
bInterfaceProtocol 0 None
iInterface 2 Gateway USB Hub Keyboard
HID Device Descriptor:
bLength 9
bDescriptorType 33
bcdHID 1.10
bCountryCode 0 Not supported
bNumDescriptors 1
bDescriptorType 34 Report
wDescriptorLength 211
Report Descriptors:
** UNAVAILABLE **
Endpoint Descriptor:
bLength 7
bDescriptorType 5
bEndpointAddress 0x82 EP 2 IN
bmAttributes 3
Transfer Type Interrupt
Synch Type None
Usage Type Data
wMaxPacketSize 0x0004 1x 4 bytes
bInterval 48
Device Status: 0x0000
(Bus Powered)

Bus 001 Device 003: ID 0443:002f Gateway, Inc.
Device Descriptor:
bLength 18
bDescriptorType 1
bcdUSB 1.10
bDeviceClass 9 Hub
bDeviceSubClass 0 Unused
bDeviceProtocol 0
bMaxPacketSize0 8
idVendor 0x0443 Gateway, Inc.
idProduct 0x002f
bcdDevice 1.00
iManufacturer 1 NMB
iProduct 2 Gateway USB Hub Keyboard
iSerial 0
bNumConfigurations 1
Configuration Descriptor:
bLength 9
bDescriptorType 2
wTotalLength 25
bNumInterfaces 1
bConfigurationValue 1
iConfiguration 2 Gateway USB Hub Keyboard
bmAttributes 0xa0
(Bus Powered)
Remote Wakeup
MaxPower 90mA
Interface Descriptor:
bLength 9
bDescriptorType 4
bInterfaceNumber 0
bAlternateSetting 0
bNumEndpoints 1
bInterfaceClass 9 Hub
bInterfaceSubClass 0 Unused
bInterfaceProtocol 0
iInterface 2 Gateway USB Hub Keyboard
Endpoint Descriptor:
bLength 7
bDescriptorType 5
bEndpointAddress 0x81 EP 1 IN
bmAttributes 3
Transfer Type Interrupt
Synch Type None
Usage Type Data
wMaxPacketSize 0x0001 1x 1 bytes
bInterval 255
Hub Descriptor:
bLength 9
bDescriptorType 41
nNbrPorts 3
wHubCharacteristic 0x000d
Per-port power switching
Compound device
Per-port overcurrent protection
bPwrOn2PwrGood 50 * 2 milli seconds
bHubContrCurrent 90 milli Ampere
DeviceRemovable 0x02
PortPwrCtrlMask 0xff
Hub Port Status:
Port 1: 0000.0103 power enable connect
Port 2: 0000.0100 power
Port 3: 0000.0100 power
Device Status: 0x0000
(Bus Powered)

Bus 001 Device 002: ID 13b1:000b Linksys WUSB11 v4.0 802.11b Adapter
Device Descriptor:
bLength 18
bDescriptorType 1
bcdUSB 1.10
bDeviceClass 255 Vendor Specific Class
bDeviceSubClass 255 Vendor Specific Subclass
bDeviceProtocol 255 Vendor Specific Protocol
bMaxPacketSize0 8
idVendor 0x13b1 Linksys
idProduct 0x000b WUSB11 v4.0 802.11b Adapter
bcdDevice 0.01
iManufacturer 1 ALinx Corp
iProduct 2 USB Device
iSerial 0
bNumConfigurations 1
Configuration Descriptor:
bLength 9
bDescriptorType 2
wTotalLength 39
bNumInterfaces 1
bConfigurationValue 1
iConfiguration 0
bmAttributes 0x80
(Bus Powered)
MaxPower 200mA
Interface Descriptor:
bLength 9
bDescriptorType 4
bInterfaceNumber 0
bAlternateSetting 0
bNumEndpoints 3
bInterfaceClass 255 Vendor Specific Class
bInterfaceSubClass 255 Vendor Specific Subclass
bInterfaceProtocol 255 Vendor Specific Protocol
iInterface 0
Endpoint Descriptor:
bLength 7
bDescriptorType 5
bEndpointAddress 0x82 EP 2 IN
bmAttributes 2
Transfer Type Bulk
Synch Type None
Usage Type Data
wMaxPacketSize 0x0040 1x 64 bytes
bInterval 0
Endpoint Descriptor:
bLength 7
bDescriptorType 5
bEndpointAddress 0x06 EP 6 OUT
bmAttributes 2
Transfer Type Bulk
Synch Type None
Usage Type Data
wMaxPacketSize 0x0040 1x 64 bytes
bInterval 0
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
Device Status: 0x0000
(Bus Powered)

Bus 001 Device 001: ID 0000:0000
Device Descriptor:
bLength 18
bDescriptorType 1
bcdUSB 1.10
bDeviceClass 9 Hub
bDeviceSubClass 0 Unused
bDeviceProtocol 0
bMaxPacketSize0 64
idVendor 0x0000
idProduct 0x0000
bcdDevice 2.06
iManufacturer 3 Linux 2.6.17-10-generic uhci_hcd
iProduct 2 UHCI Host Controller
iSerial 1 0000:00:04.2
bNumConfigurations 1
Configuration Descriptor:
bLength 9
bDescriptorType 2
wTotalLength 25
bNumInterfaces 1
bConfigurationValue 1
iConfiguration 0
bmAttributes 0xe0
Self Powered
Remote Wakeup
MaxPower 0mA
Interface Descriptor:
bLength 9
bDescriptorType 4
bInterfaceNumber 0
bAlternateSetting 0
bNumEndpoints 1
bInterfaceClass 9 Hub
bInterfaceSubClass 0 Unused
bInterfaceProtocol 0
iInterface 0
Endpoint Descriptor:
bLength 7
bDescriptorType 5
bEndpointAddress 0x81 EP 1 IN
bmAttributes 3
Transfer Type Interrupt
Synch Type None
Usage Type Data
wMaxPacketSize 0x0002 1x 2 bytes
bInterval 255
Hub Descriptor:
bLength 9
bDescriptorType 41
nNbrPorts 2
wHubCharacteristic 0x000a
No power switching (usb 1.0)
Per-port overcurrent protection
bPwrOn2PwrGood 1 * 2 milli seconds
bHubContrCurrent 0 milli Ampere
DeviceRemovable 0x00
PortPwrCtrlMask 0xff
Hub Port Status:
Port 1: 0000.0103 power enable connect
Port 2: 0000.0103 power enable connect
Device Status: 0x0003
Self Powered
Remote Wakeup Enabled

 And when I do ```
iwconfig
``` I get,
lo no wireless extensions.

eth0 no wireless extensions.

vmnet8 no wireless extensions.

vmnet1 no wireless extensions.

sit0 no wireless extensions

 Maybe I'm not doing something right. ](*,) ](*,) ](*,)

---

### Post by vintendo on 2006-12-20
well i finially got the driver loaded in the Windows Wireless Drivers program. but the wireless dosent show up in network settings :(

---

