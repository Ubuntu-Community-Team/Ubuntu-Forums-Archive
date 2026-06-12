---
title: "Trying to Compile Driver for Huawei ME906V"
date: 2013-12-09
forum: Networking &amp; Wireless
---

### Post by todd4 on 2013-12-09
Ubuntu 12.04 
I'm trying to compile drivers for 
Huawei ME906V

I'm following the directions
Link to Kernel Driver integration
[http://consumer.huawei.com/en/solutions/m2m-solutions/products/support/application-guides/detail/me906v-en.htm?id=17942](http://consumer.huawei.com/en/solutions/m2m-solutions/products/support/application-guides/detail/me906v-en.htm?id=17942)


The kernel compiles perfectly after the updates. 
After install the Huawei device should have 4 usb serial devices. 
/dev/ttyUSB0
/dev/ttyUSB1
/dev/ttyUSB2
/dev/ttyUSB3
non of these show up. 

lsusb returns the following
lsusb 
Bus 001 Device 002: ID 12d1:1573  Huawei Technologies Co. , Ltd.

It appears the the directions are generic and are not specific to the Huawei ME906V
I can't find device ID  1573 anywhere in the documentation. 


So I tried to add   
{ HW_USB_DEVICE_AND_INTERFACE_INFO(HUAWEI_VENDOR_ID, 0xff, 0x15, 0x73) },
to
static const struct usb_device_id option_ids[ ] id 
THEN  recompile the kernel.  Same results.

---

### Post by arunaprem.bianzino on 2013-12-11
I think I have a similar problem.

I installed a Huawei EM820W module to give 3G connectivity to a VBOX-3200 machine. The machine is running Ubuntu.

The module is seen as an USB controller:

```
$ sudo lsusb 
Bus 003 Device 003: ID 12d1:1404 Huawei Technologies Co., Ltd. 

```
As this is the only Huawei device appearing in the list, so I guess it is the EM820W module

There is no trace of the device among the network interfaces (e.g., as result of the ifconfig -a command, I only see *eth0* and *lo* as interfaces)

I guess I am missing the proper drivers in order to correctly see it as a network interface (I had a similar problem with a wifi interface - broadcom BCM94321MC - previously, and it was solved by changing the used drivers), but I could not find any unix driver for the device (neither on the Huawei web page)

---

### Post by ut0ugh1 on 2014-04-04
you were wrong as the declaration 
```
#define HW_USB_DEVICE_AND_INTERFACE_INFO(vend, cl, sc, pr) \
    .match_flags = USB_DEVICE_ID_MATCH_INT_INFO \
        | USB_DEVICE_ID_MATCH_VENDOR, \
    .idVendor = (vend), \
    .bInterfaceClass = (cl), \
    .bInterfaceSubClass = (sc), \
    .bInterfaceProtocol = (pr)
```
what the hex format does not identify the vid&pid but class interface subclass interface protocol

---

