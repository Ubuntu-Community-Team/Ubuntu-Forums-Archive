---
title: "Making samba link up with LDAP or our NT domain"
date: 2007-04-13
forum: Networking &amp; Wireless
---

### Post by CaptSaltyJack on 2007-04-13
I'm running Edgy Server.  I'd like to set it up so that if users in our NT domain go to \\ubuntubox\whatever, they don't need to be set up as a user on that machine, or set up with smbpasswd.  They should get a window on their Windows machine for user/password, and it will accept their NT domain user/pass, and then let them access that share.

The question is, how would user rights work?  How do I allow certain users/groups to access certain samba shares?  I already have the server set up for NT domain authentication.. I can type "id <username>" for any NT user and it finds them.  Do I just do "smbpasswd -a -n <username>" to add a user without a password and it will use their NT password?

Help :)

---

