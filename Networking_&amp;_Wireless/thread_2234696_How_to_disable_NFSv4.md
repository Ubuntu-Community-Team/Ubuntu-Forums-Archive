---
title: "How to disable NFSv4?"
date: 2014-07-16
forum: Networking &amp; Wireless
---

### Post by mic520 on 2014-07-16
There is a way to disable NFSv4, that appears as a hint in /etc/default/nfs-kernel-server:
"# To disable NFSv4 on the server, specify '--no-nfs-version 4' here"
Although, the change in this file caused following error while starting nfs:
/etc/default/nfs-kernel-server: line 13: --no-nfs-version: command not found

---

### Post by chili555 on 2014-07-16
I know little about this but I may see the problem. May we see:```
cat /etc/default/nfs-kernel-server
```I think it needs a minor tweak.

---

### Post by mic520 on 2014-07-16
Actually I needed it to prevent nobody:nogroup ownership on every newly created file in nfs share.
Finally I find solution by editing /etc/exports file. Just added no_root_squash and no_all_squash

---

### Post by SeijiSensei on 2014-07-16
I use "vers=3" in the options list on my NFS clients to force a v3 connection.

---

