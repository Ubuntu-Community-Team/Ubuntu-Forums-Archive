---
title: "Dell Wireless 5570 HSPA+ on Kubuntu 13.04"
date: 2013-10-06
forum: Networking &amp; Wireless
---

### Post by Miiro_Juuso on 2013-10-06
Hello everyone,

I'm installing Kubuntu 13.04 on Dell Latitude E7240, and can't seem to get the WWAN device working. Apparently the device is actually something manufactured by Sierra Wireless, but I can't find any information from them either. I would presume the device is supported, as this laptop is available with Ubuntu 12.04 as well.

Does anyone have any pointers on this?

lsusb -v output regarding the device:

```

Bus 002 Device 008: ID 413c:81a3 Dell Computer Corp. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x413c Dell Computer Corp.
  idProduct          0x81a3 
  bcdDevice            0.06
  iManufacturer           1 Sierra Wireless, Incorporated
  iProduct                2 Dell Wireless 5570 HSPA+ (42Mbps) Mobile Broadband Card
  iSerial                 3 
  bNumConfigurations      2
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength          204
    bNumInterfaces          4
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        2
      bAlternateSetting       0
      bNumEndpoints           3
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              0 
      ** UNRECOGNIZED:  05 24 00 10 01
      ** UNRECOGNIZED:  05 24 01 00 00
      ** UNRECOGNIZED:  04 24 02 02
      ** UNRECOGNIZED:  05 24 06 00 00
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x000c  1x 12 bytes
        bInterval               9
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
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        3
      bAlternateSetting       0
      bNumEndpoints           3
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              0 
      ** UNRECOGNIZED:  05 24 00 10 01
      ** UNRECOGNIZED:  05 24 01 00 00
      ** UNRECOGNIZED:  04 24 02 02
      ** UNRECOGNIZED:  05 24 06 00 00
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x000c  1x 12 bytes
        bInterval               9
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        8
      bAlternateSetting       0
      bNumEndpoints           3
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x86  EP 6 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x000a  1x 10 bytes
        bInterval               9
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x85  EP 5 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
        ** UNRECOGNIZED:  2c ff 42 49 53 54 00 01 07 f5 40 f6 00 00 00 00 01 f7 c4 09 02 f8 c4 09 03 f9 88 13 04 fa 10 27 05 fb 10 27 06 fc c4 09 07 fd c4 09
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
        bEndpointAddress     0x87  EP 7 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x04  EP 4 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           82
    bNumInterfaces          2
    bConfigurationValue     2
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower              500mA
    Interface Association:
      bLength                 8
      bDescriptorType        11
      bFirstInterface        12
      bInterfaceCount         2
      bFunctionClass          2 Communications
      bFunctionSubClass      14 
      bFunctionProtocol       0 
      iFunction               0 
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber       12
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         2 Communications
      bInterfaceSubClass     14 
      bInterfaceProtocol      0 
      iInterface              0 
      CDC Header:
        bcdCDC               1.10
      UNRECOGNIZED CDC:  0c 24 1b 00 01 00 10 10 80 e0 0f 20
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               9
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber       13
      bAlternateSetting       0
      bNumEndpoints           0
      bInterfaceClass        10 CDC Data
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      2 
      iInterface              0 
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber       13
      bAlternateSetting       1
      bNumEndpoints           2
      bInterfaceClass        10 CDC Data
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      2 
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
  bNumConfigurations      2
Device Status:     0x0000
  (Bus Powered)

```

Upgraded to kernel 3.11 to get the Intel WiFi working.
```

root@latitude:~# uname -a
Linux latitude 3.11.0-031100-generic #201309021735 SMP Mon Sep 2 21:36:21 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

```

Any help would be appreciated.


Thanks,

Miiro

---

### Post by varunendra on 2013-10-06
Welcome to the forums miiro!

I don't have the newer kernel, but does this return any output ? -
```
modprobe -c | grep -i 413c.*81a3
```

If not, remove the modem, re-plug and post back the output of -
```
dmesg | tail -20
```

---

### Post by Miiro_Juuso on 2013-10-07
Hi Varunendra,

Thank you for your reply. Modprobe does not return any output:
```

root@latitude:~# modprobe -c | grep -i 413c.*81a3
root@latitude:~# 

```

