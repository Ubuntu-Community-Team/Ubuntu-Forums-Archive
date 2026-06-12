---
title: "problems loading driver for USB wifi stick"
date: 2007-08-01
forum: Networking &amp; Wireless
---

### Post by arielsegal on 2007-08-01
I'm using Ubuntu 7.04
I have installed a driver for an Edimax USB wifi stick. The dirver was installed successfully, and loaded. But when I rebooted the system the driver didn't load.
I have copied and pased the results to this message.
Please help me with this problem.

Here is the result of 'lsusb' command for the usb port with the wifi stick:
--------------------------------------------------------
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0
  bMaxPacketSize0        64
  idVendor           0x148f Ralink Technology, Corp.
  idProduct          0x2573 
  bcdDevice            0.01
  iManufacturer           1 Ralink
  iProduct                2 802.11 bg WLAN
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
      (Bus Powered)
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
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0000
  (Bus Powered)
-------------------------------------------------------

Here is the result of 'dmesg' command after I tried unsuccessffully to reload the driver:
-------------------------------------------------------
[   41.337891] Loading module: rt2x00lib - CVS (N/A) by [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com).
[   41.342427] Loading module: rt73usb - CVS (N/A) by [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com).
[   41.407156] ACPI: PCI Interrupt 0000:00:11.6[C] -> Link [LNKC] -> GSI 5 (level, low) -> IRQ 5
[   41.407609] PCI: Setting latency timer of device 0000:00:11.6 to 64
[   41.458343] input: ImPS/2 Generic Wheel Mouse as /class/input/input3
[   41.501991] sd 1:0:0:0: Attached scsi generic sg0 type 0
[   41.686118] usbcore: registered new interface driver rt73usb
[   41.725027] usbcore: registered new interface driver rt2570
[   41.817069] rtusb init ====>
[   41.817173] usbcore: registered new interface driver rt73
[   41.916453] ACPI: PCI Interrupt 0000:00:11.5[C] -> Link [LNKC] -> GSI 5 (level, low) -> IRQ 5
[   41.916624] PCI: Setting latency timer of device 0000:00:11.5 to 64
[   42.293881] wmaster0: Selected rate control algorithm 'simple'
[   42.611066] wlan0: starting scan
[   42.828602] fuse init (API version 7.8)
[   42.883583] lp0: using parport0 (interrupt-driven).
[   42.947491] Adding 746980k swap on /dev/disk/by-uuid/28f278e0-727b-4198-8c67-9951d78cb42f.  Priority:-1 extents:1 across:746980k
[   43.104925] EXT3 FS on hda1, internal journal
[   43.729021] rt73usb->rt2x00_vendor_request: Error - vendor request error. Request 0x07 failed for offset 0x3040 with error -71.
[   43.730258] rt73usb->rt2x00_vendor_request: Error - vendor request error. Request 0x06 failed for offset 0x3040 with error -71.
[   43.731506] rt73usb->rt2x00_vendor_request: Error - vendor request error. Request 0x07 failed for offset 0x308c with error -71.
[   43.732754] rt73usb->rt2x00_vendor_request: Error - vendor request error. Request 0x06 failed for offset 0x308c with error -71.
[   43.734003] rt73usb->rt2x00_vendor_request: Error - vendor request error. Request 0x07 failed for offset 0x308c with error -71.
[   43.735250] rt73usb->rt2x00_vendor_request: Error - vendor request error. Request 0x07 failed for offset 0x308c with error -71.
[   43.736499] rt73usb->rt2x00_vendor_request: Error - vendor request error. Request 0x07 failed for offset 0x308c with error -71.
[   43.737747] rt73usb->rt2x00_vendor_request: Error - vendor request error. Request 0x07 failed for offset 0x308c with error -71.
[   43.738995] rt73usb->rt2x00_vendor_request: Error - vendor request error. Request 0x07 failed for offset 0x308c with error -71.
[   43.739100] rt73usb->rt2x00_bbp_read: Error - PHY_CSR3 register busy. Read failed.
[   43.740244] rt73usb->rt2x00_vendor_request: Error - vendor request error. Request 0x07 failed for offset 0x308c with error -71.
[   43.741492] rt73usb->rt2x00_vendor_request: Error - vendor request error. Request 0x06 failed for offset 0x308c with error -71.
[   43.742739] rt73usb->rt2x00_vendor_request: Error - vendor request error. Request 0x07 failed for offset 0x3090 with error -71.
[   43.743989] rt73usb->rt2x00_vendor_request: Error - vendor request error. Request 0x06 failed for offset 0x3090 with error -71.
[   43.745240] rt73usb->rt2x00_vendor_request: Error - vendor request error. Request 0x07 failed for offset 0x3090 with error -71.
[   43.746485] rt73usb->rt2x00_vendor_request: Error - vendor request error. Request 0x07 failed for offset 0x3090 with error -71.
[   43.747733] rt73usb->rt2x00_vendor_request: Error - vendor request error. Request 0x07 failed for offset 0x3090 with error -71.
[   43.748981] rt73usb->rt2x00_vendor_request: Error - vendor request error. Request 0x07 failed for offset 0x3090 with error -71.
[   43.750229] rt73usb->rt2x00_vendor_request: Error - vendor request error. Request 0x07 failed for offset 0x3090 with error -71.
[   43.750333] rt73usb->rt2x00_rf_write: Error - PHY_CSR4 register busy. Write failed.
[   43.751478] rt73usb->rt2x00_vendor_request: Error - vendor request error. Request 0x07 failed for offset 0x3090 with error -71.
[   43.752726] rt73usb->rt2x00_vendor_request: Error - vendor request error. Request 0x07 failed for offset 0x3090 with error -71.
[   43.754038] rt73usb->rt2x00_vendor_request: Error - vendor request error. Request 0x07 failed for offset 0x3090 with error -71.
[   43.755229] rt73usb->rt2x00_vendor_request: Error - vendor request error. Request 0x07 failed for offset 0x3090 with error -71.
[   43.756478] rt73usb->rt2x00_vendor_request: Error - vendor request error. Request 0x07 failed for offset 0x3090 with error -71.
[   43.756594] rt73usb->rt2x00_rf_write: Error - PHY_CSR4 register busy. Write failed.
[   43.757720] rt73usb->rt2x00_vendor_request: Error - vendor request error. Request 0x07 failed for offset 0x3090 with error -71.
[   43.758968] rt73usb->rt2x00_vendor_request: Error - vendor request error. Request 0x07 failed for offset 0x3090 with error -71.
[   43.760215] rt73usb->rt2x00_vendor_request: Error - vendor request error. Request 0x07 failed for offset 0x3090 with error -71.
[   43.761463] rt73usb->rt2x00_vendor_request: Error - vendor request error. Request 0x07 failed for offset 0x3090 with error -71.
[   43.762711] rt73usb->rt2x00_vendor_request: Error - vendor request error. Request 0x07 failed for offset 0x3090 with error -71.
[   43.762815] rt73usb->rt2x00_rf_write: Error - PHY_CSR4 register busy. Write failed.
[   43.763960] rt73usb->rt2x00_vendor_request: Error - vendor request error. Request 0x07 failed for offset 0x3090 with error -71.
[   43.765208] rt73usb->rt2x00_vendor_request: Error - vendor request error. Request 0x07 failed for offset 0x3090 with error -71.
[   43.766457] rt73usb->rt2x00_vendor_request: Error - vendor request error. Request 0x07 failed for offset 0x3090 with error -71.
[   43.767705] rt73usb->rt2x00_vendor_request: Error - vendor request error. Request 0x07 failed for offset 0x3090 with error -71.
[   43.768953] rt73usb->rt2x00_vendor_request: Error - vendor request error. Request 0x07 failed for offset 0x3090 with error -71.
[   43.769058] rt73usb->rt2x00_rf_write: Error - PHY_CSR4 register busy. Write failed.
[   43.770201] rt73usb->rt2x00_vendor_request: Error - vendor request error. Request 0x07 failed for offset 0x3090 with error -71.
[   43.771450] rt73usb->rt2x00_vendor_request: Error - vendor request error. Request 0x07 failed for offset 0x3090 with error -71.
[   43.772698] rt73usb->rt2x00_vendor_request: Error - vendor request error. Request 0x07 failed for offset 0x3090 with error -71.
[   43.773946] rt73usb->rt2x00_vendor_request: Error - vendor request error. Request 0x07 failed for offset 0x3090 with error -71.
[   43.775194] rt73usb->rt2x00_vendor_request: Error - vendor request error. Request 0x07 failed for offset 0x3090 with error -71.
[   43.775298] rt73usb->rt2x00_rf_write: Error - PHY_CSR4 register busy. Write failed.
[   43.776443] rt73usb->rt2x00_vendor_request: Error - vendor request error. Request 0x07 failed for offset 0x3090 with error -71.
[   43.777690] rt73usb->rt2x00_vendor_request: Error - vendor request error. Request 0x07 failed for offset 0x3090 with error -71.
[   43.778939] rt73usb->rt2x00_vendor_request: Error - vendor request error. Request 0x07 failed for offset 0x3090 with error -71.
[   43.780187] rt73usb->rt2x00_vendor_request: Error - vendor request error. Request 0x07 failed for offset 0x3090 with error -71.
[   43.781435] rt73usb->rt2x00_vendor_request: Error - vendor request error. Request 0x07 failed for offset 0x3090 with error -71.
[   43.781539] rt73usb->rt2x00_rf_write: Error - PHY_CSR4 register busy. Write failed.
[   43.782682] rt73usb->rt2x00_vendor_request: Error - vendor request error. Request 0x07 failed for offset 0x3090 with error -71.
[   43.783931] rt73usb->rt2x00_vendor_request: Error - vendor request error. Request 0x07 failed for offset 0x3090 with error -71.
[   43.785178] rt73usb->rt2x00_vendor_request: Error - vendor request error. Request 0x07 failed for offset 0x3090 with error -71.
[   43.786427] rt73usb->rt2x00_vendor_request: Error - vendor request error. Request 0x07 failed for offset 0x3090 with error -71.
[   43.787675] rt73usb->rt2x00_vendor_request: Error - vendor request error. Request 0x07 failed for offset 0x3090 with error -71.
[   43.787779] rt73usb->rt2x00_rf_write: Error - PHY_CSR4 register busy. Write failed.
[   43.788924] rt73usb->rt2x00_vendor_request: Error - vendor request error. Request 0x07 failed for offset 0x3090 with error -71.
[   43.790173] rt73usb->rt2x00_vendor_request: Error - vendor request error. Request 0x07 failed for offset 0x3090 with error -71.
[   43.791421] rt73usb->rt2x00_vendor_request: Error - vendor request error. Request 0x07 failed for offset 0x3090 with error -71.
[   43.792669] rt73usb->rt2x00_vendor_request: Error - vendor request error. Request 0x07 failed for offset 0x3090 with error -71.
[   43.793916] rt73usb->rt2x00_vendor_request: Error - vendor request error. Request 0x07 failed for offset 0x3090 with error -71.
[   43.794021] rt73usb->rt2x00_rf_write: Error - PHY_CSR4 register busy. Write failed.
[   43.795164] rt73usb->rt2x00_vendor_request: Error - vendor request error. Request 0x07 failed for offset 0x3090 with error -71.
[   43.796413] rt73usb->rt2x00_vendor_request: Error - vendor request error. Request 0x07 failed for offset 0x3090 with error -71.
[   43.797661] rt73usb->rt2x00_vendor_request: Error - vendor request error. Request 0x07 failed for offset 0x3090 with error -71.
[   43.798911] rt73usb->rt2x00_vendor_request: Error - vendor request error. Request 0x07 failed for offset 0x3090 with error -71.
[   43.800157] rt73usb->rt2x00_vendor_request: Error - vendor request error. Request 0x07 failed for offset 0x3090 with error -71.
[   43.800262] rt73usb->rt2x00_rf_write: Error - PHY_CSR4 register busy. Write failed.
[   43.801406] rt73usb->rt2x00_vendor_request: Error - vendor request error. Request 0x07 failed for offset 0x3090 with error -71.
[   43.802654] rt73usb->rt2x00_vendor_request: Error - vendor request error. Request 0x07 failed for offset 0x3090 with error -71.
[   43.803903] rt73usb->rt2x00_vendor_request: Error - vendor request error. Request 0x07 failed for offset 0x3090 with error -71.
[   43.805151] rt73usb->rt2x00_vendor_request: Error - vendor request error. Request 0x07 failed for offset 0x3090 with error -71.
[   43.806399] rt73usb->rt2x00_vendor_request: Error - vendor request error. Request 0x07 failed for offset 0x3090 with error -71.
[   43.806503] rt73usb->rt2x00_rf_write: Error - PHY_CSR4 register busy. Write failed.
[   43.807647] rt73usb->rt2x00_vendor_request: Error - vendor request error. Request 0x07 failed for offset 0x3090 with error -71.
[   43.808902] rt73usb->rt2x00_vendor_request: Error - vendor request error. Request 0x07 failed for offset 0x3090 with error -71.
[   43.810147] rt73usb->rt2x00_vendor_request: Error - vendor request error. Request 0x07 failed for offset 0x3090 with error -71.
[   43.811393] rt73usb->rt2x00_vendor_request: Error - vendor request error. Request 0x07 failed for offset 0x3090 with error -71.
[   43.812642] rt73usb->rt2x00_vendor_request: Error - vendor request error. Request 0x07 failed for offset 0x3090 with error -71.
[   43.812763] rt73usb->rt2x00_rf_write: Error - PHY_CSR4 register busy. Write failed.
[   43.820880] rt73usb->rt2x00_vendor_request: Error - vendor request error. Request 0x07 failed for offset 0x3024 with error -71.
[   43.822126] rt73usb->rt2x00_vendor_request: Error - vendor request error. Request 0x06 failed for offset 0x3024 with error -71.
[   43.823375] rt73usb->rt2x00_vendor_request: Error - vendor request error. Request 0x07 failed for offset 0x3020 with error -71.
[   43.824623] rt73usb->rt2x00_vendor_request: Error - vendor request error. Request 0x06 failed for offset 0x3020 with error -71.
[   43.825871] rt73usb->rt2x00_vendor_request: Error - vendor request error. Request 0x07 failed for offset 0x3040 with error -71.
[   43.827118] rt73usb->rt2x00_vendor_request: Error - vendor request error. Request 0x06 failed for offset 0x3040 with error -71.
[   43.828368] rt73usb->rt2x00_vendor_request: Error - vendor request error. Request 0x07 failed for offset 0x3050 with error -71.
[   43.829615] rt73usb->rt2x00_vendor_request: Error - vendor request error. Request 0x06 failed for offset 0x3050 with error -71.
[   43.830865] rt73usb->rt2x00_vendor_request: Error - vendor request error. Request 0x07 failed for offset 0x3040 with error -71.
[   43.832112] rt73usb->rt2x00_vendor_request: Error - vendor request error. Request 0x06 failed for offset 0x3040 with error -71.
[   43.891691] usb 4-1: USB disconnect, address 2
[   43.924158] rt73usb->rt2x00_vendor_request: Error - vendor request error. Request 0x0a failed for offset 0x0000 with error -19.
[   43.924174] rt73usb->rt2x00_vendor_request: Error - vendor request error. Request 0x06 failed for offset 0x3028 with error -19.
[   43.924181] rt73usb->rt2x00_vendor_request: Error - vendor request error. Request 0x06 failed for offset 0x3064 with error -19.
[   43.924188] rt73usb->rt2x00_vendor_request: Error - vendor request error. Request 0x07 failed for offset 0x3040 with error -19.
[   43.924195] rt73usb->rt2x00_vendor_request: Error - vendor request error. Request 0x06 failed for offset 0x3040 with error -19.
[   43.924202] rt73usb->rt2x00_vendor_request: Error - vendor request error. Request 0x0c failed for offset 0x0000 with error -19.
--------------------------------------------------------

---

### Post by kevdog on 2007-08-01
Quick question, did you download, compile and install the rt73 driver from serial monkey or use the built-in drivers?

---

### Post by arielsegal on 2007-08-02
well, I have compiled and installed the rt73 driver provided in the CD that came with the wifi stick.

---

