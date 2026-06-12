---
title: "help SAMBA include does not work"
date: 2009-02-03
forum: New to Ubuntu
---

### Post by divinenewb on 2009-02-03
Hi,

My conf

[global]
workgroup = myworkgroup
passwd program = /usr/bin/passwd %u
passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .
username map = /etc/samba/usermap.conf
load printers = No
show add printer wizard = No
panic action = /usr/share/samba/panic-action %d
invalid users = root
create mask = 0664
directory mask = 0775

include = /etc/samba/smb.%U.conf
[homes]
comment = Home Directories
read only = No
browseable = No
available = No

#> testparm
Load smb config files from /etc/samba/smb.conf
Can't find include file /etc/samba/smb..conf
Loaded services file OK.

While /etc/samba/smb.user.conf exists it says Cant find ....
(user is created to unix and to smb)


Where can be a problem? (it worked fine until i reinstalled ubuntu)

I appreciate any help!

---

### Post by cmnorton on 2009-02-05
Is their anything of interest in /var/log/samba/*? You don't need to post your logs here, but is there something that would indicate what's going on with the include?

---

