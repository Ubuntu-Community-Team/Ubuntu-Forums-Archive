---
title: "Samba Sharing - The Easy Way - Not Read Only"
date: 2007-04-24
forum: Networking &amp; Wireless
---

### Post by verevi on 2007-04-24
Sharing using the right-click sharing dialog works... however, if I un-choose the Read-Only check box, I still cannot write to the shared directory from another Ubuntu machine.  

Is this a design flaw, or a user flaw?  :)

Thanks for any thoughts....

---

### Post by bnuytten on 2007-04-24
User flaw. And you can take that literally:) 

There are two levels of security. One is the "samba" level, the second is the file system level. Say you logon to a samba share with a user called smbuser. That user is also a local system user. You can browse a share, BUT if the local user smbuser does not the rights to read/write that directory it will not be able... It's completely logically but often overlooked.

So check the directory ownership and access rights on the samba server with ls -l. You can off course do a samba logon as root :evil: so you have access to all files. Use chown to change ownership and chmod to change permissions.

---

### Post by verevi on 2007-04-24
I can, indeed, write if I chmod 777.  The user that writes is "nobody".  If I try to login using smb://myname@myserver, then my password does not work.  What is the most straight-forward way to get me logged in as the right user so that I don't have to change my permissions to so unrestrictive?

After reading a bit on the topic, it seems like I should use "user" level security and add such users using smbpasswd.  

Is there not a more GUI way to do this?

Thanks for the help.

**EDIT:**  Ok, I just added a user using smbpasswd -a username.  This works like a charm.  I almost wish this was automatically done when users are created.   Thanks for the help.

---

### Post by bnuytten on 2007-04-26
> **verevi said:**
> Is there not a more GUI way to do this?

Dunno if there is a user interface for this. There is one for system users System > Adminsitration > Users and Groups though. There are some interfaces to manage MySQL users too (mysqladmin). There is none for Apache users that I know of. So if you have time to spare, feel free ;-)

---

### Post by eldragon on 2007-05-10
so how do i know with which user im starting the samba server......

im completely lost, so, should i add to my users the user 'smbuser' and add it to my user's group?

---

### Post by bnuytten on 2007-05-10
> **eldragon said:**
> so how do i know with which user im starting the samba server......

im completely lost, so, should i add to my users the user 'smbuser' and add it to my user's group?

You're definitely confused ;-) I tried to make something meaningful out of your question but... I'll give you some facts, maybe this helps.

First off all, you start and stop the samba services (/etc/init.d/samba) using superuser (root) privileges. This is true for almost all services anyway. Once the samba services are started and you log in, you  have two options. You do not supply a user/pass (or a wrong combination) or you do supply a correct username and password. In the first case, you will be mapped onto the **system user** "nobody". In the latter case, you will be mapped onto the **samba user and system user** that has the same username you used to logon.

I'll give you an example. You created a share with the name "files". So you can access your files using \\127.0.0.1\files. Say you have a local user called "linus" which you use to login via ssh or on the local machine or whatever. You can set the password for **system user** linus with the passwd command. Say it has been set to "syspass". If you want to allow that user to access samba shares, you have to add it to the **samba users** using smbpasswd. E.g.:
```
smbpasswd -a linus
```
The password does not need to be the same, say it is "smbpass". If you configured you smb.conf in a suitable way, you will be able to access the "files" share with username "linus" and password "smbpass". Note that the system password does not come into play.

A common caveat: the directory has the following file access.
```
drwxrwxr-x   2 root  root   4096 2007-05-10 19:50 files
```
Than you will be able to read the contents of the folder but you will not be able to create or change files. Remember you have been mapped to system user "linus" which does not belong to the group "root" and is not equal to the user "root" so the "r-x" part of the file permissions are in effect. You may want to check out ```
man chown
man chmod
```

---

### Post by eldragon on 2007-05-10
ok, then im not that off....
ive created a user called 'user' with a blank password......
```

sudo smbpasswd -a user

```

ive added that user to my user group (who owns all i need to share)
used the gui so i cant give the command here :(

from the winxp machine, ive been trying to acces my smb shares, which are read/write shared....and yet i cant write there.

my smb.conf is supposedly well configured (read the wiki for that)

---

### Post by bnuytten on 2007-05-10
> **eldragon said:**
> ok, then im not that off....
ive created a user called 'user' with a blank password......
```

sudo smbpasswd -a user

```

ive added that user to my user group (who owns all i need to share)
used the gui so i cant give the command here :(

from the winxp machine, ive been trying to acces my smb shares, which are read/write shared....and yet i cant write there.

my smb.conf is supposedly well configured (read the wiki for that)

Make sure you use a username and password in windows. "Map user" than enter "Use different username/pass" or something like that. If in doubt about user/pass or something, try mounting the share from your Ubuntu box using smbclient.

---

### Post by eldragon on 2007-05-11
> **bnuytten said:**
> Make sure you use a username and password in windows. "Map user" than enter "Use different username/pass" or something like that. If in doubt about user/pass or something, try mounting the share from your Ubuntu box using smbclient.

i might be missing something....

im actually using an account called 'user' in windows, with a blank password.....same goes with  smbpasswd

EDIT:
after reading a bit more, i found out i needed to add the samba user to my group, and then add group RW permissions to folders being shared....

thanks for the help
EOEDIT

---

### Post by bnuytten on 2007-05-12
> **eldragon said:**
> i might be missing something....

im actually using an account called 'user' in windows, with a blank password.....same goes with  smbpasswd

EDIT:
after reading a bit more, i found out i needed to add the samba user to my group, and then add group RW permissions to folders being shared....

thanks for the help
EOEDIT

Great you found it yourself :-) Once you are logged in you need of course correct file permissions (see above).

---

