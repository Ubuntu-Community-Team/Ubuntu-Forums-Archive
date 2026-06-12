---
title: "cannot Medion 98200 built-in wireless o work in 7.10"
date: 2007-10-20
forum: Networking &amp; Wireless
---

### Post by Louis3 on 2007-10-20
Hi,

Having installed Ubuntu recently (and upgraded to 7.10  *very* recently) I seem unable to get my wireless  to work. Help would be highly appreciated.

Some facts:
[LIST]
[*]The PC is a MEDION 98200, bought March  2007
[*]The built in Wifi is listed under Windows Vista as 'Atheron AR5007UG' This is apparently identical to a ZyDAS zd1211rw.
[*]'lsusb' shows a ZyDASdevice, Detailed info ('lsusb -v') listed at the end of e-mail. I am not able to tell if it is actually the zd1211rw, but I know of no other ZyDAS/Atheron devices in this laptop
[*]'lsmod' shows that the zd1211rw driver is present
[*]'lshw' will not mention the device.
[*]Nothing I could think of brought the interface alive. I tried the WirelessTroubleshooting and WifiTroubleshooting community pages. I guess I'm doing something wrong...
[/LIST]

Thanks in advance
Louis

Details from lsusb -v:

Bus 005 Device 003: ID 0ace:1215 ZyDAS 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass          255 Vendor Specific Class
  bDeviceSubClass       255 Vendor Specific Subclass
  bDeviceProtocol       255 Vendor Specific Protocol
  bMaxPacketSize0        64
  idVendor           0x0ace ZyDAS
  idProduct          0x1215 
  bcdDevice           48.10
  iManufacturer          16 
  iProduct               32 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           46
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
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              0 
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
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
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
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x04  EP 4 OUT
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
can't get device qualifier: Operation not permitted
can't get debug descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

---

### Post by isoengas on 2007-10-22
Hi,

I have the same wifi adapter, and I was only able to make it work using ndiswrapper and the WinXP drivers (and blacklisting zd1211rw)

I've been told that 2.6.23 kernel has a working driver for this card, though.

---

### Post by stevechaloner on 2007-10-24
I've got this working on my laptop, courtesy of my friendly local linux expert.  From his notes:

-----------------------
Once:
tar jxvf linux-2.6.23.1.tar.bz2
cp -r linux-2.6.23.1/drivers/net/wireless/zd1211rw .
rm -rf linux-2.6.23.1

Every kernel upgrade:
cd zd1211rw
make -C /lib/modules/`uname -r`/build SUBDIRS=`pwd` modules
sudo make -C /lib/modules/`uname -r`/build SUBDIRS=`pwd` modules_install
sudo rm /lib/modules/`uname -r`/kernel/drivers/net/wireless/zd1211rw/zd1211rw.ko
sudo depmod -a

I had to add zd1211rw to /etc/modules otherwise it would not load automatically for some reason. 
-----------------------

- Steve

---

