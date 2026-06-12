---
title: "Shell programming"
date: 2010-08-14
forum: New to Ubuntu
---

### Post by kranthikiran on 2010-08-14
[COLOR=Red]t
[/COLOR]

---

### Post by limestone on 2010-08-14
ls -l
shows the file permission, type, last edited, owner, filename

---

### Post by kranthikiran on 2010-08-14
but i dont want file permission

---

### Post by limestone on 2010-08-14
ls -l > filename.txt
this makes a .txt output of the ls command.
If you don't want permissions option do ls -a
otherwise try ls --help for more options

---

### Post by geirha on 2010-08-15
You can do that with GNU find. ```
man find
``` In particular, see the -printf option.

Also see [http://mywiki.wooledge.org/UsingFind](http://mywiki.wooledge.org/UsingFind) on how to use find in general (mostly only covers the portable syntax).

---

