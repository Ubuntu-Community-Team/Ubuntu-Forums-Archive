---
title: "Vanilla Kernel and Wireless"
date: 2007-11-11
forum: Networking &amp; Wireless
---

### Post by middleware on 2007-11-11
Apart from usual things I am doing on all PCs (music, surf net, etc), I mainly use Ubuntu for kernel hacking. So I usually use vanilla kernel (kernel downloaded from kernel.org) rahter the one shipped by default.

The vanilla kernel works very well in all aspects but wireless. Regardless what 802.11/wireless compile settings I choose, Ubuntu wireless settings always disappears when booting with the vanilla kernel.

Is there any critical code for wireless not included in the mainstream code base? Or I missed anything in the complie settings?

---

### Post by kevdog on 2007-11-11
There are some wireless drivers you can build into the kernel

See the following:
[http://ubuntuforums.org/attachment.php?attachmentid=43599&d=1189921495](http://ubuntuforums.org/attachment.php?attachmentid=43599&d=1189921495)

However ubuntu has put some builtin kernel modules into their kernel -- ra, madwifi, etc.  If you need these modules they need to be compiled and inserted into the kernel as custom kernel modules.

Again I compiled a custom kernel a long time ago in Feisty and was able to get the wireless working (broadcom/ndiswrapper) however it took me a few tries since there are so many options in the configuration.

---

