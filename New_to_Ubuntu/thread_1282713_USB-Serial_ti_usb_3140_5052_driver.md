---
title: "USB-Serial ti_usb_3140_5052 driver"
date: 2009-10-04
forum: New to Ubuntu
---

### Post by nkumar3119 on 2009-10-04
I am trying to establish communication with a usb-serial device TUSB3410 with vender id 1abd and product 0040. in Ubuntu8.10 distro. When I do "sudo modprobe usbserial vendor=0x1abd product=0x0040" and dmesg, I see it launches generic driver and attaches to /dev/ttyUSB0, however I can't read or write to the device. So I tried, "sudo modprobe ti_usb_3410_5052 vendor_3410=0x1ab5 product_3140=0x0040", it launches driver but no /dev/ttyUSB0! 

I read some entries in forum and tried ti_usb_3410.rules file in /etc/udev/rules.d/ but still no change (bConfigurationValue never get changed to 2!).

Any ideas? Suggestion ?
-nkumar3119

---

