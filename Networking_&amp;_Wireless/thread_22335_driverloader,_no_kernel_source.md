---
title: "driverloader, no kernel source"
date: 2005-03-27
forum: Networking &amp; Wireless
---

### Post by pksings on 2005-03-27
I have a paid license for driverloader, which worked fine in Warty.

I only have a wireless PCI card in a rackmounted machine. No wired connection possible.

I cannot install driverloader completely, it requires true kernel source, not headers.

There is no kernel source at all available on the CDROM that I can find.

1. How can I get the source on this machine?

2. Why isn't it provided by default?


IT IS SUPPLIED, THE PACKAGE IS CALLED BUILD-ESSENTIAL ALONG WITH KERNEL-HEADERS FOR THE KERNEL, INSTALL ALL THE KERNEL HEADER PACKAGES
With Build-essential and the headers installed Driverloader install works perfectly.

---

### Post by az on 2005-03-27
1-  Ndiswrapper does not work?
2-  Look for linux-source instead of kernel-source.
3-  Good luck.

---

### Post by pksings on 2005-03-27
No, unfortunately Ndiswrapper does not work. It initializes the card but cannot talk, never sees my AP, and won't accept my ESSID.

Besides that, I have a year-plus old license for Linuxtant's driverloader to use.

---

### Post by pksings on 2005-03-27
I have searched through Synaptic for, kernel, kernel-source, source, linux, and cannot think of anything else that might find it. Surely one of those names would be attached to the kernel source?  All I have found is the headers which of course are already installed and insufficient.  

Just to be sure, I just went and searched per the previous suggestion for linux-source, no such file(s) found.

---

### Post by az on 2005-03-27
If the software cannot be built using just the linux-headers, you should get your money back.  Linux-headers (kernel-headers) exist only for making modules like this.  The only reason it is not working is because the software you bough is not properly made.

Maybe try a tarball version of the driver?

---

### Post by pksings on 2005-03-28
Regarding the software (driverloader).

I am using the driverloader tarball downloaded from Linuxant.com. It is indeed complete, and no, the headers are not sufficient to install it. They may be designed to be so, but they are not. "Build-essential" supplies whatever is missing and it now works fine.

I have now successfully installed the driver and driverloader.

The new/current issue is that in order to set the ESSID I need a piece of software called xsupplicant. And it won't ./configure. The OpenSSL implementation of Ubuntu is "incomplete or corrupt" according to my screen output.

I formatted the drives and am installing a different distro, I don't have time for this. ](*,)

---

