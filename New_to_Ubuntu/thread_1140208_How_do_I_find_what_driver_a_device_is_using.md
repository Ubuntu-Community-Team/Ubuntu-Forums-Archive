---
title: "How do I find what driver a device is using?"
date: 2009-04-27
forum: New to Ubuntu
---

### Post by bryceowen on 2009-04-27
I'm trying to solve my touchscreen issue on my own by writing a custom xorg.conf file and I've run into a small problem. I don't know what driver my touchscreen is currently using. If someone could tell me where to look, I'd appreciate it.

Here's the output of lsusb -v:
```

Bus 001 Device 002: ID 0430:0508 Sun Microsystems, Inc. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x0430 Sun Microsystems, Inc.
  idProduct          0x0508 
  bcdDevice           11.30
  iManufacturer           1 
  iProduct                2 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           34
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower               20mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      1 Boot Interface Subclass
      bInterfaceProtocol      2 Mouse
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.00
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      58
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

Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0001 1.1 root hub
  bcdDevice            2.06
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255

```
And cat /proc/bus/input/devices:
```

I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/devices/virtual/input/input0
U: Uniq=
H: Handlers=mouse0 event0 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

I: Bus=0011 Vendor=0001 Product=0001 Version=ab54
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/devices/platform/i8042/serio0/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: EV=120013
B: KEY=4 2000000 3803078 f800d001 feffffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=7
[b]
I: Bus=0003 Vendor=0430 Product=0508 Version=0100
N: Name="Fujitsu Takamisawa USB Touch Panel"
P: Phys=usb-0000:00:02.0-3/input0
S: Sysfs=/devices/pci0000:00/0000:00:02.0/usb1/1-3/1-3:1.0/input/input2
U: Uniq=
H: Handlers=mouse1 js0 event2 
B: EV=1b
B: KEY=70000 0 0 0 0 0 0 0 0
B: ABS=3
B: MSC=10
[/b]
I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/devices/platform/pcspkr/input/input3
U: Uniq=
H: Handlers=kbd event3 
B: EV=40001
B: SND=6

I: Bus=0019 Vendor=0000 Product=0002 Version=0000
N: Name="Power Button (FF)"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input4
U: Uniq=
H: Handlers=kbd event4 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button (CM)"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input5
U: Uniq=
H: Handlers=kbd event5 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0005 Version=0000
N: Name="Lid Switch"
P: Phys=PNP0C0D/button/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input6
U: Uniq=
H: Handlers=event6 
B: EV=21
B: SW=1

I: Bus=0019 Vendor=0000 Product=0006 Version=0000
N: Name="Fujitsu FUJ02B1"
P: Phys=FUJ02B1/video/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:02/FUJ02B1:00/input/input7
U: Uniq=
H: Handlers=kbd event7 
B: EV=3
B: KEY=10003 0 0 0 0 0 0 0

I: Bus=0011 Vendor=0002 Product=000a Version=0000
N: Name="TPPS/2 IBM TrackPoint"
P: Phys=isa0060/serio1/input0
S: Sysfs=/devices/platform/i8042/serio1/input/input8
U: Uniq=
H: Handlers=mouse2 event8 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

I: Bus=0019 Vendor=0000 Product=0006 Version=0000
N: Name="Video Bus"
P: Phys=/video/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:08/input/input9
U: Uniq=
H: Handlers=kbd event9 
B: EV=3
B: KEY=3f000b 0 0 0 0 0 0 0

```
Referring to [this thread]("http://ubuntuforums.org/showthread.php?t=419235"), I was planning on copying what he setup in his xorg.conf and see what it does for me. When I get to the 'Driver' line, however, I don't know what to say.

---

### Post by MontelEdwards on 2009-05-06
What do you mean "driver version"?

---

