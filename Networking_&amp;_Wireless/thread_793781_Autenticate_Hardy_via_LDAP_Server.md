---
title: "Autenticate Hardy via LDAP Server"
date: 2008-05-14
forum: Networking &amp; Wireless
---

### Post by TheSquirrel on 2008-05-14
Hi to all!
I've installed a 64bit HP client with the beautiful Kubuntu Hardy Heron.
I'm looking for a way to autenticate the OS against a LDAP server (yet installed). 
I've found [this tutorial]("http://ubuntuforums.org/showthread.php?p=3668359") (for 7.10) but seems not working with the new distro.

This is the log:
May 13 18:15:22 hp-kubuntu01 sshd[8386]: pam_ldap: reconnecting to LDAP server...
May 13 18:15:22 hp-kubuntu01 sshd[8386]: pam_ldap: ldap_simple_bind Can't contact LDAP server

May 13 18:14:57 hp-kubuntu01 sshd[8386]: PAM unable to dlopen(/lib/security/pam_pwcheck.so)
May 13 18:14:57 hp-kubuntu01 sshd[8386]: PAM [error: /lib/security/pam_pwcheck.so: cannot open shared object file: No such file or directory]
May 13 18:14:57 hp-kubuntu01 sshd[8386]: PAM adding faulty module: /lib/security/pam_pwcheck.so

Please, help me! 
:D

---

