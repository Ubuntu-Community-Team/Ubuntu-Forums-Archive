---
title: "problems installing a dependency"
date: 2009-05-03
forum: New to Ubuntu
---

### Post by trinidadflores on 2009-05-03
I have been trying to install the cnr program but it errors out saying "Error: Dependency is not satisfiable: libapt-pkg-libc6.7-6-4.6"  where can i down load this package.  i am using jaunty.

Trinidad

---

### Post by hansdown on 2009-05-03
Hi trinidadflores.

It is here.

Don't know if it will work.

[http://packages.debian.org/unstable/python/python-apt](http://packages.debian.org/unstable/python/python-apt)

---

### Post by Mark Phelps on 2009-05-04
> **trinidadflores said:**
> I have been trying to install the cnr program but it errors out saying "Error: Dependency is not satisfiable: libapt-pkg-libc6.7-6-4.6"  where can i down load this package.  i am using jaunty.

Trinidad
In my experience, "not satisfiable" can also mean a conflict with an existing installed package.  It's not satisfiable not because a package is missing, but because you would have to remove an existing package and replace it with something else.  I've run into this with different versions of tzdata.

---

