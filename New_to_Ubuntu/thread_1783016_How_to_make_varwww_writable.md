---
title: "How to make /var/www/ writable?"
date: 2011-06-15
forum: New to Ubuntu
---

### Post by kramer65 on 2011-06-15
Hello,

I just installed a lamp server on my 10.04 desktop. Server files should be in /var/www/ but I have no normal rights to put any file in there, which is quite annoying when I simply want to put file in and out of that folder to test things out.

Any help how I can do that? Would that be dangerous for the safety of my basic Ubuntu installation? I just need the server for testing purposes and I will not use it as an actual server to run a live website on..

---

### Post by jake.anq on 2011-06-15
Hi

Use these commands:
```
$sudo chmod 765 -R /var/www/
$sudo chown <username> /var/www/
$sudo chgrp <usergroup> /var/www/
```
Replace <username> with your user name and <usergroup> with your group (this will probably be the same as your username).

---

### Post by Grenage on 2011-06-15
you can list permissions with a command such as:

```
ls -l /var/www
```

If you want (for testing purposes) to change ownership or permissions, then consider using *chown* or *chmod*.  For example, the following command would allow full access for everyone:

```
sudo chmod -R 777 /var/www
```

The -R makes the command recursive.  Obviously the above would never be used in a production environment; you could also simply move the file as root:

```
sudo mv xxx /var/www/
```

---

### Post by kramer65 on 2011-06-15
great! Thanks to you both!

---

