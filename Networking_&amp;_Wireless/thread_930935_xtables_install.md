---
title: "xtables install"
date: 2008-09-26
forum: Networking &amp; Wireless
---

### Post by zlikrof on 2008-09-26
Hello,

I have major problem with installing xtables on ubuntu hardy. I need xtables to extend iptables with --tee option.

I downloaded xtables-combined (which is newer version of iptables + xtables addon) from [*here*]("http://dev.medozas.de/files/xtables/"), untarred, done ./configure, make and sudo make install. Everything seemed just OK (no errors) ...

... but, when I type "iptables" in terminal, I get an error message:
```
iptables: error while loading shared libraries: libxtables.so.0: cannot open shared object file: No such file or directory
```

Than I deleted everyting in connection with iptables with synaptic, even tried with apt-get purge and than reinstalling "old" iptables, but still - I got the same error message.

What should I do? Is there a way to fix iptables? Is there any other way to install xtables?

Thanks for answers in advance!

---

### Post by nlmark on 2008-10-07
had the same issue.

Turns out the library was put in /usr/local/lib instead of /usr/lib. Resolved it by creating a symlink, but there should be a more elegant way of handling this.

---

