---
title: "apt-get sources ?"
date: 2009-11-28
forum: New to Ubuntu
---

### Post by WitchCraft on 2009-11-28
Hi, question:

I right now installed a new server.
When I do apt-get install xy i almost always get "couldn't find package xy

The network works (i did a netinstall), and i did apt-get update.
Probably it's ?AGAIN? that there's no packages in the Swiss karmic x64 repository... ? 

The problem is I can't change my apt sources, since there seems to be no base-config anymore...


Can anybody provide me with a /etc/apt/sources.list file ?
I need to check the entries, because I sit at at a arch-linux with pacman right now...

---

### Post by WitchCraft on 2009-11-28
Bump. Please anybody copy/paste your /etc/apt/sources.list to this thread.

---

### Post by Virtual Liberty on 2009-11-28
```

deb http://archive.ubuntu.com/ubuntu/ karmic main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ karmic-updates main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu/ karmic-security main restricted universe multiverse
deb http://archive.canonical.com/ubuntu/ karmic partner

```** Removed third-party repositories.
** What is *Swiss* ?

---

### Post by diesch on 2009-11-28
```

deb http://de.archive.ubuntu.com/ubuntu/ karmic main universe restricted multiverse
deb-src http://de.archive.ubuntu.com/ubuntu/ karmic main universe restricted multiverse
deb http://security.ubuntu.com/ubuntu/ karmic-security universe main multiverse restricted
deb-src http://security.ubuntu.com/ubuntu/ karmic-security universe main multiverse restricted
deb http://de.archive.ubuntu.com/ubuntu/ karmic-updates universe main multiverse restricted
deb-src http://de.archive.ubuntu.com/ubuntu/ karmic-updates universe main multiverse restricted
deb http://de.archive.ubuntu.com/ubuntu/ karmic-backports universe main multiverse restricted
deb-src http://de.archive.ubuntu.com/ubuntu/ karmic-backports universe main multiverse restricted

```

---

### Post by WitchCraft on 2009-11-28
Thank you so much. Now it works.

multiverse and universe and partner wasn't in, although I checked the option in the install...


> **Virtual Liberty said:**
> 
** What is *Swiss* ?
ch.archive.ubuntu.com

---

