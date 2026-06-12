---
title: "Lucid - fails to boot after upgrade normally and in recovery mode"
date: 2010-05-02
forum: New to Ubuntu
---

### Post by Peter09 on 2010-05-02
For information as a follow on from this thread

[http://ubuntuforums.org/showthread.php?t=1469481](http://ubuntuforums.org/showthread.php?t=1469481)

First thanks to cisco311 for the help provided.

Finally discovered that the cause of a failure to complete startup in Recovery mode and normally was the inclusion of virtualbox usb support.

This line is fstab

> none /proc/bus/usb usbfs devgid=125,devmode=664 0 0

stopped the boot process.

Solution - see the other thread.

---

