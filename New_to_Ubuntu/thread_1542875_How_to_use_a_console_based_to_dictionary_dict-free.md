---
title: "How to use a console based to dictionary? dict-freedict-X-X"
date: 2010-07-31
forum: New to Ubuntu
---

### Post by frenchn00b on 2010-07-31
Hello,

I would like a command line to translate a word to its transalation.

Any idea how to use the dict-freedict-X-X from command line?

---

### Post by micha137b on 2010-07-31
You have to install a dict client like the package "dict", which will offer the "dict" command.  It needs a server to talk to.  Either you install a local one, requiring package "dictd" and FreeDict dictionaries.  Or you use a public server, see [http://www.luetzschena-stahmeln.de/dictd/](http://www.luetzschena-stahmeln.de/dictd/)

---

### Post by frenchn00b on 2010-08-02
> **micha137b said:**
> You have to install a dict client like the package "dict", which will offer the "dict" command.  It needs a server to talk to.  Either you install a local one, requiring package "dictd" and FreeDict dictionaries.  Or you use a public server, see [http://www.luetzschena-stahmeln.de/dictd/](http://www.luetzschena-stahmeln.de/dictd/)

yuo meant from apt-cache search : ?

dict - dictionary client
dictd - dictionary server

---

