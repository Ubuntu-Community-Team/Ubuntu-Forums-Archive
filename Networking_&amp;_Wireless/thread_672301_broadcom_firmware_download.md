---
title: "broadcom firmware download"
date: 2008-01-19
forum: Networking &amp; Wireless
---

### Post by kazbear on 2008-01-19
Is there a place I can download the broadcom firmware so I can transfer it to another box for installation with the restricted driver manager?

---

### Post by kazbear on 2008-01-20
Found a debian package and installed that.  Wireless works now.

---

### Post by spd106 on 2008-01-20
Could you please provide a link to the package you used so that we can all benefit from your solution?

If you want a user friendly guide to configuring Broadcom wireless cards see this help docs page
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy)

---

### Post by rosegarden78 on 2008-01-20
There are only a few sources - original, repositories and mirrors.  I had to download like three different bcm43xx.deb packages before finding a good one.  But I think it's built into Gutsy and the repos if you can get online with Ethernet.  After you install the package just load the module with Terminal:

sudo modprobe bcm43xx

That should do it.  Don't forget to check network-manager and network settings.

---

