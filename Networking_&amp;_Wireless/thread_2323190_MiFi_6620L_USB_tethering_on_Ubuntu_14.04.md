---
title: "MiFi 6620L USB tethering on Ubuntu 14.04"
date: 2016-05-03
forum: Networking &amp; Wireless
---

### Post by Andrew_Bainbridge on 2016-05-03
I have a MiFi 6620L device that I want to connect via USB to my Ubuntu machine. If I plug the device into a Windows box, it enumerates as an Ethernet controller. Therefore I hoped some standard Linux USB-ethernet driver would just work when I plugged it in. It didn't. I'm new to this kind of thing in Linux, so I don't know how to debug the problem.

If I run lsusb, it reports my device like this:
  Bus 002 Device 003: ID 1410:b00d Novatel Wireless

If I run ifconfig, I don't see an adapter for this device (but I do see my machine's on-board Ethernet adapter appear as eth0).

Is there any chance that the dm9601 driver would work for this device? Do I somehow need to tell the USB stack to associate that driver with my device's VID and PID? Or should I do something else altogether?

Thanks.

---

### Post by Andrew_Bainbridge on 2016-05-04
I learned a bit more about my device and Ethernet over USB in general (partly from [https://en.wikipedia.org/wiki/Ethernet_over_USB](https://en.wikipedia.org/wiki/Ethernet_over_USB)). Running usbtree on Windows I can see that the device has USB interfaces for both CDC ECM and CDC ACM. Running lsusb -t on Linux seems to agree.

$ lsusb -t

/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=ehci-pci/6p, 480M
    |__ Port 2: Dev 2, If 0, Class=Mass Storage, Driver=usb-storage, 480M
    |__ Port 5: Dev 7, If 12, Class=Communications, Driver=cdc_acm, 480M
    |__ Port 5: Dev 7, If 13, Class=CDC Data, Driver=cdc_acm, 480M
    |__ Port 5: Dev 7, If 14, Class=Human Interface Device, Driver=usbhid, 480M
    |__ Port 5: Dev 7, If 0, Class=Vendor Specific Class, Driver=, 480M
    |__ Port 5: Dev 7, If 1, Class=Vendor Specific Class, Driver=, 480M
    |__ Port 5: Dev 7, If 3, Class=Vendor Specific Class, Driver=, 480M
    |__ Port 5: Dev 7, If 4, Class=Communications, Driver=cdc_ether, 480M
    |__ Port 5: Dev 7, If 5, Class=CDC Data, Driver=cdc_ether, 480M

The fact that cdc_ether and cdc_acm are loaded looks promising. As a result of the ACM driver being loaded, I can see /dev/ttyACM0. I guess I can use PPP to connect to that somehow. However, that seems like a bad option.

My guess is that the cdc_ether driver is talking to the CDC ECM interfaces on my device and as a result, I ought to have a "usb0" adapter shown in ifconfig. Does that sound right?

---

### Post by Andrew_Bainbridge on 2016-05-05
So I did this:[FONT=courier new]

$ dmesg | grep cdc_ether
[   18.200216] cdc_ether 2-5:1.4 eth1: register 'cdc_ether' at usb-0000:00:1d.7-5, CDC Ethernet Device, 00:15:ff:80:52:90
[   18.200255] usbcore: registered new interface driver cdc_ether
[   18.203624] cdc_ether 2-5:1.4 eth4: renamed from eth1
[  972.738278] cdc_ether 2-5:1.4 eth4: unregister 'cdc_ether' usb-0000:00:1d.7-5, CDC Ethernet Device
[ 1146.310827] cdc_ether 2-5:1.4 eth1: register 'cdc_ether' at usb-0000:00:1d.7-5, CDC Ethernet Device, 00:15:ff:80:52:90
[ 1146.378903] cdc_ether 2-5:1.4 eth4: renamed from eth1
[ 1176.275853] cdc_ether 2-5:1.4 eth4: kevent 12 may have been dropped

[/FONT]The presence of 'eth4' in there surprised me. I was expecting 'usb0'. So I added the following to my /etc/network/interfaces

[FONT=courier new]auto eth4
iface eth4 inet dhcp

[/FONT]And then ran '[FONT=courier new]sudo ifup eth4[/FONT]'. Then '[FONT=courier new]ifconfig[/FONT]' listed an eth4 adapter!!! With the right MAC address!!!

[FONT=courier new]eth4      Link encap:Ethernet  HWaddr 00:15:ff:80:52:90  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
<snip>

[/FONT]So, it now works. Things I'm still confused about are:

1. How does my kernel know to load the cdc_ether driver for my device, despite the fact that its VID and PID (1410:b00d) are not listed on [http://www.linux-usb.org/usb.ids](http://www.linux-usb.org/usb.ids) or anywhere else I can find.

2. How was I supposed to know that eth4 was the adapter name? Grep'ing dmesg output seems like a hack. Is there someway to get ifconfig to list unconfigured adapters, or something?[FONT=courier new]
[/FONT]

---

