---
title: "Samba default file permission"
date: 2007-05-25
forum: Networking &amp; Wireless
---

### Post by hil on 2007-05-25
My company is using Samba for software development on Linux. I am trying to change the default umask for file permissions on Samba mounted drives. The problem is every time I write to a file or create a file on the Samba drive, the file’s execute permission is set. If the file is a directory and the execute permission is set, I have no problem with that. But if the file is a source file such as source.cpp, I don’t want the execute permission set. Is there a way to change the default file permission for Samba?

---

### Post by ruy_lopez on 2007-05-25
In your smb.conf include the lines, under the share you want these to apply (or under global, if you want it to apply globally):

```
create mask 0644      #this is for files
directory mask 0755 #this is for directories
```

Obviously, how you set the mask is up to you.

---

