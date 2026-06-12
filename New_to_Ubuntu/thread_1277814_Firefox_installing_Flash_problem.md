---
title: "Firefox installing Flash problem"
date: 2009-09-28
forum: New to Ubuntu
---

### Post by aa4bb on 2009-09-28
Trying to watch a video in Firefox, I was notified that 9.04 required Flash player. Clicked to download and clicked to install with package installer (rather than save to disk). Seemed to go OK until it stopped with error message "Dependency is not satisfiable: libnspr4-dev"

What do I do now?

---

### Post by credobyte on 2009-09-28
Fire up terminal and execute the following command:
```
sudo apt-get install flashplugin-nonfree

```

It should auto-resolve all dependencies.

---

### Post by aa4bb on 2009-09-28
Thanks very much!!

---

