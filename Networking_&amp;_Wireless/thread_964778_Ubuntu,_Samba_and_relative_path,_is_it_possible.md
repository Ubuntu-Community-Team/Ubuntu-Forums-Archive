---
title: "Ubuntu, Samba and relative path, is it possible?"
date: 2008-10-31
forum: Networking &amp; Wireless
---

### Post by Sunsawe on 2008-10-31
Hi everyone!

I have a question concerning uBuntu and Samba.:)

Our local network is divided in a FreeBSD box running a Samba server, XP boxes and Ubuntu ones.

In Samba, the shared folders are defined with relative paths.
A good example is the home directory. The path of this sharing is defined like that "/home/%U" and so after logging in, the user directly has his "home" shared. :)

This works perfectly with teh XP boxes but not with the Ubuntu ones. When trying to mount the "home" folder on Ubuntu, it just refuses with an error saying that it can't mount the folder. It doesn't even offer to login. :(
If the path is non-relative, so, like this "/home/my_user", then it works.  :confused:

Is there a way to fix this for me not to be forced to define one shared folder per user?

Thank you

---

### Post by Iowan on 2008-10-31
Someday soon, I gott update my Breezy server... but it has functional shares defined by "/home/%U" 

... or is it "/home/%S"? Try that one.

This is from my server:
```
[homes]
   comment = Home Directories
   valid users = %S
   browseable = no
   writable = yes
```

---

### Post by Sunsawe on 2008-10-31
Well actually, i tried this one. It is the one advised by the smb.conf's manpage. It didn't work. It produced exactly the same error when i tried to mount the folder, Impossible to mount the Windows share.

---

