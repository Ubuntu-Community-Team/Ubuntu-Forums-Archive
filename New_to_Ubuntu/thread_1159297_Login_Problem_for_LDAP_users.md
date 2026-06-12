---
title: "Login Problem for LDAP users"
date: 2009-05-14
forum: New to Ubuntu
---

### Post by slyost on 2009-05-14
Just installed Ubuntu 9.04 and setup LDAP and home directories, etc.  Local users can login fine to the Gnome desktop.  However when a LDAP user tries logging on they get the message that **/etc/gdm/Xsession 192 ls: not found** and will not let them logon.  If I login as a local user and su to a LDAP user there is no problem. Authentication occurs, home directoies are mounted, etc.  LDAP users can also login using safe mode.  Please help.

---

### Post by decoherence on 2009-05-14
Which directions did you follow to set it up?

Not exactly an intuitive process, eh?

---

### Post by slyost on 2009-05-14
For the LDAP part I just installed the libnss-ldap and libpam-ldap and answered the questions during install.  
 
I referred to [https://help.ubuntu.com/community/SunLDAPClientAuthentication](https://help.ubuntu.com/community/SunLDAPClientAuthentication)
using the file names on my system instead of ones in the link.  i.e. ldap.conf instead of libnss-ldap.conf.  But actually LDAP was working (tested with getent passwd) after the install so I changed nothing in these files. 
 
For the NFS I referred to [https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo).  After this home directories for LDAP users were automounted correctly (after su into the user that is).
 
Everything seems fine other than not being able to logon LDAP users (other than safe mode).
 
Sam

---

### Post by slyost on 2009-05-15
Found the solution at [http://forums13.itrc.hp.com/service/forums/questionanswer.do?admit=109447627+1242414875820+28353475&threadId=195718](http://forums13.itrc.hp.com/service/forums/questionanswer.do?admit=109447627+1242414875820+28353475&threadId=195718)

Changed the login shell for the user on the LDAP server to /bin/sh and now they can login.

---

