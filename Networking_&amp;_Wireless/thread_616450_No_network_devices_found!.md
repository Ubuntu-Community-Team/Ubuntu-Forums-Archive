---
title: "No network devices found!?"
date: 2007-11-18
forum: Networking &amp; Wireless
---

### Post by wareagle on 2007-11-18
I just resumed my computer from hibernate this morning only to have KNetworkManager tell me "no networking devices found!"  ifconfig -a only shows my local loopback connection.  However, if I plug in my $15 USB wireless card, it works fine.

I rebooted my computer and saw the following message:```
[   59.247687] PCI: Cannot allocate resource region 0 of device 0000:01:00.0
[   59.247720] PCI: Cannot allocate resource region 2 of device 0000:01:00.0
[   59.247771] PCI: Cannot allocate resource region 0 of device 0000:02:03.0
```
And the problem still persists!

EDIT: Dmesg removed.  URL no longer exists.

KInfoCenter says there are two unrecognized devices (screenshot attached)

I think this might be because I installed a bunch of updates before I put it into hibernate.

It looks similar to [this]("http://ubuntuforums.org/showthread.php?t=570893").

---

### Post by tinycamp on 2007-11-18
what updates did u install??
new kernel?

---

### Post by wareagle on 2007-11-28
I don't believe anything was a kernel update.  A bunch of them were for samba, as well as other apps.

I also was in need of a replacement reserve (CMOS) battery so I ordered and installed a new one, thinking it would solve the problem.  It did for a while but now it has come back again.

---

### Post by tinycamp on 2007-11-28
mmmm, have you tried replacing the network card?, i think it's hardware...

---

### Post by wareagle on 2008-03-04
An update for anyone who cares...

I had a bad motherboard and ended up replacing it.

---

