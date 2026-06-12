---
title: "installing wine from .tar"
date: 2009-02-01
forum: New to Ubuntu
---

### Post by eldutcho on 2009-02-01
ok time for my new problem of the week.
I'm trying to install one of the development versions of wine, 1.1.12 exactly. I downloaded the .tar file and extracted it to my home folder. However when i go into the folder and click the install file nothing happens. I ran it in the terminal to see a whole bunch of text and then terminal closes. Any suggestions?

---

### Post by x33a on 2009-02-01
first of all, why are you trying to compile it, when there are better alternatives?

if it's out of sheer curiosity, well first extract the tar.gz, then look for a file called install.txt or readme.txt. read, the instructions there and you can proceed with the compilation.

---

### Post by llamakc on 2009-02-01
[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

Searching the forums for "how to compile from source" will also yield several helpful links.

---

### Post by Bölvaður on 2009-02-01
compiling is fun.... I'm boring and thats why I use add/remove

---

### Post by eldutcho on 2009-02-01
this was just a test to attempt to get WoW to work, I was told by someone in the wine forums that they used 1.1.12 to get over a specifc problem. However i suppose 1.1.14 would contain those fixes too (go me..) I had already tried the way the readme told me to install it, nothing happens as well.

---

### Post by yeats on 2009-02-01
so at which point is the installation stalling out?
```
./configure
```

should stop and give you (useful) errors at any missing dependencies.

---

