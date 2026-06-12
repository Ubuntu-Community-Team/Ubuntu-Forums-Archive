---
title: "KINGSTON safely remove"
date: 2010-10-13
forum: New to Ubuntu
---

### Post by Lian Radu on 2010-10-13
It works to Eject it, but not Safely remove. I get this error message:
Error detaching: helper exited with exit code 1: Detaching device /dev/sdb
USB device: /sys/devices/pci0000:00/0000:00:1d.7/usb2/2-3)
SYNCHRONIZE CACHE: synchronize cache(10):  Fixed format, current;  Sense key: Key=9
 Additional sense: Logical unit not ready, cause not reportable
  Info fld=0x0 [0] 
FAILED: No such file or directory
(Continuing despite SYNCHRONIZE CACHE failure.)
STOP UNIT: start stop unit: transport: Host_status=0x07 [DID_ERROR]
Driver_status=0x00 [DRIVER_OK, SUGGEST_OK]

FAILED: No such file or directory

I have no similar problems with other flash drives.
Is this a manufacturing problem or can be fixed?

---

### Post by philinux on 2010-10-13
Eject unmounts it but leaves the power on. Safely remove unmounts and turns power off.

It is safe to unplug as long as it is unmounted.

---

