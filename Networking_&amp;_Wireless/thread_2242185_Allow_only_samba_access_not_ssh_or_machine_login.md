---
title: "Allow only samba access not ssh or machine login"
date: 2014-08-31
forum: Networking &amp; Wireless
---

### Post by tubos2 on 2014-08-31
I have a ubuntu (14.04) server setup as samba server

a user has access to the samba share but should not be allowed
to login or ssh into the server directly 

If possible how can I do that?

---

### Post by TheFu on 2014-08-31
Google found this: [http://knowledgelayer.softlayer.com/learning/how-do-i-permit-specific-users-ssh-access](http://knowledgelayer.softlayer.com/learning/how-do-i-permit-specific-users-ssh-access)
DenyGroups, DenyUsers settings for the /etc/ssh/sshd_config file.

Did that not work?

**man sshd_config** will explain more details.

---

