---
title: "No Network Connections, No Bluetooth, Rebooted to Previous Kernel"
date: 2017-05-06
forum: Networking &amp; Wireless
---

### Post by Jorge_Kappa on 2017-05-06
I suspect there was a power outage during an update. No network connections, wifi or wired, no bluetooth, a little research says problems with drivers. I booted to previous kernel, everything back to tip top normal. The question is, now what? Just wait till the next kernel update happens and everything will be beautiful again?

---

### Post by howefield on 2017-05-06
Thread moved to the "*Networking & Wireless*" for a better fit.

---

### Post by ajgreeny on 2017-05-06
When was this update, and which Ubuntu version are you using as there was a problem about 3 days ago where kernel 4.4.0-77 was installed in Ubuntu 16.04 without the linux-image-4.4.0-77-extra and the linux-header packages needed for some drivers and kernel modules to be installed.

If this is your situation boot to the older kernel again (4.4.0-75?) and run the update again; those missing packages should be installed this time.

---

