---
title: "Samsung mobile"
date: 2011-07-10
forum: New to Ubuntu
---

### Post by RobikShrestha on 2011-07-10
Does anyone know where I can find mobile driver for my samsung z170?
Wine does not support samsung pc suite. Or is there no driver at all?

---

### Post by LowSky on 2011-07-10
what do you need to do?

---

### Post by RobikShrestha on 2011-07-11
I want to be able insert, delete photos and music videos from the phone. I need a samsung pc suite compatible with linux.

---

### Post by nomko on 2011-07-11
You can connect the phone with your computer by using USB. I think you have to switch a setting on your mobile phone, i'm not quit sure. But i think you will get a message from your phone saying that you connect it to a computer. When the connecting is made, your phone acts like an external drive. Like this, you can add/remove/copy/cut/paste all sorts of files.

---

### Post by RobikShrestha on 2011-07-11
I can't change it to USB mode. There is no such option. It can be accessed via that software only.

---

### Post by nomko on 2011-07-12
Can you do this:
 
- connect your mobile to your computer
- open a terminal
- type in: lsusb
- copy the output and paste it here
 
Be sure that your mobile is turned on.

---

### Post by GerryB on 2011-07-12
It will connect as a USB drive only if you have a memory card in the phone. You can then transfer whatever you have in your internal memory to the card and then the rest is easy. I didn't need a driver for mine. Ubuntu recognized it right away. Good luck.

---

### Post by RobikShrestha on 2011-07-12
Output
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 04e8:6601 Samsung Electronics Co., Ltd Z100 Mobile Phone
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0bda:8189 Realtek Semiconductor Corp. RTL8187B Wireless 802.11g 54Mbps Network Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


Bus 002 Device 002 has the mobile phone but mine is z170 I don't know why it lists it as z100.  

I do have a memory card.

---

### Post by RobikShrestha on 2011-07-12
I also tried lsusb -v and the output is:

Bus 002 Device 003: ID 04e8:6601 Samsung Electronics Co., Ltd Z100 Mobile Phone
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            2 Communications
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x04e8 Samsung Electronics Co., Ltd
  idProduct          0x6601 Z100 Mobile Phone
  bcdDevice            0.00
  iManufacturer           1 SAMSUNG Electronics Co.,Ltd.
  iProduct                2 SAMSUNG CDMA Technologies
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           67
    bNumInterfaces          2
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         2 Communications
      bInterfaceSubClass      2 Abstract (modem)
      bInterfaceProtocol      1 AT-commands (v.25ter)
      iInterface              0 
      CDC Header:
        bcdCDC               1.09
      CDC Call Management:
        bmCapabilities       0x03
          call management
          use DataInterface
        bDataInterface          1
      CDC ACM:
        bmCapabilities       0x0f
          connection notifications
          sends break
          line coding and serial state
          get/set/clear comm features
      CDC Union:
        bMasterInterface        0
        bSlaveInterface         1 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0010  1x 16 bytes
        bInterval              32
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass        10 CDC Data
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 
      iInterface              4 Data Interface
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
Device Status:     0x0000
  (Bus Powered)

---

### Post by nomko on 2011-07-13
Ubuntu does see AND recognize your mobile phone. Like GerryB mentioned, do you have a memory card in your phone? If so, Ubuntu must recognize your mobile phone as an external drive. It is not visible as such in Nautilus?

---

### Post by RobikShrestha on 2011-07-13
I have memory card.
I tried nautilus but it does not work.
It does not work as usb mass storage device with windows, I have to use it through samsung software. So I guess card reader is the only way to go around.

---

### Post by nomko on 2011-07-14
> **RobikShrestha said:**
> I have memory card.
I tried nautilus but it does not work.
It does not work as usb mass storage device with windows, I have to use it through samsung software. So I guess card reader is the only way to go around.
 
Yes, If nothing helps, then there's only the option of removing the memory card and place it in a card reader. That should do the trick as well.

---

### Post by GerryB on 2011-07-14
There is a setting somewhere on the phone to connect to computer or usb. It's hard to believe that it doesn't connect to either Windows or Ubuntu...Have you transferred your data from the internal memory to the card? Just trying to understand....

---

### Post by RobikShrestha on 2011-07-14
It does connect on windows but only with the samsung software. I could not find the setting to set it to be used just like a pen drive. I will need a card reader. Guess that's the only solution now.

---

### Post by GerryB on 2011-07-15
"Settings" ...."PC Connection"?

---

### Post by RobikShrestha on 2011-07-15
There is no pc connections option.
It is a samsung z170

---

### Post by GerryB on 2011-07-18
Is this not on your phone?:
(page 10)
Connecting to EDGE network or
transferring data in EDGE
network
UMTS (3G) network
Connecting to UMTS (3G)
network or transferring data in
UMTS (3G) network
Voice call in progress
Out of your service area
Video call in progress
Out of your service area
Roaming network
Bluetooth active

_Connected with PC via a USB port_

Browsing Internet

---

### Post by RobikShrestha on 2011-07-20
There is the option of USB.
However in windows, I can use the phone only with Samsung PC suite and not like a pen drive. Now that PC suite does not work with UBUNTU so I want a driver or whatever it is.

---

### Post by Bodsda on 2011-07-20
According to a review [here]("http://www.gsmarena.com/samsung_z170-reviews-2030p13.php"), the phone "Can't serve as a 'plug and play' mass storage to a PC"
 
You will have to resort to bluetooth, or a seperate card reader by the sounds of it.
 
HTH,
Bodsda
 
EDIT: You could run a Virtual Machine, install Windows and then use that to transfer things to the phone. Slightly annoying, but should work.

---

