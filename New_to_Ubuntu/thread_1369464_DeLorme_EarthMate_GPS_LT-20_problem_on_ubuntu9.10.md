---
title: "DeLorme EarthMate GPS LT-20 problem on ubuntu9.10"
date: 2010-01-01
forum: New to Ubuntu
---

### Post by fastness on 2010-01-01
Lenovo ThinkPad X61 Tablet + ubuntu 9.10 +Logitech MX Revolution BLuetooth Mouse
dmesg
..
[    7.122163] cypress 4-1:1.0: DeLorme Earthmate USB converter detected
[    7.125360] usb 4-1: DeLorme Earthmate USB converter now attached to ttyUSB0
[    7.125383] usbcore: registered new interface driver cypress
[    7.125387] cypress_m8: v1.09:Cypress USB to Serial Driver
..
[   13.887259] earthmate ttyUSB0: cypress_serial_control - failed sending serial line settings - -71
[   13.887355] earthmate ttyUSB0: cypress_m8 suspending failing port 0 - interval might be too short
[   13.887427] earthmate ttyUSB0: cypress_open - failed submitting read urb, error -2
..
[  746.708074] usb 4-1: new low speed USB device using uhci_hcd and address 3
[  746.889960] usb 4-1: configuration #1 chosen from 1 choice
[  746.892913] cypress 4-1:1.0: DeLorme Earthmate USB converter detected
[  746.895968] usb 4-1: DeLorme Earthmate USB converter now attached to ttyUSB0
[ 1001.125819] earthmate ttyUSB0: cypress_serial_control - failed sending serial line settings - -71
[ 1001.125830] earthmate ttyUSB0: cypress_m8 suspending failing port 0 - interval might be too short
[ 1001.143830] usb 4-1: cypress_read_int_callback - unexpected nonzero read status received: -84

cat /dev/ttyUSB0
cat: /dev/ttyUSB0: Input/output error

---

### Post by sbromley on 2010-02-02
Hi all, I've just purchased an Earthmate GPS LT-20 and I am having the same problems.
I've read the available history online, including this reference:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/111694/comments/20](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/111694/comments/20)
which seem to hint at everything being resolved long ago. But this is not the case.
I've tried hacking on the cypress_m8 kernel module but I'm not getting anywhere.
Here are my details: Ubuntu 9.10, Linux 2.6.31-17-generic #54-Ubuntu SMP Thu Dec 10 17:01:44 UTC 2009 x86_64 GNU/Linux.
lsusb gives:
Bus 003 Device 026: ID 1163:0200 DeLorme Publishing, Inc. Earthmate GPS (LT-20, LT-40)
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x1163 DeLorme Publishing, Inc.
  idProduct          0x0200 Earthmate GPS (LT-20, LT-40)
  bcdDevice            1.11
  iManufacturer           3 
  iProduct                1 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           41
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower              400mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      0 No Subclass
      bInterfaceProtocol      0 None
      iInterface              0 
      ** UNRECOGNIZED:  09 21 10 01 21 01 22 25 00
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
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval              10

More than anything, I would just like to know if this is still an active issue. Could anyone please comment?

Best regards,
Sam

---

