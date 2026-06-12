---
title: "Replicated Failover Domain Controller and file server using LDAP"
date: 2008-07-10
forum: Networking &amp; Wireless
---

### Post by NaughtyusMaximus on 2008-07-10
I'm trying to set up Replicated Failover Domain Controller and file server using LDAP, as in this guide:

[http://wiki.samba.org/index.php/1.0._Configuring_Samba](http://wiki.samba.org/index.php/1.0._Configuring_Samba)

Does anyone have a better guide than this?  Essentially, I can get to the step where I'm supposed to be creating new users for the system before I get lost.  I've figured out that I need to have two conf files in /etc/smbldap-tools which aren't referenced in the guide, and have put those there with the values I think are correct.. However, on the user creation step, I still end up with:

```
smbldap-useradd -a -m root 

Error looking for next uid in sambaDomainName=HATFIELD,dc=mydomain,dc=local:No such object at /usr/share/perl5/smbldap_tools.pm line 1071.

```

Any thoughts?

---

### Post by NaughtyusMaximus on 2008-07-11
<bump for more eyes>

---

