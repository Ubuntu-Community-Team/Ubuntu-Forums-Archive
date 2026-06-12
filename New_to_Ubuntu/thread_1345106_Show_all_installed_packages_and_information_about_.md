---
title: "Show all installed packages and information about them"
date: 2009-12-03
forum: New to Ubuntu
---

### Post by daffy_dowden on 2009-12-03
I know that running the command:

dpkg --get-selections 

lists all of the packages installed on my server, but is it possible to return a sentence or a paragraph for each of the installed packages, so I know what each of them does? Perhaps their man page would suffice.

Thanks,
Daf

---

### Post by Cheesemill on 2009-12-03
Try:
```
aptitude search ~i
```

---

### Post by daffy_dowden on 2009-12-04
Thanks Cheesemill, this is just what I'm after. I presume ~i is some kind of search for packages that are installed. 

Though is it possible to change the number of characters printed off? 

Daf

---

