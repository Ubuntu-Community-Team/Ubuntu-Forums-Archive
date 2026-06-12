---
title: "Gutsy and LDAP, need help"
date: 2007-12-18
forum: Networking &amp; Wireless
---

### Post by indralaily on 2007-12-18
i have ldap server, in my ldap server i have account 'pokemon' this is local account & i add using migration tool into my ldap directory (include uid, password, etc).
The problem is i try to change password for user 'pokemon' from my ldap server (local computer) and success, my new password is 'newpass', i try login
$ ssh pokemon@localhost
i can login with my new password

but when i try login from another computer, say it from computer with IP 192.168.0.70, in this computer, not have local account 'pokemon' so it will contact ldap server. 
First try i login as 'pokemon' and use password 'newpass' i can't login, wrong password, 
second, i try login using 'pokemon' but use my old password, i can login successfully.

how to synchronize password in ldap directory, so when i change my password from ldap server (local computer for my account) it'll update my password in my ldap directory?

i using Ubuntu gutsy (7.10) for my ldap server, sometimes i found 'login timed out after 60 seconds'.
i connect from client using gutsy to

how to fix this

thanks for your help.

---

