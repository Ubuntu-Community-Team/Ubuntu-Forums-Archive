---
title: "How to download programs that terminal can't find"
date: 2008-12-08
forum: New to Ubuntu
---

### Post by tegnoto89 on 2008-12-08
If the terminal says "no such package" when I do sudo apt-get install, how do I get it?

---

### Post by MarblePanther on 2008-12-08
try searching in synaptic package manager (not quick search).  Hit the search button and type in a key word.

---

### Post by m_duck on 2008-12-08
If you want to stay in the command line you can use one of```
apt-cache search keywords

aptitude search keywords
```
The first command does not need root privaliges, I cannot remember if the second does or not.

---

### Post by drs305 on 2008-12-08
Here is the ubuntu wiki on repositories. You might find some answers on how to enable certain repositories if you cannot find the package:
[Repositories/Ubuntu]("https://help.ubuntu.com/community/Repositories/Ubuntu")

[Repositories/CommandLine]("https://help.ubuntu.com/community/Repositories/CommandLine")

---

### Post by MarblePanther on 2008-12-08
a good site is [http://getdeb.net](http://getdeb.net) for finding packages not in the repos

---

