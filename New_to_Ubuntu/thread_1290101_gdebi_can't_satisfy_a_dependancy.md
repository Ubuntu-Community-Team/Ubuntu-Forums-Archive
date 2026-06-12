---
title: "gdebi can't satisfy a dependancy"
date: 2009-10-13
forum: New to Ubuntu
---

### Post by tropdoug on 2009-10-13
I am trying to install the gnome commander program from the deb package at [http://www.getdeb.net/search.php?keywords=gnome-commander](http://www.getdeb.net/search.php?keywords=gnome-commander) when Gdebi opens there is a red error message that reads > Error: Dependancy is not satisfiable: libexiv2-5

I tried doing sudo apt-get install libexiv2-5 but it cannot be found. Does this mean that I cannot install Gnome-Commander?

Any assistance appreciated

---

### Post by zero-n on 2009-10-13
do you have this problem with other packages or it's only with gnome commander.

---

### Post by 3rdalbum on 2009-10-13
It's present in 9.10 (as is Gnome Commander itself); what version of Ubuntu are you using?

If you're using an older Ubuntu that doesn't have libexiv2-5, then you can't install the debian package, but you may be able to compile the program from source.

---

### Post by earthpigg on 2009-10-13
it shows up in synaptic for me on a 9.04-derived ubuntu install.

in fact, i have the package installed (whatever it is).

have you run ***sudo apt-get update***, lately?

like... since you installed ubuntu on that system?

---

