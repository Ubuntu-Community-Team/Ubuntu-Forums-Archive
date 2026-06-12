---
title: "How do you have apache broadcast my external hard drive instead of /var/www"
date: 2010-05-09
forum: New to Ubuntu
---

### Post by theweasel2345 on 2010-05-09
I have all the things I need on my external hard drive. I would put all the files from my external hard drive to my computer, but my computer is not large enough to store all the files. I have tried to change the DirectoryRoot in the /etc/apache2/sites-available/default but I get an error saying Syntax error on line 8 of /etc/apache2/sites-enabled/000-default: DocumentRoot takes one argument, Root directory of the document tree
Does anyone have any ideas

---

### Post by cariboo on 2010-05-09
Why not make a symlink to your external hard drive, cd into /var/www, then type:

```
sudo ln -s /media/external wwwdocs
```

substitute the proper path and directory name for the example above.

---

