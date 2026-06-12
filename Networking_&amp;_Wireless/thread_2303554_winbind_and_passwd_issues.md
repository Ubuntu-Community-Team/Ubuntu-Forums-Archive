---
title: "winbind and passwd issues"
date: 2015-11-19
forum: Networking &amp; Wireless
---

### Post by mstjohn1974 on 2015-11-19
I successfully configured a Ubuntu 15.10 Workstation to authenticate  against Active Directory the only thing left so far is the ability to  change the Active Directory password. When I enter the command passwd as  logged in Active Directory User I see the following:

_**Case 1:**_
aduser@xenomorph:~$ passwd
Changing password for aduser
(current) NT password: 
passwd: Permission denied
passwd: password unchanged

_**Case 2:**_
aduser@xenomorph:~$ passwd aduser
Changing password for aduser
(current) NT password: 
passwd: Permission denied
passwd: password unchanged

_**Case 3:**_
aduser@xenomorph:~$ passwd DOMAIN\\aduser
Changing password for DOMAIN\aduser
(current) NT password: 
passwd: Permission denied
passwd: password unchanged

In all three situations I receive the following logs (The user name changes but the errors are the same):

Nov 19 12:58:59 xenomorph passwd[5691]: pam_unix(passwd:chauthtok): user "aduser" does not exist in /etc/passwd
Nov 19 12:58:59 xenomorph passwd[5691]: pam_winbind(passwd:chauthtok): getting password (0x0000002a)
Nov 19 12:59:03 xenomorph passwd[5691]: pam_winbind(passwd:chauthtok): user 'aduser' granted access
Nov 19 12:59:03 xenomorph passwd[5691]: pam_unix(passwd:chauthtok): user "aduser" does not exist in /etc/passwd
Nov 19 12:59:03 xenomorph passwd[5691]: pam_winbind(passwd:chauthtok): getting password (0x00000012)

my pam.d file: common-password looks like this one (I removed all comments for better readability):

password   [success=2 default=ignore]   pam_unix.so obscure use_authtok try_first_pass sha512
password   [success=1 default=ignore]   pam_winbind.so use_authtok try_first_pass
password       requisite         pam_deny.so
password       required         pam_permit.so
password       optional         pam_gnome_keyring.so 

I don't have any clue how to solve the issue. Any ideas?

---

