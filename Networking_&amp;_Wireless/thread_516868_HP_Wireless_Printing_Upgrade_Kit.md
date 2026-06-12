---
title: "HP Wireless Printing Upgrade Kit"
date: 2007-08-03
forum: Networking &amp; Wireless
---

### Post by McGivrer on 2007-08-03
Does any one has ever get work the "HP Wireless Printing Upgrade Kit" on Ubuntu (Feisty) ?

I've just bought this kit with a new HP Photosmart 2575, and hoped that it will work through WIFI... but actually only work on WindowsXP ! :(

More information:
the device is named SDCAB-0603 (regulatory model)

---

### Post by McGivrer on 2007-08-06
up ?

---

### Post by Merlum on 2007-08-19
Hello,
I have the same device.
Here are some details:
- there is a WIFI dongle to put on the USB connector of the printer.
- there is a WIFI USB key to put on the computer.
This should replace the standard USB cable by a network connection ; I have no Windows so I could not see how this device works.

The lsusb -vvv of the USB key:

Bus 1 Device 4: ID 03f0:ca02 Hewlett-Packard 
Bus 1 Device 4: ID 03f0:ca02 Hewlett-Packard 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x03f0 Hewlett-Packard
  idProduct          0xca02 
  bcdDevice            1.00
  iManufacturer           1 Manufacturer_Realtek_RTL8187_
  iProduct                2 Wireless Adapter
  iSerial                 [snip]
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           39
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          4 Wireless Network Card
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           3
      bInterfaceClass         0 (Defined at Interface level)
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              5 Bulk-IN,Bulk-OUT,Bulk-OUT
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
        bEndpointAddress     0x02  EP 2 OUT
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

I think this is a new network device (notice the Realtek_RTL8187 string)
Hope this helps...
Regards

---

### Post by Merlum on 2007-08-19
OK, this *is* a RTL8187 device.
I made it work in Ad-Hoc mode with another USB key, just by adding the right USB entry in the r8187 driver sources.
Here is the patch for r8187_core.c located in the original driver sources.
I just sent this patch to the r8187 driver author.

Regards,
Thierry

--- r8187_core.c.orig	2007-08-19 22:25:41.000000000 +0200
+++ r8187_core.c	2007-08-19 18:16:24.000000000 +0200
@@ -86,11 +86,15 @@
 #ifndef USB_VENDOR_ID_NETGEAR

 #define USB_VENDOR_ID_NETGEAR		0x0846

 #endif

+#ifndef USB_VENDOR_ID_HP

+#define USB_VENDOR_ID_HP		0x03f0

+#endif

 

 static struct usb_device_id rtl8187_usb_id_tbl[] = {

 	{USB_DEVICE(USB_VENDOR_ID_REALTEK, 0x8187)},

 	{USB_DEVICE(USB_VENDOR_ID_NETGEAR, 0x6100)},

 	{USB_DEVICE(USB_VENDOR_ID_NETGEAR, 0x6a00)},

+	{USB_DEVICE(USB_VENDOR_ID_HP, 0xca02)},

 

 	{}

 };

---

### Post by fishter on 2007-11-06
The wireless dongle that goes in your PC or laptop is simply a wireless dongle.  It's needed during setup and if you don't already have a wireless network.  If you have an existing wireless network then the upgrade kit can use that.

The important part is the software that you have to install on your PC to enable the HP printer driver to send the information wirelessly to the printer.

So far as I can tell the part that plugs into the printer sits on the network (it takes an IP address via DHCP, or static), and listens on ports 34447 and 34448.  However, these aren't standard ports associated with printing.  For instance ports 631 and 9100 are fairly common for CUPS and for IPP.

If any Ubuntu developers (or anyone else) wants to help figure out how we can get these devices working in Ubuntu, then please let us know, and we can give you the output of any commands you tell us to run.  (I don't have the experience or knowledge to be of any more help).

---

