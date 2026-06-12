---
title: "cannot install deb packages with linux mint 7"
date: 2009-08-23
forum: New to Ubuntu
---

### Post by PatrickMoore on 2009-08-23
im having a persistant issue with trying to install normal debian packages with package installer.
included is a screenshot,
basically its saying that im running update manager or synaptec. neither are running in fact i just booted the computer and when straight to install a package i downloaded last evening.
any help would be appreciated

---

### Post by PatrickMoore on 2009-08-23
when i start synaptec i get this message


```
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

```

---

### Post by jrox717 on 2009-08-23
Have you tried entering 
```
 sudo dpkg --configure -a 
```
into a terminal (Applications > Accessories > Terminal) ?

---

### Post by jimmy the saint on 2009-08-23
Did you try running that command?  It happened to me once before.  The package manager did not close gracefully and other ones still think it is running.  That command should clear things up.  open a terminal and run

```
sudo dpkg --configure -a
```

Beat by quick typing jrox

---

### Post by PatrickMoore on 2009-08-23
im running that now. it started frostwire and then stated my ip address and its been sitting there for about a minute and a half

---

### Post by PatrickMoore on 2009-08-23
now i cannot remove anything via term either im never using frostwire again

---

### Post by PatrickMoore on 2009-08-23
solved it was frostwire. i managed to uninstall it and now everything is a ok

---

