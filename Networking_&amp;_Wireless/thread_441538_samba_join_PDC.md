---
title: "samba join PDC"
date: 2007-05-12
forum: Networking &amp; Wireless
---

### Post by jrock2004 on 2007-05-12
I have freeBSD running a samba PDC. What I was wondering is how do I set my ubuntu 7.04 to join that domain like I can do with my windows machines?

Thanks

---

### Post by [S|G] on 2007-05-13
First you have to edit your /etc/samba/smb.conf file and set some parameters:
```

workgroup = domain
security = domain
password server = [Name of your PDC]
encrypt passwords = yes

```
Then use this command on the terminal:
```

net rpc join -U [administrator]

```
Where [administrator] is the username of the domain's administrator.

---

