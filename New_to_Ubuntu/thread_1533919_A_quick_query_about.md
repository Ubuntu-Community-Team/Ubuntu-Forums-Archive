---
title: "A quick query about /"
date: 2010-07-18
forum: New to Ubuntu
---

### Post by new__buntu on 2010-07-18
What are the default permissions set for the / directory? Also, how would I go about finding them on my own, as I can't very well use an "ls -l" to take a peek? 

Thanks ahead of time.

---

### Post by AlphaLexman on 2010-07-18
You should be able to:
```
cd /
```
and then,
```
ls -l
```
You can't?

---

### Post by mcphargus on 2010-07-18
running `stat /` will give you the permissions for the root directory. It'll be the middle line.

---

### Post by new__buntu on 2010-07-18
> **AlphaLexman said:**
> You should be able to:
```
cd /
```and then,
```
ls -l
```You can't?


That would work if I wanted to see the permissions for all the files inside of /, unless you know something I don't. 

Also, thanks McPhargus - worked great.

---

### Post by mcphargus on 2010-07-18
that's what we're here for :)

---

