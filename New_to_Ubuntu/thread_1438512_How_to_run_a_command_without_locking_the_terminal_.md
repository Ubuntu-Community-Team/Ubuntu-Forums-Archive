---
title: "How to run a command without locking the terminal window"
date: 2010-03-25
forum: New to Ubuntu
---

### Post by new_tolinux on 2010-03-25
Hi,

I know there is some command to run a program without the terminal windows waiting for it.
For example: when I run nautilus from the terminal, the terminal now keeps waiting until I close that nautilus window. What I want is to start nautilus and continue to use that terminal window.

I only forgot what command that was. ](*,)

---

### Post by mcduck on 2010-03-25
```
somecommand &
```
..or if you want also to be able to close the terminal window without the program you started closing:
```
nohup somecommand &
```

---

### Post by l.billon on 2010-03-25
Hi!
To run nautilus in background:
```
$ nautilus &
```
works for nearly every application.
You can also ctrl+z to suspend an application while it's running, then
```
$ bg
```
to have it run in background, or ```
$ fg
``` to bring it to foreground.

---

### Post by new_tolinux on 2010-03-25
Thanks, that was wat I'm looking for.

Edit: thanks l.billon also, I'll write it down (may become handy someday later)

---

