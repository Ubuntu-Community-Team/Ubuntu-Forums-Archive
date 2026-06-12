---
title: "Time Capsule Driving Me Nuts"
date: 2008-06-28
forum: Networking &amp; Wireless
---

### Post by Tlon on 2008-06-28
I've got an ubuntu 8.04 box hooked directly up to an Apple Time Capsule, running kde services.  I've tried pretty much everything to get the disk to mount, but kept getting the samba "error 13: access denied" error.  So I haven't gotten the space to mount.

At one point, I came across instructions for browsing the space through KDE / Konqueror.  I type smb://MACHINENAME/sharename into the address bar and, sure enough, it browses right to it.  I thought it must have been something that I did in the interim that gave me the access privileges (because both the device and its disk are separately pw protected), but, after a reboot, the device is still browseable -- but only from Konqueror.  My fstab edit didn't result in the automount that I'd hoped, and I still get that irritating error.

Can anyone shed some light on this?

---

