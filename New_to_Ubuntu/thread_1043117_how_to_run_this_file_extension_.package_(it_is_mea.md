---
title: "how to run this file extension .package (it is meant for ubuntu )"
date: 2009-01-18
forum: New to Ubuntu
---

### Post by fuser312 on 2009-01-18
OK i downloaded Vdrift from its site, and i got this file vdrift-2007-03-23-full.package

now,how could i run this file, i have never heard of some .package extension in my linux experience.

from the site i choose to download linux binaries and not source.

---

### Post by aomlives on 2009-01-18
This should help:

[http://autopackage.org/](http://autopackage.org/)

---

### Post by mcduck on 2009-01-18
That's Autopackage.

Just run the package in a terminal, it will install Autopackage tools first and then the actual program. After that you should be able to just click to install all .package files.

```
./vdrift-2007-03-23-full.package
```

(you might need to set the file to be executable first, with "chomd +x vdrift-2007-03-23-full.package")

More info about Autopackage: [http://autopackage.org/]("http://autopackage.org/")

---

### Post by Michael.Godawski on 2009-01-18
True.

some more pics on installing this package here:

[LIST]
[*][http://autopackage.org/docs/howto-install/?PHPSESSID=07fa6bbbe6411b6724baf52374842d69](http://autopackage.org/docs/howto-install/?PHPSESSID=07fa6bbbe6411b6724baf52374842d69)
[/LIST]

---

### Post by fuser312 on 2009-01-18
thanx guys

---

### Post by fuser312 on 2009-01-18
how could i delete a post?

---

### Post by RomeReactor on 2009-01-18
Hi. You don't need to use **./** if you specify the complete path; and remember that Ubuntu is case-sensistive, so the correct path would be:
```
/home/user/**Desktop**/packagename.package
```

The easiest way would be to open the terminal, change to the desktop directory:
```
cd Desktop
```
and then run the program:
```
./vdrift-2007-03-23-full.package
```

---

### Post by YellowHammer on 2009-01-25
This thread helped me alot!  Thanks.

---

