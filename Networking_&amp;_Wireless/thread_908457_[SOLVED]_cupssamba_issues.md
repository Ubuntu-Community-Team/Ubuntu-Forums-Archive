---
title: "[SOLVED] cups/samba issues"
date: 2008-09-02
forum: Networking &amp; Wireless
---

### Post by moore.bryan on 2008-09-02
i was following [this]("http://www.math.colostate.edu/%7Ereinholz/freebsd/smb_print_client.html") thread, was successful in the smbclient command, but no matter what i set in cups, it says it can't print to the printer. ideas?

EDIT:
------
more specific info:
```
smbclient -W admin -L hs-h307-01 -U bmoore
``` gives me this:
```
Domain=[ADMIN] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

        Sharename       Type      Comment
        ---------       ----      -------
        IPC$            IPC       Remote IPC
        print$          Disk      Printer Drivers
        ADMIN$          Disk      Remote Admin
        C$              Disk      Default share
        LJ4000          Printer   HP LaserJet 4000 Series PCL6
Domain=[ADMIN] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

        Server               Comment
        ---------            -------

        Workgroup            Master
        ---------            -------

```
but ```
smb://bmoore/password@admin/LJ4000
``` doesn't work in cups.

---

### Post by moore.bryan on 2008-09-02
solved! for anyone else wondering, apparently the page i was looking at wasn't explicit enough in its directions for me. ;-)
```
smb://bmoore/password@admin/LJ4000
```
should have been:
```
smb://ADMIN/bmoore:password@HS-H307-01/LJ4000
```

---

