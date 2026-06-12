---
title: "new to ubuntu- problems linksys wusb54v2"
date: 2007-01-03
forum: Networking &amp; Wireless
---

### Post by miclo987 on 2007-01-03
Hello,

I am trying to install and am having problems with the linksys wusb54v2.  I have read all related posts and cannot find a answer.  
this is what I did
1.  I installed ndiswrapper the latest version.  
2.  download drivers from linksys in windows xp 
3.  transfer files to ubuntu 6.10 Edgy Eft
4.  went to folder driver wusb54gv2
5. sudo su
6.  ndiswrapper -l (no drivers  installed)
7. ndiswrapper -i WUSB54Gv2.inf
8. driver installed hardware present
9. modprobe ndiswrapper
10. lshw -C network (not present)
11. iwconfig (not present)
12. ifconfig (notpresent)
13. ndiswrapper -m
14.  module configuration contains directive install usb:v13B1p000Dd*dc*dsc*dp*ic*isc*ip* /sbin/modprobe ndiswrapper
;you should delete thatmodule configuration contains directive install usb:v13B1p0011d*dc*dsc*dp*ic*isc*ip* /sbin/modprobe ndiswrapper
;you should delete thatmodule configuration contains directive install usb:v13B1p001Ad*dc*dsc*dp*ic*isc*ip* /sbin/modprobe ndiswrapper
;you should delete thatAdding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper
root@user-laptop:/home/user/Desktop/Linksys Driver/WUSB54Gv4_20050503/Drivers/WUSB54Gv2# modprobe ndiswrapper
root@user-laptop:/home/user/Desktop/Linksys Driver/WUSB54Gv4_20050503/Drivers/WUSB54Gv2# ndiswrapper -m
module configura> tion contains directive install usb:v13B1p000Dd*dc*dsc*dp*ic*isc*ip* /sbin/modprobe ndiswrapper
;you should delete thatmodule configuration contains directrtive install usb:v13B1p0011d*dc*dsc*dp*ic*isc*ip* /sbin/modprobe ndiswrapper
;you should delete thatmodule configuration contains directive install usb:v13B1p001Ad*dc*dsc*dp*ic*isc*ip* /sbin/modprobe ndiswrapper
;you should delete thatmodprobe config already contains alias directive
(it did say this before I tried other things but still doesn't work)
15.  also tried depmod -a

If anyone has any ideas it would be greatly appreciated.  I tried to get the prism54.org files but they where .asm.  I also haven't tried linux-wlan-ng because I don't know how to use it. I think I removed the mod for pegaus, and rmmod ndiswrapper then sudo apt-get install ndiswrapper-utils-1.8. tried [http://rt2x00.serialmonkey.com/wiki/index.php?title=Main_Page](http://rt2x00.serialmonkey.com/wiki/index.php?title=Main_Page) that did work.  

lsusb -vv

Bus 002 Device 002: ID 13b1:000a Linksys 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x13b1 Linksys
  idProduct          0x000a 
  bcdDevice           10.20
  iManufacturer           1 Cisco-Linksys
  iProduct                2 Wireless-G USB Network Adapter
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           53
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
      bNumEndpoints           5
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
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
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
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         0
  bNumConfigurations      1
Device Status:     0x0000
  (Bus Powered)

thank you for your time and help.  I am new to linux and am not sure what I am really doing.

sincerely,

miclo

---

