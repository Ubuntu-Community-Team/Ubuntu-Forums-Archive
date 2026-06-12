---
title: "Deleted Repository!!!"
date: 2009-04-24
forum: New to Ubuntu
---

### Post by smileyguy on 2009-04-24
I acccidentally deleted the repositorylisted under Third Party Apps in my Synaptics Package Manager! Inow only have the one listed as [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) (says **source code**) next to it.

Does anybody know that the other one was in the default Ubunto 9.04 installation (it's a fresh install)? It was the one **without source code** next to it in parentheses.

Please help to calm my obsessive pedantic little mind!

---

### Post by nandemonai on 2009-04-24
> **smileyguy said:**
> I acccidentally deleted the repositorylisted under Third Party Apps in my Synaptics Package Manager! Inow only have the one listed as [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) (says **source code**) next to it.

Does anybody know that the other one was in the default Ubunto 9.04 installation (it's a fresh install)? It was the one **without source code** next to it in parentheses.

Please help to calm my obsessive pedantic little mind!

Same one but binary.

```
# deb http://archive.canonical.com/ubuntu jaunty partner
# deb-src http://archive.canonical.com/ubuntu jaunty partner
```

---

### Post by El Zoido on 2009-04-24
Don't worry, should be easy!

If I'm not mistaken, just enter the exact data from the source codes repo (->EDIT, copy stuff, -> ADD), but choose binary instead of source for "type"

---

### Post by ibuclaw on 2009-04-24
You mean:
```
deb http://archive.canonical.com/ubuntu jaunty partner
```
and
```
deb-src http://archive.canonical.com/ubuntu jaunty partner
```

?

Regards
Iain

---

### Post by smileyguy on 2009-04-24
Ah thanks :)

---

