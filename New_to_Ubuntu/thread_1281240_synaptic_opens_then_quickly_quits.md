---
title: "synaptic opens then quickly quits"
date: 2009-10-03
forum: New to Ubuntu
---

### Post by virtualsamana on 2009-10-03
I am having a problem with synaptic package manager and add/remove programs. If I open either of these applications, they will open for a split second and then quit.

---

### Post by Paqman on 2009-10-03
Go to Applications > Accesories > Terminal and launch Synaptic with this command:
```
gksu synaptic
```

Then please post the error messages that it generates.

---

### Post by jmszr on 2009-10-03
virtualsamana,

This fixed a similar problem for me:

```
sudo rm /var/cache/apt/*.bin
```

Hope that helps.

---

### Post by virtualsamana on 2009-10-05
Thanks Paq and jm,

Jm -  your terminal script worked. Thank you!

Do you know why the problem occured in the first place and what the terminal script did to fix it?

---

### Post by jmszr on 2009-10-05
virtualsamana,

This is the best explanation I've come across:

> **ciscosurfer said:**
> Sometimes the package cache can get scrambled or corrupt or just needs to be rebuilt. The command```
sudo rm /var/cache/apt/*.bin
```effectively removes all files that end with .bin, so what this means is that the pkgcache.bin and srcpkgcache.bin files will be removed, thus forcing apt to recreate new package (and source package if you build from source) caches. It is one way to allow apt to start fresh again. And because Synaptic uses apt as its backend, removing these files helps Synpatic along.

---

