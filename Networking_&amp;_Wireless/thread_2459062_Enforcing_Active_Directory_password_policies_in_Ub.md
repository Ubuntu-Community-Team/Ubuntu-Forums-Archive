---
title: "Enforcing Active Directory password policies in Ubuntu 20.04"
date: 2021-03-10
forum: Networking &amp; Wireless
---

### Post by thinkpad770x on 2021-03-10
I have setup a test lab for Ubuntu 20.04 which authenticates against active directory. I have created 2 potential setups. One setup is bound via winbind. The other uses sssd. When I set the password of a user account to be reset on next logon Im still able to logon to ubuntu in either case without resetting the AD password. Ubuntu tells me the password has expired but then continues the logon process. Is there a way to prvent logon when the AD password has expired? Better yet is there a way to force the password change on the logon screen similar to Windows?

---

### Post by TheFu on 2021-03-10
The Unix way is to use PAM settings for many login controls.
  
No clue about AD. Sorry. We don't use it.
But normal POSIX LDAP [https://serverfault.com/questions/735793/how-to-force-ldap-user-to-change-password-at-first-login](https://serverfault.com/questions/735793/how-to-force-ldap-user-to-change-password-at-first-login)
[https://manpages.ubuntu.com/manpages/focal/man1/ldappasswd.1.html](https://manpages.ubuntu.com/manpages/focal/man1/ldappasswd.1.html)

[https://help.ubuntu.com/community/ActiveDirectoryHowto](https://help.ubuntu.com/community/ActiveDirectoryHowto) You've probably already seen that.

ssh logins with keys bypass this, so beware.  Most of my logins to systems use ssh-keys, never passwords.  Only new ssh connections would check the passwd entry for a locked account. That entry can be in the local db or ldap or nis+ or nis. PAM would need to be setup to use ldap.  AD is some kind of LDAP, right?

---

### Post by thinkpad770x on 2021-03-11
Yes Microsoft Active Directory uses Kerberos LDAP authentication

---

### Post by thinkpad770x on 2021-03-11
Everything looks correct and Authentication works flawlessly. It looks like the AD password requirements are being picked up as well. Heck I can even change the AD password from the terminal using passwd DOMAIN//username. It seems strange that Im unable to change the password upon the logon screen when in Windows active directory I set a temp password with "change password upon next logon" option selected. Seems there is a piece missing int he puzzle

---

