---
title: "Replace gedit with geany"
date: 2009-11-04
forum: New to Ubuntu
---

### Post by shoaibi on 2009-11-04
Just one short question:
Is there a way that i can replace gedit with geany globally or for atleast my user without opening properties of every file and changing default editor to geany?

Solution:
I tried:
```

alias gedit=geany

```
but for programs that use absolute path binary it didn't work e.g. for most of the programs, so i made a hack:
```

cd /usr/bin
cp gedit gedit.orig
cp geany gedit

```

---

