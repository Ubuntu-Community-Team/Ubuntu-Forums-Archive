---
title: "ttyUSB"
date: 2009-09-14
forum: New to Ubuntu
---

### Post by supererki on 2009-09-14
computer is asking me a question at the moment :

 Specify the serial interface used to connect your Windows CE device to the desktop. Possible serial interfaces are:

ttyS0: First serial port (COM1: on DOS and Windows) 
ttyS1: Second serial port (COM2: on DOS and Windows) 
ircomm0: First IrDA communication port
ircomm1: Second IrDA communication port 
ttyUSB0: First USB-Serial port
ttyUSB1: Second USB-Serial port 


-------------
sudo lsusb -v gives me :

Bus 006 Device 058: ID 03f0:1016 Hewlett-Packard Jornada 548 / iPAQ HW6515 Pocket PC
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        16
  idVendor           0x03f0 Hewlett-Packard
  idProduct          0x1016 Jornada 548 / iPAQ HW6515 Pocket PC
  bcdDevice            0.00
  iManufacturer           1 HP
  iProduct                2 HP USB Sync
  iSerial                 3 00337535-2220-0186-0800-0050bf1977e0
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xc0
      Self Powered
    MaxPower                2mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
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
Device Status:     0x0001
  Self Powered

thats the one!
now, how can i figure what TTY it is? is it tty6 because its on bus 6?

---

### Post by supererki on 2009-09-14
nobody?

---

