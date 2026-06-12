---
title: "NIS/NFS breaks xorg"
date: 2019-04-02
forum: Networking &amp; Wireless
---

### Post by s0ftcorn on 2019-04-02
Hi!

The clients on our network get authentication information from NIS and mount the home directory via NFS.
Since i updated the NIS/NFS server to debian 9 the login managers on the clients are basically broken. Sometimes the login works, sometimes it doesnt.
The nsswitch.conf:

```

passwd:         compat nis
group:          compat nis
shadow:         compat nis
gshadow:        files


hosts:          files mdns4_minimal [NOTFOUND=return] dns myhostname
networks:       files


protocols:      db files
services:       db files
ethers:         db files
rpc:            db files


netgroup:       nis
```

the autofs file:

```
* -fstype=nfs,default,vers=3,retry=0 10.0.0.3:/home/&
```

journalctl tells errors like:

```

Apr 02 13:11:46 AStA-SR-R kernel: i915 0000:00:02.0: firmware: failed to load i915/kbl_dmc_ver1_01.bin (-2)
Apr 02 13:11:46 AStA-SR-R kernel: i915 0000:00:02.0: Direct firmware load for i915/kbl_dmc_ver1_01.bin failed with error -2
Apr 02 13:11:46 AStA-SR-R kernel: i915 0000:00:02.0: Failed to load DMC firmware [https://01.org/linuxgraphics/intel-linux-graphics-firmwares], disabling runtime power

Apr 02 13:11:46 AStA-SR-R avahi-daemon[433]: chroot.c: open() failed: No such file or directory

(which dont seem related, but xorg stuff:)

Apr 02 13:11:47 AStA-SR-R /usr/lib/gdm3/gdm-x-session[514]: (EE) open /dev/fb0: Permission denied
Apr 02 13:11:47 AStA-SR-R /usr/lib/gdm3/gdm-x-session[514]: (WW) Falling back to old probe method for vesa
Apr 02 13:11:47 AStA-SR-R /usr/lib/gdm3/gdm-x-session[514]: (WW) VGA arbiter: cannot open kernel arbiter, no multi-card support





```

things i tried:
setting MINGID for YP to 0.
Removing any desktop environment generated configs from user home.
chmod 777 ~


Any ideas? Im using Ubuntu 18.04 on the clients.

---

