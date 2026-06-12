---
title: "Modprobe"
date: 2007-02-12
forum: Networking &amp; Wireless
---

### Post by moitio on 2007-02-12
I installed Ubuntu 6.06 and installed ndiswrapper off the CD. After upgrading to Edgy and trying to use ndiswrapper-common and ndiswrapper-utils, and trying to install the drivers as normal, when I did "sudo modprobe ndiswrapper" it came back "FATAL: Module ndiswrapper not found."

I had a search through and found that there was no ndiswrapper.ko in my kernal directory anywhere. I presume that ndiswrapper-common should be installing this file?

Thanks, Tom

---

### Post by spd106 on 2007-02-12
Not really, the ndiswrapper module is included with the linux-image-`uname -r` package and it should appear in the /lib/modules/`uname -r`/kernel/drivers/net/ndiswrapper directory.

The ndiswrapper-common and ndis-utils packages contain the userspace tools needed to install the driver firmware.

I suggest that you make sure that you have the latest versions of the linux-image and ndiswrapper-utils-v1.8 packages.

---

