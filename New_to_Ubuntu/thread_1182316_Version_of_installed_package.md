---
title: "Version of installed package"
date: 2009-06-08
forum: New to Ubuntu
---

### Post by rmeske on 2009-06-08
I have tried to find how to do this with no avail.  I would like to find out what packages I have installed and the version of each.  I tried apt-get -V but that did not display what I expected.

Any help would be apprectiated.

---

### Post by nandemonai on 2009-06-08
```
dpkg --list
```

```
aptitude search '~i'
```

```
apt-cache policy packagename
```

---

### Post by rmeske on 2009-06-08
Thank you!

That is exactly what I was looking for.

---

