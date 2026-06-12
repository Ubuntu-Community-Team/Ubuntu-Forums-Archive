---
title: "gcc Error"
date: 2008-12-11
forum: New to Ubuntu
---

### Post by Mombie on 2008-12-11
I'm trying to install gcc on Ubuntu for an assignment in School, but after running the *sudo apt-get install gcc*, I receive this error when trying to preform *./configure --prefix=$HOME/units174* command:
[I][CENTER]
loading cache ./config.cache
checking for gcc... gcc
checking whether the C compiler (gcc  ) works... no
configure: error: installation or configuration problem: C compiler cannot create executables.[/CENTER][/I]

Most of the other computers in the class aren't having this issue, just I seem to be. Any help would be appreciated.
Thanks.

---

### Post by Michael.Godawski on 2008-12-11
Perhaps some packages are missing. Install these too:

```
sudo apt-get install build-essential make manpages-dev autoconf automake1.9 libtool flex bison gcc-doc
```

---

