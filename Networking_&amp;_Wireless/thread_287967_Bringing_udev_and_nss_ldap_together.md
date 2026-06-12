---
title: "Bringing udev and nss_ldap together"
date: 2006-10-29
forum: Networking &amp; Wireless
---

### Post by supermihi on 2006-10-29
Hello,
we are using centralized user and group management with LDAP. One Problem I am experiencing is that udev starts before networking, so e.g. "GROUP=" are not evaluated if the group is available via LDAP only. Even worse, if the group exists in /etc/group and also, but with another gid in the directory, it can give you some headaches.
I had that problem with the cdrom group, which was gid 19 in the directory and gid 24 in /etc/group. A user couldn't access the drive, even since "ls -l /dev/hdc" showed cdrom as group and also "id <user>" showed that he was in that group. But the gid's didn't match.
What I am doing now is to check that on every machine cdrom is gid 19,but this seems like a very hackish solution to me. Is there a more "ubuntu way" to do this? Can I start networking before udev?

---

