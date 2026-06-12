---
title: "Linksys WUSB300 help!"
date: 2008-02-23
forum: Networking &amp; Wireless
---

### Post by vortex_noob on 2008-02-23
Hi, I'm really new at this...
Can anybody tell me how to get this new Linksys WUSB300 Wireless N USB adapter to work?:confused:
Thanks

---

### Post by Hightide on 2008-02-23
HI Vortex Noob

I am guessing that its a Broadcom 43xx chipset. Have a look at Dark Noob's [how to]("http://ubuntuforums.org/showthread.php?t=405990").

It may help.


regards

:)

---

### Post by vortex_noob on 2008-02-25
i did this command in terminal:

lsusb -v
and it says that my chipset is marvell
it doesnt say which type
> 
Bus 005 Device 008: ID 13b1:0029 Linksys 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x13b1 Linksys
  idProduct          0x0029 
  bcdDevice            0.01
  iManufacturer           1 MARVELL 
  iProduct                2 Wireless-N USB network adapter v1021
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          4 #02
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              500mA
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
can't get debug descriptor: Connection timed out
Device Status:     0x0000
  (Bus Powered)


do u think it's a broadcom 43xx chipset?? 
I tried googling on this adapter but hasnt found any useful info

---

