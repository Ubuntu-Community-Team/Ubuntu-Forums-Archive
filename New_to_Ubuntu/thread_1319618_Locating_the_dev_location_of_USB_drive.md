---
title: "Locating the /dev/ location of USB drive?"
date: 2009-11-08
forum: New to Ubuntu
---

### Post by six30two on 2009-11-08
Trying to install a boot USB for a memory test. The Readme says this:

3) As root type: dd if=memtest86-3.5.usb of=dev where dev is the device
the key is assigned to. Use the base device (ie. /dev/sdc) not a partition
designation (ie. /dev/sdc1).

How do I determine the key the USB drive is assigned to? I tried lsusb, but it's not giving me anything like /dev/sdc. It shows me some USB devices - a couple of root hubs and then the drive I'm trying to use, and says something about it being assigned to 002, so would I type /dev/sdc2? sdc002? I'm not sure.

---

### Post by LewRockwell on 2009-11-08
```
sudo fdisk -l
```that is a dash lower-case "L"...NOT a "one"

.

---

### Post by six30two on 2009-11-08
Thank you.

---

