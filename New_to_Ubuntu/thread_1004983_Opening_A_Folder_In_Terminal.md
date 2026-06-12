---
title: "Opening A Folder In Terminal"
date: 2008-12-07
forum: New to Ubuntu
---

### Post by Lieske on 2008-12-07
I was wondering if it's possible to open a folder from Terminal. Right now I'm in a certain directory in Terminal, and I want to open the actual folder so I can browse through it, but I can't find a way to get to it without the use of Terminal.

---

### Post by taurus on 2008-12-07
If you want to change to a directory, just use the cd command.  Assuming the name of the directory is called Desktop (by the way, desktop is not the same as Desktop since Unix is case sensitive), you would run

```
cd Desktop
```
And if you want the listing of all files/directories in there, just run

```
ls -la
```

---

### Post by snova on 2008-12-07
```
nautilus .
```

To open Nautilus in the current directory, or

```
nautilus directory/name
```

To open it anywhere at all.

---

### Post by pyromanic123boom on 2008-12-07
open a folder from the terminal:

$ nautilus /directory/here

---

### Post by Lieske on 2008-12-07
Snova, I tried using the nautilus command, and it opened my home folder, not the directory I was in.

---

### Post by snova on 2008-12-07
It works when I test it. Perhaps you missed the dot? There's a period following 'nautilus', which represents the current directory. Otherwise, Nautilus will start in its default location, which would be your home directory.

---

