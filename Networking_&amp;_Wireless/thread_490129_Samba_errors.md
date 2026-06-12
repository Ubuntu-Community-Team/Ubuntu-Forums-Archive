---
title: "Samba errors"
date: 2007-07-02
forum: Networking &amp; Wireless
---

### Post by lexarrow on 2007-07-02
Could someone please tell me how to deal with these errors?

```
Jul  2 11:22:40 sopolec smbd[10708]: [2007/07/02 11:22:40, 0] auth/auth_util.c:create_builtin_administrators(785) 
Jul  2 11:22:40 sopolec smbd[10708]:   create_builtin_administrators: Failed to create Administrators 
Jul  2 11:22:40 sopolec smbd[10708]: [2007/07/02 11:22:40, 0] auth/auth_util.c:create_builtin_users(751) 
Jul  2 11:22:40 sopolec smbd[10708]:   create_builtin_users: Failed to create Users 
```

Thank you!

---

### Post by bigken on 2007-07-02
sudo apttitude install samba

sudo smbpasswd -a yourname

sudo smbpasswd -e yourname

---

### Post by lexarrow on 2007-07-02
Samba is up to date and I can use it. The problem is that after a while the (whole)server becomes unusable, crashes. I just don't know what the problem is. I've been looking at the logs and I've seen the samba error, now I think it's because ntfs-3g. Is there any way I can see the last thing that happened before the server crashed?

Thanks!

---

