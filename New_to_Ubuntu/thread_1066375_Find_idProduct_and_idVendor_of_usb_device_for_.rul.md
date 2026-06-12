---
title: "Find idProduct and idVendor of usb device for .rules file"
date: 2009-02-10
forum: New to Ubuntu
---

### Post by mattgilbertnet on 2009-02-10
Hello,

I'm trying to do with this guy did (just skip to the last post):

[http://ubuntuforums.org/archive/index.php/t-784639.html](http://ubuntuforums.org/archive/index.php/t-784639.html)

That being, change the permissions in a file in /etc/udev/ to allow a non-superuser to run ops and access a cvs "disposable" camcorder over usb. I did what he did, saving a new rule file called 42-cvs-permissions.rules with these 2 lines:


SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", ATTRS{idVendor}=="0dca", ATTRS{idProduct}=="0027", MODE="0666"
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", ATTRS{idVendor}=="167b", ATTRS{idProduct}=="0101", MODE="0666"

(SUBSYSTEM=="usb_device" changed to SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device" for Hardy, and SYSFS changed to ATTRS, as per this thread: [https://bugs.launchpad.net/ubuntu/+source/udev/+bug/210421](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/210421) Let me know if I got that wrong.)

But no luck. Perhaps the vendor or product ids are off if we have different versions of the camcorder? How do I know what the vendor or product ids should be? Newbie here, so lots of details would be awesome!

---

### Post by sdennie on 2009-02-10
You would probably find this guide useful: [http://reactivated.net/writing_udev_rules.html](http://reactivated.net/writing_udev_rules.html).  The section called, "Finding suitable information from sysfs" describes how to get the information you need.

---

