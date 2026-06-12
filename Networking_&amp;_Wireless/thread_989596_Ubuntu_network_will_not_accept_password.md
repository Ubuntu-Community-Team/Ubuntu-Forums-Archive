---
title: "Ubuntu network will not accept password"
date: 2008-11-21
forum: Networking &amp; Wireless
---

### Post by MacDuff on 2008-11-21
Trying to share files between ubuntu machines (8.04) over a wired local network (samba) running through a router.  When I attempt to read a file that is supposedly shared and visible, I am asked for my password but when I enter the pasword it is not accepted.

What must be set/changed to get read/write access to the files on other machines?

Thanks

---

### Post by Iowan on 2008-11-21
Username must exist for Ubuntu (passwd) AND Samba (smbpasswd). Beyond that, it may help to post /etc/samba/smb.conf.

---

