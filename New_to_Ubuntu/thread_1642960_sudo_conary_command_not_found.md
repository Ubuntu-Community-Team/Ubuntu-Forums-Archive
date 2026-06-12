---
title: "sudo: conary: command not found"
date: 2010-12-11
forum: New to Ubuntu
---

### Post by mancroft on 2010-12-11
Am trying to run

```
$ sudo conary erase icedtea-jre icedtea-jdk icedtea-gcjwebplugin --no-deps

```

and get the error

```
sudo: conary: command not found

```

Any ideas as to what the problem is?

---

### Post by Rubi1200 on 2010-12-11
If you are using Ubuntu, I don't believe the package is available in the official repositories unless you installed it from another PPA.

Try the command ```
locate conary
```

Ubuntu 10.04 uses Synaptic, apt-get, and aptitude.

---

### Post by mancroft on 2010-12-11
Thanks Rubi1200.

locate conary gives:

/usr/share/vim/vim72/syntax/conaryrecipe.vim

---

### Post by supererki on 2010-12-11
Why don't you just use the built-in package management system - APT ?

apt-get remove icedtea-jre icedtea-jdk icedtea-gcjwebplugin

---

### Post by Rubi1200 on 2010-12-11
The locate command does not help you. What it found is something that is part of the vim package and has nothing to do with package management.

I suggest you go with supererki's recommendation to remove those packages.

---

### Post by mancroft on 2010-12-11
> **Rubi1200 said:**
> The locate command does not help you. What it found is something that is part of the vim package and has nothing to do with package management.

I suggest you go with supererki's recommendation to remove those packages.

OK.

Thanks guys.

---

