---
title: "How do I find ubuntu version installed on computer"
date: 2009-03-15
forum: New to Ubuntu
---

### Post by hill0093 on 2009-03-15
How do I find ubuntu version installed on computer?

---

### Post by taurus on 2009-03-15
Applications -> Accessories -> Terminal
```
lsb_release -a
```

---

### Post by unutbu on 2009-03-15
Type
```
lsb_release -a
```
in a terminal.

Output will look something like this:
```
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 8.10
Release:	8.10
Codename:	intrepid
```

---

### Post by hill0093 on 2009-03-15
Sorry I am not at the ubuntu computer right now 
so I can't try it right now. 
But on the previous post I don't see 
whether or not it's 64-bit or 32-bit, 
and I need to know.

---

### Post by taurus on 2009-03-15
```
uname -m
```
i686 = 32bit
x86_64 = 64bit

---

### Post by gandaran on 2009-03-15
-----------

---

### Post by hill0093 on 2009-03-15
Thank you, taurus.

---

