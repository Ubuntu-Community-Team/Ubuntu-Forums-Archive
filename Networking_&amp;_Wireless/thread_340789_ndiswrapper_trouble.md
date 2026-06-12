---
title: "ndiswrapper trouble"
date: 2007-01-17
forum: Networking &amp; Wireless
---

### Post by chipdip on 2007-01-17
Ok, I had an old Belkin USB network adapter in my closet, so I decided to try to get it working in Ubuntu. I installed ndiswrapper and ndisgtk, and ran ndisgtk to set up the driver. I selected the correct driver, but when I try to install it, I get:
> FATAL: Error inserting ndiswrapper (/lib/modules/2.6.17-10-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument
Any ideas?

---

### Post by phossal on 2007-01-18
Have you tried installing the driver from the command line? And, is the driver an .inf file?

---

### Post by chipdip on 2007-01-19
Yep, tried "ndiswrapper -i rf72.inf" (I think thats the driver name in the directory.

---

