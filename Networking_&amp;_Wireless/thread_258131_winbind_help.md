---
title: "winbind help"
date: 2006-09-15
forum: Networking &amp; Wireless
---

### Post by zachtib on 2006-09-15
I'm trying to set up winbind to get the command line utilities working, suchs as `wbinfo -u` and such

i've installed winbind and samba from repos (I'm on edgy, btw but I don't think thats the problem)

running `wbinfo -p` returns:
```
Ping to winbindd failed on fd -1
Could not ping winbindd!
```

and /var/log/samba/log.winbind:
```

[2006/09/15 14:16:12, 1] nsswitch/winbindd.c:main(978)
  winbindd version 3.0.22 started.
  Copyright The Samba Team 2000-2004
[2006/09/15 14:16:12, 0] nsswitch/winbindd.c:main(1071)
  unable to initalize domain list

```

used to be much longer, so maybe i've fixed _something_

---

### Post by bartenst on 2006-09-18
I am experiencing exactly the same problem with Samba 2.0.22. Here is my smb.conf:

> [global]
# separate domain and username with '+', like DOMAIN+username
     netbios name = BORGWAHUUAT
     winbind separator = +
     # use uids from 10000 to 20000 for domain users
     winbind uid = 10000-20000
     # use gids from 10000 to 20000 for domain groups
     #winbind gid = 10000-20000
     winbind gid = 500-1000
     # allow enumeration of winbind users and groups
     # might need to disable these next two for performance
     # reasons on the winbindd host
     winbind enum users = yes
     winbind enum groups = yes
     # give winbind users a real shell (only needed if they have
     template homedir = /home/%D/%U
     template shell = /bin/bash

     #security=domain
     security = ADS
     workgroup = BORGEGG
     realm = BORG-EGG.AT
     encrypt passwords = yes
     password server = *
     wins server = 192.168.1.30
     winbind use default domain = yes
     os level = 18
     local master = No
     dns proxy = No


---

### Post by bartenst on 2006-09-18
It seems that the problem went away after I issued the join command:
> net ads join -U Administrator
Afterwards winbind started successfully.

---

### Post by zachtib on 2006-09-18
> **bartenst said:**
> It seems that the problem went away after I issued the join command:

Afterwards winbind started successfully.


huh? I'm confused, what exactly does this do?

---

