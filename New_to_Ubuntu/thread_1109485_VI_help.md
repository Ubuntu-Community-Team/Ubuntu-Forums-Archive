---
title: "VI help"
date: 2009-03-28
forum: New to Ubuntu
---

### Post by eddski on 2009-03-28
I'm playing around with vi on a practice file, and I was the delete command and then retrieve command ( "3p ) and i get an error reading " E353 nothing in register 3". This is after I deleted 8 different lines/chars. Any suggestions as to what I'm doing wrong?

---

### Post by fly-by-night on 2009-03-28
Try the programming section.

[http://ubuntuforums.org/forumdisplay.php?f=310](http://ubuntuforums.org/forumdisplay.php?f=310)

---

### Post by bzhao on 2009-05-23
use command at your home dir:
 ls -ld .vim*
make sure the owner and permissions of the listed file are right.

Bill Z

---

### Post by mvalviar on 2009-05-23
> **eddski said:**
> I'm playing around with vi on a practice file, and I was the delete command and then retrieve command ( "3p ) and i get an error reading " E353 nothing in register 3". This is after I deleted 8 different lines/chars. Any suggestions as to what I'm doing wrong?

Note that when you delete(vim term for cut) lines or chars they are stored in the automatic registers 0-9 to view the contents of the auto registers (and others) use ":registers <Enter>"

Perhaps this is the 1st time you deleted a section of text and the only available register is register '0'.

---

