---
title: "USB Mouse doesn't work after reboot"
date: 2009-05-25
forum: New to Ubuntu
---

### Post by albertjvm on 2009-05-25
This is not an urgent problem by any means. After upgrading to Jaunty, my usb mouse does not work after reboot, If i unplug it and replug it, it works fine. I'm just wondering if any one has a solution to this, or even a way to automate the re-enabling of a usb port.

---

### Post by fatality_uk on 2009-05-28
Can you enter the following command into a terminal and post the results here.

```
lsusb
```

---

### Post by xavierp94 on 2009-05-28
> **albertjvm said:**
> This is not an urgent problem by any means. After upgrading to Jaunty, my usb mouse does not work after reboot, If i unplug it and replug it, it works fine. I'm just wondering if any one has a solution to this, or even a way to automate the re-enabling of a usb port.
Is it a usb wireless mouse? If that's it, then its normal.

---

### Post by albertjvm on 2009-05-29
No, it's not wireless.

results of lsusb are:
~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 046d:c045 Logitech, Inc. Optical Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 043d:0093 Lexmark International, Inc. X5250
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

