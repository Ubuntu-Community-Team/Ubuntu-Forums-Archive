---
title: "python-nautilus installed but not usable"
date: 2010-09-27
forum: New to Ubuntu
---

### Post by carrarin on 2010-09-27
Hello everyone, 

I installed python-nautilus from synaptic package manager. However, I can't import the package in my python programs... i get the following message...
```
>>> import nautilus
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ImportError: No module named nautilus

```


Why is this ... thanks!
carrarin

---

### Post by diesch on 2010-09-27
python-nautilus is for writing nautilus plugins, it doesn't work for standalone programs.

See  /usr/share/doc/python-nautilus/README.Debian for where to put your plugins so that Nautilus finds them.

---

