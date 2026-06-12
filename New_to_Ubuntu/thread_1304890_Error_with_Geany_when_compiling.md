---
title: "Error with Geany when compiling"
date: 2009-10-29
forum: New to Ubuntu
---

### Post by SpinningAround on 2009-10-29
Remove please, solved it. Installed java jdk

---

### Post by blazemore on 2009-10-29
For reference:

If you have the Source repositories enabled, you can use the command
```
sudo apt-get build-dep **packagename**
```

That will download the dependencies for building the version in the repo. However, the version from the svn or website is likely to be a later version, so watch out. It's still a good place to start.

---

