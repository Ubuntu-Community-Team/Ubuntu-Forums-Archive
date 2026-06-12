---
title: "%U is not working in [homes]"
date: 2014-01-02
forum: Networking &amp; Wireless
---

### Post by daylight2 on 2014-01-02
I'm trying to setup shadow_copy2 mechanism for [homes] share.
First, for simplicity I made the following settings in /etc/samba/smb.conf:
```

...
[homes]
   comment = Home Directories
   browseable = no
   inherit acls = Yes
   follow symlinks = yes
   wide links = yes
   vfs objects = shadow_copy2
   shadow: snapdir = /srv/shadows/users/**john**
   shadow: sort = desc
# shadow: format = @GMT-%Y.%m.%d-%H.%M.%S
   read only = no
   create mask = 0700
   directory mask = 0700
   valid users = %S
...

```
and it worked perfectly, when I logged in as **john**: I could perfectly see "Previous versions". Now I want to be able to login as any user, so I changed snapdir to .../%U:
```

...
[homes]
   comment = Home Directories
   browseable = no
   inherit acls = Yes
   follow symlinks = yes
   wide links = yes
   vfs objects = shadow_copy2
   shadow: snapdir = /srv/shadows/users/**%U**
   shadow: sort = desc
# shadow: format = @GMT-%Y.%m.%d-%H.%M.%S
   read only = no
   create mask = 0700
   directory mask = 0700
   valid users = %S
...

```
And this way it does not work, even if I log in as john. What could I do wrong?
I'm on ubuntu server 12.04x64, smbd version 3.6.3

---

