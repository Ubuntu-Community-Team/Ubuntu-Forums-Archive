---
title: "WUA 1340 using ra73"
date: 2008-04-03
forum: Networking &amp; Wireless
---

### Post by shadowjester on 2008-04-03
My desktop's dead in the water without wireless (campus is wireless only).  I'm trying to follow TripleWithCheese's method to get it working found here: [http://ubuntuforums.org/showthread.php?t=270756&highlight=wua+1340+ralink](http://ubuntuforums.org/showthread.php?t=270756&highlight=wua+1340+ralink) but I keep on running into an error with the "make all" command.  Error is as follows:

```
make: *** /lib/modules/2.6.22-14-rt/build: No such file or directory.  Stop.
make: *** [all] Error 2
```

I have the build-essential package installed (had to download the debs (and dependancies) via my laptop, but it's up to date) so this message doesn't make much sense to me.  Anyone help?

---

### Post by shadowjester on 2008-04-04
Still looking for some help.

---

### Post by shadowjester on 2008-04-04
.

---

### Post by shadowjester on 2008-04-05
.

---

### Post by StevenHarper on 2008-05-26
Have you run 

```
.configure
```

before you have tried the 

```
make all
```


Steve

---

