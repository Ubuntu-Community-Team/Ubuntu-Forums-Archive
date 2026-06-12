---
title: "Can't share folder via samba (error msg)"
date: 2006-12-30
forum: Networking &amp; Wireless
---

### Post by negativ on 2006-12-30
Right-clicking on any folder yields a GNOME dialog box that says:

"The configuration could not be loaded.
You are not allowed to access the system configuration"

:confused: 

I don't know why I wouldn't be able to share subdirectories in my own home directory.

Any ideas?

---

### Post by Iowan on 2006-12-30
It almost sounds like **/etc/samba/smb.conf** is corrupted.

Does running **testparm** reveal any issues?

---

