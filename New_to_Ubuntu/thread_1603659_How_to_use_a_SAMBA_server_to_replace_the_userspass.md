---
title: "How to use a SAMBA server to replace the users/password (winbind)"
date: 2010-10-23
forum: New to Ubuntu
---

### Post by honeybear on 2010-10-23
Hello,

With winbind it is possible to remove the /etc/passwd of a machine and let it use the users/passwords of a samba server... Anyone has the configuration files for that?

[COLOR="Red"](no kerberos ! for simple)[/COLOR]


> File: /etc/conf.d/samba

#add "winbind" to the daemon_list for winbind to start
daemon_list="smbd nmbd winbind"


---

