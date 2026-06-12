---
title: "Netatalk not using LDAP"
date: 2008-09-16
forum: Networking &amp; Wireless
---

### Post by rrwright on 2008-09-16
I have an 8.04 server running as a PDC using Samba and LDAP for authentication. Everything works fine there. I am trying to install Netatalk for the Mac clients to connect to the fileserver. Netatalk is up and running just fine but will only allow connections from standard linux users (users listed in /etc/passwd). It doesn't seem to be querying LDAP at all. The symlinks in /usr/lib/netatalk do include:
```
uams_clrtxt.so -> uams_pam.so
uams_dhx.so -> uams_dhx_pam.so
```
Am I missing something obvious in the Netatalk config? Is there other PAM/LDAP config that needs to happen? Thanks!


- Ryan

---

### Post by cosmicmonkey on 2009-03-18
I'm waking this thread back up.   I'm attempting to get netatalk to authenticate with Active Directory.

---

### Post by rrwright on 2009-03-20
And I would still love to know the answer to this if anyone has skills in that direction! Thanks.

---

### Post by cosmicmonkey on 2010-01-14
> **cosmicmonkey said:**
> I'm waking this thread back up.   I'm attempting to get netatalk to authenticate with Active Directory.

Actually I got this to work without LDAP.   I used winbind and authenticated off of our domain controller.  Had to modify pam as well.

---

