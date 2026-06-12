---
title: "Samba on second drive"
date: 2015-06-02
forum: Networking &amp; Wireless
---

### Post by richard115 on 2015-06-02
Server crashed and could not resolve with rescue so added another drive as new installation. Samba was installed on old configuration, now 2nd drive.  Win clients cannot see it. Do I need a path added in smb.conf or add drive in fstab? GUI sees drives under computer.

---

### Post by TheFu on 2015-06-02
Yes, it must be mounted under the fstab (i.e. a real, honest, mount), then you should use whatever method you used previously to deal with samba sharing - gui, smb.conf, whatever.

---

