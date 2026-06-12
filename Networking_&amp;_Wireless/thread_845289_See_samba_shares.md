---
title: "See samba shares"
date: 2008-06-30
forum: Networking &amp; Wireless
---

### Post by gionnico on 2008-06-30
How can I see the samba shares in xubuntu, like I do with ubuntu from:
Places -> Network -> Windows Network -> Domain ?

---

### Post by prshah on 2008-06-30
> **gionnico said:**
> How can I see the samba shares in xubuntu, like I do with ubuntu from:
Places -> Network -> Windows Network -> Domain ?

You'll have to install pyNeighbourhood, since thunar (xubuntu file manager) does not handle samba path names/protocols (smb://).

```
sudo apt-get install pyneighborhood
```

---

