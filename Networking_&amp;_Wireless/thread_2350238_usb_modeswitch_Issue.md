---
title: "usb_modeswitch Issue"
date: 2017-01-22
forum: Networking &amp; Wireless
---

### Post by mavik30 on 2017-01-22
Hello All,

We are using MiFi 4G LTE Global USB Modem U620L, Ubuntu 16.04 recompiled the kernel with product and vendor id.

It worked on 15.04 with out any problem, but with ubuntu 16.04, below is the outcome.


> sudo usb_modeswitch &#8211;v 0x1410 &#8211;p 0x9020 &#8211;u 2
Looking for default devices ...
No devices in default mode found. nothing to do.

Changed with 1 2 3 4 and displayed same message
lsusb> 
bus 003 device 005: ID 1410:9022 Novatel Wireles

> 
ls &#8211;l /dev/ttyUSB*
crw-rw---- 1 root dialout 188, 0 Feb 11 16:35 /dev/ttyUSB0


Tried with some tweaks still not working. 

How to solve this.

Thank You,
Answers Appreciated.

---

### Post by jeremy31 on 2017-01-22
Remove the USB device, open the file manager, insert the device and see if a new device appears on the left side of the window, you could also do ```
dmesg | tail -20
``` 20 seconds after inserting the device.

You might just need to eject whatever new is detected in order to use it as a modem

---

### Post by mavik30 on 2017-01-24
Thanks, for replay.
dmesg | tail -20 (attach)

---

### Post by jeremy31 on 2017-01-25
Are you using a USB hub with a few devices connected?

---

### Post by mavik30 on 2017-01-25
Yes, for USB keyboard and mouse.

Just now checked, (attach)
```
sudo usb_modeswitch –v 0x1410 –p 0x9020 –u 2
```

Still not connecting.

---

### Post by mavik30 on 2017-01-27
Any suggestions to work on Ubuntu 16.04.

---

### Post by jeremy31 on 2017-01-27
Does anything new show up on the left side of the file manager when the device is plugged in?  A lot of these devices have a small amount of memory that is used to hold Windows drivers and that usually needs to be ejected for the device to work

---

### Post by mavik30 on 2017-01-28
No, it show nothing on left side of the explorer. What i think is, only internet is not connecting. USB got detected and config@ to 2.

---

### Post by jeremy31 on 2017-01-28
A post [here](https://www.raspberrypi.org/forums/viewtopic.php?f=28&t=121326) indicates that making a udev rule may help
```
sudo -H gedit /etc/udev/rules.d/99-vzw_u620l.rules
```
Enter the following
```
SUBSYSTEM=="usb", ATTR{idVendor}=="1410", ATTR{idProduct}=="9020", ATTR{bConfigurationValue}=="1", ATTR{bConfigurationValue}="2"
```

Save, exit and reboot

---

