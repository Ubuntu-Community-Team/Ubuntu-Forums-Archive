---
title: "udev rules for usb touch screen"
date: 2011-06-01
forum: New to Ubuntu
---

### Post by goblet05 on 2011-06-01
Hi,
I am new to Ubuntu (and to Linux). I posted this in the forum 'Hardware & Laptops' yesterday but now realize that was the wrong place.
I am trying to write a user mode driver for a touch sensor. I have written a Windows driver for it and am now trying it in Ubuntu 10.10. I need to be able to write to the sensor, but not as root since this would be too dangerous for my users.

My problem is that I cannot persist changing the access permissions for 'other' users. I can do it with chmod but this doesn't persist. I have read Daniel Drakes excellent 'Writing udev Rules' but without success. I have put my rule in /etc/udev/rules.d/95-local.rules

My rule is SUBSYSTEM=="usb", ATTR{idVendor}=="14c8", ATTR{idProduct}=="0004", MODE="0666"
I also tried adding a colon MODE:="0666"

restart udev returns a process number so I guess it works but ls -l gives me crx-rx-r-- root root.........
The sensor can be found in /dev/bus/usb/002 and I have used udevadm info to get the attributes of the sensor (I already knew idVendor and idProduct. All web help forums where people had success with this problem were using usb flash drives. Would there be a difference for a USB touch sensor? Using chmod I can read and write data to/from the sensor.

any help is greatly appreciated. If this is the wrong forum could someone please point me in the right direction.

Goblet05

---

