---
title: "make dvd shrink executable"
date: 2011-06-18
forum: New to Ubuntu
---

### Post by telltom on 2011-06-18
Hi folks,
i'm trying to run a program called dvdshrink in wine but i don't know how to make it executable in Xubuntu 10.10. If i right click on the file the choice is not there. thanks

---

### Post by TeoBigusGeekus on 2011-06-18
No need for it. Just run
```
wine /path/file.exe
```
As far as linux is concerned, the file is not executed; wine is.

---

### Post by sandyd on 2011-06-18
> **telltom said:**
> Hi folks,
i'm trying to run a program called dvdshrink in wine but i don't know how to make it executable in Xubuntu 10.10. If i right click on the file the choice is not there. thanks
Right click, properties -> permissions.
I don't know about XFCE, so if that isn't an option, do 
```

chmod +x /path/to/file

```
> **TeoBigusGeekus said:**
> No need for it. Just run
```
wine /path/file.exe
```
As far as linux is concerned, the file is not executed; wine is.
WINE needs executable premissions to run an exe program.

---

### Post by TeoBigusGeekus on 2011-06-18
> **sandyd said:**
> 
WINE needs executable premissions to run an exe program.
I didn't know that (haven't used wine for a long time). Thanks for the info.

---

### Post by LowSky on 2011-06-18
> **TeoBigusGeekus said:**
> I didn't know that (haven't used wine for a long time). Thanks for the info.

Its some stupid new annoyance. Makes running Windows applications more of a chore.

---

