---
title: "Permissions to edit file system"
date: 2008-12-10
forum: New to Ubuntu
---

### Post by olimb on 2008-12-10
When I try to edit
File System/etc/modprobe.d/blacklist 
I get a message
Could not save the file.
You do not have the permissions necessary to save the file.
Question 
How do I get permissions?
Also does it matter which folder is used, blacklist or blacklist-modem
Thanks
olimb

---

### Post by ayoung on 2008-12-10
Issue ```
ls -l
``` from within the ```
/etc/modprobe.d
``` directory.  This will show the owners of the file: first user, then group.  These are ```
root
``` by default for the file in question.  You probably shouldn't change ownership, rather, preface your editing with sudo, e.g., ```
sudo emacs /etc/modprobe.d/blacklist
```.  This will prompt you for your password and grant you permission to edit and save the file in question.

Cheers.

---

### Post by ibuclaw on 2008-12-10
sudo if you are running in the commandline,
```
sudo vi /etc/modprobe.d/blacklist
```
Or gksudo if you are running in GUI.

Press Alt+F2
```
gksudo gedit /etc/modprobe.d/blacklist
```

Regards
Iain

---

### Post by bbright20 on 2008-12-10
> **olimb said:**
> When I try to edit
File System/etc/modprobe.d/blacklist 
I get a message
Could not save the file.
You do not have the permissions necessary to save the file.
Question 
How do I get permissions?
Also does it matter which folder is used, blacklist or blacklist-modem
Thanks
olimb

Force the command using the sudo command.

---

### Post by billgoldberg on 2008-12-10
```
gksudo gedit /etc/modprobe.d/blacklist 
```

---

### Post by sisco311 on 2008-12-10
When you have a little time, please read:

[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

and

[https://help.ubuntu.com/community/FilePermissions]("https://help.ubuntu.com/community/FilePermissions")


by the way, nano is another text edior:
```
sudo nano /etc/modprobe.d/blacklist
```

---