I am unable to unplug the modem, as it is a PCI Express mini card. However, the complete dmesg output is as follows:
```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 3.11.0-031100-generic (apw@gomeisa) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #201309021735 SMP Mon Sep 2 21:36:21 UTC 2013
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.11.0-031100-generic root=UUID=25b76ef6-ad5d-4e77-903b-4a0031d573da ro quiet splash i8042.reset i8042.nomux vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000004efff] usable
[    0.000000] BIOS-e820: [mem 0x000000000004f000-0x000000000004ffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000050000-0x000000000009efff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009f000-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000cf9bbfff] usable
[    0.000000] BIOS-e820: [mem 0x00000000cf9bc000-0x00000000cf9c2fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000cf9c3000-0x00000000d05d6fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000d05d7000-0x00000000d0aa6fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000d0aa7000-0x00000000d7db3fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000d7db4000-0x00000000d7ffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000d8000000-0x00000000d8759fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000d875a000-0x00000000d87fffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000d8800000-0x00000000d8fadfff] usable
[    0.000000] BIOS-e820: [mem 0x00000000d8fae000-0x00000000d8ffffff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000d9000000-0x00000000da71bfff] usable
[    0.000000] BIOS-e820: [mem 0x00000000da71c000-0x00000000da7fffff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000da800000-0x00000000dbcf8fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000dbcf9000-0x00000000dbffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000dd000000-0x00000000df1fffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000f8000000-0x00000000fbffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed00000-0x00000000fed03fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed1ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ff000000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000021edfffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] efi: EFI v2.31 by American Megatrends
[    0.000000] efi:  ACPI 2.0=0xd8fef000  ACPI=0xd8fef000  SMBIOS=0xf04c0  MPS=0xfd6c0 
[    0.000000] efi: mem00: type=3, attr=0xf, range=[0x0000000000000000-0x0000000000008000) (0MB)
[    0.000000] efi: mem01: type=7, attr=0xf, range=[0x0000000000008000-0x000000000003d000) (0MB)
[    0.000000] efi: mem02: type=4, attr=0xf, range=[0x000000000003d000-0x000000000004f000) (0MB)
[    0.000000] efi: mem03: type=0, attr=0xf, range=[0x000000000004f000-0x0000000000050000) (0MB)
[    0.000000] efi: mem04: type=3, attr=0xf, range=[0x0000000000050000-0x000000000009f000) (0MB)
[    0.000000] efi: mem05: type=0, attr=0xf, range=[0x000000000009f000-0x00000000000a0000) (0MB)
[    0.000000] efi: mem06: type=2, attr=0xf, range=[0x0000000000100000-0x0000000001506000) (20MB)
[    0.000000] efi: mem07: type=7, attr=0xf, range=[0x0000000001506000-0x0000000002000000) (10MB)
[    0.000000] efi: mem08: type=2, attr=0xf, range=[0x0000000002000000-0x0000000003406000) (20MB)
[    0.000000] efi: mem09: type=7, attr=0xf, range=[0x0000000003406000-0x00000000343c4000) (783MB)
[    0.000000] efi: mem10: type=2, attr=0xf, range=[0x00000000343c4000-0x00000000361da000) (30MB)
[    0.000000] efi: mem11: type=7, attr=0xf, range=[0x00000000361da000-0x00000000978d4000) (1558MB)
[    0.000000] efi: mem12: type=2, attr=0xf, range=[0x00000000978d4000-0x00000000ccac9000) (849MB)
[    0.000000] efi: mem13: type=4, attr=0xf, range=[0x00000000ccac9000-0x00000000ccbc9000) (1MB)
[    0.000000] efi: mem14: type=7, attr=0xf, range=[0x00000000ccbc9000-0x00000000ce46f000) (24MB)
[    0.000000] efi: mem15: type=4, attr=0xf, range=[0x00000000ce46f000-0x00000000cec06000) (7MB)
[    0.000000] efi: mem16: type=7, attr=0xf, range=[0x00000000cec06000-0x00000000cec14000) (0MB)
[    0.000000] efi: mem17: type=4, attr=0xf, range=[0x00000000cec14000-0x00000000cec62000) (0MB)
[    0.000000] efi: mem18: type=7, attr=0xf, range=[0x00000000cec62000-0x00000000cec6f000) (0MB)
[    0.000000] efi: mem19: type=4, attr=0xf, range=[0x00000000cec6f000-0x00000000ced13000) (0MB)
[    0.000000] efi: mem20: type=7, attr=0xf, range=[0x00000000ced13000-0x00000000ced20000) (0MB)
[    0.000000] efi: mem21: type=4, attr=0xf, range=[0x00000000ced20000-0x00000000cedc4000) (0MB)
[    0.000000] efi: mem22: type=7, attr=0xf, range=[0x00000000cedc4000-0x00000000cedd1000) (0MB)
[    0.000000] efi: mem23: type=4, attr=0xf, range=[0x00000000cedd1000-0x00000000cee35000) (0MB)
[    0.000000] efi: mem24: type=7, attr=0xf, range=[0x00000000cee35000-0x00000000cee38000) (0MB)
[    0.000000] efi: mem25: type=4, attr=0xf, range=[0x00000000cee38000-0x00000000cee86000) (0MB)
[    0.000000] efi: mem26: type=7, attr=0xf, range=[0x00000000cee86000-0x00000000cee93000) (0MB)
[    0.000000] efi: mem27: type=4, attr=0xf, range=[0x00000000cee93000-0x00000000cef37000) (0MB)
[    0.000000] efi: mem28: type=7, attr=0xf, range=[0x00000000cef37000-0x00000000cef44000) (0MB)
[    0.000000] efi: mem29: type=4, attr=0xf, range=[0x00000000cef44000-0x00000000cefe8000) (0MB)
[    0.000000] efi: mem30: type=7, attr=0xf, range=[0x00000000cefe8000-0x00000000ceff5000) (0MB)
[    0.000000] efi: mem31: type=4, attr=0xf, range=[0x00000000ceff5000-0x00000000cf099000) (0MB)
[    0.000000] efi: mem32: type=7, attr=0xf, range=[0x00000000cf099000-0x00000000cf0a6000) (0MB)
[    0.000000] efi: mem33: type=4, attr=0xf, range=[0x00000000cf0a6000-0x00000000cf14a000) (0MB)
[    0.000000] efi: mem34: type=7, attr=0xf, range=[0x00000000cf14a000-0x00000000cf157000) (0MB)
[    0.000000] efi: mem35: type=4, attr=0xf, range=[0x00000000cf157000-0x00000000cf1fb000) (0MB)
[    0.000000] efi: mem36: type=7, attr=0xf, range=[0x00000000cf1fb000-0x00000000cf208000) (0MB)
[    0.000000] efi: mem37: type=4, attr=0xf, range=[0x00000000cf208000-0x00000000cf2ac000) (0MB)
[    0.000000] efi: mem38: type=7, attr=0xf, range=[0x00000000cf2ac000-0x00000000cf2b9000) (0MB)
[    0.000000] efi: mem39: type=4, attr=0xf, range=[0x00000000cf2b9000-0x00000000cf35d000) (0MB)
[    0.000000] efi: mem40: type=7, attr=0xf, range=[0x00000000cf35d000-0x00000000cf36a000) (0MB)
[    0.000000] efi: mem41: type=4, attr=0xf, range=[0x00000000cf36a000-0x00000000cf9bc000) (6MB)
[    0.000000] efi: mem42: type=10, attr=0xf, range=[0x00000000cf9bc000-0x00000000cf9c3000) (0MB)
[    0.000000] efi: mem43: type=4, attr=0xf, range=[0x00000000cf9c3000-0x00000000cfd59000) (3MB)
[    0.000000] efi: mem44: type=3, attr=0xf, range=[0x00000000cfd59000-0x00000000d05ab000) (8MB)
[    0.000000] efi: mem45: type=4, attr=0xf, range=[0x00000000d05ab000-0x00000000d05bc000) (0MB)
[    0.000000] efi: mem46: type=3, attr=0xf, range=[0x00000000d05bc000-0x00000000d05ce000) (0MB)
[    0.000000] efi: mem47: type=4, attr=0xf, range=[0x00000000d05ce000-0x00000000d05d7000) (0MB)
[    0.000000] efi: mem48: type=6, attr=0x800000000000000f, range=[0x00000000d05d7000-0x00000000d0aa7000) (4MB)
[    0.000000] efi: mem49: type=4, attr=0xf, range=[0x00000000d0aa7000-0x00000000d0ab9000) (0MB)
[    0.000000] efi: mem50: type=7, attr=0xf, range=[0x00000000d0ab9000-0x00000000d0ac2000) (0MB)
[    0.000000] efi: mem51: type=4, attr=0xf, range=[0x00000000d0ac2000-0x00000000d0b55000) (0MB)
[    0.000000] efi: mem52: type=7, attr=0xf, range=[0x00000000d0b55000-0x00000000d0b62000) (0MB)
[    0.000000] efi: mem53: type=4, attr=0xf, range=[0x00000000d0b62000-0x00000000d0c06000) (0MB)
[    0.000000] efi: mem54: type=7, attr=0xf, range=[0x00000000d0c06000-0x00000000d0c13000) (0MB)
[    0.000000] efi: mem55: type=4, attr=0xf, range=[0x00000000d0c13000-0x00000000d0cb7000) (0MB)
[    0.000000] efi: mem56: type=7, attr=0xf, range=[0x00000000d0cb7000-0x00000000d0cc4000) (0MB)
[    0.000000] efi: mem57: type=4, attr=0xf, range=[0x00000000d0cc4000-0x00000000d0d39000) (0MB)
[    0.000000] efi: mem58: type=7, attr=0xf, range=[0x00000000d0d39000-0x00000000d0f28000) (1MB)
[    0.000000] efi: mem59: type=4, attr=0xf, range=[0x00000000d0f28000-0x00000000d1048000) (1MB)
[    0.000000] efi: mem60: type=7, attr=0xf, range=[0x00000000d1048000-0x00000000d1054000) (0MB)
[    0.000000] efi: mem61: type=4, attr=0xf, range=[0x00000000d1054000-0x00000000d10a2000) (0MB)
[    0.000000] efi: mem62: type=7, attr=0xf, range=[0x00000000d10a2000-0x00000000d10af000) (0MB)
[    0.000000] efi: mem63: type=4, attr=0xf, range=[0x00000000d10af000-0x00000000d1248000) (1MB)
[    0.000000] efi: mem64: type=7, attr=0xf, range=[0x00000000d1248000-0x00000000d124c000) (0MB)
[    0.000000] efi: mem65: type=4, attr=0xf, range=[0x00000000d124c000-0x00000000d127b000) (0MB)
[    0.000000] efi: mem66: type=7, attr=0xf, range=[0x00000000d127b000-0x00000000d1288000) (0MB)
[    0.000000] efi: mem67: type=4, attr=0xf, range=[0x00000000d1288000-0x00000000d1325000) (0MB)
[    0.000000] efi: mem68: type=7, attr=0xf, range=[0x00000000d1325000-0x00000000d1332000) (0MB)
[    0.000000] efi: mem69: type=4, attr=0xf, range=[0x00000000d1332000-0x00000000d13d6000) (0MB)
[    0.000000] efi: mem70: type=7, attr=0xf, range=[0x00000000d13d6000-0x00000000d13e3000) (0MB)
[    0.000000] efi: mem71: type=4, attr=0xf, range=[0x00000000d13e3000-0x00000000d1557000) (1MB)
[    0.000000] efi: mem72: type=7, attr=0xf, range=[0x00000000d1557000-0x00000000d1564000) (0MB)
[    0.000000] efi: mem73: type=4, attr=0xf, range=[0x00000000d1564000-0x00000000d15e7000) (0MB)
[    0.000000] efi: mem74: type=7, attr=0xf, range=[0x00000000d15e7000-0x00000000d15f4000) (0MB)
[    0.000000] efi: mem75: type=4, attr=0xf, range=[0x00000000d15f4000-0x00000000d1698000) (0MB)
[    0.000000] efi: mem76: type=7, attr=0xf, range=[0x00000000d1698000-0x00000000d16a5000) (0MB)
[    0.000000] efi: mem77: type=4, attr=0xf, range=[0x00000000d16a5000-0x00000000d1749000) (0MB)
[    0.000000] efi: mem78: type=7, attr=0xf, range=[0x00000000d1749000-0x00000000d174d000) (0MB)
[    0.000000] efi: mem79: type=4, attr=0xf, range=[0x00000000d174d000-0x00000000d192f000) (1MB)
[    0.000000] efi: mem80: type=7, attr=0xf, range=[0x00000000d192f000-0x00000000d1935000) (0MB)
[    0.000000] efi: mem81: type=4, attr=0xf, range=[0x00000000d1935000-0x00000000d1eb9000) (5MB)
[    0.000000] efi: mem82: type=7, attr=0xf, range=[0x00000000d1eb9000-0x00000000d1ec0000) (0MB)
[    0.000000] efi: mem83: type=4, attr=0xf, range=[0x00000000d1ec0000-0x00000000d1f67000) (0MB)
[    0.000000] efi: mem84: type=7, attr=0xf, range=[0x00000000d1f67000-0x00000000d1f6b000) (0MB)
[    0.000000] efi: mem85: type=4, attr=0xf, range=[0x00000000d1f6b000-0x00000000d20ef000) (1MB)
[    0.000000] efi: mem86: type=7, attr=0xf, range=[0x00000000d20ef000-0x00000000d20f1000) (0MB)
[    0.000000] efi: mem87: type=4, attr=0xf, range=[0x00000000d20f1000-0x00000000d25e9000) (4MB)
[    0.000000] efi: mem88: type=7, attr=0xf, range=[0x00000000d25e9000-0x00000000d25ef000) (0MB)
[    0.000000] efi: mem89: type=4, attr=0xf, range=[0x00000000d25ef000-0x00000000d2d9e000) (7MB)
[    0.000000] efi: mem90: type=7, attr=0xf, range=[0x00000000d2d9e000-0x00000000d2d9f000) (0MB)
[    0.000000] efi: mem91: type=4, attr=0xf, range=[0x00000000d2d9f000-0x00000000d2dc1000) (0MB)
[    0.000000] efi: mem92: type=7, attr=0xf, range=[0x00000000d2dc1000-0x00000000d2dc4000) (0MB)
[    0.000000] efi: mem93: type=4, attr=0xf, range=[0x00000000d2dc4000-0x00000000d2dd2000) (0MB)
[    0.000000] efi: mem94: type=7, attr=0xf, range=[0x00000000d2dd2000-0x00000000d2ddf000) (0MB)
[    0.000000] efi: mem95: type=4, attr=0xf, range=[0x00000000d2ddf000-0x00000000d5000000) (34MB)
[    0.000000] efi: mem96: type=7, attr=0xf, range=[0x00000000d5000000-0x00000000d5944000) (9MB)
[    0.000000] efi: mem97: type=1, attr=0xf, range=[0x00000000d5944000-0x00000000d5962000) (0MB)
[    0.000000] efi: mem98: type=3, attr=0xf, range=[0x00000000d5962000-0x00000000d6000000) (6MB)
[    0.000000] efi: mem99: type=7, attr=0xf, range=[0x00000000d6000000-0x00000000d7db4000) (29MB)
[    0.000000] efi: mem100: type=6, attr=0x800000000000000f, range=[0x00000000d7db4000-0x00000000d8000000) (2MB)
[    0.000000] efi: mem101: type=7, attr=0xf, range=[0x00000000d8000000-0x00000000d875a000) (7MB)
[    0.000000] efi: mem102: type=5, attr=0x800000000000000f, range=[0x00000000d875a000-0x00000000d8800000) (0MB)
[    0.000000] efi: mem103: type=7, attr=0xf, range=[0x00000000d8800000-0x00000000d8fae000) (7MB)
[    0.000000] efi: mem104: type=9, attr=0xf, range=[0x00000000d8fae000-0x00000000d9000000) (0MB)
[    0.000000] efi: mem105: type=7, attr=0xf, range=[0x00000000d9000000-0x00000000da71c000) (23MB)
[    0.000000] efi: mem106: type=10, attr=0xf, range=[0x00000000da71c000-0x00000000da800000) (0MB)
[    0.000000] efi: mem107: type=7, attr=0xf, range=[0x00000000da800000-0x00000000dbced000) (20MB)
[    0.000000] efi: mem108: type=2, attr=0xf, range=[0x00000000dbced000-0x00000000dbcf9000) (0MB)
[    0.000000] efi: mem109: type=0, attr=0xf, range=[0x00000000dbcf9000-0x00000000dc000000) (3MB)
[    0.000000] efi: mem110: type=0, attr=0x8000000000000000, range=[0x00000000dd000000-0x00000000df200000) (34MB)
[    0.000000] efi: mem111: type=11, attr=0x8000000000000001, range=[0x00000000f8000000-0x00000000fc000000) (64MB)
[    0.000000] efi: mem112: type=11, attr=0x8000000000000001, range=[0x00000000fec00000-0x00000000fec01000) (0MB)
[    0.000000] efi: mem113: type=11, attr=0x8000000000000001, range=[0x00000000fed00000-0x00000000fed04000) (0MB)
[    0.000000] efi: mem114: type=11, attr=0x8000000000000001, range=[0x00000000fed1c000-0x00000000fed20000) (0MB)
[    0.000000] efi: mem115: type=11, attr=0x8000000000000001, range=[0x00000000fee00000-0x00000000fee01000) (0MB)
[    0.000000] efi: mem116: type=11, attr=0x8000000000000001, range=[0x00000000ff000000-0x0000000100000000) (16MB)
[    0.000000] efi: mem117: type=7, attr=0xf, range=[0x0000000100000000-0x000000021ee00000) (4590MB)
[    0.000000] SMBIOS 2.7 present.
[    0.000000] DMI: Dell Inc. Latitude E7240/05PTPV, BIOS A03 08/14/2013
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] No AGP bridge found
[    0.000000] e820: last_pfn = 0x21ee00 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-DBFFF write-protect
[    0.000000]   DC000-DFFFF uncachable
[    0.000000]   E0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0000000000 mask 7E00000000 write-back
[    0.000000]   1 base 0200000000 mask 7FE0000000 write-back
[    0.000000]   2 base 00E0000000 mask 7FE0000000 uncachable
[    0.000000]   3 base 00DE000000 mask 7FFE000000 uncachable
[    0.000000]   4 base 00DD000000 mask 7FFF000000 uncachable
[    0.000000]   5 base 021F000000 mask 7FFF000000 uncachable
[    0.000000]   6 base 021EE00000 mask 7FFFE00000 uncachable
[    0.000000]   7 disabled
[    0.000000]   8 disabled
[    0.000000]   9 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 8GB, type WB
[    0.000000] reg 1, base: 8GB, range: 512MB, type WB
[    0.000000] reg 2, base: 3584MB, range: 512MB, type UC
[    0.000000] reg 3, base: 3552MB, range: 32MB, type UC
[    0.000000] reg 4, base: 3536MB, range: 16MB, type UC
[    0.000000] reg 5, base: 8688MB, range: 16MB, type UC
[    0.000000] reg 6, base: 8686MB, range: 2MB, type UC
[    0.000000] total RAM covered: 8126M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K     chunk_size: 64M     num_reg: 9      lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3GB, range: 512MB, type WB
[    0.000000] reg 3, base: 3536MB, range: 16MB, type UC
[    0.000000] reg 4, base: 3552MB, range: 32MB, type UC
[    0.000000] reg 5, base: 4GB, range: 4GB, type WB
[    0.000000] reg 6, base: 8GB, range: 512MB, type WB
[    0.000000] reg 7, base: 8686MB, range: 2MB, type UC
[    0.000000] reg 8, base: 8688MB, range: 16MB, type UC
[    0.000000] e820: update [mem 0xdd000000-0xffffffff] usable ==> reserved
[    0.000000] e820: last_pfn = 0xdbcf9 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [mem 0x000fd970-0x000fd97f] mapped at [ffff8800000fd970]
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] Base memory trampoline at [ffff88000008b000] 8b000 size 24576
[    0.000000] Using GB pages for direct mapping
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] BRK [0x02fe4000, 0x02fe4fff] PGTABLE
[    0.000000] BRK [0x02fe5000, 0x02fe5fff] PGTABLE
[    0.000000] BRK [0x02fe6000, 0x02fe6fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x21ec00000-0x21edfffff]
[    0.000000]  [mem 0x21ec00000-0x21edfffff] page 2M
[    0.000000] BRK [0x02fe7000, 0x02fe7fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x21c000000-0x21ebfffff]
[    0.000000]  [mem 0x21c000000-0x21ebfffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x200000000-0x21bffffff]
[    0.000000]  [mem 0x200000000-0x21bffffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x00100000-0xcf9bbfff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0x3fffffff] page 2M
[    0.000000]  [mem 0x40000000-0xbfffffff] page 1G
[    0.000000]  [mem 0xc0000000-0xcf7fffff] page 2M
[    0.000000]  [mem 0xcf800000-0xcf9bbfff] page 4k
[    0.000000] init_memory_mapping: [mem 0xcf9c3000-0xd05d6fff]
[    0.000000]  [mem 0xcf9c3000-0xcf9fffff] page 4k
[    0.000000]  [mem 0xcfa00000-0xd03fffff] page 2M
[    0.000000]  [mem 0xd0400000-0xd05d6fff] page 4k
[    0.000000] BRK [0x02fe8000, 0x02fe8fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0xd0aa7000-0xd7db3fff]
[    0.000000]  [mem 0xd0aa7000-0xd0bfffff] page 4k
[    0.000000]  [mem 0xd0c00000-0xd7bfffff] page 2M
[    0.000000]  [mem 0xd7c00000-0xd7db3fff] page 4k
[    0.000000] BRK [0x02fe9000, 0x02fe9fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0xd8000000-0xd8759fff]
[    0.000000]  [mem 0xd8000000-0xd85fffff] page 2M
[    0.000000]  [mem 0xd8600000-0xd8759fff] page 4k
[    0.000000] init_memory_mapping: [mem 0xd8800000-0xd8fadfff]
[    0.000000]  [mem 0xd8800000-0xd8dfffff] page 2M
[    0.000000]  [mem 0xd8e00000-0xd8fadfff] page 4k
[    0.000000] init_memory_mapping: [mem 0xd9000000-0xda71bfff]
[    0.000000]  [mem 0xd9000000-0xda5fffff] page 2M
[    0.000000]  [mem 0xda600000-0xda71bfff] page 4k
[    0.000000] init_memory_mapping: [mem 0xda800000-0xdbcf8fff]
[    0.000000]  [mem 0xda800000-0xdbbfffff] page 2M
[    0.000000]  [mem 0xdbc00000-0xdbcf8fff] page 4k
[    0.000000] init_memory_mapping: [mem 0x100000000-0x1ffffffff]
[    0.000000]  [mem 0x100000000-0x1ffffffff] page 1G
[    0.000000] RAMDISK: [mem 0x343c4000-0x361d9fff]
[    0.000000] ACPI: RSDP 00000000d8fef000 00024 (v02 DELL  )
[    0.000000] ACPI: XSDT 00000000d8fef088 00094 (v01 DELL    CBX3    01072009 AMI  00010013)
[    0.000000] ACPI: FACP 00000000d8ffcae0 0010C (v05 DELL    CBX3    01072009 AMI  00010013)
[    0.000000] ACPI Error: Gpe0Block - 32-bit FADT register is too long (32 bytes, 256 bits) to convert to GAS struct - 255 bits max, truncating (20130517/tbfadt-202)
[    0.000000] ACPI: DSDT 00000000d8fef1b0 0D92E (v02 DELL    CBX3    00000014 INTL 20091112)
[    0.000000] ACPI: FACS 00000000da7fe080 00040
[    0.000000] ACPI: APIC 00000000d8ffcbf0 00072 (v03 DELL    CBX3    01072009 AMI  00010013)
[    0.000000] ACPI: FPDT 00000000d8ffcc68 00044 (v01 DELL    CBX3    01072009 AMI  00010013)
[    0.000000] ACPI: SLIC 00000000d8ffccb0 00176 (v03 DELL    CBX3    01072009 MSFT 00010013)
[    0.000000] ACPI: SSDT 00000000d8ffce28 00200 (v01  INTEL sensrhub 00000000 INTL 20120711)
[    0.000000] ACPI: SSDT 00000000d8ffd028 00548 (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    0.000000] ACPI: SSDT 00000000d8ffd570 00AD8 (v01  PmRef    CpuPm 00003000 INTL 20051117)
[    0.000000] ACPI: HPET 00000000d8ffe048 00038 (v01 DELL    CBX3    01072009 AMI. 00000005)
[    0.000000] ACPI: SSDT 00000000d8ffe080 00455 (v01 SataRe SataTabl 00001000 INTL 20091112)
[    0.000000] ACPI: MCFG 00000000d8ffe4d8 0003C (v01 DELL    CBX3    01072009 MSFT 00000097)
[    0.000000] ACPI: ASF! 00000000d8ffe518 000A5 (v32 INTEL       HCG 00000001 TFSM 000F4240)
[    0.000000] ACPI: MSDM 00000000d8ffe5c0 00055 (v03 DELL    CBX3    06222004 AMI  00010013)
[    0.000000] ACPI: BGRT 00000000d8ffe618 00038 (v00     \xfffffff3\xffffffee          01072009 AMI  00010013)
[    0.000000] ACPI: DMAR 00000000d8ffe650 000B0 (v01 INTEL      HSW  00000001 INTL 00000001)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000021edfffff]
[    0.000000] Initmem setup node 0 [mem 0x00000000-0x21edfffff]
[    0.000000]   NODE_DATA [mem 0x21edf4000-0x21edf8fff]
[    0.000000]  [ffffea0000000000-ffffea00087fffff] PMD -> [ffff880216400000-ffff88021e3fffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000]   Normal   [mem 0x100000000-0x21edfffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00001000-0x0004efff]
[    0.000000]   node   0: [mem 0x00050000-0x0009efff]
[    0.000000]   node   0: [mem 0x00100000-0xcf9bbfff]
[    0.000000]   node   0: [mem 0xcf9c3000-0xd05d6fff]
[    0.000000]   node   0: [mem 0xd0aa7000-0xd7db3fff]
[    0.000000]   node   0: [mem 0xd8000000-0xd8759fff]
[    0.000000]   node   0: [mem 0xd8800000-0xd8fadfff]
[    0.000000]   node   0: [mem 0xd9000000-0xda71bfff]
[    0.000000]   node   0: [mem 0xda800000-0xdbcf8fff]
[    0.000000]   node   0: [mem 0x100000000-0x21edfffff]
[    0.000000] On node 0 totalpages: 2072983
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 55 pages reserved
[    0.000000]   DMA zone: 3997 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 13968 pages used for memmap
[    0.000000]   DMA32 zone: 893946 pages, LIFO batch:31
[    0.000000]   Normal zone: 18360 pages used for memmap
[    0.000000]   Normal zone: 1175040 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x1808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-39
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
[    0.000000] smpboot: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 56
[    0.000000] PM: Registered nosave memory: [mem 0x0004f000-0x0004ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000fffff]
[    0.000000] PM: Registered nosave memory: [mem 0xcf9bc000-0xcf9c2fff]
[    0.000000] PM: Registered nosave memory: [mem 0xd05d7000-0xd0aa6fff]
[    0.000000] PM: Registered nosave memory: [mem 0xd7db4000-0xd7ffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xd875a000-0xd87fffff]
[    0.000000] PM: Registered nosave memory: [mem 0xd8fae000-0xd8ffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xda71c000-0xda7fffff]
[    0.000000] PM: Registered nosave memory: [mem 0xdbcf9000-0xdbffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xdc000000-0xdcffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xdd000000-0xdf1fffff]
[    0.000000] PM: Registered nosave memory: [mem 0xdf200000-0xf7ffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xf8000000-0xfbffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfc000000-0xfebfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec01000-0xfecfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed00000-0xfed03fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed04000-0xfed1bfff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed1c000-0xfed1ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed20000-0xfedfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee00000-0xfee00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee01000-0xfeffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xff000000-0xffffffff]
[    0.000000] e820: [mem 0xdf200000-0xf7ffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 29 pages/cpu @ffff88021ea00000 s86720 r8192 d23872 u524288
[    0.000000] pcpu-alloc: s86720 r8192 d23872 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 2040536
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.11.0-031100-generic root=UUID=25b76ef6-ad5d-4e77-903b-4a0031d573da ro quiet splash i8042.reset i8042.nomux vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] xsave: enabled xstate_bv 0x7, cntxt size 0x340
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 7937152K/8291932K available (7400K kernel code, 1082K rwdata, 3420K rodata, 1380K init, 1484K bss, 354780K reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=4.
[    0.000000]     Offload RCU callbacks from all CPUs
[    0.000000]     Offload RCU callbacks from CPUs: 0-255.
[    0.000000] NR_IRQS:16640 nr_irqs:984 16
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 33554432 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.004000] tsc: Detected 2693.666 MHz processor
[    0.000002] Calibrating delay loop (skipped), value calculated using timer frequency.. 5387.33 BogoMIPS (lpj=10774664)
[    0.000004] pid_max: default: 32768 minimum: 301
[    0.000016] init_memory_mapping: [mem 0xd05d7000-0xd0aa6fff]
[    0.000018]  [mem 0xd05d7000-0xd05fffff] page 4k
[    0.000018]  [mem 0xd0600000-0xd09fffff] page 2M
[    0.000019]  [mem 0xd0a00000-0xd0aa6fff] page 4k
[    0.000035] init_memory_mapping: [mem 0xd7db4000-0xd7ffffff]
[    0.000036]  [mem 0xd7db4000-0xd7dfffff] page 4k
[    0.000036]  [mem 0xd7e00000-0xd7ffffff] page 2M
[    0.000043] init_memory_mapping: [mem 0xd875a000-0xd87fffff]
[    0.000044]  [mem 0xd875a000-0xd87fffff] page 4k
[    0.000050] init_memory_mapping: [mem 0xdd000000-0xdf1fffff]
[    0.000051]  [mem 0xdd000000-0xdf1fffff] page 2M
[    0.016269] Security Framework initialized
[    0.016278] AppArmor: AppArmor initialized
[    0.016279] Yama: becoming mindful.
[    0.016655] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.017747] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.018199] Mount-cache hash table entries: 256
[    0.018323] Initializing cgroup subsys memory
[    0.018329] Initializing cgroup subsys devices
[    0.018331] Initializing cgroup subsys freezer
[    0.018332] Initializing cgroup subsys blkio
[    0.018333] Initializing cgroup subsys perf_event
[    0.018334] Initializing cgroup subsys hugetlb
[    0.018353] CPU: Physical Processor ID: 0
[    0.018354] CPU: Processor Core ID: 0
[    0.018357] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
[    0.018357] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[    0.019194] mce: CPU supports 7 MCE banks
[    0.019204] CPU0: Thermal monitoring enabled (TM1)
[    0.019212] Last level iTLB entries: 4KB 0, 2MB 0, 4MB 0
[    0.019212] Last level dTLB entries: 4KB 64, 2MB 0, 4MB 0
[    0.019212] tlb_flushall_shift: 6
[    0.019294] Freeing SMP alternatives memory: 24K (ffffffff81e69000 - ffffffff81e6f000)
[    0.020657] ACPI: Core revision 20130517
[    0.026922] ACPI: All ACPI Tables successfully acquired
[    0.030389] ftrace: allocating 30693 entries in 120 pages
[    0.039995] dmar: Host address width 39
[    0.039997] dmar: DRHD base: 0x000000fed90000 flags: 0x0
[    0.040005] dmar: IOMMU 0: reg_base_addr fed90000 ver 1:0 cap c0000020660462 ecap f0101a
[    0.040006] dmar: DRHD base: 0x000000fed91000 flags: 0x1
[    0.040010] dmar: IOMMU 1: reg_base_addr fed91000 ver 1:0 cap d2008020660462 ecap f010da
[    0.040010] dmar: RMRR base: 0x000000d7f18000 end: 0x000000d7f26fff
[    0.040011] dmar: RMRR base: 0x000000dd000000 end: 0x000000df1fffff
[    0.040132] IOAPIC id 2 under DRHD base  0xfed91000 IOMMU 1
[    0.040133] HPET id 0 under DRHD base 0xfed91000
[    0.040254] Enabled IRQ remapping in x2apic mode
[    0.040255] Enabling x2apic
[    0.040256] Enabled x2apic
[    0.040263] Switched APIC routing to cluster x2apic.
[    0.040868] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.080535] smpboot: CPU0: Intel(R) Core(TM) i7-4600U CPU @ 2.10GHz (fam: 06, model: 45, stepping: 01)
[    0.080542] TSC deadline timer enabled
[    0.080548] Performance Events: PEBS fmt2+, 16-deep LBR, Haswell events, full-width counters, Intel PMU driver.
[    0.080553] ... version:                3
[    0.080554] ... bit width:              48
[    0.080555] ... generic registers:      4
[    0.080556] ... value mask:             0000ffffffffffff
[    0.080556] ... max period:             0000ffffffffffff
[    0.080557] ... fixed-purpose events:   3
[    0.080558] ... event mask:             000000070000000f
[    0.081594] NMI watchdog: Disabled lockup detectors by default for full dynticks
[    0.081595] NMI watchdog: You can reactivate it with 'sysctl -w kernel.watchdog=1'
[    0.081651] smpboot: Booting Node   0, Processors  #1 #2 #3 OK
[    0.126571] Brought up 4 CPUs
[    0.126574] smpboot: Total of 4 processors activated (21549.32 BogoMIPS)
[    0.130324] devtmpfs: initialized
[    0.131116] EVM: security.selinux
[    0.131117] EVM: security.SMACK64
[    0.131118] EVM: security.capability
[    0.131158] PM: Registering ACPI NVS region [mem 0xcf9bc000-0xcf9c2fff] (28672 bytes)
[    0.131159] PM: Registering ACPI NVS region [mem 0xda71c000-0xda7fffff] (933888 bytes)
[    0.131715] regulator-dummy: no parameters
[    0.131744] RTC time: 16:17:18, date: 10/07/13
[    0.131766] NET: Registered protocol family 16
[    0.131863] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.131864] ACPI: bus type PCI registered
[    0.131866] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.131898] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000)
[    0.131900] PCI: MMCONFIG at [mem 0xf8000000-0xfbffffff] reserved in E820
[    0.138288] PCI: Using configuration type 1 for base access
[    0.138293] dmi type 0xB1 record - unknown flag
[    0.138904] bio: create slab <bio-0> at 0
[    0.139014] ACPI: Added _OSI(Module Device)
[    0.139015] ACPI: Added _OSI(Processor Device)
[    0.139016] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.139017] ACPI: Added _OSI(Processor Aggregator Device)
[    0.140377] ACPI: EC: Look up EC in DSDT
[    0.141752] ACPI: Executed 1 blocks of module-level executable AML code
[    0.143657] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.263056] ACPI: SSDT 00000000dbdb2c18 003D3 (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.263537] ACPI: Dynamic OEM Table Load:
[    0.263539] ACPI: SSDT           (null) 003D3 (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.267184] ACPI: SSDT 00000000dbdb2618 005AA (v01  PmRef    ApIst 00003000 INTL 20051117)
[    0.267735] ACPI: Dynamic OEM Table Load:
[    0.267736] ACPI: SSDT           (null) 005AA (v01  PmRef    ApIst 00003000 INTL 20051117)
[    0.275043] ACPI: SSDT 00000000dbdb1d98 00119 (v01  PmRef    ApCst 00003000 INTL 20051117)
[    0.275523] ACPI: Dynamic OEM Table Load:
[    0.275524] ACPI: SSDT           (null) 00119 (v01  PmRef    ApCst 00003000 INTL 20051117)
[    0.335027] ACPI: Interpreter enabled
[    0.335034] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20130517/hwxface-571)
[    0.335041] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20130517/hwxface-571)
[    0.335059] ACPI: (supports S0 S3 S4 S5)
[    0.335061] ACPI: Using IOAPIC for interrupt routing
[    0.335090] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.351229] ACPI: ACPI Dock Station Driver: 1 docks/bays found
[    0.608480] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-3e])
[    0.609045] PCI host bridge to bus 0000:00
[    0.609048] pci_bus 0000:00: root bus resource [bus 00-3e]
[    0.609049] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    0.609050] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    0.609051] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.609052] pci_bus 0000:00: root bus resource [mem 0x000dc000-0x000dffff]
[    0.609054] pci_bus 0000:00: root bus resource [mem 0xdf200000-0xfeafffff]
[    0.609060] pci 0000:00:00.0: [8086:0a04] type 00 class 0x060000
[    0.609123] pci 0000:00:02.0: [8086:0a16] type 00 class 0x030000
[    0.609132] pci 0000:00:02.0: reg 0x10: [mem 0xf7800000-0xf7bfffff 64bit]
[    0.609137] pci 0000:00:02.0: reg 0x18: [mem 0xe0000000-0xefffffff 64bit pref]
[    0.609141] pci 0000:00:02.0: reg 0x20: [io  0xf000-0xf03f]
[    0.609196] pci 0000:00:03.0: [8086:0a0c] type 00 class 0x040300
[    0.609202] pci 0000:00:03.0: reg 0x10: [mem 0xf7e34000-0xf7e37fff 64bit]
[    0.609279] pci 0000:00:14.0: [8086:9c31] type 00 class 0x0c0330
[    0.609293] pci 0000:00:14.0: reg 0x10: [mem 0xf7e20000-0xf7e2ffff 64bit]
[    0.609340] pci 0000:00:14.0: PME# supported from D3hot D3cold
[    0.609369] pci 0000:00:14.0: System wakeup disabled by ACPI
[    0.609393] pci 0000:00:16.0: [8086:9c3a] type 00 class 0x078000
[    0.609410] pci 0000:00:16.0: reg 0x10: [mem 0xf7e3f000-0xf7e3f01f 64bit]
[    0.609467] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    0.609517] pci 0000:00:16.3: [8086:9c3d] type 00 class 0x070002
[    0.609531] pci 0000:00:16.3: reg 0x10: [io  0xf0e0-0xf0e7]
[    0.609538] pci 0000:00:16.3: reg 0x14: [mem 0xf7e3d000-0xf7e3dfff]
[    0.609644] pci 0000:00:19.0: [8086:155a] type 00 class 0x020000
[    0.609657] pci 0000:00:19.0: reg 0x10: [mem 0xf7e00000-0xf7e1ffff]
[    0.609663] pci 0000:00:19.0: reg 0x14: [mem 0xf7e3c000-0xf7e3cfff]
[    0.609669] pci 0000:00:19.0: reg 0x18: [io  0xf080-0xf09f]
[    0.609715] pci 0000:00:19.0: PME# supported from D0 D3hot D3cold
[    0.615109] pci 0000:00:19.0: System wakeup disabled by ACPI
[    0.615146] pci 0000:00:1b.0: [8086:9c20] type 00 class 0x040300
[    0.615160] pci 0000:00:1b.0: reg 0x10: [mem 0xf7e30000-0xf7e33fff 64bit]
[    0.615219] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.615262] pci 0000:00:1b.0: System wakeup disabled by ACPI
[    0.615297] pci 0000:00:1c.0: [8086:9c10] type 01 class 0x060400
[    0.615368] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.615411] pci 0000:00:1c.0: System wakeup disabled by ACPI
[    0.615450] pci 0000:00:1c.3: [8086:9c16] type 01 class 0x060400
[    0.615520] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.615564] pci 0000:00:1c.3: System wakeup disabled by ACPI
[    0.615597] pci 0000:00:1c.4: [8086:9c18] type 01 class 0x060400
[    0.615667] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.615711] pci 0000:00:1c.4: System wakeup disabled by ACPI
[    0.615746] pci 0000:00:1d.0: [8086:9c26] type 00 class 0x0c0320
[    0.615766] pci 0000:00:1d.0: reg 0x10: [mem 0xf7e3b000-0xf7e3b3ff]
[    0.615852] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.615894] pci 0000:00:1d.0: System wakeup disabled by ACPI
[    0.615927] pci 0000:00:1f.0: [8086:9c43] type 00 class 0x060100
[    0.616093] pci 0000:00:1f.2: [8086:282a] type 00 class 0x010400
[    0.616107] pci 0000:00:1f.2: reg 0x10: [io  0xf0d0-0xf0d7]
[    0.616113] pci 0000:00:1f.2: reg 0x14: [io  0xf0c0-0xf0c3]
[    0.616120] pci 0000:00:1f.2: reg 0x18: [io  0xf0b0-0xf0b7]
[    0.616127] pci 0000:00:1f.2: reg 0x1c: [io  0xf0a0-0xf0a3]
[    0.616133] pci 0000:00:1f.2: reg 0x20: [io  0xf060-0xf07f]
[    0.616140] pci 0000:00:1f.2: reg 0x24: [mem 0xf7e3a000-0xf7e3a7ff]
[    0.616173] pci 0000:00:1f.2: PME# supported from D3hot
[    0.616232] pci 0000:00:1f.3: [8086:9c22] type 00 class 0x0c0500
[    0.616245] pci 0000:00:1f.3: reg 0x10: [mem 0xf7e39000-0xf7e390ff 64bit]
[    0.616263] pci 0000:00:1f.3: reg 0x20: [io  0xf040-0xf05f]
[    0.616396] pci 0000:00:1c.0: PCI bridge to [bus 01]
[    0.616538] pci 0000:02:00.0: [8086:08b1] type 00 class 0x028000
[    0.616619] pci 0000:02:00.0: reg 0x10: [mem 0xf7d00000-0xf7d01fff 64bit]
[    0.616888] pci 0000:02:00.0: PME# supported from D0 D3hot D3cold
[    0.616924] pci 0000:02:00.0: System wakeup disabled by ACPI
[    0.623157] pci 0000:00:1c.3: PCI bridge to [bus 02]
[    0.623162] pci 0000:00:1c.3:   bridge window [mem 0xf7d00000-0xf7dfffff]
[    0.625044] pci 0000:03:00.0: [1217:8520] type 00 class 0x080501
[    0.625063] pci 0000:03:00.0: reg 0x10: [mem 0xf7c01000-0xf7c01fff]
[    0.625076] pci 0000:03:00.0: reg 0x14: [mem 0xf7c00000-0xf7c007ff]
[    0.625193] pci 0000:03:00.0: PME# supported from D3hot D3cold
[    0.625223] pci 0000:03:00.0: System wakeup disabled by ACPI
[    0.632902] pci 0000:00:1c.4: PCI bridge to [bus 03]
[    0.632907] pci 0000:00:1c.4:   bridge window [mem 0xf7c00000-0xf7cfffff]
[    0.633004] acpi PNP0A08:00: Requesting ACPI _OSC control (0x1d)
[    0.633197] acpi PNP0A08:00: ACPI _OSC control (0x18) granted
[    0.667299] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.667347] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.667393] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 *10 11 12 14 15)
[    0.667438] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 *10 11 12 14 15)
[    0.667482] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 *5 6 10 11 12 14 15)
[    0.667526] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.667570] ACPI: PCI Interrupt Link [LNKG] (IRQs *3 4 5 6 10 11 12 14 15)
[    0.667614] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.687904] ACPI: Enabled 2 GPEs in block 00 to 7F
[    0.687911] ACPI: \_SB_.PCI0: notify handler is installed
[    0.687975] Found 1 acpi root devices
[    0.688021] ACPI: EC: GPE = 0x27, I/O: command/status = 0x934, data = 0x930
[    0.688108] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.688111] vgaarb: loaded
[    0.688112] vgaarb: bridge control possible 0000:00:02.0
[    0.688250] SCSI subsystem initialized
[    0.688252] ACPI: bus type ATA registered
[    0.688299] libata version 3.00 loaded.
[    0.688328] ACPI: bus type USB registered
[    0.688342] usbcore: registered new interface driver usbfs
[    0.688351] usbcore: registered new interface driver hub
[    0.688377] usbcore: registered new device driver usb
[    0.688486] PCI: Using ACPI for IRQ routing
[    0.689745] PCI: pci_cache_line_size set to 64 bytes
[    0.689788] e820: reserve RAM buffer [mem 0x0004f000-0x0004ffff]
[    0.689790] e820: reserve RAM buffer [mem 0x0009f000-0x0009ffff]
[    0.689791] e820: reserve RAM buffer [mem 0xcf9bc000-0xcfffffff]
[    0.689792] e820: reserve RAM buffer [mem 0xd05d7000-0xd3ffffff]
[    0.689794] e820: reserve RAM buffer [mem 0xd7db4000-0xd7ffffff]
[    0.689795] e820: reserve RAM buffer [mem 0xd875a000-0xdbffffff]
[    0.689797] e820: reserve RAM buffer [mem 0xd8fae000-0xdbffffff]
[    0.689798] e820: reserve RAM buffer [mem 0xda71c000-0xdbffffff]
[    0.689799] e820: reserve RAM buffer [mem 0xdbcf9000-0xdbffffff]
[    0.689801] e820: reserve RAM buffer [mem 0x21ee00000-0x21fffffff]
[    0.689875] NetLabel: Initializing
[    0.689876] NetLabel:  domain hash size = 128
[    0.689877] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.689886] NetLabel:  unlabeled traffic allowed by default
[    0.689943] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.689949] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.691965] Switched to clocksource hpet
[    0.695093] AppArmor: AppArmor Filesystem Enabled
[    0.695115] pnp: PnP ACPI init
[    0.695127] ACPI: bus type PNP registered
[    0.695186] system 00:00: [mem 0xfed40000-0xfed44fff] has been reserved
[    0.695189] system 00:00: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.695197] pnp 00:01: [dma 4]
[    0.695207] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.695218] pnp 00:02: Plug and Play ACPI device, IDs INT0800 (active)
[    0.695291] pnp 00:03: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.695377] system 00:04: [io  0x0680-0x069f] has been reserved
[    0.695378] system 00:04: [io  0xffff] has been reserved
[    0.695380] system 00:04: [io  0xffff] has been reserved
[    0.695381] system 00:04: [io  0xffff] has been reserved
[    0.695383] system 00:04: [io  0x1c00-0x1cfe] has been reserved
[    0.695384] system 00:04: [io  0x1d00-0x1dfe] has been reserved
[    0.695385] system 00:04: [io  0x1e00-0x1efe] has been reserved
[    0.695387] system 00:04: [io  0x1f00-0x1ffe] has been reserved
[    0.695388] system 00:04: [io  0x1800-0x18fe] could not be reserved
[    0.695389] system 00:04: [io  0x164e-0x164f] has been reserved
[    0.695391] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.695412] pnp 00:05: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.695440] system 00:06: [io  0x1854-0x1857] has been reserved
[    0.695442] system 00:06: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    0.695472] system 00:07: [io  0x04d0-0x04d1] has been reserved
[    0.695474] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.695504] pnp 00:08: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.695521] pnp 00:09: Plug and Play ACPI device, IDs DLL05ca PNP0f13 (active)
[    0.720057] pnp 00:0a: Plug and Play ACPI device, IDs PNP0401 (disabled)
[    0.728167] system 00:0b: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.728170] system 00:0b: [mem 0xfed10000-0xfed17fff] has been reserved
[    0.728171] system 00:0b: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.728173] system 00:0b: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.728175] system 00:0b: [mem 0xf8000000-0xfbffffff] has been reserved
[    0.728177] system 00:0b: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.728179] system 00:0b: [mem 0xfed90000-0xfed93fff] could not be reserved
[    0.728181] system 00:0b: [mem 0xfed45000-0xfed8ffff] has been reserved
[    0.728183] system 00:0b: [mem 0xff000000-0xffffffff] has been reserved
[    0.728184] system 00:0b: [mem 0xfee00000-0xfeefffff] could not be reserved
[    0.728186] system 00:0b: [mem 0xf7fef000-0xf7feffff] has been reserved
[    0.728188] system 00:0b: [mem 0xf7ff0000-0xf7ff0fff] has been reserved
[    0.728191] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.760002] pnp: PnP ACPI: found 12 devices
[    0.760005] ACPI: bus type PNP unregistered
[    0.766071] pci 0000:00:1c.0: bridge window [io  0x1000-0x0fff] to [bus 01] add_size 1000
[    0.766074] pci 0000:00:1c.0: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 01] add_size 200000
[    0.766075] pci 0000:00:1c.0: bridge window [mem 0x00100000-0x000fffff] to [bus 01] add_size 200000
[    0.766088] pci 0000:00:1c.0: res[14]=[mem 0x00100000-0x000fffff] get_res_add_size add_size 200000
[    0.766089] pci 0000:00:1c.0: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
[    0.766090] pci 0000:00:1c.0: res[13]=[io  0x1000-0x0fff] get_res_add_size add_size 1000
[    0.766093] pci 0000:00:1c.0: BAR 14: assigned [mem 0xdf200000-0xdf3fffff]
[    0.766095] pci 0000:00:1c.0: BAR 15: assigned [mem 0xdf400000-0xdf5fffff 64bit pref]
[    0.766097] pci 0000:00:1c.0: BAR 13: assigned [io  0x2000-0x2fff]
[    0.766099] pci 0000:00:1c.0: PCI bridge to [bus 01]
[    0.766101] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
[    0.766104] pci 0000:00:1c.0:   bridge window [mem 0xdf200000-0xdf3fffff]
[    0.766107] pci 0000:00:1c.0:   bridge window [mem 0xdf400000-0xdf5fffff 64bit pref]
[    0.766111] pci 0000:00:1c.3: PCI bridge to [bus 02]
[    0.766114] pci 0000:00:1c.3:   bridge window [mem 0xf7d00000-0xf7dfffff]
[    0.766119] pci 0000:00:1c.4: PCI bridge to [bus 03]
[    0.766122] pci 0000:00:1c.4:   bridge window [mem 0xf7c00000-0xf7cfffff]
[    0.768204] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.768207] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.768208] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.768210] pci_bus 0000:00: resource 7 [mem 0x000dc000-0x000dffff]
[    0.768211] pci_bus 0000:00: resource 8 [mem 0xdf200000-0xfeafffff]
[    0.768213] pci_bus 0000:01: resource 0 [io  0x2000-0x2fff]
[    0.768215] pci_bus 0000:01: resource 1 [mem 0xdf200000-0xdf3fffff]
[    0.768216] pci_bus 0000:01: resource 2 [mem 0xdf400000-0xdf5fffff 64bit pref]
[    0.768218] pci_bus 0000:02: resource 1 [mem 0xf7d00000-0xf7dfffff]
[    0.768220] pci_bus 0000:03: resource 1 [mem 0xf7c00000-0xf7cfffff]
[    0.768246] NET: Registered protocol family 2
[    0.768421] TCP established hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.768600] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.768722] TCP: Hash tables configured (established 65536 bind 65536)
[    0.768737] TCP: reno registered
[    0.768750] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    0.768776] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    0.768830] NET: Registered protocol family 1
[    0.768840] pci 0000:00:02.0: Boot video device
[    0.769166] PCI: CLS 64 bytes, default 64
[    0.769202] Trying to unpack rootfs image as initramfs...
[    1.135102] Freeing initrd memory: 30808K (ffff8800343c4000 - ffff8800361da000)
[    1.135110] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    1.135112] software IO TLB [mem 0xc8ac9000-0xccac9000] (64MB) mapped at [ffff8800c8ac9000-ffff8800ccac8fff]
[    1.135230] Scanning for low memory corruption every 60 seconds
[    1.135398] Initialise module verification
[    1.135425] audit: initializing netlink socket (disabled)
[    1.135432] type=2000 audit(1381162638.120:1): initialized
[    1.156351] bounce pool size: 64 pages
[    1.156358] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.157241] VFS: Disk quotas dquot_6.5.2
[    1.157266] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.157547] fuse init (API version 7.22)
[    1.157595] msgmni has been set to 15776
[    1.157858] Key type asymmetric registered
[    1.157860] Asymmetric key parser 'x509' registered
[    1.157878] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    1.157900] io scheduler noop registered
[    1.157902] io scheduler deadline registered (default)
[    1.157916] io scheduler cfq registered
[    1.158049] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.158057] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.158104] efifb: probing for efifb
[    1.158545] efifb: framebuffer at 0xe0000000, mapped to 0xffffc9000a000000, using 4160k, total 4160k
[    1.158546] efifb: mode is 1366x768x32, linelength=5504, pages=1
[    1.158546] efifb: scrolling: redraw
[    1.158548] efifb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    1.160203] Console: switching to colour frame buffer device 170x48
[    1.161752] fb0: EFI VGA frame buffer device
[    1.161756] intel_idle: MWAIT substates: 0x11142120
[    1.161757] intel_idle: v0.4 model 0x45
[    1.161758] intel_idle: lapic_timer_reliable_states 0xffffffff
[    1.162630] ACPI: AC Adapter [AC] (off-line)
[    1.162716] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    1.163556] ACPI: Lid Switch [LID0]
[    1.163590] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.163594] ACPI: Power Button [PBTN]
[    1.163617] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    1.163619] ACPI: Sleep Button [SBTN]
[    1.163642] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    1.163644] ACPI: Power Button [PWRF]
[    1.163972] ACPI: Requesting acpi_cpufreq
[    1.199823] thermal LNXTHERM:00: registered as thermal_zone0
[    1.199826] ACPI: Thermal Zone [THM] (25 C)
[    1.199867] GHES: HEST is not enabled!
[    1.199946] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.200893] serial 0000:00:16.3: enabling device (0000 -> 0003)
[    1.216197] ACPI: Battery Slot [BAT0] (battery present)
[    1.221171] 0000:00:16.3: ttyS4 at I/O 0xf0e0 (irq = 19) is a 16550A
[    1.227911] Linux agpgart interface v0.103
[    1.228874] brd: module loaded
[    1.229337] loop: module loaded
[    1.229583] libphy: Fixed MDIO Bus: probed
[    1.229644] tun: Universal TUN/TAP device driver, 1.6
[    1.229645] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.229673] PPP generic driver version 2.4.2
[    1.229702] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.229704] ehci-pci: EHCI PCI platform driver
[    1.231908] ehci-pci 0000:00:1d.0: setting latency timer to 64
[    1.231916] ehci-pci 0000:00:1d.0: EHCI Host Controller
[    1.231922] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    1.231933] ehci-pci 0000:00:1d.0: debug port 2
[    1.235822] ehci-pci 0000:00:1d.0: cache line size of 64 is not supported
[    1.235835] ehci-pci 0000:00:1d.0: irq 21, io mem 0xf7e3b000
[    1.247775] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    1.247790] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    1.247792] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.247793] usb usb1: Product: EHCI Host Controller
[    1.247795] usb usb1: Manufacturer: Linux 3.11.0-031100-generic ehci_hcd
[    1.247796] usb usb1: SerialNumber: 0000:00:1d.0
[    1.251908] hub 1-0:1.0: USB hub found
[    1.251911] hub 1-0:1.0: 3 ports detected
[    1.259982] ehci-platform: EHCI generic platform driver
[    1.259990] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.259991] ohci-platform: OHCI generic platform driver
[    1.259996] uhci_hcd: USB Universal Host Controller Interface driver
[    1.260103] xhci_hcd 0000:00:14.0: setting latency timer to 64
[    1.260106] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    1.260111] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 2
[    1.260207] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
[    1.260227] xhci_hcd 0000:00:14.0: irq 58 for MSI/MSI-X
[    1.260262] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    1.260264] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.260265] usb usb2: Product: xHCI Host Controller
[    1.260267] usb usb2: Manufacturer: Linux 3.11.0-031100-generic xhci_hcd
[    1.260268] usb usb2: SerialNumber: 0000:00:14.0
[    1.260272] ACPI: Battery Slot [BAT1] (battery absent)
[    1.260349] xHCI xhci_add_endpoint called for root hub
[    1.260351] xHCI xhci_check_bandwidth called for root hub
[    1.260370] hub 2-0:1.0: USB hub found
[    1.260378] hub 2-0:1.0: 9 ports detected
[    1.261726] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    1.261728] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 3
[    1.261742] usb usb3: New USB device found, idVendor=1d6b, idProduct=0003
[    1.261743] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.261744] usb usb3: Product: xHCI Host Controller
[    1.261745] usb usb3: Manufacturer: Linux 3.11.0-031100-generic xhci_hcd
[    1.261746] usb usb3: SerialNumber: 0000:00:14.0
[    1.261783] xHCI xhci_add_endpoint called for root hub
[    1.261784] xHCI xhci_check_bandwidth called for root hub
[    1.261796] hub 3-0:1.0: USB hub found
[    1.261801] hub 3-0:1.0: 4 ports detected
[    1.267808] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.268441] i8042: Warning: Keylock active
[    1.270085] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.270089] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.270150] mousedev: PS/2 mouse device common for all mice
[    1.270273] rtc_cmos 00:05: RTC can wake from S4
[    1.270385] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    1.270411] rtc_cmos 00:05: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    1.270453] device-mapper: uevent: version 1.0.3
[    1.270493] device-mapper: ioctl: 4.25.0-ioctl (2013-06-26) initialised: dm-devel@redhat.com
[    1.270590] cpuidle: using governor ladder
[    1.270747] cpuidle: using governor menu
[    1.270755] ledtrig-cpu: registered to indicate activity on CPUs
[    1.270757] EFI Variables Facility v0.08 2004-May-17
[    1.271592] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.275738] ashmem: initialized
[    1.275844] TCP: cubic registered
[    1.275901] NET: Registered protocol family 10
[    1.276017] NET: Registered protocol family 17
[    1.276024] Key type dns_resolver registered
[    1.276191] PM: Hibernation image not present or could not be loaded.
[    1.276194] Loading module verification certificates
[    1.277197] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: 394cd8cbf63c2fa10ba65b7514a71f2cce77b906'
[    1.277204] registered taskstats version 1
[    1.278853] Key type trusted registered
[    1.280176] Key type encrypted registered
[    1.281767]   Magic number: 1:965:286
[    1.281773] ppp ppp: hash matches
[    1.281847] rtc_cmos 00:05: setting system clock to 2013-10-07 16:17:19 UTC (1381162639)
[    1.282354] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.282355] EDD information not available.
[    1.283203] Freeing unused kernel memory: 1380K (ffffffff81d10000 - ffffffff81e69000)
[    1.283204] Write protecting the kernel read-only data: 12288k
[    1.284533] Freeing unused kernel memory: 780K (ffff88000273d000 - ffff880002800000)
[    1.285600] Freeing unused kernel memory: 676K (ffff880002b57000 - ffff880002c00000)
[    1.298612] udevd[114]: starting version 175
[    1.331217] wmi: Mapper loaded
[    1.337434] sdhci: Secure Digital Host Controller Interface driver
[    1.337437] sdhci: Copyright(c) Pierre Ossman
[    1.340733] [drm] Initialized drm 1.1.0 20060810
[    1.341026] pps_core: LinuxPPS API ver. 1 registered
[    1.341028] pps_core: Software ver. 5.3.6 - Copyright 2005-2007 Rodolfo Giometti <giometti@linux.it>
[    1.341134] sdhci-pci 0000:03:00.0: SDHCI controller found [1217:8520] (rev 1)
[    1.341213] mmc0: Unknown controller version (3). You may experience problems.
[    1.341256] mmc0: Hardware doesn't specify timeout clock frequency.
[    1.342215] PTP clock support registered
[    1.344556] ahci 0000:00:1f.2: version 3.0
[    1.344701] ahci 0000:00:1f.2: irq 59 for MSI/MSI-X
[    1.344722] ahci: SSS flag set, parallel bus scan disabled
[    1.346690] e1000e: Intel(R) PRO/1000 Network Driver - 2.3.2-k
[    1.346692] e1000e: Copyright(c) 1999 - 2013 Intel Corporation.
[    1.359794] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 4 ports 6 Gbps 0x3 impl RAID mode
[    1.359798] ahci 0000:00:1f.2: flags: 64bit ncq stag led clo only pio slum part sxs deso sadm sds apst 
[    1.359801] ahci 0000:00:1f.2: setting latency timer to 64
[    1.360139] scsi0 : ahci
[    1.360200] scsi1 : ahci
[    1.360265] scsi2 : ahci
[    1.360330] scsi3 : ahci
[    1.387883] ata1: SATA max UDMA/133 abar m2048@0xf7e3a000 port 0xf7e3a100 irq 59
[    1.387887] ata2: SATA max UDMA/133 abar m2048@0xf7e3a000 port 0xf7e3a180 irq 59
[    1.387889] ata3: DUMMY
[    1.387890] ata4: DUMMY
[    1.388080] e1000e 0000:00:19.0: setting latency timer to 64
[    1.388157] e1000e 0000:00:19.0: Interrupt Throttling Rate (ints/sec) set to dynamic conservative mode
[    1.388182] e1000e 0000:00:19.0: irq 60 for MSI/MSI-X
[    1.551802] e1000e 0000:00:19.0 eth0: registered PHC clock
[    1.551815] e1000e 0000:00:19.0 eth0: (PCI Express:2.5GT/s:Width x1) f0:1f:af:38:20:b7
[    1.551816] e1000e 0000:00:19.0 eth0: Intel(R) PRO/1000 Network Connection
[    1.551849] e1000e 0000:00:19.0 eth0: MAC: 11, PHY: 12, PBA No: FFFFFF-0FF
[    1.552617] [drm] Memory usable by graphics device = 2048M
[    1.552620] checking generic (e0000000 410000) vs hw (e0000000 10000000)
[    1.552621] fb: conflicting fb hw usage inteldrmfb vs EFI VGA - removing generic driver
[    1.552630] Console: switching to colour dummy device 80x25
[    1.552686] i915 0000:00:02.0: setting latency timer to 64
[    1.571665] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    1.580245] i915 0000:00:02.0: irq 61 for MSI/MSI-X
[    1.580250] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    1.580251] [drm] Driver supports precise vblank timestamp query.
[    1.580292] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    1.621649] fbcon: inteldrmfb (fb0) is primary device
[    1.703957] usb 1-1: New USB device found, idVendor=8087, idProduct=8000
[    1.703958] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.704103] hub 1-1:1.0: USB hub found
[    1.704203] hub 1-1:1.0: 8 ports detected
[    1.707633] ata1: SATA link down (SStatus 0 SControl 300)
[    1.871625] usb 2-3: new full-speed USB device number 2 using xhci_hcd
[    1.888991] usb 2-3: New USB device found, idVendor=8087, idProduct=07dc
[    1.888993] usb 2-3: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    2.027568] ata2: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    2.055528] usb 2-4: new high-speed USB device number 3 using xhci_hcd
[    2.059847] ata2.00: ATA-8: LITEONIT LMT-256M6M mSATA 256GB, DM8110D, max UDMA/133
[    2.059848] ata2.00: 500118192 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.091931] ata2.00: configured for UDMA/133
[    2.092082] scsi 1:0:0:0: Direct-Access     ATA      LITEONIT LMT-256 DM81 PQ: 0 ANSI: 5
[    2.092216] sd 1:0:0:0: [sda] 500118192 512-byte logical blocks: (256 GB/238 GiB)
[    2.092243] sd 1:0:0:0: Attached scsi generic sg0 type 0
[    2.092327] sd 1:0:0:0: [sda] Write Protect is off
[    2.092329] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.092367] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.093979]  sda: sda1 sda2 sda3
[    2.094606] sd 1:0:0:0: [sda] Attached SCSI disk
[    2.135478] tsc: Refined TSC clocksource calibration: 2693.763 MHz
[    2.146188] usb 2-4: New USB device found, idVendor=0c45, idProduct=64d2
[    2.146190] usb 2-4: New USB device strings: Mfr=2, Product=1, SerialNumber=0
[    2.146191] usb 2-4: Product: Laptop_Integrated_Webcam_HD
[    2.146192] usb 2-4: Manufacturer: CN07YYTT7248737AA4WTA00
[    2.319466] usb 2-5: new full-speed USB device number 4 using xhci_hcd
[    2.347281] usb 2-5: config 0 has an invalid interface number: 3 but max is 2
[    2.347283] usb 2-5: config 0 has no interface number 2
[    2.362055] usb 2-5: New USB device found, idVendor=0a5c, idProduct=5801
[    2.362057] usb 2-5: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    2.362058] usb 2-5: Product: 5880
[    2.362059] usb 2-5: Manufacturer: Broadcom Corp
[    2.362060] usb 2-5: SerialNumber: 0123456789ABCD
[    2.362211] usb 2-5: config 0 descriptor??
[    2.543377] usb 2-7: new high-speed USB device number 5 using xhci_hcd
[    2.560329] usb 2-7: config 1 has an invalid interface number: 8 but max is 3
[    2.560331] usb 2-7: config 1 has no interface number 1
[    2.560774] usb 2-7: config 2 has an invalid interface number: 12 but max is 1
[    2.560775] usb 2-7: config 2 has an invalid interface number: 13 but max is 1
[    2.560776] usb 2-7: config 2 has an invalid interface number: 13 but max is 1
[    2.560777] usb 2-7: config 2 has no interface number 0
[    2.560778] usb 2-7: config 2 has no interface number 1
[    2.561426] usb 2-7: New USB device found, idVendor=413c, idProduct=81a3
[    2.561428] usb 2-7: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    2.561429] usb 2-7: Product: Dell Wireless 5570 HSPA+ (42Mbps) Mobile Broadband Card
[    2.561430] usb 2-7: Manufacturer: Sierra Wireless, Incorporated
[    2.608118] usb 2-7: USB disconnect, device number 5
[    2.827400] [drm] Enabling RC6 states: RC6 on, RC6p off, RC6pp off
[    3.135231] Switched to clocksource tsc
[    3.223105] Console: switching to colour frame buffer device 170x48
[    3.230888] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[    3.230893] i915 0000:00:02.0: registered panic notifier
[    3.359324] acpi device:40: registered as cooling_device4
[    3.391517] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    3.391616] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input5
[    3.391777] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    3.677668] EXT4-fs (sda2): INFO: recovery required on readonly filesystem
[    3.677674] EXT4-fs (sda2): write access will be enabled during recovery
[    3.840003] EXT4-fs (sda2): recovery complete
[    3.840698] EXT4-fs (sda2): mounted filesystem with ordered data mode. Opts: (null)
[    3.976176] init: ureadahead main process (349) terminated with status 5
[    4.061971] Adding 8291324k swap on /dev/sda3.  Priority:-1 extents:1 across:8291324k SSFS
[    4.076818] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro
[    4.167671] udevd[474]: starting version 175
[    4.213369] lp: driver loaded but no devices found
[    4.428250] Bluetooth: Core ver 2.16
[    4.428331] NET: Registered protocol family 31
[    4.428335] Bluetooth: HCI device and connection manager initialized
[    4.428347] Bluetooth: HCI socket layer initialized
[    4.428352] Bluetooth: L2CAP socket layer initialized
[    4.428362] Bluetooth: SCO socket layer initialized
[    4.454160] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    4.454167] Bluetooth: BNEP filters: protocol multicast
[    4.454181] Bluetooth: BNEP socket layer initialized
[    4.457271] Bluetooth: RFCOMM TTY layer initialized
[    4.457287] Bluetooth: RFCOMM socket layer initialized
[    4.457291] Bluetooth: RFCOMM ver 1.11
[    4.500093] ppdev: user-space parallel port driver
[    4.508207] parport_pc 00:0a: [io  0x0378-0x037b]
[    4.508274] parport_pc 00:0a: [irq 5]
[    4.522486] init: avahi-cups-reload main process (684) terminated with status 1
[    4.543014] cfg80211: Calling CRDA to update world regulatory domain
[    4.568582] Intel(R) Wireless WiFi driver for Linux, in-tree:
[    4.568589] Copyright(c) 2003-2013 Intel Corporation
[    4.568651] iwlwifi 0000:02:00.0: enabling device (0000 -> 0002)
[    4.595856] iwlwifi 0000:02:00.0: can't disable ASPM; OS doesn't have ASPM control
[    4.595938] iwlwifi 0000:02:00.0: irq 62 for MSI/MSI-X
[    4.602545] iwlwifi 0000:02:00.0: loaded firmware version 22.0.7.0 op_mode iwlmvm
[    4.607080] type=1400 audit(1381162642.825:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=789 comm="apparmor_parser"
[    4.607828] type=1400 audit(1381162642.825:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=789 comm="apparmor_parser"
[    4.608252] type=1400 audit(1381162642.825:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=789 comm="apparmor_parser"
[    4.612610] mei_me 0000:00:16.0: setting latency timer to 64
[    4.612669] mei_me 0000:00:16.0: irq 63 for MSI/MSI-X
[    4.641568] mei_me 0000:00:16.0: NFC MEI VERSION: IVN 0x1 Vendor ID 0x1 Type 0x1
[    4.648897] iwlwifi 0000:02:00.0: Detected Intel(R) Dual Band Wireless AC 7260, REV=0x144
[    4.648970] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[    4.649119] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[    4.686826] ACPI Warning: 0x0000000000001828-0x000000000000182f SystemIO conflicts with Region \PMIO 1 (20130517/utaddress-251)
[    4.686843] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    4.686898] ACPI Warning: 0x0000000000001c30-0x0000000000001c3f SystemIO conflicts with Region \GPRL 1 (20130517/utaddress-251)
[    4.686907] ACPI Warning: 0x0000000000001c30-0x0000000000001c3f SystemIO conflicts with Region \GPR_ 2 (20130517/utaddress-251)
[    4.686916] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    4.686966] ACPI Warning: 0x0000000000001c00-0x0000000000001c2f SystemIO conflicts with Region \GPRL 1 (20130517/utaddress-251)
[    4.686973] ACPI Warning: 0x0000000000001c00-0x0000000000001c2f SystemIO conflicts with Region \GPR_ 2 (20130517/utaddress-251)
[    4.686983] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    4.686987] lpc_ich: Resource conflict(s) found affecting gpio_ich
[    4.776594] parport_pc 00:0a: activated
[    4.776605] parport_pc 00:0a: reported by Plug and Play ACPI
[    4.776754] parport_pc 00:0a: disabled
[    4.786818] usbcore: registered new interface driver btusb
[    4.797631] Linux video capture interface: v2.00
[    4.802420] Bluetooth: hci0: read Intel version: 370710018002030d16
[    4.802426] Bluetooth: hci0: Intel device is already patched. patch num: 16
[    4.821591] type=1400 audit(1381162643.037:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=918 comm="apparmor_parser"
[    4.822496] type=1400 audit(1381162643.037:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=918 comm="apparmor_parser"
[    4.846878] uvcvideo: Found UVC 1.00 device Laptop_Integrated_Webcam_HD (0c45:64d2)
[    4.884832] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[    4.896110] input: Laptop_Integrated_Webcam_HD as /devices/pci0000:00/0000:00:14.0/usb2/2-4/2-4:1.0/input/input6
[    4.897712] usbcore: registered new interface driver uvcvideo
[    4.897718] USB Video Class driver (1.1.1)
[    4.901776] snd_hda_intel 0000:00:03.0: enabling device (0000 -> 0002)
[    4.902053] HDA driver get symbol successfully from i915 module
[    4.902118] snd_hda_intel 0000:00:03.0: irq 64 for MSI/MSI-X
[    4.904075] snd_hda_intel 0000:00:1b.0: irq 65 for MSI/MSI-X
[    4.917259] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[    4.929091] hda_codec: invalid CONNECT_LIST verb 5[1]:0
[    4.929169] hda_codec: invalid CONNECT_LIST verb 6[1]:0
[    4.929230] hda_codec: invalid CONNECT_LIST verb 7[1]:0
[    4.929680] input: HDA Intel MID HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:03.0/sound/card0/input7
[    4.929836] input: HDA Intel MID HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:03.0/sound/card0/input8
[    4.929967] input: HDA Intel MID HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:03.0/sound/card0/input9
[    4.951402] SKU: Nid=0x1d sku_cfg=0x40700001
[    4.951409] SKU: port_connectivity=0x1
[    4.951411] SKU: enable_pcbeep=0x1
[    4.951414] SKU: check_sum=0x00000000
[    4.951417] SKU: customization=0x00000000
[    4.951419] SKU: external_amp=0x0
[    4.951421] SKU: platform_type=0x0
[    4.951424] SKU: swap=0x0
[    4.951426] SKU: override=0x1
[    4.951727] autoconfig: line_outs=1 (0x16/0x0/0x0/0x0/0x0) type:line
[    4.951732]    speaker_outs=1 (0x14/0x0/0x0/0x0/0x0)
[    4.951735]    hp_outs=1 (0x15/0x0/0x0/0x0/0x0)
[    4.951738]    mono: mono_out=0x0
[    4.951740]    inputs:
[    4.951743]      Dock Mic=0x19
[    4.951746]      Headset Mic=0x1a
[    4.951749]      Internal Mic=0x12
[    4.951753] realtek: No valid SSID, checking pincfg 0x40700001 for NID 0x1d
[    4.951756] realtek: Enabling init ASM_ID=0x0001 CODEC_ID=10ec0292
[    4.959734] input: HDA Intel PCH Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card1/input10
[    4.961709] input: HDA Intel PCH Dock Line Out as /devices/pci0000:00/0000:00:1b.0/sound/card1/input11
[    4.961880] input: HDA Intel PCH Dock Mic as /devices/pci0000:00/0000:00:1b.0/sound/card1/input12
[    4.988406] input: Dell WMI hotkeys as /devices/virtual/input/input13
[    5.005382] cfg80211: World regulatory domain updated:
[    5.005389] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    5.005394] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    5.005398] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    5.005401] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    5.005404] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    5.005408] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    5.011399] nfc: nfc_init: NFC Core ver 0.1
[    5.013475] NET: Registered protocol family 39
[    5.033422] Probing NFC pn544
[    5.046147] init: failsafe main process (975) killed by TERM signal
[    5.185358] type=1400 audit(1381162643.401:7): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1112 comm="apparmor_parser"
[    5.186101] type=1400 audit(1381162643.401:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1112 comm="apparmor_parser"
[    5.186269] type=1400 audit(1381162643.401:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=1111 comm="apparmor_parser"
[    5.186622] type=1400 audit(1381162643.405:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1112 comm="apparmor_parser"
[    5.494499] e1000e 0000:00:19.0: irq 60 for MSI/MSI-X
[    5.598271] e1000e 0000:00:19.0: irq 60 for MSI/MSI-X
[    5.598394] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    5.603201] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[    5.603352] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[    5.611729] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    5.731779] vboxdrv: module verification failed: signature and/or required key missing - tainting kernel
[    5.736678] vboxdrv: Found 4 processor cores.
[    5.736920] vboxdrv: fAsync=0 offMin=0x3c9 offMax=0x2f4b
[    5.737031] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[    5.737035] vboxdrv: Successfully loaded version 4.2.18 (interface 0x001a0005).
[    5.801058] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input14
[    5.813485] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input15
[    5.956749] vboxpci: IOMMU not found (not registered)
[   12.008731] init: plymouth-stop pre-start process (1687) terminated with status 1
[   12.903656] usb 2-7: new high-speed USB device number 6 using xhci_hcd
[   12.920576] usb 2-7: config 1 has an invalid interface number: 8 but max is 3
[   12.920581] usb 2-7: config 1 has no interface number 1
[   12.920840] usb 2-7: config 2 has an invalid interface number: 12 but max is 1
[   12.920842] usb 2-7: config 2 has an invalid interface number: 13 but max is 1
[   12.920844] usb 2-7: config 2 has an invalid interface number: 13 but max is 1
[   12.920846] usb 2-7: config 2 has no interface number 0
[   12.920848] usb 2-7: config 2 has no interface number 1
[   12.921377] usb 2-7: New USB device found, idVendor=413c, idProduct=81a3
[   12.921379] usb 2-7: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[   12.921381] usb 2-7: Product: Dell Wireless 5570 HSPA+ (42Mbps) Mobile Broadband Card
[   12.921383] usb 2-7: Manufacturer: Sierra Wireless, Incorporated
[   12.941346] usbcore: registered new interface driver usbserial
[   12.941368] usbcore: registered new interface driver usbserial_generic
[   12.941381] usbserial: USB Serial support registered for generic
[   12.944322] usbcore: registered new interface driver sierra
[   12.944341] usbserial: USB Serial support registered for Sierra USB modem
[   12.947525] usbcore: registered new interface driver cdc_wdm
[   12.949657] usbcore: registered new interface driver cdc_ncm
[   12.952491] cdc_mbim 2-7:2.12: cdc-wdm0: USB WDM device
[   12.952787] cdc_mbim 2-7:2.12 wwan0: register 'cdc_mbim' at usb-0000:00:14.0-7, CDC MBIM, 0a:cb:b7:43:69:95
[   12.952821] usbcore: registered new interface driver cdc_mbim
[   21.762620] wlan0: authenticate with 00:26:24:79:15:8e
[   21.763406] wlan0: send auth to 00:26:24:79:15:8e (try 1/3)
[   21.765172] wlan0: authenticated
[   21.765269] iwlwifi 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   21.765272] iwlwifi 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   21.768362] wlan0: associate with 00:26:24:79:15:8e (try 1/3)
[   21.770707] wlan0: RX AssocResp from 00:26:24:79:15:8e (capab=0x411 status=0 aid=2)
[   21.773652] wlan0: associated
[   21.773689] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   27.319045] init: cups-browsed main process ended, respawning
[   27.326045] init: cups-browsed main process ended, respawning

```

