---
title: "problem with installing opera 10"
date: 2009-10-04
forum: New to Ubuntu
---

### Post by yakoza on 2009-10-04
hi
i'v installed opera 10 but when i click on its icon nothing happend
and when i run it in terminal i get this error

```
naser@naser-desktop:~$ opera
ERROR: ld.so: object 'libjvm.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libawt.so' from LD_PRELOAD cannot be preloaded: ignored.
/home/naser/lib/opera/10.00/opera: error while loading shared libraries: libqt-mt.so.3: cannot open shared object file: No such file or directory
```

---

### Post by Arup on 2009-10-04
> **yakoza said:**
> hi
i'v installed opera 10 but when i click on its icon nothing happend
and when i run it in terminal i get this error

```
naser@naser-desktop:~$ opera
ERROR: ld.so: object 'libjvm.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libawt.so' from LD_PRELOAD cannot be preloaded: ignored.
/home/naser/lib/opera/10.00/opera: error while loading shared libraries: libqt-mt.so.3: cannot open shared object file: No such file or directory
```

Which version did you install? It should be either the qt3 .deb or qt4 .deb.

Do a sudo apt-get --purge remove opera 

Go to your home folder, hit ctrl+h and delete the opera folder and then re-install the deb file.

---

### Post by yakoza on 2009-10-04
i'm trying to install opera-10.00-4585.gcc4-shared-qt3.i386

---

### Post by Arup on 2009-10-04
[ftp://ftp.opera.com/pub/opera/linux/1000/final/en/i386/opera_10.00.4585.gcc4.qt3_i386.deb](ftp://ftp.opera.com/pub/opera/linux/1000/final/en/i386/opera_10.00.4585.gcc4.qt3_i386.deb)

This is what you need.

---

### Post by yakoza on 2009-10-04
> **Arup said:**
> [ftp://ftp.opera.com/pub/opera/linux/1000/final/en/i386/opera_10.00.4585.gcc4.qt3_i386.deb](ftp://ftp.opera.com/pub/opera/linux/1000/final/en/i386/opera_10.00.4585.gcc4.qt3_i386.deb)

This is what you need.

tnx, guy

---

