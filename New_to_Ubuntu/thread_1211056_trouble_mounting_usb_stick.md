---
title: "trouble mounting usb stick"
date: 2009-07-12
forum: New to Ubuntu
---

### Post by Jgpeder on 2009-07-12
Hi,
I've been trying to mount my old 128 mb creative Muvo mp3 player/usb stick.
Problem is that the device doesn't appear when I write "sudo fdisk -l".
Any ideas?

My new usb stick automounts and appears as /dev/sdb1.

-Jesper

---

### Post by GCoffee on 2009-07-12
Right click on panel, click add to panel, then search disk mounter, add that.

---

### Post by Jgpeder on 2009-07-13
> **GCoffee said:**
> Right click on panel, click add to panel, then search disk mounter, add that.

Thanks, but nothing happens! Other ideas?

---

### Post by rockerphil on 2009-07-13
the first thing that pops to mind is to run this command to see if it's even being detected by the system

```
lsusb
```

that will list all USB devices connected to the machine. secondly, what is the format of the partition on the USB stick? and also could you post te output of ```
sudo fdisk -l
```

---

### Post by bodhi.zazen on 2009-07-13
Sounds as if you either do not have the drivers (which would be odd) or have a bad disk.

Is you device listed here ?

[http://www.qbik.ch/usb/devices/search_res.php?pattern=Muvo](http://www.qbik.ch/usb/devices/search_res.php?pattern=Muvo)

---