Looking more closely, I can see that a wwan0 device is being registered. Could this be the card?

```

root@latitude:~# nmcli nm status
RUNNING         STATE           WIFI-HARDWARE   WIFI       WWAN-HARDWARE   WWAN      
running         connected       enabled         enabled    enabled         disabled  

```

The network manager applet, however, doesn't know anything about it, nor can I connect to the (presumed) device:
```

root@latitude:~# cu -l /dev/cdc-wdm0 
cu: open (/dev/cdc-wdm0): Permission denied
cu: /dev/cdc-wdm0: Line in use

```

Any ideas?

Thanks,

Miiro

---

### Post by Miiro_Juuso on 2013-10-07
Quick update:

[LIST=1]
[*]Disabling the WWAN card from BIOS hides wwan0 and /dev/cdc-wdm0 devices, so these are probably what I'm looking for.
[*]The device is actually a Sierra Wireless AirPrime MC8805, branded as Dell Wireless 5570. Interestingly enough, basically no relevant Google hits for this device and Linux, apart from Sierra Wireless datasheets stating Linux support for this device.
[/LIST]

As it seems the device is however recognized, how would I go about creating a connection and/or making the device visible in the network manager applet?

Thanks,

Miiro

---

### Post by varunendra on 2013-10-08
> **Miiro_Juuso said:**
> 
```
[   12.903656] usb 2-7: new high-speed USB device number 6 using **xhci_hcd**
[   12.920576] usb 2-7: config 1 has an invalid interface number: 8 but max is 3
[   12.920581] usb 2-7: config 1 has no interface number 1
[   12.920840] usb 2-7: config 2 has an invalid interface number: 12 but max is 1
[   12.920842] usb 2-7: config 2 has an invalid interface number: 13 but max is 1
[   12.920844] usb 2-7: config 2 has an invalid interface number: 13 but max is 1
[   12.920846] usb 2-7: config 2 has no interface number 0
[   12.920848] usb 2-7: config 2 has no interface number 1
[   12.921377] usb 2-7: New USB device found, **idVendor=413c, idProduct=81a3**
[   12.921379] usb 2-7: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[   12.921381] usb 2-7: Product: Dell Wireless 5570 HSPA+ (42Mbps) Mobile Broadband Card
[   12.921383] usb 2-7: Manufacturer: Sierra Wireless, Incorporated
[   12.941346] [B]usbcore: registered new interface driver usbserial
[   12.941368] usbcore: registered new interface driver usbserial_generic
[   12.941381] usbserial: USB Serial support registered for generic
[   12.944322] usbcore: registered new interface driver sierra
[   12.944341] usbserial: USB Serial support registered for Sierra USB modem
[   12.947525] usbcore: registered new interface driver cdc_wdm
[   12.949657] usbcore: registered new interface driver cdc_ncm[/B]
[   12.952491] cdc_mbim 2-7:2.12: cdc-wdm0: USB WDM device
[   12.952787] cdc_mbim 2-7:2.12 wwan0: register 'cdc_mbim' at usb-0000:00:14.0-7, CDC MBIM, 0a:cb:b7:43:69:95
[   12.952821] usbcore: registered new interface driver cdc_mbim

```
Looks like something similar like a 3g/4g modem located on a USB3 bus. But not sure how the sierra or other drivers got loaded for it.

