---
title: "advice on removing applications"
date: 2009-08-01
forum: New to Ubuntu
---

### Post by rburkartjo on 2009-08-01
using the command line what is the best way to remove some programs. i want to remove minefield 3.6, google chrome, chromium web browser. /tks

---

### Post by wojox on 2009-08-01
```
sudo apt-get --purge remove <application>
```

Thanks philinux, forgot that part.

---

### Post by philinux on 2009-08-01
He will need sudo for that.

sudo apt-get .......

---

### Post by unutbu on 2009-08-01
If minefield 3.6, google chrome, and chromium web browser were not installed from .debs, then uninstalling becomes a bit tricky.

Download the installer, .tar.bz2, or whatever you used to install the program(s). Look for a README, INSTALL or UNINSTALL file for instructions on how to uninstall. (Sometimes you get lucky...)

If you installed it with the command 
```

make install
```

Then in the same directory try typing 
```

make uninstall
```
Sometimes the developer is nice and provides an "uninstall" target in the Makefile.

If none of that works, then perhaps try using checkinstall.
checkinstall is a package in the repos. It can monitor installation scripts and instead of actually installing the files directly, it makes a .deb. So the idea is, you use checkinstall to create the deb, you reinstall from the deb, then remove the deb using Synaptic or "sudo dpkg -r PACKAGE".

See [http://ubuntuforums.org/showpost.php?p=7635985&postcount=10](http://ubuntuforums.org/showpost.php?p=7635985&postcount=10) for an example of how this is done. If you'd like more details, please post a link to the installers for programs you've installed.

---

### Post by W4l0ck on 2009-08-01
lol! n00b

---

### Post by rburkartjo on 2009-08-02
tks

---

### Post by rburkartjo on 2009-08-02
even though i marked as solved here is a good link i found for removing both google chrome and the chromium web browser 
[http://ohioloco.ubuntuforums.org/showthread.php?t=1179746](http://ohioloco.ubuntuforums.org/showthread.php?t=1179746)

---

