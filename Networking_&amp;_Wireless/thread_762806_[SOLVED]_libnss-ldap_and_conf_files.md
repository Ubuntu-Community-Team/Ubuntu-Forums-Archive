---
title: "[SOLVED] libnss-ldap and conf files"
date: 2008-04-22
forum: Networking &amp; Wireless
---

### Post by WeyOh on 2008-04-22
Hi,

I tried on HardyRC to install libnss-ldap following the instructions on this howto [https://help.ubuntu.com/community/LDAPClientAuthentication](https://help.ubuntu.com/community/LDAPClientAuthentication) but when I install it it doesn't create the file /etc/libnss-ldap.conf. The same happens with libpam-ldap (/etc/pam_ldap.conf). Does anyone know where the conf file is, do I have to create it manually?

Cheers,

Sam

---

### Post by klinibm on 2008-07-16
I'm experiencing the same problem.  Any guidance will be much appreciated.

  -Sam

---

### Post by WeyOh on 2008-07-17
Hey klinibm,

I've found out that these files have ceased to exist. The configuration details are now in /etc/ldap.conf and /etc/ldap/ldap.conf. That guide should really be updated! *hint*

Hope this helps.

Sam

---

### Post by dmaf on 2010-08-24
just copy /etc/ldap.conf and rename to /etc/libnss-ldap.conf
i've try, and successfully..:D

read also : [http://ldots.org/ldap/](http://ldots.org/ldap/)
Hope this help..

---

