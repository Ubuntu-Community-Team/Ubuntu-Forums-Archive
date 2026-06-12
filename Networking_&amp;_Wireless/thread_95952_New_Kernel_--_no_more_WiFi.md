---
title: "New Kernel -- no more WiFi"
date: 2005-11-27
forum: Networking &amp; Wireless
---

### Post by diamond on 2005-11-27
I just upgraded my kernel from 2.6.12.9 to 2.6.13. I used the Synaptic package manager to install the kernel image, the source and the headers, and I was able to successfully boot into the new kernel. Everything seems fine, except that it no longer sees wlan0. I am running Ubuntu 5.10 on a Dell Inspiron 600m with the WLAN 1350 WiFi card. I tried going through the steps to re-install ndiswrapper and the bcmwl5 driver under the new kernel, but it just told me that they are already installed. I checked my /etc/network/interfaces file, and it shows the correct entry for wlan0. But the OS just doesn't see the device. It still works fine when I boot under the previous kernel.

What am I missing?

---

### Post by spd106 on 2005-11-28
The ndiswrapper module is kernel specific. So you will have to compile it against the new kernel sources. Then reinstall the driver. 

If you want to use to different kernels i'm not sure what you need to do. Probably symlink to two different versions of ndiswrapper.

Have a look on the ndiswrapper website.

---

### Post by esmail on 2005-11-29
hi,

i had a similar problem, turns out i didn't install the required restricted modules,
so you might want to check that.


i'm still a bit confused on the kernel numbering (eg 2.6.12-10 vs 1.6.12.16) etc.
or this:

linux-image-2.6.12-10-686 (2.6.12-10.24)

This is what I have most currently installed and it works well on my TP23 with
wirless card (netgear wg511):

linux-686 (2.6.12.16.1)
linux-image-686 (2.6.12.16.1)
linux-restricted-modules-686 (2.6.12.16.1)

(again, I'm not sure what the difference is between the first one and
the others, maybe just a catch-all for all the required packages just
like gcc or g++ will refer to the most current versions).

Esmail

---

