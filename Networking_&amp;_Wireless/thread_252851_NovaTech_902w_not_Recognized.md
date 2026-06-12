---
title: "NovaTech 902w not Recognized"
date: 2006-09-07
forum: Networking &amp; Wireless
---

### Post by williamts99 on 2006-09-07
I purchased a few Novatech 902w wireless adapters from Newegg.com a while ago and finally decided to try and load them on my Ubuntu machines instead just sitting there doing nothing with them :-)  So I hooked one up and restarted my computer hoping that it would be like my D-Link WNA-2330 and just work.  Well that didn't happen, so I fired up the terminal and issued the lsusb command.  Here was the output...

```
Bus 003 Device 004: ID 0eb0:9020
Bus 003 Device 001: ID 0000:0000
Bus 001 Device 005: ID 046d:c016 Logitech, Inc. M-UV69a Optical Wheel Mouse
Bus 001 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
```

The first device is the wireless adapter, but it doesn't show up with a name so I did lsusb -v and received this output...

```
Bus 003 Device 004: ID 0eb0:9020
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0
  bDeviceProtocol         0
  bMaxPacketSize0        64
  idVendor           0x0eb0
  idProduct          0x9020
  bcdDevice            0.01
  iManufacturer           1 Ralink
  iProduct                2 802.11g WLAN + Pen Drive
  iSerial                 0
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              300mA
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
Device Status:     0x0000
  (Bus Powered)
```


Which confirms what I thought, it is an ralink chipset but I am wondering why it is not recognized as I thought the ralink chipsets worked out of the box on Ubuntu.

How do I figure out exactly what chipset it is?  Why is it not being recognized?  How do I go about fixing this issue?  And how do I ensure that it gets fixed for future versions of Ubuntu?

Thank You

---

### Post by williamts99 on 2006-09-08
Oh yea, and for the D-Link WNA-2330 all I did was install Network Manager and everything was perfect.

---

### Post by williamts99 on 2006-10-29
Found the problem, and filed a bug [https://launchpad.net/distros/ubuntu/+bug/61797](https://launchpad.net/distros/ubuntu/+bug/61797)

Exact same problem and a fix included.

[http://rt2x00.serialmonkey.com/phpBB2/viewtopic.php?t=1513&sid=a70814e4a3611d1cda067c6907689855](http://rt2x00.serialmonkey.com/phpBB2/viewtopic.php?t=1513&sid=a70814e4a3611d1cda067c6907689855)

Problem was the vendor ID was not included
{ USB_DEVICE(0x0eb0, 0x9020)}, /* Novatech NV-902W */ \

According to serialmonkey, the ID was patched into the cvs Monday June 12th 2006.

It is the rt2570 chip

---

