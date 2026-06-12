---
title: "Samba Group Permissions Help"
date: 2008-05-31
forum: Networking &amp; Wireless
---

### Post by drunkn on 2008-05-31
Hi,

I am trying to make all files and directories made under a samba share have the write option enabled for the group, aka:

drwxrwx---

I've tried using the options 'create mask', 'directory mask', 'force create mode' and 'force directory mode' but nothing seems to enable that 'w' for the files/directories....it always gets written as drwxr-xr-x.

Please help me...

---

### Post by dmizer on 2008-06-01
it would be very helpful if you posted the contents of your /etc/samba/smb.conf file.

you may also find your answer by looking at the samba server howto linked in my sig.

---

