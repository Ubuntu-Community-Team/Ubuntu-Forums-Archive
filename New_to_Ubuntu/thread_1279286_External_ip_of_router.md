---
title: "External ip of router"
date: 2009-09-30
forum: New to Ubuntu
---

### Post by A_M_S on 2009-09-30
Hello.

How can i get the ip of the external interface (Internet interface) of a router from the CLI?


Tnx.

---

### Post by peculiar penguin on 2009-09-30
Try something like
```
wget -q -O - http://whatismyip.org
```

---

### Post by credobyte on 2009-09-30
Try this one: [http://code.activestate.com/recipes/439094/](http://code.activestate.com/recipes/439094/)

---

