---
title: "saving environment variables"
date: 2009-02-19
forum: New to Ubuntu
---

### Post by mrcactu5 on 2009-02-19
how do i save environment variables in konsole? or linux in general.  

for that matter, how do i set an environment variables?

for that matter what do environment variables actually do and where are they stored?

in any case, whenever i try to set one, and close konsole, it doesn't remember once i start it up again.  probably something i'm forgetting.

---

### Post by taurus on 2009-02-19
Set them in ~/.bashrc.

---

### Post by mrcactu5 on 2009-02-19
but how do i access a hidden folder?

---

### Post by taurus on 2009-02-19
Open a terminal and run

```
ls -la ~
```

---

### Post by iaculallad on 2009-02-19
> **mrcactu5 said:**
> but how do i access a hidden folder?

While on nautilus, you could press the Ctrl+H combo key to show all hidden files and folders..

Or through terminal:

```
cd ~/.bashrc
```

---

