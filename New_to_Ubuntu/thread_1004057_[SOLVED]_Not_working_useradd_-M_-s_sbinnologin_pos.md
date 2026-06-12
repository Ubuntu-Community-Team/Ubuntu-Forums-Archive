---
title: "[SOLVED] Not working: useradd -M -s /sbin/nologin postfix"
date: 2008-12-06
forum: New to Ubuntu
---

### Post by BassKozz on 2008-12-06
I am following [this guide]("http://souptonuts.sourceforge.net/postfix_tutorial.html") on how to setup postfix to work with Gmail, and it wants me to issue the following command to create a user "postfix":
```
useradd -M -s /sbin/nologin postfix
```
But it's not working, I assume because the "-M" is no longer supported for useradd (or atleast I can't find it in the "useradd --help") so how can I create this user with these settings?
TiA,
-BassKozz

---

### Post by BassKozz on 2008-12-06
Maybe if I rephrase the question it will help:
How can I create a user without a /home/ directory and without login (ssh/bash) privileges?

---

### Post by BassKozz on 2008-12-09
Solution:
```
sudo useradd -d /dev/null -s /sbin/nologin username
```
Creates a user who's home directory = /dev/null
And who's login = /sbin/nologin

Therefore user won't have a home directory and can't login to shell.

---

