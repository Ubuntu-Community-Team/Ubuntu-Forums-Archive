---
title: "dpkg error"
date: 2010-08-13
forum: New to Ubuntu
---

### Post by miguelesquirol on 2010-08-13
I installed lethe, but after uninstalling it, now I have a error everytime I try to update Ubuntu. I get an error every time I try to update ubuntu, also I can't delete Lethe from synaptics or with the computer janitor. I tried to reinstall the program but I get a 

rm:cannot remove /etc/lethe: no such file or directory
dpkg error processing lethe (--remove)
subprocess installed post-removal script returned error exit status 1

:(

thanks for any help

---

### Post by jtarin on 2010-08-13
Post the error message you get.

---

### Post by miguelesquirol on 2010-08-17
Here is the message when I try to upgrade:

E: I wasn't able to locate file for the lethe package. This might mean you need to manually fix this package.
Writing extended state information... Done
E: I wasn't able to locate file for the lethe package. This might mean you need to manually fix this package.
E: Internal error: couldn't generate list of packages to download

---

### Post by jtarin on 2010-08-17
Re-install the package again from a deb package of lethe (with dpkg -i <packagename>).

---

### Post by miguelesquirol on 2010-08-17
I did it and I got this error message:

dpkg: warning: old post-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
Eliminando archivos de configuracion
rm: cannot remove `/etc/lethe': No such file or directory
dpkg: error processing lethe_0.32_all.deb (--install):
 subprocess new post-removal script returned error exit status 1
Eliminando archivos de configuracion
rm: cannot remove `/etc/lethe': No such file or directory
dpkg: error while cleaning up:
 subprocess new post-removal script returned error exit status 1
Errors were encountered while processing:
 lethe_0.32_all.deb

---

### Post by earthpigg on 2010-08-17
hi,

EDIT: actually, im going to edit out my unconventional solution. conventional possible solutions haven't been exhausted yet.

can you run this command for us, and show us the output?

sudo dpkg -C

from man dpkg:

>         -C, --audit
              Searches for packages that have been installed only partially on
              your system. dpkg will suggest what to do with them to get  them
              working.

---

### Post by jtarin on 2010-08-17
[Dealing with troublesome package upgrades or removals.]("http://www.debian-administration.org/articles/251")

---

### Post by sandyd on 2010-08-17
> **miguelesquirol said:**
> I installed lethe, but after uninstalling it, now I have a error everytime I try to update Ubuntu. I get an error every time I try to update ubuntu, also I can't delete Lethe from synaptics or with the computer janitor. I tried to reinstall the program but I get a 

rm:cannot remove /etc/lethe: no such file or directory
dpkg error processing lethe (--remove)
subprocess installed post-removal script returned error exit status 1

:(

thanks for any help
```

sudo dpkg --remove --force-remove-reinstreq lethe
```

---

### Post by miguelesquirol on 2010-08-18
the sudo dpkg -C output is this:

The following packages are in a mess due to serious problems during
installation.  They must be reinstalled for them (and any packages
that depend on them) to function properly:
 lethe                Lethe - El congelador de particiones libre


and the force remove came out with this:

dpkg: warning: overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 143652 files and directories currently installed.)
Removing lethe ...
Eliminando archivos de configuracion
rm: cannot remove `/etc/lethe': No such file or directory
dpkg: error processing lethe (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 lethe

---

### Post by miguelesquirol on 2010-08-20
I follow the link, [Dealing with troublesome package upgrades or removals]("http://www.debian-administration.org/articles/251"). and I managed to fix it, thanks

---

### Post by jtarin on 2010-08-20
Your welcome! It's good you have solved your problem.

---

