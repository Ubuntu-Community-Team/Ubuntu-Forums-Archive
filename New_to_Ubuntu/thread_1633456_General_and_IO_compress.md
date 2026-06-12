---
title: "General and IO compress"
date: 2010-11-29
forum: New to Ubuntu
---

### Post by drordh on 2010-11-29
hey, i am trying to install those programs, and in both i have the same error:
 make install

!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
ERROR: Can't create '/usr/local/man/man3'
mkdir /usr/local/man/man3: Permission denied at /usr/share/perl/5.10/ExtUtils/Install.pm line 483

!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
 at -e line 1
make: *** [pure_site_install] Error 13

anyone any idea?

---

### Post by cariboo on 2010-11-29
When installing programs outside your home directory, you need to be root. The command would be:

```
sudo make install
```

---

