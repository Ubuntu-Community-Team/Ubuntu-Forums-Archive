---
title: "Univeral Wireless Dell Drivers"
date: 2007-05-13
forum: Networking &amp; Wireless
---

### Post by wetbo529 on 2007-05-13
Hey does anyone know where I can find wireless dell drivers for my card. Im new to this ubuntu thing and I dont even know how to find out what card I have inside. any help?

---

### Post by spd106 on 2007-05-14
If you open System > Admin > Device Manager and look through the PCI section you should find the wireless device listed. If it says it's a Dell Truemobile then you have a Broadcom card. This means you will have to install either ndiswrapper or the bcm43xx-fwcutter packages.

There are multiple guides to doing this in the forum and wiki help docs.

To extract the windows driver use the cabextract utility on the Dell .exe file or if you still have a windows partition you can search for the drivers, they will be something like bcmwl5.inf and bcmwl5.sys.

---

