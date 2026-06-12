---
title: "Basic shell command"
date: 2010-08-27
forum: New to Ubuntu
---

### Post by youngfellow on 2010-08-27
hi
is there any command to find out which OS am i using in Shell script?

---

### Post by AlphaLexman on 2010-08-27
```
uname -o
```

---

### Post by nich0s on 2010-08-27
To find your OS:
```
uname --o
```


To find your distro:
```
 cat /etc/*-release
```

---

### Post by youngfellow on 2010-08-29
thank you

---

### Post by scorp123 on 2010-08-29
> **AlphaLexman said:**
> ```
uname -o
``` That's Linux-only, on BSD-like OS'es and commercial Unix variants this might fail.

Depending on what OP wants, e.g. maybe write a shell script that is supposed to work on different platforms (Linux? Solaris? BSD? Mac OS X?), then it would be better to use an option that works on all of them, e.g.
```
uname -s
```

Or go for the full output and then parse it?
```
uname -a
```


Example output:

**_Ubuntu 10.04 server (32-bit):_**
```
> uname -o
GNU/Linux

> uname -s
Linux

> uname -a
Linux jsp01 2.6.32-24-generic-pae #41-Ubuntu SMP Thu Aug 19 02:43:57 UTC 2010 i686 GNU/Linux
```

**_Mac OS X 10.6.4 (64-bit); userland and options are BSD-like:_**
```
> uname -o
uname: illegal option -- o
usage: uname [-amnprsv]

> uname -s
Darwin

> uname -a
Darwin macbookpro0341 10.4.0 Darwin Kernel Version 10.4.0: Fri Apr 23 18:27:12 PDT 2010; root:xnu-1504.7.4~1/RELEASE_X86_64 x86_64
```

**_Solaris 10 Update 8, SPARC, 64-bit; userland and options are classic "System V"-like (= 1970'ish before the GNU movement improved all those userland tools):_**
```
> uname -o
uname: illegal option -- o
usage:  uname [-snrvmapiX]
        uname [-S system_name]

> uname -s
SunOS

> uname -a
SunOS sgd024 5.10 Generic_142900-07 sun4v sparc SUNW,Sun-Blade-T6300
```

As you can see "uname -o" only really works on Linux ... If that's the only Unix-like OS OP is ever going to use ... fine. If not then I'd suggest to tinker with options that are known to work everywhere, e.g. "uname -a" ...

Just my 0.02€ :D

---

### Post by Vaphell on 2010-08-29
and that's why you always try **<cmd> --help** or **man <cmd>** on every command to see the available options and switches :)

---

### Post by fatality_uk on 2010-08-29
To find out more about any linux command, you can use man or --help but alos the best web site is:

[http://linuxmanpages.com/](http://linuxmanpages.com/)

---

### Post by jtarin on 2010-08-29
Or you can turn the box over and see what version it is.

---

### Post by PocketDog on 2010-08-29
Kind of related, is ```
cat /etc/issue
``` Ubuntu only, Debian only, Linux only or *nix only?

---

