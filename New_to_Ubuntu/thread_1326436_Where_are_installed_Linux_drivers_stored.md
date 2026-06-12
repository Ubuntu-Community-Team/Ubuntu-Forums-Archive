---
title: "Where are installed Linux drivers stored?"
date: 2009-11-14
forum: New to Ubuntu
---

### Post by Dullstar on 2009-11-14
Trying to find where they are stored so I can get hardware that Ubuntu supports to work on slightly older releases of other distributions.

---

### Post by falconindy on 2009-11-14
Modules are in /lib/modules/`uname -r`/.

Installing drivers isn't as simple as copying them over to an old install and referencing them. The kernel needs to be aware of them as well.

---

### Post by dzon65 on 2009-11-14
Indeed.You have to be really carefull when doing this.You might wanna check for upgrading your kernel as well before installing drivers.

---

