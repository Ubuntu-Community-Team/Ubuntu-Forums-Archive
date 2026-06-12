---
title: "mount.nfs: access denied by server while mounting"
date: 2008-10-06
forum: Networking &amp; Wireless
---

### Post by engineer85 on 2008-10-06
Hi all,

I'm having trouble using nfs to mount a remote filesystem (all of it, from /) on my local machine. Here is what I tried:

```
controls@UTAEngineer:/bin$ sudo mount Engineer:/ /Engineer.home/
mount.nfs: access denied by server while mounting Engineer:/
```

Here is the output of my /etc/exports file


```
controls@UTAEngineer:/bin$ cat /etc/exports 
# /etc/exports: the access control list for filesystems which may be exported
#		to NFS clients.  See exports(5).
#
# Example for NFSv2 and NFSv3:
# /srv/homes       hostname1(rw,sync) hostname2(ro,sync)
#
# Example for NFSv4:
# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt)
# /srv/nfs4/homes  gss/krb5i(rw,sync)
#
/home Engineer(rw,no_subtree_check,no_root_squash)
/home UTAEngineer(rw,no_subtree_check,no_root_squash)
/ Engineer(rw,no_subtree_check,no_root_squash)
/ UTAEngineer(rw,no_subtree_check,no_root_squash)
```

Any suggestions? Please let me know if you need more info.

---

