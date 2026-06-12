---
title: "nfs / fstab mounting doubt..."
date: 2014-02-19
forum: Networking &amp; Wireless
---

### Post by pinolo on 2014-02-19
I've just updated an ubuntu server from 10.04 to 12.04, and I don't understand why a network NFS shared folder located in a partition is called in the /etc/fstab file like this:

UUID=<correctUUID>  [FONT=trebuchet ms]  /home    ext4    noauto    0    2

before than upgrading, this partition was mounted correctly, while after the upgrade I've to mount manually or I have to change noauto with auto.

I've seen on google that often NFS partitions are signed with noauto option in the fstab file, but how is possible that they are effectively mounted? Where are they really mounted?[/FONT]

---

### Post by steeldriver on 2014-02-19
AFAIK the noauto flag means that the system will not try to mount the device at boot time - perhaps you previously had a mount command somewhere like /etc/rc.local that was mounting it post-boot?

---

### Post by papibe on 2014-02-19
Hi pinolo.

That example is not a NFS mounting point, but your local home directory. Could you post your /etc/fstab to get a better idea what is the situation?

Regards.

---

### Post by VamPikmin on 2014-02-19
From memory nfs shares are under /etc/exports

---

