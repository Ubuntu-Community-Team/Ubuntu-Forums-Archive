---
title: "samba and nautilus"
date: 2010-11-24
forum: New to Ubuntu
---

### Post by Pintocow on 2010-11-24
From what I've read the shares for samba should be in smb.conf with something like this.
[Guest Share]
        comment = Guest access share
        path = /path/to/dir/to/share
        browseable = yes
        read only = yes
        guest ok = yes
Ive set up multiple shares through Nautilus's share tab and when viewing my smb.conf file none of these shares are in there. They work just fine but if I want to edit their options not using Nautilus, where do I do it?

If I do enter the shares manually into smb.conf will this be a problem? 

running 10.04 by the way

---

### Post by ptn107 on 2010-11-24
Correct me if I'm wrong, but I believe shares made through nautilus will reside in /var/lib/samba/usershares ?

---

### Post by pricetech on 2010-11-24
Why not just share using Samba.  Install, if you haven't already, system-config-samba which will give you a dandy GUI configuration tool.

---

### Post by endotherm on 2010-11-24
ok, there are 1.5 flavors of samba.
there is classic samba, where there is NO GUI, and all config is in /etc/samba/smb.conf
there is also userspace samba (Nautilus-share) which uses teh smb.conf for global settings and applies share definitions per user from /var/lib/samba/usershares

if you have a share in the usersshares, make sure you do not have it in your smb.conf. the two need to be carefully coordinated so that there is no overlap.

---

