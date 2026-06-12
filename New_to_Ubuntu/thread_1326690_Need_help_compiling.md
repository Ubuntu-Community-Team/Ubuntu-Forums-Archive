---
title: "Need help compiling"
date: 2009-11-14
forum: New to Ubuntu
---

### Post by cygnis1 on 2009-11-14
I am trying to compile gpointing-device-settings 1.3.2.  I was able to configure and make.  But when I tried make install, I got this (these) error message:
john@john-laptop:~/Downloads/gpointing-device-settings-1.3.2$ make install
Making install in src
make[1]: Entering directory `/home/john/Downloads/gpointing-device-settings-1.3.2/src'
make[2]: Entering directory `/home/john/Downloads/gpointing-device-settings-1.3.2/src'
test -z "/usr/local/lib" || /bin/mkdir -p "/usr/local/lib"
 /bin/bash ../libtool   --mode=install /usr/bin/install -c   libgpds.la '/usr/local/lib'
libtool: install: /usr/bin/install -c .libs/libgpds.so.0.1.0 /usr/local/lib/libgpds.so.0.1.0
/usr/bin/install: cannot create regular file `/usr/local/lib/libgpds.so.0.1.0': Permission denied
make[2]: *** [install-libLTLIBRARIES] Error 1
make[2]: Leaving directory `/home/john/Downloads/gpointing-device-settings-1.3.2/src'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/john/Downloads/gpointing-device-settings-1.3.2/src'
make: *** [install-recursive] Error 1
john@john-laptop:~/Downloads/gpointing-device-settings-1.3.2$ 

what does this error message mean?  and what should I do next?
I am running Karmic.
Thanks,
Cygnis1

---

### Post by scragar on 2009-11-14
```
sudo make install
```
Or look into fakeroot and creating a .deb

---

### Post by sandyd on 2009-11-14
> **cygnis1 said:**
> I am trying to compile gpointing-device-settings 1.3.2.  I was able to configure and make.  But when I tried make install, I got this (these) error message:
john@john-laptop:~/Downloads/gpointing-device-settings-1.3.2$ make install
Making install in src
make[1]: Entering directory `/home/john/Downloads/gpointing-device-settings-1.3.2/src'
make[2]: Entering directory `/home/john/Downloads/gpointing-device-settings-1.3.2/src'
test -z "/usr/local/lib" || /bin/mkdir -p "/usr/local/lib"
 /bin/bash ../libtool   --mode=install /usr/bin/install -c   libgpds.la '/usr/local/lib'
libtool: install: /usr/bin/install -c .libs/libgpds.so.0.1.0 /usr/local/lib/libgpds.so.0.1.0
/usr/bin/install: cannot create regular file `/usr/local/lib/libgpds.so.0.1.0': Permission denied
make[2]: *** [install-libLTLIBRARIES] Error 1
make[2]: Leaving directory `/home/john/Downloads/gpointing-device-settings-1.3.2/src'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/john/Downloads/gpointing-device-settings-1.3.2/src'
make: *** [install-recursive] Error 1
john@john-laptop:~/Downloads/gpointing-device-settings-1.3.2$ 

what does this error message mean?  and what should I do next?
I am running Karmic.
Thanks,
Cygnis1
put "sudo" in front of make install
or do checkinstall

---

### Post by cygnis1 on 2009-11-14
Thanks, it seems to have worked.

---

