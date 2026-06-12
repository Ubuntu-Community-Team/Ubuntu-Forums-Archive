---
title: "how to remove everything kde?"
date: 2009-11-18
forum: New to Ubuntu
---

### Post by northwestuntu on 2009-11-18
i by accident installed a kde program which installed a bunch of kde stuff.  i want to keep my desktop a pure gnome.  is there a command that will uninstall all the kde? i have already uninstalled the kde program.

---

### Post by kansasnoob on 2009-11-18
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by fahadsadah on 2009-11-18
```

sudo apt-get autoremove

```
In future, to avoid this problem, use aptitude rather than apt-get

kansasnoob's solution will not help, as you have installed just one program, not the whole of KDE.

---

### Post by northwestuntu on 2009-11-18
thanks guys

---

