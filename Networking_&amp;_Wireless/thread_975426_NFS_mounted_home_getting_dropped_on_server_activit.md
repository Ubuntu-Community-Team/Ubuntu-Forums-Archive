---
title: "NFS mounted /home getting dropped on server activity"
date: 2008-11-08
forum: Networking &amp; Wireless
---

### Post by Chas_E_Erath on 2008-11-08
Hi.

I have two (2) ubuntu computers (very vanilla hardware (ie. no scsi, no raid, no water-cooled vector processors)).  The primary computer (skink) exports /home via NFS.

```


chas@skink:~$ cat /etc/exports
/home  franky(rw,async,no_subtree_check,no_root_squash,no_all_squash)

```


The secondary computer (franky) mounts /home via NFS at boot.

```

chas@franky:~$ grep skink /etc/fstab
skink:/home     /home           nfs    rw,user,noauto,exec  0   0

```

I can log in on franky and everything is just peachy unless someone is logged in and using skink.  In that case, franky seems to lose the NFS mount, and it takes a minute or 2 for it to sync up again.  Then I can do a thing or two until it happens again, and again and again...

I'm fairly certain (I think) that the problem has something to do with disk reads/writes on skink.  Whatever the case, franky is unusable when someone is logged in on skink.

Any hints, solutions, or advise will be accepted with profound gratitude, joyous praise, and animal sacrifice (if warranted and desired).

Thanks.
Chas E. Erath

---

