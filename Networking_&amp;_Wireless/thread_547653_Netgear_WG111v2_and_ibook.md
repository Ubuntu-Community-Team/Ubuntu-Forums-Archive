---
title: "Netgear WG111v2 and ibook"
date: 2007-09-10
forum: Networking &amp; Wireless
---

### Post by Bergera on 2007-09-10
I was able to install fiesty fawn on my g3 600mhz ibook over the weekend, and I was able to get X working with the help of these forums.

Now I am having trouble getting my netgear wg111v2 working with the ibook. It works great with my dell inspiron 5150, but not my ibook.

Here is what dmesg says when I insert in and try to set it up.

[48267.544553] usb 2-1: new full speed USB device using ohci_hcd and address 2
[48267.755819] usb 2-1: configuration #1 chosen from 1 choice
[48270.622499] wmaster0: Selected rate control algorithm 'simple'
[48270.923659] wiphy0: hwaddr 00:14:6c:62:49:f7, rtl8187 V1 + rtl8225
[48270.923710] usbcore: registered new interface driver rtl8187
[48425.120087] RF Calibration Failed!!!! 652
[48432.937030] wmaster0: Does not support passive scan, disabled
[48443.814792] wlan0: no IPv6 routers present

Thanks for any help you can provide.
-Aaron

---

### Post by Bergera on 2007-09-10
here is the information from the lsusb -v command

Bus 001 Device 002: ID 0846:6a00 NetGear, Inc. WG111 WiFi (v2)
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x0846 NetGear, Inc.
  idProduct          0x6a00 WG111 WiFi (v2)
  bcdDevice            1.00
  iManufacturer           1 
  iProduct                2 
  iSerial                 3 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           39
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          4 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           3
      bInterfaceClass         0 (Defined at Interface level)
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              5 
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
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0

---

### Post by bwiklak on 2007-09-10
Hi, 
I have the same problem with the same USB wifi dongle and IBook G3 600Mhz. I can see hardware installed but no network is recognized. On Compaq N610c everything works fine out of th box.

I still digging, and trying to find drivers rtl8187 for 2.6.x kernel so I can rebuild them.
Is I'll get it working I will post results. Also if someone knows solution please post it here.

---

### Post by Bergera on 2007-09-10
thanks, good to see that their is another person with the problem, maybe the two of us can figure it out. I just tried it on my i386 laptop and it works great, and the dmesg output looks the same.

I agree that maybe recompiling the rtl8187 drivers may fix it.

heres to hoping

---

