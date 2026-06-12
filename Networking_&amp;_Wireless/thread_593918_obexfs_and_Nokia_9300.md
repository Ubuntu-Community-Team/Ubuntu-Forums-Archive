---
title: "obexfs and Nokia 9300"
date: 2007-10-27
forum: Networking &amp; Wireless
---

### Post by Ji31 on 2007-10-27
Hi,

yesterday I have bought Nokia 9300. I don't want any constacts/email/sms synchronization, but I just need file transfer (via DKU2- usb cable).

After obexftp and obexfs install I tried to type:
```
sudo obexfs -u l /mnt/9300
``` but the directory is still empty and I get warning: ```
Segmentation fault (core dumped)

```

When I typed:
```
sudo -H nautilus /mnt/9300
```

the response was:
```
(nautilus:6506): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
Initializing gnome-mount extension

```

What can I do? Thank you.

---

### Post by Ji31 on 2007-10-28
Any linux guru knows please? :-k

---

