---
title: "Root file-browser"
date: 2010-02-07
forum: New to Ubuntu
---

### Post by igriego on 2010-02-07
Is there a way to open a root file browser instead of going through the terminal under su?

---

### Post by tom.swartz07 on 2010-02-07
> **igriego said:**
> Is there a way to open a root file browser instead of going through the terminal under su?

Yepper

in a terminal 

```
gksudo nautilus
```

---

### Post by nhasian on 2010-02-07
if you dont want to use the terminal you can press Alt-F2 and then enter the command

```
gksu nautilus
```

---

### Post by 3rdalbum on 2010-02-07
Install the "nautilus-gksu" package in Synaptic Package Manager. The next time you log in, you'll be able to right-click any folder or file and choose "Open as Administrator".

---

### Post by igriego on 2010-02-07
Thanks you all that was great and fast!!

---

### Post by aysiu on 2010-02-07
If you don't want to Alt-F2 or use the terminal every time, you can create a keyboard shortcut or launcher for the command ```
gksudo nautilus
```

---

