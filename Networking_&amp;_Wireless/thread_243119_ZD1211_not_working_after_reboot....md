---
title: "ZD1211 not working after reboot..."
date: 2006-08-24
forum: Networking &amp; Wireless
---

### Post by JeBeKe on 2006-08-24
My ZD1211 is perfectly working on Dapper.
I only have to unplug and plug it.
After a reboot, the device is not detected, not even visible with "lsusb".
If I then unplug it, and plug it in again, then everything is ok.

What have I forgotten?

---

### Post by SimonJW on 2006-08-24
After the reboot, when the card isn't working, try running
```
sudo modprobe zd1211
```
and see if that brings up the card

---

### Post by az on 2006-08-24
> **JeBeKe said:**
> My ZD1211 is perfectly working on Dapper.


Is there a bug report about this?  It sounds like a udev problem.

It should not do that - it is not your fault.

If there is a bug report about it, please add to it, if you can.  Or at least subscribe to it and see if an eventual fix works for you or not (let them know if it does not).

---

