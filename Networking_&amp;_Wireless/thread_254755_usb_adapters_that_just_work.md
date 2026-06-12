---
title: "usb adapters that just work?"
date: 2006-09-10
forum: Networking &amp; Wireless
---

### Post by bennycb on 2006-09-10
I have seen lists of cards that work with 6.06 - but I need to use a USB stick and I'm tearing my hair out trying to make it work.

If I can get wireless working, I can use Ubuntu so is there a list of USB adapters that work out of the box? 

If I can find one that will definitely work, I'll just buy it because I haven't got the time to spend trying to make the one I have work right. It will be worth it to say byebye Windows. Otherwise I will have to abandon Ubuntu instead :( 

Cheers

Ben

---

### Post by lukew on 2006-09-10
Hi,

I am using the linksys usb11v4 and it was detected on its own, shown using lsusb. I had to use ndswrapper but that we very simple! It only take 10 minutes and there are always people to help when you are stuck!

Luke

---

### Post by bennycb on 2006-09-12
Thanks for your reply.

I am trying to work out whether my usb adapter will work (can't find it in any lists). With ndiswraper I have installed the Windows driver, and entering ndiswrapper -l says that the driver is present but the hardware is not.

Is there a way that a newb can get his head round, of getting the actual hardware recognised?

Below is some output from lsusb -v

Cheers

Ben

> 

Bus 003 Device 002: ID 18e8:6201
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0
  bDeviceProtocol         0
  bMaxPacketSize0        64
  idVendor           0x18e8
  idProduct          0x6201
  bcdDevice           87.65
  iManufacturer           1 WINBOND
  iProduct                2 Usb2Wlan
  iSerial                 3 101d350112
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           49
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           4
      bInterfaceClass         0 (Defined at Interface level)
      bInterfaceSubClass      0
      bInterfaceProtocol      0
      iInterface              0
      UNRECOGNIZED:  03 08 3f
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x04  EP 4 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               1
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




---

