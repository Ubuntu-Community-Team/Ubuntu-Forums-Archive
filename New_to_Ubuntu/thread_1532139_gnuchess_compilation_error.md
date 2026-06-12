---
title: "gnuchess compilation error"
date: 2010-07-16
forum: New to Ubuntu
---

### Post by prabhuvishnumurthy on 2010-07-16
a

---

### Post by prabhuvishnumurthy on 2010-07-16
b

---

### Post by mc4man on 2010-07-16
I guess if you wanted to build you could pass a CFLAG like this and use an earlier gcc 

On lucid/karmic

```
CC=gcc-3.4 CFLAGS=-D_POSIX_C_SOURCE=200112L ./configure

```
which did build and run it successfully

Then looking for a gui board (xboard) noticed it (gnuchess) is in the repo's thru lucid so why not just use that instead...

---

### Post by prabhuvishnumurthy on 2010-07-17
c

---

### Post by prabhuvishnumurthy on 2010-07-17
d

---

