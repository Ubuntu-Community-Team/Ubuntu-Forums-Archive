---
title: "Sbf_Flash"
date: 2010-09-17
forum: New to Ubuntu
---

### Post by Captainflowers91 on 2010-09-17
Ok, so I've been trying to install sbf_flash to root my droid into Ubuntu and so far no luck. I've downloaded the application from 

[http://blog.opticaldelusion.org/2010/07/new-sbfflash-features.html#more](http://blog.opticaldelusion.org/2010/07/new-sbfflash-features.html#more)

then created a new directory and put the file in that. The problem is, I have to idea how to install and run the program. I know this is a novice problem, but I've always installed things through terminal promts, never this way.

---

### Post by kybKenny on 2011-01-05
Hmm, the question is somewhat outdated, but for future reference:

you make the file executable with: ```
$ chmod o+x ./sbf_flash
``` (./ thereby referencing to the current directory/folder)

then you run it by calling it directly:

```
$ sudo ./sbf_flash
```

all this happens in a terminal (as indicated by the "$")

why the "./" ? Because calling a program without a path to it will need that program to be in a directory that's listed in an environment variable called $PATH. Unlike in DOS, the current directory is normally not part of $PATH in Linux.

---

### Post by trestevenson on 2011-07-17
> **kybKenny said:**
> Hmm, the question is somewhat outdated, but for future reference:

you make the file executable with: ```
$ chmod o+x ./sbf_flash
``` (./ thereby referencing to the current directory/folder)

then you run it by calling it directly:

```
$ sudo ./sbf_flash
```

all this happens in a terminal (as indicated by the "$")

why the "./" ? Because calling a program without a path to it will need that program to be in a directory that's listed in an environment variable called $PATH. Unlike in DOS, the current directory is normally not part of $PATH in Linux.

Thanks for this!

---

