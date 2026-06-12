---
title: "can't view windows workgroup"
date: 2007-08-21
forum: Networking &amp; Wireless
---

### Post by jbayone on 2007-08-21
When I go to Places->Network->Windows Network, the only domain that shows up is MSHOME, not Strawman, the one my XP machines are on.  I've tried editing the workgroup= section in smb.conf but to no avail.  Any suggestions?

---

### Post by moore.bryan on 2007-08-21
*what does ```
smbclient -L Strawman
``` show?*

---

### Post by jbayone on 2007-08-21
It says connection failed

---

