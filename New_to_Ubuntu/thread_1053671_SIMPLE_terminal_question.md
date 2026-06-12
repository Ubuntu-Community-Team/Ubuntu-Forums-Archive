---
title: "SIMPLE terminal question"
date: 2009-01-28
forum: New to Ubuntu
---

### Post by brandon82 on 2009-01-28
Can someone please tell my why  the bashrc shows up when using the command ls --all but not simply using ls? (im very new) 
Thanks

---

### Post by zabien1970 on 2009-01-28
try man ls

---

### Post by Dr Small on 2009-01-28
Because your .bashrc file is hidden (with the dot), so running `ls -a` will show "all" files.

---

### Post by brandon82 on 2009-01-28
i should have done that before posting.. problem solved. Thanks! !

---

### Post by sisco311 on 2009-01-28
> **zabien1970 said:**
> try man ls

+1

Hidden files are not listed by default.
In your file manager you have to press Ctrl+H, in the shell you have to use the -a flag. :)
[quote=man ls] -a, --all
              do not ignore entries starting with .
[/quote];)

---

