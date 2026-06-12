---
title: "Apache2 error 404 file not found"
date: 2009-10-16
forum: New to Ubuntu
---

### Post by adrenalin6 on 2009-10-16
I edited the files so the root is /home/adrenalin6/www and it opens the index.html file. But when I tell it to go to another directory it cant find it. for example, ```
 /home/adrenalin6/www/cgi-bin/cutecast
``` then its lost. Its not lost at the cgi-bin directory, its stuck at the cutecast directory. Any help would be appreciated.

- Henry

---

### Post by adrenalin6 on 2009-10-17
> **adrenalin6 said:**
> I edited the files so the root is /home/adrenalin6/www and it opens the index.html file. But when I tell it to go to another directory it cant find it. for example, ```
 /home/adrenalin6/www/cgi-bin/cutecast
``` then its lost. Its not lost at the cgi-bin directory, its stuck at the cutecast directory. Any help would be appreciated.

- Henry

I moved the cutecast folder and it finds it. now its not executing the perl script or the cgi. When i direct it to it, its gives me a the open,save option to it.

---

### Post by OpenGuard on 2009-10-17
Perl scripts should be executable:

```
sudo chmod +x script.pl

```

---

