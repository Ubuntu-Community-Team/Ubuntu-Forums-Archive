---
title: "change www directory permission"
date: 2011-01-29
forum: New to Ubuntu
---

### Post by maaz4 on 2011-01-29
hi friends
how can i change ' www ' directory permissions in ubuntu ?

HELP PLZ

---

### Post by mikewhatever on 2011-01-29
For the lack of more detailed info, look at 'man chmod' and 'man chown'.

---

### Post by smithr.michael1997 on 2011-01-29
Presumably you want to change the ownership of the directory from root to yourself? In that case run:
```
chown -R <your_username> /var/www/
```
With root level privileges. E.G.
```
sudo chown -R <username> /var/www/
```

---

### Post by 3rdalbum on 2011-01-29
You're going about it the wrong way; the www directory should never need to have its permissions changed from the default.

The www directory is owned by the user account associated with Apache, the web server. Only the Apache user account and root can put or modify files in the 'www' directory. This is by design - it's quite a secure way of running because it allows Apache to run in a limited user account and access only the files it needs, and also prevents other users from modifying internet-facing web pages.

If you want to put files into the 'www' directory, you should open up your file manager as root:

```
gksudo nautilus
```

and put them in there.

Always modify the original version and then copy it to 'www' - never modify the internet-facing version directly. And never change the permissions on any system directory such as 'www' unless you know exactly what you are doing and why.

---

