---
title: "Retrieve who accesses/edited/created/deleted samba shared folder via Samba Log file"
date: 2010-08-04
forum: New to Ubuntu
---

### Post by rohan2k10 on 2010-08-04
how can we track who accessed the samba shared folder...

His/her IP details and folders/files that he created, edited or deleted.

How can we maintain log files to retrieve such information.

Please help.

---

### Post by sikander3786 on 2010-08-04
Hi.

I think this log is already present unless you have turned it off in you smb.conf file.

Path = /var/log/samba/access.log

Regards.

---

