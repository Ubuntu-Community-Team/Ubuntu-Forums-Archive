---
title: "another smb problem.. can't access the share"
date: 2006-11-16
forum: Networking &amp; Wireless
---

### Post by badr on 2006-11-16
I'm having issues with samba with my fileserver. here is an extract from my smb.conf

```
[cerbexshared]
path = /media/file-server/cerbex/shared
comment = cerbex shared files
available = yes
browseable = yes
public = yes
writable = yes
force create mode  = 0770
force directory mask = 0770

[home]
path = /home
comment = home for users
available = yes
browseable = yes
public = yes
writable = yes
create mode  = 0775
```


I can navigate the home share without any problem but i'm having issues with cerbex/shared. no one can log into it right now, much less see the files or edit them. 

For whatever reason, ownership is set to ROOT and not the groups. How do I go about sorting that out? thanks a million

---

