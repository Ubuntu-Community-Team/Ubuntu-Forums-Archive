---
title: "permission denied when moving files"
date: 2010-07-23
forum: New to Ubuntu
---

### Post by manObject on 2010-07-23
I am a website developer and having previously used the Microsoft Windows way of doing things for many years, I am experiencing growing pains getting to grips with the users, groups and permissions system in Ubuntu. For example I keep getting 'permission denied' errors when I try to move my existing website folder hierarchy (html, php, etc) to \var\www\, which is the document root for the web server, so they have to be in that folder in order to get served. The only way I have so far found to get round this problem without wasting precious time is to log in as root, but clearly this is hardly a good idea for system integrity.
Does someone know a better way? A shell script for moving a batch of files from the home folder to /var/www/ would be ideal, but as a Ubuntu newbie it might take me ages to work out exactly how to do that.

---

### Post by dapperdanny77 on 2010-07-23
i don't see problems moving files as root - it's more important to run the service not as root user - if you have a standard ubuntu apache installation the server runs as www-data user. This means the files you copied should have permissions which enables apache to read it.

for instance:
chown -R www-data /your/data/directory
chmod -R go-rwx /your/data/directory  #this removes all permissions from group and others 

take this as an example for permission settings - other settings could make more sense - depends on your needs ...

---

### Post by Locke_99GS on 2010-07-23
/var/www is owned by root. Use "sudo" temporarily give you root access. Use "sudo su" to temporarily switch yourself to root.

```
sudo mv /home/manObject/html/blah/blah /var/www
```

---

### Post by DrMelon on 2010-07-23
Or if you want a script to move everything from one folder to /var/www:

```

#!/bin/bash
cp /source/of/files/* /var/www/

```

Then save it as movefiles.sh or something memorable, and do:
```

sudo chmod 755 movefiles.sh

```
to enable execution of the script, and then when you want to use it:
```

sudo sh movefiles.sh

```

And that's that!

---

### Post by mapes12 on 2010-07-23
If you want a GUI way.............

Log into your normal account.

In Terminal ```
gksudo nautilus
```will launch the file browser with super user privileges and you should be able to move stuff wherever you like.

Warning - close down the file browser when finished to avoid any accidents and if you delete anything while using nautilus in this way remember to hold down the Shift key when deleting. Otherwise your system will fill up with Trash.

---

### Post by manObject on 2010-07-23
> **Locke_99GS said:**
> /var/www is owned by root. Use "sudo" temporarily give you root access. Use "sudo su" to temporarily switch yourself to root.

```
sudo mv /home/manObject/html/blah/blah /var/www
```

Thanks a lot - I'm getting the idea slowly...

---

### Post by manObject on 2010-07-23
> **mapes12 said:**
> If you want a GUI way.............

Log into your normal account.

In Terminal ```
gksudo nautilus
```will launch the file browser with super user privileges and you should be able to move stuff wherever you like.

Warning - close down the file browser when finished to avoid any accidents and if you delete anything while using nautilus in this way remember to hold down the Shift key when deleting. Otherwise your system will fill up with Trash.

Hey!
That's really neat. I had no idea...

---

### Post by manObject on 2010-07-23
> **DrMelon said:**
> Or if you want a script to move everything from one folder to /var/www:

```

#!/bin/bash
cp /source/of/files/* /var/www/

```Then save it as movefiles.sh or something memorable, and do:
```

sudo chmod 755 movefiles.sh

```to enable execution of the script, and then when you want to use it:
```

sudo sh movefiles.sh

```And that's that!


Great!
Just what the patient ordered!
Many Thanks

---

### Post by manObject on 2010-07-23
> **dapperdanny77 said:**
> i don't see problems moving files as root - it's more important to run the service not as root user - if you have a standard ubuntu apache installation the server runs as www-data user. This means the files you copied should have permissions which enables apache to read it.

for instance:
chown -R www-data /your/data/directory
chmod -R go-rwx /your/data/directory  #this removes all permissions from group and others 

take this as an example for permission settings - other settings could make more sense - depends on your needs ...

Thanks a lot, Dapper; you solved my problem :))

---

