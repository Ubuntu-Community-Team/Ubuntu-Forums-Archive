---
title: "Where is Vista?"
date: 2009-01-04
forum: New to Ubuntu
---

### Post by poscomp on 2009-01-04
I run Ubuntu 8.10 and everything works fine except it won't see my Vista drive's or printers. It see's all my XP machines just fine and it see's the Vista machine name but when I go to logon to a drive nothing is there. When I run Kubuntu from the same computer the drives all show up and I can attach and copy files just fine. I think it's a SAMBA file but I don't know which file to load. Can anyone help me?

---

### Post by handydan918 on 2009-01-04
> **poscomp said:**
> I run Ubuntu 8.10 and everything works fine except it won't see my Vista drive's or printers. It see's all my XP machines just fine and it see's the Vista machine name but when I go to logon to a drive nothing is there. When I run Kubuntu from the same computer the drives all show up and I can attach and copy files just fine. I think it's a SAMBA file but I don't know which file to load. Can anyone help me?

you could start by comparing the /etc/samba/smb.conf

---

### Post by kansasnoob on 2009-01-04
> **poscomp said:**
> I run Ubuntu 8.10 and everything works fine except it won't see my Vista drive's or printers. It see's all my XP machines just fine and it see's the Vista machine name but when I go to logon to a drive nothing is there. When I run Kubuntu from the same computer the drives all show up and I can attach and copy files just fine. I think it's a SAMBA file but I don't know which file to load. Can anyone help me?

Kubuntu has different front-ends to handle ntfs-3g. With Ubuntu try installing either ntfsprogs or ntfs-config.

I always use ntfsprogs but it allows full read & write support to ntfs so you can destroy stuff if you have a 'doof" moment!

---

