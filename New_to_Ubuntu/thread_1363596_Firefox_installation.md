---
title: "Firefox installation"
date: 2009-12-24
forum: New to Ubuntu
---

### Post by mosaabJ on 2009-12-24
Hi
I just want to know where exactly is firefox installed in ubuntu 9.10 as I am trying to add new profiles for my firefox and the one shown in the mozilla site is not the same for me.

---

### Post by bodhi.zazen on 2009-12-24
firefox profiles are in ~/.mozilla/firefox

---

### Post by lovinglinux on 2009-12-24
Tod add a new profile, close Firefox and run this on a terminal:

```
firefox -P
```

This will launch the Profile Manager.

If you don't want to close Firefox and keep using your current profile while creating a new one, then run this instead:

```
firefox -P -no-remote
```

For more stuff read [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567)

---

### Post by mosaabJ on 2009-12-24
> **bodhi.zazen said:**
> firefox profiles are in ~/.mozilla/firefox


> **lovinglinux said:**
> Tod add a new profile, close Firefox and run this on a terminal:

```
firefox -P
```

This will launch the Profile Manager.

If you don't want to close Firefox and keep using your current profile while creating a new one, then run this instead:

```
firefox -P -no-remote
```

For more stuff read [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567)

Thanks to both of you this has been really helpful and it has solved my problems

---

### Post by redcarpet on 2009-12-24
If ever you want to find stuff with a a particular name you could always do
_find / -name <*string*> _and sit back for a couple of minutes while it goes chrurning. It is a good start to your search.

---

