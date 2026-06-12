---
title: "wireless k/b, mouse &amp; remote, possible?"
date: 2010-10-21
forum: New to Ubuntu
---

### Post by bance on 2010-10-21
Hi all, 
 
mythbuntu 10. 04, 2.6.35-25 generic Acer aspire Revo 3610
 
I want to have, a wireless k/b & mouse and a remote (mceusb)all working at the same time. Is this possible? If so what do I have to do to enable this? 
 
The k/b & mouse work out of the box, but I can't get the remote to work.

```
david@david-desktop:~$ lsusb
Bus 002 Device 016: ID 1532:0200 Razer USA, Ltd 
Bus 002 Device 015: ID 1532:0009 Razer USA, Ltd 
Bus 002 Device 014: ID 1532:0103 Razer USA, Ltd 
Bus 002 Device 013: ID 04f2:0963 Chicony Electronics Co., Ltd 
Bus 002 Device 012: ID 147a:e03e Formosa Industrial Computing, Inc. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
``````
david@david-desktop:~$ lsusb -v
<snip>
Bus 002 Device 013: ID 04f2:0963 Chicony Electronics Co., Ltd 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x04f2 Chicony Electronics Co., Ltd
  idProduct          0x0963 
  bcdDevice            1.01
  iManufacturer           1 
  iProduct                2 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           59
    bNumInterfaces          2
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower               98mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      1 Boot Interface Subclass
      bInterfaceProtocol      1 Keyboard
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.11
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      63
         Report Descriptors: 
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval              10
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      1 Boot Interface Subclass
      bInterfaceProtocol      2 Mouse
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.11
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength     404
         Report Descriptors: 
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval              10
can't get device qualifier: Operation not permitted
can't get debug descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

Bus 002 Device 012: ID 147a:e03e Formosa Industrial Computing, Inc. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x147a Formosa Industrial Computing, Inc.
  idProduct          0xe03e 
  bcdDevice           10.01
  iManufacturer           1 
  iProduct                2 
  iSerial                 3 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           57
    bNumInterfaces          2
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower              100mA
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
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
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
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      0 No Subclass
      bInterfaceProtocol      0 None
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.00
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      19
         Report Descriptors: 
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval              10
can't get device qualifier: Operation not permitted
can't get debug descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)
<snip>
``````
david@david-desktop:~$ dmesg | grep lirc
[   35.210186] lirc_dev: IR Remote Control driver registered, major 61 
[   35.224824] lirc_mceusb: Windows Media Center Edition USB IR Transceiver driver for LIRC 1.90
[   35.224834] lirc_mceusb: Daniel Melander <lirc@rajidae.se>, Martin Blatter <martin_a_blatter@yahoo.com>, Dan Conti <dconti@acm.wwu.edu>
[   35.224934] usbcore: registered new interface driver lirc_mceusb
``````
david@david-desktop:~$  dmesg | grep mceusb
[   35.224824] lirc_mceusb: Windows Media Center Edition USB IR Transceiver driver for LIRC 1.90
[   35.224834] lirc_mceusb: Daniel Melander <lirc@rajidae.se>, Martin Blatter <martin_a_blatter@yahoo.com>, Dan Conti <dconti@acm.wwu.edu>
[   35.224934] usbcore: registered new interface driver lirc_mceusb

``````
david@david-desktop:~$ cat /proc/bus/input/devices
I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
U: Uniq=
H: Handlers=kbd event0 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/devices/virtual/input/input2
U: Uniq=
H: Handlers=mouse0 event2 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

I: Bus=0001 Vendor=10ec Product=0662 Version=0001
N: Name="HDA Digital PCBeep"
P: Phys=card0/codec#0/beep0
S: Sysfs=/devices/pci0000:00/0000:00:08.0/input/input8
U: Uniq=
H: Handlers=kbd event8 
B: EV=40001
B: SND=6

I: Bus=0003 Vendor=04f2 Product=0963 Version=0111
N: Name="Chicony 2.4G Multimedia Wireless Kit"
P: Phys=usb-0000:00:04.0-6/input0
S: Sysfs=/devices/pci0000:00/0000:00:04.0/usb2/2-6/2-6:1.0/input/input17
U: Uniq=
H: Handlers=kbd event3 
B: EV=120013
B: KEY=10000 7 ff800000 7ff febeffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=7

I: Bus=0003 Vendor=04f2 Product=0963 Version=0111
N: Name="Chicony 2.4G Multimedia Wireless Kit"
P: Phys=usb-0000:00:04.0-6/input1
S: Sysfs=/devices/pci0000:00/0000:00:04.0/usb2/2-6/2-6:1.1/input/input18
U: Uniq=
H: Handlers=kbd mouse1 event4 
B: EV=1f
B: KEY=837fff 2c3027 bf004444 0 0 70001 f84 8a27c000 667bfa d941dfed 9e0000 0 0 0
B: REL=143
B: ABS=1 0
B: MSC=10



```Any help much appreciated,

---

### Post by LowSky on 2010-10-21
they should all work with no issue. I and many others run wireless K/M and remotes.

reinstall mythbuntu-lirc-generator or go to the mythbuntu control center to fix your remote settings.

---

### Post by bance on 2010-10-21
Thanks for your reply Lowsky,

I searched high and low for info.... and turned up nothing obviously useful.

When I delved a little deeper, at the LIRC site I came up with [_this_]("http://www.lirc.org/html/configure.html#multiple"). The only thing is I understand that ubuntu installs Lirc in different places than when lirc is compiled from source, so I'm not sure how relevant it is?

I also found [this]("http://www.mythtv.org/wiki/MultiLIRC"), but it dates from early 2009, I think there have been many changes since then and hence once again the relevancy is doubtful.

I have tried to use control centre to configure myth for the remote, but I still get no response either on-screen or with irw.

I'm not sure how I would re-install mythbuntu lirc generator....

Did you notice that there is no reference to the mceusb remote in the output from ''cat /proc/bus/input/devices''. I don't know if that has any relevance?

---

### Post by bance on 2010-10-23
OK did a clean install of maverick, remote works fine, now to get sound:confused:

---

