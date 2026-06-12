---
title: "Error: Dependency is not satisfiable: libnotify1 (&gt;= 0.5.0)"
date: 2011-04-23
forum: New to Ubuntu
---

### Post by ravitejamulpuri on 2011-04-23
I'm using ubuntu 10.04 and while i am trying to install linuxdcp using deb i am getting this particular error .

Error: Dependency is not satisfiable: libnotify1 (>= 0.5.0)

any idea what this is and how to overcome this??

---

### Post by Locke_99GS on 2011-04-23
10.04 only provides libnotify1 v0.4.5. It looks like the package you want to install may be for Maverick, Natty, or possibly Sid. 

You can attempt to install the required 0.5.0 version of libnotify1 from the Maverick repo, but you may or may not run into dependency-hell trying to get that installed. I'd give it a shot though - dpkg won't let you install it unless it can satisfy all the dependencies.

See the depends for libnotify1 in Maverick:
```

Package: libnotify1
Version: 0.5.0-2ubuntu1
Provides: libnotify1-gtk2.10
Depends: libc6 (>= 2.7), libdbus-glib-1-2 (>= 0.78), libglib2.0-0 (>= 2.16.0), libgtk2.0-0 (>= 2.18.0)

```

edit: forgot to link to Maverick package for you. sorry. Here it is:
[http://packages.ubuntu.com/maverick/libnotify1](http://packages.ubuntu.com/maverick/libnotify1)

---

