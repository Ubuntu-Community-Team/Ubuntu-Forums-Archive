---
title: "No Life in my USB Wireless Adapter"
date: 2008-01-14
forum: Networking &amp; Wireless
---

### Post by Daz902 on 2008-01-14
Hi there,

I went through most of the posts on here but my issues doesn't seem to be falling into any of the categories. I successfully installed the driver for my Belkin Wireless G USB network adapter running on my laptop using ndiswrapper. The trouble is that it doesn't seem to recognize that it's there. It has the driver but doesn't make the connection between the hardware and wlan0. It's as though plugging it in doesn't actually activate the driver. 

ndiswrapper -l 
blkwgu : driver installed

Note - previous to this I tried both rt2500 and rt73 drivers with the same results.

When I plug the device in, I get the following in syslog. 

Jan 14 22:24:43 NetworkManager: <debug> [1200363883.888According to syslog:107] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_11_50_bb_58_77'). 
Jan 14 22:24:43 NetworkManager: <debug> [1200363883.917454] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_11_50_bb_58_77_0'). 
Jan 14 22:24:44 NetworkManager: <debug> [1200363884.742898] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_50d_705a_noserial_usbraw'). 

Any ideas?

Thanks

---

### Post by PhaderSYD on 2008-01-18
i had the same problem with my buffalo 125g usb wlan.

it was working for months and then suddenly no response when i plugged it in so i went to argos bought a new one, it worked fine so i put the old one in the box and took it back

---

