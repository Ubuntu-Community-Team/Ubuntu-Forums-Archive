---
title: "Automatically mount Wifi connected NFS on reboot"
date: 2007-01-11
forum: Networking &amp; Wireless
---

### Post by AchimRS on 2007-01-11
Hi all,
I try to automatically remount a server connected via NFS and a WiFi card on my laptop. Currently I'm using Edgy with a WEP encrypted Atheros connection to an NFS server.

If I do a manual mount, everything is OK, but if I add the appropriate lines intothe /etc/fstab, nothing happend. I guess it is because of the late connection via WEP encryption and the password access - but maybe it's something different.

I tried in the fstab the following parameters:
  nfs defaults 0 0
  nfs rw,user,noauto 0 0
  nfs rw,hard,intr 0 0
all without success.
Do anybody have an idea what to do (parameters in fstab or something else) to have the nfs servers mounted on the client automatically after each reboot (without manually "mount" them).

Thanks
  Achim

---

