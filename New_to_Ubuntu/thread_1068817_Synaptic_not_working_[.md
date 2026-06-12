---
title: "Synaptic not working :["
date: 2009-02-13
forum: New to Ubuntu
---

### Post by spidydude on 2009-02-13
Whenever I go to install a program via the Add/Remove Programs application or the Synaptic Package Manager, I get this error message.

E: /var/cache/apt/archives/rhythmbox_0.11.5-0ubuntu8_i386.deb: files list file for package `libfribidi0' is missing final newline

Any ideas?

---

### Post by Hospadar on 2009-02-13
It sounds like probably something happened while you package lists were updating.  You can reaload them through synaptic or "software sources" or just open a terminal and ```
sudo apt-get update
```
Your machine will probably do this periodically when it notifies you of updates you need, but maybe it died or you shut off your machine while it was happening.

See if that works, if not there may be some manual editing you could do to make it work.

---

### Post by spidydude on 2009-02-13
I did that, it still does not work. :[

---

### Post by SuperSonic4 on 2009-02-13
```
sudo rm /var/lib/dpkg/info/libfribidi0*

sudo apt-get update
```

the first command will:
 
> This doesn't mean the package has been removed, just the pre/post-install scripts, md5sums, and file lists related to it. You should reinstall the package - even if you plan to remove it, as those deleted and currupted files related to it will be replaced with non-currupted ones.

or ```
sudo dpkg --configure -a
```

As a side note isn't rhythmbox installed by default on ubuntu?

---

### Post by spidydude on 2009-02-13
It is, but I had no need for it before, so I removed it.

---

