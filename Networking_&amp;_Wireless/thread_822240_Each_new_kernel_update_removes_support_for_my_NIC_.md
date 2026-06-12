---
title: "Each new kernel update removes support for my NIC card."
date: 2008-06-08
forum: Networking &amp; Wireless
---

### Post by alguin2 on 2008-06-08
When I originally installed Ubuntu 8.04 (Hardy Heron, kernel 2.6.24-16-generic), I realized that I had no internet connection because my NIC card (RealTek  RTL8168C/RTL8111C Gigabit NIC) was not supported.

Searching through Ubuntu Forums, I came upon the solution, (**[COLOR="Blue"][http://ubuntuforums.org/showthread.php?t=799662&page=2](http://ubuntuforums.org/showthread.php?t=799662&page=2)[/COLOR]**) , which required downloading the latest driver from RealTek, compiling it, and installing. After a quick reboot, network support came up without a problem.

When I upgraded to 2.6.24-17, network support again disappeared, and I had to re-compile/install the r8168 driver in order to get the network up for the new kernel version. 

My questions as I face an update to 2.6.24-18:
1. How can I verify if the new r8168 driver is included in the next release of the kernel (2.6.24-18-generic)?
2. Is there a quick way of installing the driver?  (ie. can I simply copy the r8168.s=ko file to **/lib/modules/KernelVers/kernel/drivers/net/** )?
3. Will the new r8168 driver ever be included in a future kernel release? If so, how do I find out when it's planned for release. 

Thanks

---

### Post by avtolle on 2008-06-08
You're also facing an update to 2.6.24-19 generic as well, which will also require you, I believe, to compile the driver again. To verify whether the driver is in -18 or -19, I don't know any other way but to upgrade to the new kernel and see (although there may be something around elsewhere that would tell you).

EDIT: [http://ubuntuforums.org/showthread.php?t=817407](http://ubuntuforums.org/showthread.php?t=817407) is the announcement concerning the upgrade to the -18 kernel, and clearly specifies that recompilation of third party drivers will be required.

---

### Post by alguin2 on 2008-06-15
Thanks for the reply.  I have too many projects that I've started and so I can (for now) forego the latest kernel upgrades.

---

### Post by Sheroth on 2008-06-20
Just thought I would add for all those searching for solutions that the new kernel updates also affect Ubuntu 7.10 in the same way as Ubuntu 8.04.  The same fix works for Gutsy as for Hardy.

---

