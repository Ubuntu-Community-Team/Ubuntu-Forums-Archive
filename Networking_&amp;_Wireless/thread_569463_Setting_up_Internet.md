---
title: "Setting up Internet"
date: 2007-10-07
forum: Networking &amp; Wireless
---

### Post by roe-ur-boat on 2007-10-07
Hi there,

I am having problems connecting to the internet in Ubuntu as firstly, This is the first time I've ever used an OS that's not Windows, and secondly, I can't find any answers to my question on these forums here.

My problem is that I have an ISDN connection connected to my computer via USB. How do I get connected to the internet with this?

roe-ur-boat

---

### Post by ZGMF-X20A on 2007-10-07
I also experience tht. I tried the sudo pppoeconf in terminal. But no use. I'm using nVidia nForce networking controller for LAN card

---

### Post by roe-ur-boat on 2007-10-09
Please someone help. I am new to this and haven't a clue.

---

### Post by roe-ur-boat on 2007-10-14
Come on guys, please help.

---

### Post by NightCrawler03X on 2007-10-14
If it's possible, use cat5e cables (or cat5) depending on what ports are available to you.
I use to be on a wireless lan, but then it went pear-shaped.
Wires are still the way to go with networking.

If possible, could you take some pictures of all the ports available to the device(s) you have? (try taking pictures of the actual devices aswell) then upload the pictures to imageshack or something and post them here.

If that's not possible, try and explain in better detail everything about your connection and what devices you use, etc.

Only then can we diagnose your problem.

---

### Post by roe-ur-boat on 2007-10-14
I don't get what you mean. I have [THIS](http://images.ciao.com/iuk/images/products/normal/546/product-18546.jpg) modem and it's connected by USB.

---

### Post by NightCrawler03X on 2007-10-14
Ah, sorry, I was thinking about something else.

sorry, I don't know what to advise.

---

### Post by roe-ur-boat on 2007-10-14
Damn that was pointless... xD Anyone else?

---

### Post by SamiDelovely on 2007-10-14
well i'm in the same boat bub, but i'm closer than u i think cause i used an Ethernet cable. See that help thingy on Ubuntu says that USB is pretty much useless, cause u NEED internet to d-load drivers and utilities. Kind of stupid, but the thing that DOES work is either wireless(which i don't use) and ethernet cable thanks to my bro. So yeah. Ethernet something should be on your shopping list.

---

### Post by roe-ur-boat on 2007-10-15
Well I am able to dl stuff on windows and transfer it over, and even if i did use an ethernet cable, I wouldn't have any idea how it works.

---

### Post by NightCrawler03X on 2007-10-15
> and even if i did use an ethernet cable, I wouldn't have any idea how it works.
So long as you have your network card working, you should just be able to plug in the network cables and have internet access.

---

### Post by mips on 2007-10-15
> **roe-ur-boat said:**
> I don't get what you mean. I have [THIS]("http://images.ciao.com/iuk/images/products/normal/546/product-18546.jpg") modem and it's connected by USB.

Thats a picture which is pretty worthless to be honest.

1. Tell us the Brand & Model number of the device.

2. With the device plugged in post the output of **lsusb -v** or **sudo lsusb -v** here.

---

### Post by mips on 2007-10-15
Simple google search reveals this:

[http://trustusbta.sourceforge.net/](http://trustusbta.sourceforge.net/)
[http://sourceforge.net/projects/trustusbta](http://sourceforge.net/projects/trustusbta)

---

### Post by roe-ur-boat on 2007-10-15
> **mips said:**
> Simple google search reveals this:

[http://trustusbta.sourceforge.net/](http://trustusbta.sourceforge.net/)
[http://sourceforge.net/projects/trustusbta](http://sourceforge.net/projects/trustusbta)
I saw those drivers before but what do i do with them? I will try that lsusb -v thing now and post the output.

---

### Post by roe-ur-boat on 2007-10-15
This isn't the full output, just the part that involves my modem.

```
Bus 002 Device 002: ID 07b0:0007 Trust Technologies 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            2 Communications
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x07b0 Trust Technologies
  idProduct          0x0007 
  bcdDevice            1.00
  iManufacturer           1 
  iProduct                1 ISDN USB TA
  iSerial                 1 ISDN USB TA
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength          199
    bNumInterfaces          2
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower               90mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           0
      bInterfaceClass         2 Communications
      bInterfaceSubClass    128 
      bInterfaceProtocol    255 
      iInterface              0 
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           0
      bInterfaceClass        10 CDC Data
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol    255 Vendor specific
      iInterface              0 
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       1
      bNumEndpoints          16
      bInterfaceClass        10 CDC Data
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol    255 Vendor specific
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0010  1x 16 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0010  1x 16 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0010  1x 16 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0010  1x 16 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0010  1x 16 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0010  1x 16 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x04  EP 4 OUT
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0010  1x 16 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0010  1x 16 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x05  EP 5 OUT
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0010  1x 16 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x85  EP 5 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0010  1x 16 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x06  EP 6 OUT
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0010  1x 16 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x86  EP 6 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0010  1x 16 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x07  EP 7 OUT
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0010  1x 16 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x87  EP 7 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0010  1x 16 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x08  EP 8 OUT
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0010  1x 16 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x88  EP 8 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0010  1x 16 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       2
      bNumEndpoints           6
      bInterfaceClass        10 CDC Data
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol    255 Vendor specific
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               4
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               4
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               4
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x05  EP 5 OUT
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0010  1x 16 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x06  EP 6 OUT
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0010  1x 16 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x07  EP 7 OUT
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0010  1x 16 bytes
        bInterval               1
Device Status:     0x0000
  (Bus Powered)
```

---

### Post by mips on 2007-10-16
Ok the ISDN adapter is seen by your computer which is a start.

Next look at those drivers and install them, read the guides. I do not have such a card so can't really help any further. Just follow the instructions.

---

### Post by roe-ur-boat on 2007-10-16
> **mips said:**
> Ok the ISDN adapter is seen by your computer which is a start.

Next look at those drivers and install them, read the guides. I do not have such a card so can't really help any further. Just follow the instructions.
Ok I'll look into finding how to install them then do it and post back results. Thanks for all your help btw.

---

