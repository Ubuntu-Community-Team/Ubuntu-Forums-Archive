---
title: "How to install Apache?"
date: 2009-04-25
forum: New to Ubuntu
---

### Post by zzzonked on 2009-04-25
How do I install Apache? Using Ubuntu 8.04. I've installed LAMP using tasksel, but a quick search for Apache in my file system returned nothing. PHP and MySQL seem to have been installed though. If it IS installed, where is it (by default)?

---

### Post by cerealtx on 2009-04-25
u might open terminal and type
```
 ps -All | grep apache
``` 
it could be running already, and u could open synaptic and type apache in and see if it says its installed can't remember where its installed(its many places that it effects)

---

### Post by dtoronto on 2009-04-25
To install apache2:

```
$ sudo apt-get install apache
```

just double check to make sure it isn't already there, if there's corruption or something you may need to use purge to get rid of the old files.  Cheers!

---

### Post by cerealtx on 2009-04-25
> **dtoronto said:**
> To install apache2:

```
$ sudo apt-get install apache
```

just double check to make sure it isn't already there, if there's corruption or something you may need to use purge to get rid of the old files.  Cheers!

its apache2 not apache

---

### Post by dtoronto on 2009-04-25
> its apache2 not apache

sorry about that, correction:

```
$ sudo apt-get install apache2
```

---

