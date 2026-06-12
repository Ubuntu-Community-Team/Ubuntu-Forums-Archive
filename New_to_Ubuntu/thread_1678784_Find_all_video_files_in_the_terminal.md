---
title: "Find all video files in the terminal"
date: 2011-01-31
forum: New to Ubuntu
---

### Post by oldmankit on 2011-01-31
An easy question I am sure.

How do I find ALL movie files in a current directory and all subdirectories? e.g.  .mov, .avi, .mp4

I am trying all kinds of things like ```
find ./ -iname '*mov'
``` but can't find a way to get all of the different types with one command.

---

### Post by Vaphell on 2011-01-31
```
find . -iname '*.txt' -or -iname '*.py' -or -iname '*.sh'
```

you can use more elaborate conditions with -not (!), -and (-a) and -or (-o)

---

### Post by oldmankit on 2011-01-31
> **Vaphell said:**
> ```
find . -iname '*.txt' -or -iname '*.py' -or -iname '*.sh'
```you can use more elaborate conditions with -not (!), -and (-a) and -or (-o)

Thank you!  I'm glad it's so simple! :KS

---

