---
title: "LDAP non-local users cannot log on"
date: 2007-11-09
forum: Networking &amp; Wireless
---

### Post by linuxsurfer on 2007-11-09
We have a SUN ldap server that I have set up a Gutsy box to login to, by this howto: [https://help.ubuntu.com/community/LDAPClientAuthentication](https://help.ubuntu.com/community/LDAPClientAuthentication)

It is able to authenticate users, but when I try to login from GDM as an LDAP user I get this message: "Cannot set your user group; you will not be able to log in. Please contact your system administrator."

I have searched and searched, and nobody seems to know why this would happen. Oddly enough, the one user that is a local user (jdoe) IS able to log into the system using the ldap username/password. But this is the only one that works. 

I have already set up libpam-ldap to automatically create the home directories via the above howto; I don't know if that is the issue or not. Any ideas?

---

### Post by alfonsograna on 2008-02-26
> **linuxsurfer said:**
> We have a SUN ldap server that I have set up a Gutsy box to login to, by this howto: [https://help.ubuntu.com/community/LDAPClientAuthentication](https://help.ubuntu.com/community/LDAPClientAuthentication)

It is able to authenticate users, but when I try to login from GDM as an LDAP user I get this message: "Cannot set your user group; you will not be able to log in. Please contact your system administrator."

I have searched and searched, and nobody seems to know why this would happen. Oddly enough, the one user that is a local user (jdoe) IS able to log into the system using the ldap username/password. But this is the only one that works. 

I have already set up libpam-ldap to automatically create the home directories via the above howto; I don't know if that is the issue or not. Any ideas?

Same problem any ones how to start with this issue

---

### Post by jglj on 2008-05-12
Had the same initial problem; but the problem vanished when using a NFS-mounted /home (in my case exported fra the LDAP-server itself as a test).
I'm trying to make the local /home avaiable to the users since I have a lot of users using cached name service directory.

---

