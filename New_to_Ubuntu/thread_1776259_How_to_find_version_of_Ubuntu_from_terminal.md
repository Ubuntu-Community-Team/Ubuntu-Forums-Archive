---
title: "How to find version of Ubuntu from terminal?"
date: 2011-06-05
forum: New to Ubuntu
---

### Post by L Campbell on 2011-06-05
I guess the title explains it all.

TIA

---

### Post by amauk on 2011-06-05
```
cat /etc/lsb-release
```

---

### Post by alphacrucis2 on 2011-06-05
> **L Campbell said:**
> I guess the title explains it all.

TIA

Kernel:

```
uname -a
```

Ubuntu:

```
lsb_release -a
```

---

### Post by dFlyer on 2011-06-05
another way is from terminal enter:

more /etc/lsb-release

press enter

---

### Post by alphacrucis2 on 2011-06-05
> **dFlyer said:**
> another way is from terminal enter:

more /etc/lsb-release

press enter

or even

```
less /etc/lsb-release
```

And as we know less is always more :P

---

### Post by ubudog on 2011-06-05
Another way:
```
cat /etc/issue
```

---

### Post by Jesua on 2012-09-03
> **amauk said:**
> ```
cat /etc/lsb-release
```

Thanks...

---

