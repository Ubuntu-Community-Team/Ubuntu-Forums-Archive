---
title: "Huawei CDC Modem C300 on Ubuntu 8.04"
date: 2008-06-22
forum: Networking &amp; Wireless
---

### Post by anandjm on 2008-06-22
I have a Huawei CDMA Mobile C5320 which supports three modes. 
[LIST=1]
[*]USB Disk
[*]Data
[*]PC Sync
[/LIST]
Windows detects it as CDC C300 modem in data mode. In Ubuntu/8.04, when the phone is plugged in, dmesg shows the following:

[COLOR="DarkSlateGray"][INDENT][ 1677.351701] usb 2-1: USB disconnect, address 2
[ 1681.363228] usb 2-1: new full speed USB device using uhci_hcd and address 3
[ 1679.524635] usb 2-1: configuration #1 chosen from 1 choice[/INDENT]
[/COLOR]
No driver is loaded. I tried doing a modprobe cdc-acm. But it still does not detect the modem. lsusb for the device shows the following:
[COLOR="DarkSlateGray"]
[INDENT]Bus 002 Device 003: ID 12d1:3197 Huawei Technologies Co., Ltd.[/INDENT][/COLOR]

A "sudo lsusb -v -d 12d1:3197" gives me:
 
[COLOR="DarkSlateGray"][INDENT]
Bus 002 Device 003: ID 12d1:3197 Huawei Technologies Co., Ltd. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.01
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x12d1 Huawei Technologies Co., Ltd.
  idProduct          0x3197 
  bcdDevice            0.00
  iManufacturer           1 Huawei, Technologies
  iProduct                2 Huawei Technologies C300
  iSerial                 3 Serial Number
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           39
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9

      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           3
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              4 Data Interface
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval             128
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
Device Status:     0x0001
  Self Powered[/INDENT][/COLOR]

Strangely though in PC-Sync mode, the cdc-acm driver gets loaded. lsusb lists the device as:
[COLOR="DarkSlateGray"][INDENT]Bus 002 Device 004: ID 0ac8:8581 Z-Star Microelectronics Corp.[/INDENT][/COLOR]
Corresponding dmesg output is:
[COLOR="DarkSlateGray"][INDENT][ 2116.599260] usb 2-1: new full speed USB device using uhci_hcd and address 4
[ 2116.753458] usb 2-1: configuration #1 chosen from 1 choice
[ 2116.759918] /build/buildd/linux-2.6.24/drivers/usb/class/cdc-acm.c: This device cannot do calls on its own. It is no modem.
[ 2116.759945] cdc_acm 2-1:1.0: ttyACM0: USB ACM device
[/INDENT][/COLOR]
Since it is not a modem and just a cdc serial port, it cannot be used for dialing. 

I have earlier used the Huawei CDMA C2900i Mobile (E220) and it used to work. Anybody with some leads on how to go about getting it to work. Googling did not get me anything.

---

### Post by anandjm on 2008-06-23
A "sudo modprobe usbserial vendor=0x12d1 product=0x3197" did the trick. Strange though I thought I had tried it earlier but did not find it working. But sadly the speed is quite slow. Read somewhere that option module gives faster data transfer. 

[IMG]http://ubuntuforums.org/images/icons/icon7.gif[/IMG]

---

### Post by anandjm on 2008-06-24
I seem to have finally fixed the problem by adding support for my device in option.c and recompiling the module. [IMG]http://ubuntuforums.org/images/smilies/smiley-faces-75.gif[/IMG] The patch file is as follows:

[INDENT]
*** /usr/src/linux-source-2.6.24/drivers/usb/serial/option.c    2008-06-18 19:35:04.000000000 +0530
--- option.c    2008-06-24 10:56:41.000000000 +0530
***************
*** 109,114 ****
--- 109,115 ----
  #define HUAWEI_PRODUCT_E600                   0x1001
  #define HUAWEI_PRODUCT_E220                   0x1003
  #define HUAWEI_PRODUCT_E220BIS                        0x1004
+ #define HUAWEI_PRODUCT_C300                   0x3197

  #define NOVATELWIRELESS_VENDOR_ID             0x1410
  #define DELL_VENDOR_ID                                0x413C
***************
*** 158,163 ****
--- 159,165 ----
        { USB_DEVICE(OPTION_VENDOR_ID, OPTION_PRODUCT_ETNA_KOI_MODEM) },
        { USB_DEVICE(OPTION_VENDOR_ID, OPTION_PRODUCT_ETNA_KOI_NETWORK) },
        { USB_DEVICE(HUAWEI_VENDOR_ID, HUAWEI_PRODUCT_E600) },
