---
title: "New Kernel Update, Wireless Down..."
date: 2008-10-15
forum: Networking &amp; Wireless
---

### Post by Daghita on 2008-10-15
I have a Toshiba Satellite P15-S420 using Atheros drivers and after the kernel update it stopped working. Wireless was down, although I still had wired access.

Tried ifconfig to see if wifi0 was even detected, and nothing. I looked for restricted drivers to be listed, and nothing. I then when into the Synaptic Package Manager and looked up "nvidia."

I scrolled through looking for the restricted packages. It showed "linux-restricted-modules-2.6.24-19-generic" and "linux-restricted-modules-2.6.24-19-rt" being used. I then noticed the updated version of "-21" listed but not used.

I selected the generic and rt -21 version to be listed and *POOF* magic happened. So, hopefully this might help someone out in the near future...

---

