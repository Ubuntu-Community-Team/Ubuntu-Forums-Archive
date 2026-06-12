---
title: "Uninstalling LDAP from source"
date: 2005-10-05
forum: Networking &amp; Wireless
---

### Post by Elijah on 2005-10-05
I sorta messed up our current install of ldap and would like to rebuild the source again, but I can' t uninstall it with 'make uninstall'

root@server01:/home/admin/openldap-2.2.26 # make uninstall
make: *** No rule to make target `uninstall'.  Stop.

maybe I'll try apt-getting that slapd package instead ... but I needed to remove the source binaries from /usr/local/ first ... trouble is I might remove some things that I'm not supposed to ... can anyone help me out?

---

### Post by cwaldbieser on 2005-10-05
[QUOTE=Elijah]I sorta messed up our current install of ldap and would like to rebuild the source again, but I can' t uninstall it with 'make uninstall'
root@server01:/home/admin/openldap-2.2.26 # make uninstall
make: *** No rule to make target `uninstall'.  Stop.
maybe I'll try apt-getting that slapd package instead ... but I needed to remove the source binaries from /usr/local/ first ... trouble is I might remove some things that I'm not supposed to ... can anyone help me out?[/QUOTE]
Maybe you could try making it again with "checkinstall".  Then you could just remove the .deb it creates and it should remove all the files it installed.

---

