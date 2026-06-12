---
title: "Cannot cd to a folder with $ in the name."
date: 2011-01-18
forum: New to Ubuntu
---

### Post by palantir6er on 2011-01-18
I am trying to use the terminal to move to a directory called $bin
I can open the folder with nautilus but when I try it from the command line,
cd $bin
cd /$bin/

both move me back to my main directory. I am in the parent directory when I issue either of these commands.

How can I navigate inside and does $ have a special meaning to bash (I suspect it does)??

---

### Post by mc4man on 2011-01-18
Probably a poor idea to have $ in a dir. name.
if you must cd to it then use '' around either the path and dir. name or just dir. name
 '$bin'

---

### Post by Joeb454 on 2011-01-18
mc4man is probably right about having $ in your directory names.

An alternative option to encasing your directory in quotes would be to escape it, so something like ```
cd /\$bin/
```

---

### Post by palantir6er on 2011-01-18
Its a directory from some old Fortran code so perhaps the original authors had a reason.

Anyway, single quotes seem to work. Thanks!

---

