---
title: "samba &amp; acl"
date: 2007-10-09
forum: Networking &amp; Wireless
---

### Post by thoralf on 2007-10-09
hi there,

how would i mount a samba volume with its access control lists enabled?
i have my /-filesystem mounted with acls and tried various combinations of

mount -t cifs -o user=joedoe,sfu //server/share /mnt

but that didn't work - getfacl just doesn't show the acl bits.

thank you for your help,
thoralf.

---

