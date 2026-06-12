---
title: "edit smb.conf - permissions?"
date: 2009-03-19
forum: New to Ubuntu
---

### Post by aquascrotum on 2009-03-19
Have just got my 1st Ubuntu 8.10 install up and running and am trying to share a media folder stored on an external HDD.

I installed the file sharing app but get the following message........

'net usershare' returned error 255: net usershare add: cannot share path /media/HD-CEU2/Media as we are restricted to only sharing directories we own.
	Ask the administrator to add the line "usershare owner only = False" 
	to the [global] section of the smb.conf to allow this.

I'm a complete noob - I located the smb.conf file and but now I'm unable to save the changes.

How do I save the change to the smb.conf file?

---

### Post by kanikilu on 2009-03-19
You need to edit the conf file as root, one way to do that is:

```
gksudo gedit /etc/samba/smb.conf
```

---

### Post by aquascrotum on 2009-03-19
Thanks - solved the editing the smb.conf file but I'm still getting the same error message when trying to share the folder.

Have I inserted the line properly in the file? All I've put in is 

# usershare owner only = False

under the Global section.

---

### Post by aquascrotum on 2009-03-19
Ignore - sorted.

---

