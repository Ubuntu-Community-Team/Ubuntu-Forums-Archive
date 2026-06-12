---
title: "What is the default Samba user for Gutsy Gibbon so Windows users can see file shares?"
date: 2007-10-30
forum: Networking &amp; Wireless
---

### Post by Yfrwlf on 2007-10-30
Pretty much what the topic subject says.  On a fresh Gutsy install, you can share out folders for other Gutsy users, and they can access them without getting a user name and password prompt.  Windows machines, however, (even though those are quickly diminishing in numbers where I live) are prompted with a user name and password, so my question is (hopefully) simple..

What is Gusty's default Samba user name that is being used to access other Gutsy shares?  When Gutsy accesses the Windows shares, it shows up in Windows as user "GUEST".  When the Windows computer tries to access Gutsy shares, GUEST does not work for the user name with the password blank, or GUEST, or guest, or ubuntu, nothing I've tried works.  I also tried using nobody for the name.

After doing a```
sudo pdbedit -L -w
```I got a huge list of users (which of most were also system users), but there is no user that is obviously what Samba uses.

I know how to create another Samba user by doing```
smbpasswd -a user
```and such, but does anyone know what the *default* user is?  There has to be one if I'm able to have Gutsy shares access one another, right?

Any help would be greatly appreciated, thank you. :)

---

