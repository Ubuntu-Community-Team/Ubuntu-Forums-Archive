---
title: "Samba PDC on Ubuntu 7.10: Windows hosts cannot join cldap"
date: 2008-01-20
forum: Networking &amp; Wireless
---

### Post by glauco.b on 2008-01-20
Hello

I'm trying to build a Samba based Primary Domain Controller with LDAP authentication support.

I followed this great tutorial about:
[http://www.howtoforge.com/openldap-samba-domain-controller-ubuntu7.10](http://www.howtoforge.com/openldap-samba-domain-controller-ubuntu7.10)

Everything worked just fine (ok, apart from bios updates and other hardware-related stuff :( ), the server went up, LDAP went up, Samba went up too.

BUT: Windows XP boxes cannot join to my brand new domain. I applied any existing regedit hack, but the problem is different: looking from wireshark, it happens that Windows XP tries to connect to LDAP over UDP (UDP port 389) making a cldap query. This obviously does not work, since openldap does not support UDP, at least not in the Ubuntu package.

Looking around, I found that this is the default behaviour for Windows hosts: they make this netlogon query over UDP and if the server answers, then it becomes the PDC, and the rest of the LDAP communication goes over TCP.

Now my question:
How can I make Samba or something else answer to the netlogon queries?????
Is there a parameter in the smb.conf file or winbind that makes samba listen for those damn queries?


Please, help me in some way: 

It's been 16 hours of work, but there is no way to get out of this mess. I also broke the LDAP installation in a way it is not possible to recover, so I guess I'll have to reinstall the whole system  ](*,)

---

