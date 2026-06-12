---
title: "USB Wifi Dongle: Make Genius Model GW-7200U"
date: 2008-05-02
forum: Networking &amp; Wireless
---

### Post by hannah187 on 2008-05-02
Hi,
I am trying to figure the chipset. Have already visited 
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported#head-603c9481d6c6288b6b674cc50132d21f6d539c53](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported#head-603c9481d6c6288b6b674cc50132d21f6d539c53)

However could not find any reference of Genius Model GW-7200U. I also have run command
lsusb -v | less at the terminal with my USB dongle plugged in. Please find below the response in the terminal:
__________________________________________________________
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x0457 Silicon Integrated Systems Corp.
  idProduct          0x0163 
  bcdDevice            1.00
  iManufacturer           0 
  iProduct                0 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           39
    bNumInterfaces          1
    bConfigurationValue     1
:can't get device qualifier: Operation not permitted
can't get debug descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)
can't get hub descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

________________________________________________

Please give me pointer.

Many thanks as always

---

### Post by dstew on 2008-05-02
The dongle has a Silicon Integrated Systems chipset, variety 0163. The PCI id number is 0457:0163 (the combination of the idVendor and idProduct lines). If you search for this ID, you find this chipset in some Mentor wireless cards, and you can get it to work using ndiswrapper. The windows driver you need is named sis163u.sys, and the .inf file to install it is sis163u.inf.

---

### Post by hannah187 on 2008-05-03
> **dstew said:**
> The dongle has a Silicon Integrated Systems chipset, variety 0163. The PCI id number is 0457:0163 (the combination of the idVendor and idProduct lines). 


Hey thanks.. Just interrested where and how you got this info.

Cheers

---

### Post by hannah187 on 2008-05-03
> **hannah187 said:**
> Hey thanks.. Just interrested where and how you got this info.

Cheers

Hey no worries.. I now understand how you got the info. Appreciate your help.

Thanks a lot

---

