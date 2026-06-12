---
title: "How to show one page at a time in Terminal for long strings..."
date: 2010-06-29
forum: New to Ubuntu
---

### Post by onthefence on 2010-06-29
In a DOS terminal, there was a way to display one screen at a time when asking for a list of directories or something. I can't remember what it is, but does anyone know the equivalent in linux terminal?

Specifically, I am working with Parted. It may be a special command specific to that app. But I'm willing to try things. I can't scroll back up, so need to show one page at a time.

Thanks!

---

### Post by da burger on 2010-06-29
Pipe the output of the command to either less or more (both do similar jobs in slightly different ways).
```
command | less
```
```
command | more
```

less allows you to scroll from within even a non-scrollable terminal, more prints a page then you press enter to bring up every line after that.

---

### Post by onthefence on 2010-06-29
awesome! Thanks!

---

### Post by da burger on 2010-06-29
No problem. Please mark this thread solved.

Angus

---

### Post by oldos2er on 2010-06-29
Shift-PgUp and Shift PgDn also work in terminal or tty.

---