+       { USB_DEVICE(HUAWEI_VENDOR_ID, HUAWEI_PRODUCT_C300) },
        { USB_DEVICE_AND_INTERFACE_INFO(HUAWEI_VENDOR_ID, HUAWEI_PRODUCT_E220, 0xff, 0xff, 0xff) },
        { USB_DEVICE_AND_INTERFACE_INFO(HUAWEI_VENDOR_ID, HUAWEI_PRODUCT_E220BIS, 0xff, 0xff, 0xff) },
        { USB_DEVICE(NOVATELWIRELESS_VENDOR_ID, 0x1100) }, /* Novatel Merlin XS620/S640 */
[/INDENT]

Now just need to  create a hal rules for the device.

---

### Post by ajack on 2009-05-28
> **anandjm said:**
> I seem to have finally fixed the problem by adding support for my device in option.c and recompiling the module. [IMG]http://ubuntuforums.org/images/smilies/smiley-faces-75.gif[/IMG] The patch file is as follows:

[INDENT]
*** /usr/src/linux-source-2.6.24/drivers/usb/serial/option.c    2008-06-18 19:35:04.000000000 +0530
--- option.c    2008-06-24 10:56:41.000000000 +0530
***************
*** 109,114 ****
--- 109,115 ----
  #define HUAWEI_PRODUCT_E600                   0x1001
  #define HUAWEI_PRODUCT_E220                   0x1003
  #define HUAWEI_PRODUCT_E220BIS                        0x1004
+ #define HUAWEI_PRODUCT_C300                   0x3197

  #define NOVATELWIRELESS_VENDOR_ID             0x1410
  #define DELL_VENDOR_ID                                0x413C
***************
*** 158,163 ****
--- 159,165 ----
        { USB_DEVICE(OPTION_VENDOR_ID, OPTION_PRODUCT_ETNA_KOI_MODEM) },
        { USB_DEVICE(OPTION_VENDOR_ID, OPTION_PRODUCT_ETNA_KOI_NETWORK) },
        { USB_DEVICE(HUAWEI_VENDOR_ID, HUAWEI_PRODUCT_E600) },
+       { USB_DEVICE(HUAWEI_VENDOR_ID, HUAWEI_PRODUCT_C300) },
        { USB_DEVICE_AND_INTERFACE_INFO(HUAWEI_VENDOR_ID, HUAWEI_PRODUCT_E220, 0xff, 0xff, 0xff) },
        { USB_DEVICE_AND_INTERFACE_INFO(HUAWEI_VENDOR_ID, HUAWEI_PRODUCT_E220BIS, 0xff, 0xff, 0xff) },
        { USB_DEVICE(NOVATELWIRELESS_VENDOR_ID, 0x1100) }, /* Novatel Merlin XS620/S640 */
[/INDENT]

Now just need to  create a hal rules for the device.

I can't seem to get this file... what did you do to get this far?  I was only successful up to the:

sudo modprobe usbserial vendor=0x12d1 product=0x3197

command... help!!!

---

### Post by GeorgeVita on 2009-05-28
Hi **ajack**,

Recent version of Ubuntu (9.04) has the usbserial driver encapsulated into kernel (cannot run as driver to add parameters for a non detected modem).You can read more to:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/345002/](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/345002/)
> Pete Graner: The module is no longer complied in the kernel. You can get it now by enabling the -proposed repo and updating the kernel, or you can wait until it hits the -updates repo.

The above "bug" fixed by restoring the usbserial to be a module again! To try it go to:
System > Administration > Software Sources > Update > tick Pre-released updates
then close, reload or go directly to System > Administration > Update Manager and do the update.

Of course you need an internet connection via ethernet or wireless!

Regards,
George

---

### Post by ajack on 2009-05-28
> **GeorgeVita said:**
> Hi **ajack**,

Recent version of Ubuntu (9.04) has the usbserial driver encapsulated into kernel (cannot run as driver to add parameters for a non detected modem).You can read more to:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/345002/](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/345002/)


The above "bug" fixed by restoring the usbserial to be a module again! To try it go to:
System > Administration > Software Sources > Update > tick Pre-released updates
then close, reload or go directly to System > Administration > Update Manager and do the update.

Of course you need an internet connection via ethernet or wireless!

Regards,
George

Hi George... The 9.04 reference is for my home laptop, I am using 8.04 on my work laptop as 8.04 is an LTS build.  All I need is to get the bl**dy Huawei C300 phone to connect me to the internet.  Anyway, thanks for your help. Much appreciated.

---

### Post by GeorgeVita on 2009-05-29
> **ajack said:**
> I can't seem to get this file... what did you do to get this far?  I was only successful up to the:

sudo modprobe usbserial vendor=0x12d1 product=0x3197

command... help!!!

Hi again, sorry for the misunderstanding, after above what ports created?

From terminal: **ls /dev/ttyU* /dev/ttyA* /dev/ttyH***
  
My opinion is that using 8.04 the best way to connect is the wvdial method. Do you have any experience on wvdial?

Regards,
George

---

