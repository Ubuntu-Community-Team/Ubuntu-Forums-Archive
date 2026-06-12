---
title: "how to view permission status of my folders?"
date: 2009-07-05
forum: New to Ubuntu
---

### Post by heyyy on 2009-07-05
im just curious 
also is there a simple easy to use guide to introduce me to linux without "experimenting" too much with my system?

---

### Post by l-x-l on 2009-07-05
to check permissions.. right click on a folder in Nautilus, then go to properties & select the "permissions" tab.

---

### Post by credobyte on 2009-07-05
```
cd $HOME
ls -l

```

You'll see something like this :
```
**[COLOR=Red]drwxr-xr-x[/COLOR] 4 dainis dainis**  4096 2009-07-05 03:48 Bildes
**[COLOR=Red]drwxr-xr-x[/COLOR] 2 dainis dainis**  4096 2009-07-05 20:13 Desktop
**[COLOR=Red]drwxr-xr-x[/COLOR] 2 dainis dainis**  4096 2009-07-05 18:39 Filmas
**[COLOR=Red]drwxr-xr-x[/COLOR] 2 dainis dainis**  4096 2009-07-05 03:48 Gr&#257;matas

```

---

