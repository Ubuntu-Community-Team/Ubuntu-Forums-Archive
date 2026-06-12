---
title: "Accessing Samba Server from Ubuntu"
date: 2007-11-10
forum: Networking &amp; Wireless
---

### Post by mcduarte2000 on 2007-11-10
Feeling very frustrated. I can access an external samba server on my home network,but only as read-only, unless using the root user.

What I have on my fstab is:

//lua/Volume_1 /mnt/lua smbfs auto 0 0

Can someone help me and tell me what exactly should I put on this line, so that any user on my computer has full privileges on this external samba server?

Thanks a lot!

Miguel

---

### Post by mcduarte2000 on 2007-11-10
Found a solution:

```

//lua/Volume_1	/mnt/lua	smbfs	user,rw,sync,auto,exec,uid=miguel	0	0

```

---

