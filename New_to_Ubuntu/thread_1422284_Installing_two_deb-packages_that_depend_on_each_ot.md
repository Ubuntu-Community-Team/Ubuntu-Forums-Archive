---
title: "Installing two deb-packages that depend on each other?"
date: 2010-03-05
forum: New to Ubuntu
---

### Post by auh2o on 2010-03-05
Alright, here's one for you:

I have downloaded two deb-packages. The dependency of one package is the other, and vice versa. If I open either with the Package Installer I get the error message ***Dependency is not satisfiable.*** How do I install these two packages together?

---

### Post by blazemore on 2010-03-05
From the command-line
```
sudo dpkg -i --force-all *.deb
```

---

### Post by auh2o on 2010-03-06
**Thank you! **

Marking as solved.

---

