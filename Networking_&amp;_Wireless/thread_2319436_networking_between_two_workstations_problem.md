---
title: "networking between two workstations problem"
date: 2016-04-04
forum: Networking &amp; Wireless
---

### Post by bruno_labont on 2016-04-04
I have two workstations with ubuntu 14.04. They are connected through a simple router with an ethernet cable. I can ping both ways with success. 
Samba is installed and I added the following lines to smb.conf : 
workgroup = home
security = user
[share]
comment = ubuntu file server share
path //quad/utilisateur/linux share (witch is the path of one of my computers)
browsable = yes
guest ok = yes
read only = no
create mask = 0755
[homes]
comment = home directorys
browsable = yes
valid users %S

My two computers have the same password but not the same usernames. I can see the home folder when browsing the network but when I'm trying to access the home workgroup icon
ubuntu asks me for the username and password. I then enter my computer username and proper password and It doesn't work, the login window reappears. 
I am recently very deep in linux but it's only been a few mounths, Thanks for any help!

---

### Post by Chuck_McManis on 2016-04-06
You want to use smbpasswd to set up passwords for SMB file access. See smbpasswd(5) and smbpasswd(8)

---

### Post by Morbius1 on 2016-04-06
In addition to smbpasswd I would like to introduce you to what will become your very best friend: a little utility called testparm. You run it this way:
```
testparm -s
```

What you will discover is that to samba this path is jibberish - in fact it will make that share "unavailable":
> path //quad/utilisateur/linux share
And you're missing an "=" here:
> valid users %S

---

