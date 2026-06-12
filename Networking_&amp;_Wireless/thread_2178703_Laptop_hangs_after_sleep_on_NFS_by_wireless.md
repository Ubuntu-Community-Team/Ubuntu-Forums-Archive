---
title: "Laptop hangs after sleep on NFS by wireless"
date: 2013-10-04
forum: Networking &amp; Wireless
---

### Post by skyglow on 2013-10-04
System wireless network has NFS4 mounted on /home.
After sleep laptop hangs and do not display anything, not even the password request.
WIth ctrl+alt+F1 i can log another shell but lightdm is completely crashed; even "restart lightdm" doesn't work i have video artifacts.

Ubuntu 12.04.3
AMD A4-4355M APU with Radeon(tm) HD Graphics (fam: 15, model: 10, stepping: 01)
NFS mounted with autofs5
config follows.

/etc/auto.master
```
/home /etc/auto.home --timeout=300
```

/etc/auto.home
```
* -fstype=nfs4,rw,soft,intr,async 192.168.1.254:/home/&
```

---

### Post by skyglow on 2013-10-14
any ideas? i'm still experiencing this issue :(

---

