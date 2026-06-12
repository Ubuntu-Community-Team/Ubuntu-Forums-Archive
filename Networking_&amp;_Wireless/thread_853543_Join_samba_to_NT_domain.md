---
title: "Join samba to NT domain"
date: 2008-07-08
forum: Networking &amp; Wireless
---

### Post by ientzy on 2008-07-08
I use samba 3.0.28a, instal with "apt-get install samba"
and winbind with "apt-get install winbind".
I have this configuration on smb.conf
[global]
workgroup = RO1
security = DOMAIN
encrypt passwords = Yes
template shell = /bin/bash
idmap uid = 15000-20000
idmap gid = 15000-20000
template homedir = /usr/home/%D/%U
winbind enum users = Yes
winbind enum groups = Yes
--------------------------------------
My /etc/nsswitch.conf look like this:

passwd:   files winbind
group:    files winbind
shadow:   files winbind
---------------------------------------
When i gve "net join -D RO1 -U Administrator"
password: Realpass
i get: "Joined domain RO1"
This is nice, i check users and groups with "wbinfo -u" and "wbinfo -g", is ok that to. But when i check the event log from NT Domain, i have this error:


"The session setup from the computer LINUXTEST failed because there is no trust account in the security database for this computer. The name of the account referenced in the security database is LINUXTEST$." Event ID 5723.

I think this is a problem with my configuration, becouse i try with suse and work, and i whant ubuntu not suse. Maybe somebody already have this error and can tell me where is the problem or problems.

---

### Post by ientzy on 2008-07-09
C`mon guys, nobody have this problem before me?

---

