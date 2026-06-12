---
title: "vuze"
date: 2009-05-27
forum: New to Ubuntu
---

### Post by tanha on 2009-05-27
I installed vuze through the repositories. Now, when I uninstall it, synaptic says it removed it, but it's still in the menu and still launches when I select it? Why doesn't it get uninstalled?

---

### Post by kpkeerthi on 2009-05-27
Can you post the outputs of
```
dpkg -l | grep vuze
```
and
```
dpkg -l | grep azureus
```
?

---

### Post by tanha on 2009-05-27
> **kpkeerthi said:**
> Can you post the outputs of
```
dpkg -l | grep vuze
```
and
```
dpkg -l | grep azureus
```
?

Seeing azureus gave me an idea... it was also installed. removed azereus, it removed vuze. thanks!

---

