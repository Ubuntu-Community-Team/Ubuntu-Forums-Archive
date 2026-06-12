---
title: "ls with a wildcard but without directory  recursion"
date: 2011-04-18
forum: New to Ubuntu
---

### Post by Contrarian on 2011-04-18
If I do "ls -alh" it returns the current directory.  If I do "ls -alh f*" it does a wild card search, but searches the current directory recursively.

Am I able to prevent the recursive search?  I just want to search the contents of the current directory for all files that match a current wild card search (in this case, anything that starts with the letter 'f').

---

### Post by erind on 2011-04-18
Try **ls** with **-d** option.

```
ls -lhd f*
```

---

### Post by bodhi.zazen on 2011-04-18
Just to point out additional tools, depending on your needs, you can use grep or find

ls -lAh | grep -e '^f'

find . -maxdepth 1 -type f -name 'f*'

---

