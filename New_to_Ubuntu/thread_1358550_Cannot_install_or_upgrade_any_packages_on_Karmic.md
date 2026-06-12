---
title: "Cannot install or upgrade any packages on Karmic"
date: 2009-12-18
forum: New to Ubuntu
---

### Post by mercnet on 2009-12-18
I ran into some disk error problems that I allowed ubuntu to fix, however, now I cannot update or install anything. When I do a system update, everything downloads, and then when it tries to install, I receive this error:
```
E: /var/cache/apt/archives/sysvinit-utils_2.87dsf-4ubuntu12_i386.deb: unable to create updated files list file for package sysvinit-utils
```

I performed apt-get update, and then apt-get upgrade, and received this error (note there is a huge list of dpkg warnings of packages missing):
```
dpkg: warning: files list file for package `gnome-power-manager' missing, assuming package has no files currently installed.
dpkg: warning: files list file for package `libxcomposite-dev' missing, assuming package has no files currently installed.
(Reading database ... 16 files and directories currently installed.)
Preparing to replace sysvinit-utils 2.87dsf-4ubuntu11 (using .../sysvinit-utils_2.87dsf-4ubuntu12_i386.deb) ...
Unpacking replacement sysvinit-utils ...
dpkg: error processing /var/cache/apt/archives/sysvinit-utils_2.87dsf-4ubuntu12_i386.deb (--unpack):
 unable to create updated files list file for package sysvinit-utils: No such file or directory
Errors were encountered while processing:
 /var/cache/apt/archives/sysvinit-utils_2.87dsf-4ubuntu12_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I am lost on what to do since I cannot reinstall dpkg without receiving these errors.

---

### Post by diesch on 2009-12-18
The package manager's database is seriously damaged - that's quite bad :-(

Maybe
```
 sudo touch /var/lib/dpkg/info/sysvinit-utils.list
```
is enough to let you install the new *sysvinit-utils* package. But I would think about reinstalling the system to avoid further problems.

---

### Post by mercnet on 2009-12-20
Thanks, I ended up reinstalling Ubuntu since there were no solutions found on the internet.

---

