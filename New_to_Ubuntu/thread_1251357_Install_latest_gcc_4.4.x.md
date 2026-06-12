---
title: "Install latest gcc 4.4.x"
date: 2009-08-27
forum: New to Ubuntu
---

### Post by flylehe on 2009-08-27
Hi,
I wonder how to install latest gcc (4.4.x) under Kubuntu 9.04?
THanks and regards

---

### Post by ptn107 on 2009-08-28
The easiest way is to add Karmic's repository to your sources.list.  And just do a quick upgrade for gcc.  You may need to change 'us' to a server closer to you.  Heads up though, it may pull in lots of packages with it.  After upgrading gcc remove the karmic line from your sources to avoid upgrading anything else by accident.

```
echo "deb http://us.archive.ubuntu.com/ubuntu karmic main restricted" | sudo tee -a /etc/apt/sources.list && sudo aptitude update && sudo aptitude install gcc
```

---

