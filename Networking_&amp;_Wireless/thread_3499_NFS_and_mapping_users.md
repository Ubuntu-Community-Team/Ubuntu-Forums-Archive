---
title: "NFS and mapping users"
date: 2004-11-06
forum: Networking &amp; Wireless
---

### Post by AndersAA on 2004-11-06
I'm trying to mount a nfs directory on my server in ubuntu over nfs, the problem is that the users are not in sync with the server.

I tried this:

/mnt/storage/dump 192.168.0.2(async,rw,all_squash,anonuid=1000,anongid=1000,no_subtree_check)

and then exportfs -ar, but it seems to have absolutly no effect on the client, umount && mount still shows owner as 1001:10 as it is on the server.

---

