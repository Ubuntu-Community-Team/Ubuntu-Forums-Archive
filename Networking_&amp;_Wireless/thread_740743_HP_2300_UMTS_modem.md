---
title: "HP 2300 UMTS modem"
date: 2008-03-31
forum: Networking &amp; Wireless
---

### Post by Carceri on 2008-03-31
I have been trying to get the HP 2300 Broadband Wireless Module (UMTS modem) to work with Ubuntu 7.10 on my HP 2510p laptop without any luck so far.

The HP 2300 uses the Qualcomm MSM6280 chipset and the Sierra Wireless MC8775 module, which should be supported under Linux. The device is installed as a mini PCI card, and recognized as the following USB device:

```
Bus 002 Device 003: ID 03f0:1e1d Hewlett-Packard 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x03f0 Hewlett-Packard
  idProduct          0x1e1d 
  bcdDevice            0.01
  iManufacturer           1 HP
  iProduct                2 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           67
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           7
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              3 Data Interface
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0010  1x 16 bytes
        bInterval             128
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x04  EP 4 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x85  EP 5 IN
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
Device Status:     0x0000
  (Bus Powered)

```
In order for the system to load drivers for the device, I have created a file:

/etc/udev/rules.d/50-sierra-umts.rules

with the following lines:

SUBSYSTEM=="usb", SYSFS{idProduct}=="1e1d", SYSFS{idVendor}=="03f0", RUN+="/sbin/modprobe usbserial vendor=0x03f0 product=0x1e1d"
SUBSYSTEM=="usb", SYSFS{idProduct}=="1e1d", SYSFS{idVendor}=="03f0", RUN+="/sbin/modprobe sierra"

When booting, dmesg lists the following:

[   33.700000] usbcore: registered new interface driver usbserial
[   33.700000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/usb-serial.c: USB Serial support registered for generic
[   33.700000] usbserial_generic 4-1:1.0: generic converter detected
[   33.700000] usb 4-1: generic converter now attached to ttyUSB0
[   33.700000] usb 4-1: generic converter now attached to ttyUSB1
[   33.700000] usb 4-1: generic converter now attached to ttyUSB2
[   33.700000] usbcore: registered new interface driver usbserial_generic
[   33.700000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/usb-serial.c: USB Serial Driver core
[   33.836000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/usb-serial.c: USB Serial support registered for Sierra USB modem (1 port)
[   33.836000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/usb-serial.c: USB Serial support registered for Sierra USB modem (3 port)
[   33.836000] usbcore: registered new interface driver sierra
[   33.836000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/sierra.c: USB Driver for Sierra Wireless USB modems: v.1.0.6

According to various documentation for the Sierra chipset, one should now be able to use /dev/ttyUSB1 as a modem, but when I run:

sudo pppd noauth nodetach /dev/ttyUSB1 user '' connect '/usr/sbin/chat ABORT BUSY ABORT "NO CARRIER" "" ATZ OK ATDT*99# CONNECT'

It just times out with the message "Connect script failed". If I use wvdial to connect to the modem, I get:

WvDial<*1>: WvDial: Internet dialer version 1.56
WvModem<*1>: Cannot get information for serial port.
WvDial<*1>: Initializing modem.
WvDial<*1>: Sending: ATZ
WvDial<*1>: Sending: ATQ0
WvDial<*1>: Re-Sending: ATZ
WvDial<Err>: Modem not responding.

Any ideas what I need to do, to make this work?

---

### Post by Carceri on 2008-04-02
I solved this, in case people come here with a similar problem. There is a more detailed guide here:

[http://foomagic.org/wiki/index.php/Using_the_Sierra_mc8755_WWAN_card_under_linux](http://foomagic.org/wiki/index.php/Using_the_Sierra_mc8755_WWAN_card_under_linux)

but what really mattered was

1) My pppd line is wrong, and doesn't work
2) The modem is /dev/ttyUSB2, and not /dev/ttyUSB1 as most documents say

All I did was to run wvdialconf, and it autodetected the modem on the other ports.

---

