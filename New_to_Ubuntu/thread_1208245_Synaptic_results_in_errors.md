---
title: "Synaptic results in errors"
date: 2009-07-09
forum: New to Ubuntu
---

### Post by LinuxFox on 2009-07-09
I thought it was a dependency for a game I was trying to install, but when I tried a different package (specifically automake) on Synaptic, it resulted in an error.

Is there anyway to fix such errors and install what I need?  Some help please, I can't seem to understand what's wrong.

Edit: here's the errors I keep getting if it helps...
```
E: /var/cache/apt/archives/m4_1.4.10-1_i386.deb: unable to create `./usr/share/doc/m4/examples/exp.m4'
E: /var/cache/apt/archives/autoconf_2.61-4_all.deb: unable to create `./usr/share/autoconf/INSTALL'
E: /var/cache/apt/archives/autotools-dev_20070725.1_all.deb: unable to create `./usr/share/doc/autotools-dev/examples/autogen.sh'
E: /var/cache/apt/archives/automake_1%3a1.10.1-2_all.deb: unable to create `./usr/share/doc/automake/TODO.gz'
```

---

### Post by mano cazalet on 2009-07-09
what is the error message?

---

### Post by LinuxFox on 2009-07-09
> **mano cazalet said:**
> what is the error message?I edited them into my original post after trying it again to install automake.

---

### Post by LinuxFox on 2009-07-09
Sorry for the double post, but I thought this might be worth adding.  I decided to try installing automake via apt-get in the Terminal and the Terminal put out a slightly different error...

```
Errors were encountered while processing:
 /var/cache/apt/archives/m4_1.4.10-1_i386.deb
 /var/cache/apt/archives/autoconf_2.61-4_all.deb
 /var/cache/apt/archives/autotools-dev_20070725.1_all.deb
 /var/cache/apt/archives/automake_1%3a1.10.1-2_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Is there any reason why packages on the repository won't install?

---

### Post by mano cazalet on 2009-07-09
maybe an [HTML]apt-get -f install[/HTML] solves it

---

### Post by LinuxFox on 2009-07-09
> **mano cazalet said:**
> maybe an [HTML]apt-get -f install[/HTML] solves itI just tried that and I got the same results as when I did apt-get before.

---