> **Miiro_Juuso said:**
> The device is actually a Sierra Wireless AirPrime MC8805, branded as Dell Wireless 5570. Interestingly enough, basically no relevant Google hits for this device and Linux, apart from Sierra Wireless datasheets **[COLOR="#FF0000"]stating Linux support for this device[/COLOR]**.
Link please, maybe we can get some hint there.

The closest device the sierra driver supports (in my 3.2.0-36 kernel) is "413c : **8133**" not "413c | **[COLOR="#FF0000"]81a3[/COLOR]**". Obviously the version in your kernel doesn't support that PID either, otherwise the modprobe command I gave must have returned an output.

---

### Post by bmork on 2013-10-09
> **varunendra said:**
> Looks like something similar like a 3g/4g modem located on a USB3 bus. But not sure how the sierra or other drivers got loaded for it.


Link please, maybe we can get some hint there.

The closest device the sierra driver supports (in my 3.2.0-36 kernel) is "413c : **8133**" not "413c | **[COLOR=#FF0000]81a3[/COLOR]**". Obviously the version in your kernel doesn't support that PID either, otherwise the modprobe command I gave must have returned an output.

This device is supported by the CDC MBIM **class** driver, so it doesn't need any device specific entry.  In theory....  But that's before we get to the long list of firmware bugs most likely present in this device, like the other Sierra Wireless MBIM devices we've encountered so far.

