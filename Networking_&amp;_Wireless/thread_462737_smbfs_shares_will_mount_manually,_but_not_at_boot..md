---
title: "smbfs shares will mount manually, but not at boot."
date: 2007-06-03
forum: Networking &amp; Wireless
---

### Post by Adapted.Cat on 2007-06-03
I have had this problem in both Dapper and Feisty.

Before you ask, yes I have smbfs installed.
I can mount shares quite happily (as root) from
the command line - indeed, I can do 'mount -a -t smbfs'
and it'll run without error. However, at boot nothing
mounts. I get these messages, which may be relevant:

```

[   38.711119] smbfs: mount_data version 1029990773 is not supported
[   38.711352] smbfs: mount_data version 1029990773 is not supported
[   38.711460] smbfs: mount_data version 1029990773 is not supported
[   38.711566] smbfs: mount_data version 1029990773 is not supported

```

Any ideas?

---

