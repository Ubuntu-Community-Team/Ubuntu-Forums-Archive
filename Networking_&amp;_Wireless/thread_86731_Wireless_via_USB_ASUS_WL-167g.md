---
title: "Wireless via USB ASUS WL-167g"
date: 2005-11-06
forum: Networking &amp; Wireless
---

### Post by MightyMouse on 2005-11-06
Wireless is pretty difficult to configure and I have by now collected a lot of information. I know that the ASUS USB Wlan adapter contains the RT2500 chipset ( see [http://ralink.rapla.net/](http://ralink.rapla.net/) , courtesy fromAgent86!!!) and this one is compatible with Linux. 
Once the adaptor isconnected vie the USB port I get the following

Bus 004 Device 002: ID 0b05:1706 ASUSTek Computer, Inc.
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0
  bDeviceProtocol         0
  bMaxPacketSize0        64
  idVendor           0x0b05 ASUSTek Computer, Inc.
  idProduct          0x1706
  bcdDevice            0.01
  iManufacturer           1
  iProduct                2
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
can't get device qualifier: Operation not permitted
can't get debug descriptor: Operation not permitted

So the system detects the USB adapter, but I cant see it with iwconfig and therefore neither nduswrapper or WIndows Wireless Driver gui can connect it to the driver I have and that should work.

lo        no wireless extensions.

eth1      no wireless extensions.

eth0      NOT READY!  ESSID:off/any
          Mode:Managed  Channel:0  Access Point: 00:00:00:00:00:00
          Tx-Power=31 dBm   Sensitivity=0/200
          Retry min limit:0   RTS thr=0 B   Fragment thr=0 B
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

Etoh0 is another wireless card (this is a Laptop) that uses a Insel chip set and therefore is named eth0 instead of wlan0. This card I can't get working either, but I anyhow would prefer to use the ASUS USB stick (I have more than one computer)

So I really appreciate any help on making my breezy understand that there is a Wlan adapter at the USB-port it should use for wireless.

Thanks, MightyMouse

---

### Post by Flyby on 2005-12-30
Hy,

I 'm newb to ubuntu and linux and i have also an ASUS WL-167G 802.11g USB card stick so i 'm currious to get this working. There's no backup cabled network available so it's quite important to me to get this working.

grtz

---

### Post by ruiruas on 2008-02-14
Hi,
I don't own this device, but I'm interested in buying a usb adapter and so I'm looking for the ones that work...
I've found a howto in this location. It's in portuguese, but I think you'll be able to follow the code parts.
Read it at:

[http://rdk.homeip.net/wiki/doku.php?...ess:asuswl-167](http://rdk.homeip.net/wiki/doku.php?...ess:asuswl-167)

If you can make it work, please post a new message for the comunity!

---

