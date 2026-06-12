---
title: "Broadband Connection"
date: 2009-10-05
forum: New to Ubuntu
---

### Post by topdog2009 on 2009-10-05
I am trying to connect to broadband using Bell Mobility USB stick in Canada. Bell tell me that they support windows only.

Any idea how I can use this stick within Ubuntu?

I have occasionally got on line but I do not how - it does not seem to be a regular occurrence <vbg>

Thanks

Brian

---

### Post by StuartN on 2009-10-05
> **topdog2009 said:**
> Any idea how I can use this stick within Ubuntu?

Type **lsusb** in a terminal and it will give you vendor:device information, from which you might get more help.

---

### Post by topdog2009 on 2009-10-06
The information provided by lsusb apart from telling me the hub and usb being used only gave the name of the manufacturer of the USB.

Brian

---

### Post by StuartN on 2009-10-06
> **topdog2009 said:**
> The information provided by lsusb apart from telling me the hub and usb being used only gave the name of the manufacturer of the USB.

The output from lsusb, for example *Bus 001 Device 008: ID 0d7d:1600 Phison Electronics Corp.*, gives a vendor and device id in the form 0d7d:1600 that usefully identifies the internal electronics.

---

### Post by topdog2009 on 2009-10-08
I started this on a different thread and then lost it. I use Bell Mobility USB stick to get access to High Speed. I cannot guarantee getting online. Ubuntu does not always connect.
Any idea? I am from Canada

lsusb provides this information Bus 006 Device 002: ID 1410:4100 Novatel Wireless U727

Brian

---

### Post by cariboo on 2009-10-08
I've merged your two threads. When looking for your posts click on Search at the top of the page and select Find All Your Posts.

---

### Post by ibuclaw on 2009-10-08
If it sometimes fails, try reloading the module:
```

sudo rmmod usbserial
sudo modprobe usbserial vendor=0x1410 product=0x4100

```
If not, disengage the internal storage
```
sudo eject /dev/cdrom1
```

Then try to access the net.

Regards
Iain

---