Please see the thread [http://ubuntuforums.org/showthread.php?t=2165362](http://ubuntuforums.org/showthread.php?t=2165362) .  It has instructions on how to test the connection using mbim tools, and also how to patch the driver in case that's necessary.

See also the discussion at [http://www.spinics.net/lists/netdev/msg248535.html](http://www.spinics.net/lists/netdev/msg248535.html) regarding the ZLP workaround. If we can have a positive confirmation that this device need the workaround, then that is a good enough reason for me to propose enabling that workaround by default for all devices.  Possible with a whitelist for devices known *not* to need it, as suggested by David Miller, initially set to the Ericsson vendor ID.


EDIT:  BTW, if you don't want to play with MBIM, then it is perfectly possible to run the device in "legacy mode" by switching to USB configuration #1.  Due to another firmware bug most likely present, it is best to do this immediately after the device is detected, e.g. from an udev rule.  The sample rule here should be easy to adapt if you want to test this: [http://ubuntuforums.org/showthread.php?t=2121838&p=12550186#post12550186](http://ubuntuforums.org/showthread.php?t=2121838&p=12550186#post12550186)

Note that Linux selects the MBIM configuration by default because proper USB classes are preferred over vendor specific functions.  That's why you end up with cfg #2 being selected by default here instead of cfg #1

---

### Post by varunendra on 2013-10-10
Thanks for clarifying that bmork, I know some other drivers (b43 for example) that load without a PID entry in it, but it is the first time I got any idea of 'how'. :)

@Miiro, please follow the suggestions by bmork and let us know the result -
> **bmork said:**
> Please see the thread [http://ubuntuforums.org/showthread.php?t=2165362](http://ubuntuforums.org/showthread.php?t=2165362) .  It has instructions on how to test the connection using mbim tools, and also how to patch the driver in case that's necessary.

See also the discussion at [http://www.spinics.net/lists/netdev/msg248535.html](http://www.spinics.net/lists/netdev/msg248535.html) regarding the ZLP workaround.....

You may be helping him in improving the driver, or at least support for your device.

---

### Post by bmork on 2013-11-05
Just FYI: I went on and enabled the "ZLP workaround" by default in the cdc_mbim driver.  The patch should go in Linux v3.13.

It's far too intrusive to be a candidate for stable kernel releases, but you'd probably want to try the modem again once you get a 3.13 or later kernel from your distro. Which of course will take a while - the 3.13 release is expected in January 2014.  I guess that means Ubuntu 14.04, is that correct?

---

### Post by varunendra on 2013-11-05
> **bmork said:**
> Just FYI: I went on and enabled the "ZLP workaround" by default in the cdc_mbim driver.  The patch should go in Linux v3.13.

Thanks for the update bmork, and a huge thanks for the good work you've been doing to make it better. :)

> the 3.13 release is expected in January 2014.  I guess that means Ubuntu 14.04, is that correct?
14.04 will be released in April 2014, so it should definitely come with the latest stable kernel.

But I think the updates for its beta testing versions and 13.10 should provide it via repositories much earlier, maybe in February, or early March at most.

---

### Post by sealek on 2013-12-24
I have this modem too, i made changes written in this topic but i have other strange behavior - please look there:

[http://ubuntuforums.org/showthread.php?t=2195299](http://ubuntuforums.org/showthread.php?t=2195299)

---

