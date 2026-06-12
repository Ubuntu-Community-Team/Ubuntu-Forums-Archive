---
title: "When uninstalling programs..."
date: 2010-05-12
forum: New to Ubuntu
---

### Post by completely new on 2010-05-12
...how do I know which extra packages were installed with the particular program? For example, when I installed kdenlive, it came with another 15 packages, however I'm only sure about two of them being related to kdenlive because only they have "kdenlive" in the name, while the others, I presume, are still on my computer. So how do I find and remove them?

---

### Post by semafor on 2010-05-12
Packages like kdenlive requires a lot of software to work. It depends on other software to work.

Often, apt (the package manager) can install software that ends up being without dependencies and use. These can be uninstalled by using the terminal and ```
$ sudo apt-get autoremove
```

The dependencies can be found with the following code
```
$dpkg -s package | grep ^Depends
```

---

