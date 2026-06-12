---
title: "openLDAP/ldap-utils package problems"
date: 2015-05-12
forum: Networking &amp; Wireless
---

### Post by Mike_Cataldo on 2015-05-12
I've got a working installation of openLDAP on 14.04.  I'm able to add and search using ldapadd and ldapsearch after following the Ubuntu posted documentation.  I'm able to login using LDAP credentials.  From every test I can perform I believe I have a working installation of openLDAP.

At the end of the documentation it talks about installing a series of utility scripts that make managing the directory easier.  I cannot get these scripts to run and based on other posts I believe its the line below when setting up ldapscripts.conf.

sudo sh -c "echo -n 'secret' > /etc/ldapscripts/ldapscripts.passwd"

Many posts suggest 'secret' needs to be the encrypted version of the LDAP password.  I've tried various combinations of encrypting the password (using slappasswd) but continue to get the error below in ldapscripts.log

ldap_bind: Invalid credentials (49).

Any help would be greatly appreciated.

---

