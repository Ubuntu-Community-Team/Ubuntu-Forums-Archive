---
title: "unable to update system"
date: 2009-03-25
forum: New to Ubuntu
---

### Post by fiskking on 2009-03-25
At the top corner of my screen there is an exclamation stating that my update info. is outdated and causing networking problems. within terminal I used

```
 cat /etc/apt/sources.list
```

and the output:

```
deb http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://us.archive.ubuntu.com/ubuntu/ hardy-security main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-security restricted main multiverse universe #Added by software-properties
deb http://us.archive.ubuntu.com/ubuntu/ hardy-security universe
deb http://us.archive.ubuntu.com/ubuntu/ hardy-security multiverse
```

I am currently running Hardy Heron.  Hope this can help.

Fisk

---

### Post by halitech on 2009-03-25
open sources.list and put a # in front of the lines that include fiesty. Its no longer supported so thats where the outdated message is coming from.

```
gksudo gedit /etc/apt/sources.list
```

---

