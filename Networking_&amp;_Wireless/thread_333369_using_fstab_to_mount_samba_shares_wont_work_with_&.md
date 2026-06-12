---
title: "using fstab to mount samba shares wont work with &quot;.smbcredentials&quot;"
date: 2007-01-07
forum: Networking &amp; Wireless
---

### Post by Hefeweiz3n on 2007-01-07
Hi,

I have a problem with samba shares that i want to mount from my win2k3 server.
This should happen everytime i boot, so i editet fstab accordingly.

So now i have multiple entries that all look like
```
//<ip>/<share> /mnt/<mount> smbfs credentials=<homedir>/.smbcredentials,iocharset=iso8859-15,codepage=cp850,dir_mode=0777  0 0
```
With "mount -all" i get the following errormessage:
```
6069: session setup failed: ERRDOS - ERRnoaccess (Access denied.)
SMB connection failed

```
So i changed the entries to using username and password
```
//<ip>/<share> /mnt/<mount> smbfs username=xxx,password=yyy,iocharset=iso8859-15,codepage=cp850,dir_mode=0777  0 0
```
Now that works, but for obvious Securityreasons i dont actually wanna shout my password out to the world which is why i want to use credentials-file.

The credentials-file is also set up correctly, it is the same as from my old ubuntu, where all of the above worked fine.

Does anyone have a plausible reason for all this and/or a solution?

It would help me a lot.

---

### Post by Hefeweiz3n on 2007-01-10
Doesnt anyone have an idea?

---

### Post by Iowan on 2007-01-10
[http://www.ubuntuforums.org/showthread.php?t=288534](http://www.ubuntuforums.org/showthread.php?t=288534)
This format looks similar (cifs vs smbfs)... The **<homedir>** is kosher?

---

