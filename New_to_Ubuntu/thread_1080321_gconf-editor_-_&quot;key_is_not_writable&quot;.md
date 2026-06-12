---
title: "gconf-editor - &quot;key is not writable&quot;"
date: 2009-02-25
forum: New to Ubuntu
---

### Post by goldgin on 2009-02-25
Hello, this post is a reply to an archived post: 
[http://ubuntuforums.org/showthread.php?t=709460](http://ubuntuforums.org/showthread.php?t=709460)

> **gconf-editor key is not writable**
hi all. well at one point in time i was able to uncheck and check the can_suspend and can_hibernate boxes, but now for some reason i cannot uncheck them and when i try to run gconf-editor as root, (sudo su) i get the following
(gconf-editor:912: GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
any suggestions?


One solution is to edit the main gconf files directly:

```

gksu gedit /etc/gconf/gconf.xml.defaults/%gconf-tree.xml
gksu gedit /etc/gconf/gconf.xml.mandatory/%gconf-tree.xml

```

and make their contents look like this:

```

<?xml version="1.0"?>
<gconf>
</gconf>

```

You can then use gksu gconf-editor to alter defaults and mandatory again ;)

---

### Post by taseedorf on 2009-02-26
try opening it with root permissions

---

### Post by wowoto on 2010-12-24
```
 sudo rm /home/username/.gconf/apps/metacity/general/%gconf.xml 
 sudo rm /home/username/.gconf/apps/metacity/%gconf.xml 

```

---

