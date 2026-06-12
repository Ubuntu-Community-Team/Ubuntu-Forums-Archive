---
title: "Samba server help"
date: 2010-11-24
forum: New to Ubuntu
---

### Post by Guruprasad on 2010-11-24
I have samba file server on Ubuntu. I want all the files and folders created by Ubuntu clients to have permission 770. How to set this? Currently all files and directories are created with permission 744

---

### Post by ptn107 on 2010-11-24
You can use the following in the global section for all shares, or put them in each share section for a per share basis:

```
create mask = 770
directory mask = 770
```

---

