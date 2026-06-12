---
title: "samba mount goes dead and locks-up gnome"
date: 2008-11-15
forum: Networking &amp; Wireless
---

### Post by graysky on 2008-11-15
I have a my amd64 box connected to an i386 via a samba share mounted via CIFS.  The i386 box that has the share on it got shutdown while it was still mounted on my amd64 box which caused most of my apps to freeze up.  Rhythmbox, my desktop icons, active windows, etc just froze up.  I also couldn't kill them by their PID on the shell.

When I did a ctrl+alt+F1 and logged in, I saw a bunch of this message:

```
CIFS VFS: Unexpected lookup error -112
```

When I attempted a umount with either the -l or -f switch, nothing happened except for this error:

```
umount error 16: device or resource busy
```

How does one handle this without a reboot?

---

