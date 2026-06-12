---
title: "Broken Package Help"
date: 2009-09-11
forum: New to Ubuntu
---

### Post by quietbear on 2009-09-11
So, I just upgraded to Jaunty last night, and today I am trying to upgrade Kdenlive to the latest version.

It was going well until I was almost finished and I got this error:

> You have 1 broken package on your system!

Use the "Broken" filter to locate it.

So I went to synaptic, looked at the broken packages and there is one.

I checked it for re-instalation, and it starts then I get this error:

> E: /var/cache/apt/archives/frei0r-plugins_1.1.22git20090409+repack-0ubuntu1_i386.deb: trying to overwrite `/usr/lib/frei0r-1/3dflippo.so', which is also in package frei0r

Help?

I looked in /usr/lib for the frei0r-1 folder, and it is not there, I had already deleted it but I still get the errors.

It is really bothering me.  Kdenlive works even with the error, but with the broken package it makes management of the system difficult.

---

### Post by zvacet on 2009-09-12
```
sudo apt-get -f install
```

---

### Post by quietbear on 2009-09-12
when I do that I get this error eventually:

> dpkg: error processing /var/cache/apt/archives/frei0r-plugins_1.1.22git20090409+repack-0ubuntu1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/frei0r-1/3dflippo.so', which is also in package frei0r
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/frei0r-plugins_1.1.22git20090409+repack-0ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

