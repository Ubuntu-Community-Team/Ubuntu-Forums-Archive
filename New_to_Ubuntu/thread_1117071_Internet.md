---
title: "Internet"
date: 2009-04-05
forum: New to Ubuntu
---

### Post by Y2L on 2009-04-05
How do I find o Ubuntu what type of wireless internet card I have?

---

### Post by Chemical Imbalance on 2009-04-05
open up Terminal (under Accessories):

lspci

---

### Post by Y2L on 2009-04-05
when I do that it says comman not found any idea why?

---

### Post by The Cog on 2009-04-05
I'm sure that command is part of the standard install. To double-check, it's teh lower-case version of LSPCI - right? If it's missing, you should perhaps reinstall. Although lshw (lower-case LSHW) will also tell you, in great detail.

---

### Post by Chemical Imbalance on 2009-04-05
> **Y2L said:**
> when I do that it says comman not found any idea why?

copy and paste this into your terminal to make sure you have it spelled right:

```
lspci
```

---

### Post by asmoore82 on 2009-04-06
you will probably like the graphical `lshw` - it's `lshw-gtk` and it's in the repos
```
sudo apt-get install lshw-gtk
```

It will show up in the menus at "System -> Preferences -> Hardware Lister"
but to run it with full access,
you could Alt+F2 and
```
gksudo lshw-gtk
```

---

### Post by JoshuaRL on 2009-04-06
"lspci" is a standard Linux command.  Are you having any other issues or problems?  Did you have anything break recently?  On every version of Linux I've tried (and especially Ubuntu) it's been there.

---

