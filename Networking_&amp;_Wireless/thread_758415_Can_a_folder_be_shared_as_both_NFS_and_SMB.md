---
title: "Can a folder be shared as both NFS and SMB?"
date: 2008-04-18
forum: Networking &amp; Wireless
---

### Post by stchman on 2008-04-18
I have some folders that I want to share as both SMB and NFS.  Is this possible?

Thanks.

---

### Post by MrFSL on 2008-04-18
Yes.

---

### Post by stchman on 2008-04-18
> **MrFSL said:**
> Yes.

So you can put the same folder for example

/media/share

in the /etc/exports and /etc/samba/smb.conf files?

Cool.  I find that NFS works better for Linux but the Windows machines in my house can look at the Samba shares very easily.

---

