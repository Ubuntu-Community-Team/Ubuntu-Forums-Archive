---
title: "Wireless USB...soooo close but no dice."
date: 2005-08-11
forum: Networking &amp; Wireless
---

### Post by tikirob on 2005-08-11
I am really new to Linux and so far everything is fine with the exception of my WLAN. I have a USB WLAN adapter (Linksys WSUB54G).  I have the NDISWRAPPER installed and went through the steps.  It tells me the hardware and driver are OK but then I get this error:

sudo modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.10-5-686/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation not permitted

Thanks for the help.

---

### Post by luc1972 on 2005-08-25
I am having the same trouble but with a different wireless card.  It seems to be with the ndiswrapper modules wanting to find the kernel source.  I am going to try un-installing and re-installing ndiswrapper and see what that does.

---

