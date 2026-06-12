---
title: "Installed Opera, Can't Uninstall?"
date: 2009-02-20
forum: New to Ubuntu
---

### Post by Testrum on 2009-02-20
Hello, I just installed Opera wanting to try it out and decided I didn't like. I have tried removing it threw the synaptic package manager and threw Add/Remove programs and I can't seem to find it in either list :???:

---

### Post by davideotape on 2009-02-20
I'm guessing that you downloaded a .deb file from the opera website. If so, all you need to do (I think) is delete that .deb file. Cruft remover should find it for you (System -> Administration -> Cruft Remover)

---

### Post by SpenceMakesSense on 2009-02-20
try 
```
 sudo apt-get autoremove opera
```

---

### Post by Bölvaður on 2009-02-20
or if that doesn't work you may need to use the installer/uninstaller

```
$ sudo dpkg -P opera 
```

---

### Post by Testrum on 2009-02-20
> **SpenceMakesSense said:**
> try 
```
 sudo apt-get autoremove opera
```
Ah, yes this worked. Thanks to both of you.

---

