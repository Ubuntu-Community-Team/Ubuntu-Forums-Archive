---
title: "Lost Wireless after Update with Feisty"
date: 2007-09-08
forum: Networking &amp; Wireless
---

### Post by dacky on 2007-09-08
After updating Feisty after a fresh install I lose wireless, the system does not even see the hardware.   This has happened 3 times now.  After reading some on the internet, it seems to be a problem with updating the kernel to -16 from -15.  It seems this new kernel has issues.  The card is Netgear which works great with live cd and fresh install.  I have seen no clear answers in any forums or bugs list or anything.  Can anyone give me any clear guidelines besides not updating the system?  The update also seems to kill my nvidia restricted drive detection.

---

### Post by kevdog on 2007-09-08
You had kernel modules loaded in the old kernel, but when you upgraded kernels, the modules need to be reinserted into the new kernel.  This means that you need to reinstall the drivers or download the drivers into the new kernel.  How did you install the wirless drivers originally??

---

