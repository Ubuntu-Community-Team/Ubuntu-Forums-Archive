---
title: "Disk Usage Analyser doesn't show up"
date: 2009-02-07
forum: New to Ubuntu
---

### Post by Aceloop on 2009-02-07
Hi. everyone

The problem I'm having is Disk Usage Analyser doesn't display when I click on it, I see it about 0.1 sec and it just disappears, the thing is with guest accounts it works perfect. I tried to reinstall but the problem is still their.

---

### Post by ptn107 on 2009-02-07
Pop open a terminal (Applications -> Accessories -> Terminal).  Type:

```
baobab
```

Post any errors.

---

### Post by Aceloop on 2009-02-07
> **ptn107 said:**
> Pop open a terminal (Applications -> Accessories -> Terminal).  Type:

```
baobab
```

Post any errors.

i get "Segmentation fault".

---

### Post by ptn107 on 2009-02-07
It's a known bug ([https://bugs.launchpad.net/ubuntu/+source/gnome-utils/+bug/284923](https://bugs.launchpad.net/ubuntu/+source/gnome-utils/+bug/284923)).  It will be fixed in 9.04.  For now do the following:

1. Press ALT+F2, type: gconf-editor

2. Navigate to the key apps/baobab/properties/

3. On the right remove any key that contains 'file:///'

---

### Post by Aceloop on 2009-02-07
> **ptn107 said:**
> It's a known bug ([https://bugs.launchpad.net/ubuntu/+source/gnome-utils/+bug/284923](https://bugs.launchpad.net/ubuntu/+source/gnome-utils/+bug/284923)).  It will be fixed in 9.04.  For now do the following:

1. Press ALT+F2, type: gconf-editor

2. Navigate to the key apps/baobab/properties/

3. On the right remove any key that contains 'file:///'

thank you alot. I appreciate the help.

---

