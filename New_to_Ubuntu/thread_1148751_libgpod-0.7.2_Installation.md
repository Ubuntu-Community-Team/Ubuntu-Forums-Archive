---
title: "libgpod-0.7.2 Installation"
date: 2009-05-04
forum: New to Ubuntu
---

### Post by ThatOneGuyThere on 2009-05-04
I'm trying to install libgpod-0.7.2 to access an ipod through Amarok.  Most problems I have had, I've just googled and found the answers easy enough.  However, I am stuck here.

I have followed the steps in the installation guide, however when I get to final stage of it to install and type in "Make Install" I receive this error message:
```
Making install in src
make[1]: Entering directory `/home/james/Desktop/libgpod-0.7.2/src'
make[2]: Entering directory `/home/james/Desktop/libgpod-0.7.2/src'
test -z "/usr/local/lib" || /bin/mkdir -p "/usr/local/lib"
 /bin/bash ../libtool   --mode=install /usr/bin/install -c  'libgpod.la' '/usr/local/lib/libgpod.la'
/usr/bin/install -c .libs/libgpod.so.4.1.0 /usr/local/lib/libgpod.so.4.1.0
/usr/bin/install: cannot create regular file `/usr/local/lib/libgpod.so.4.1.0': Permission denied
make[2]: *** [install-libLTLIBRARIES] Error 1
make[2]: Leaving directory `/home/james/Desktop/libgpod-0.7.2/src'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/james/Desktop/libgpod-0.7.2/src'
make: *** [install-recursive] Error 1

```Any idea on what the problem may be?  Thanks a lot!

---

### Post by oOarthurOo on 2009-05-04
Well, this error here:
```
/usr/bin/install: cannot create regular file `/usr/local/lib/libgpod.so.4.1.0': Permission denied
```
It seems to indicate maybe you didn't prepend sudo to your command.

More to the point, however, is there any reason why you simply can't
```
sudo apt-get install libgpod-common
```
On Jaunty, it has very 0.70

---

### Post by nothingspecial on 2009-05-04
You gotta sudo it -

```
sudo make install
```

That means doing it as root. You can`t just have any software installing itself on your system.

---

### Post by ThatOneGuyThere on 2009-05-04
Hey, thanks, I tried that, but it appears to not be the problem because I guess I have the latest already.  The readout was
```
james@james-desktop:~/Desktop/libgpod-0.7.2$ sudo apt-get install libgpod-common
[sudo] password for james: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libgpod-common is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

Thanks again.

---

### Post by ThatOneGuyThere on 2009-05-04
> **nothingspecial said:**
> You gotta sudo it -

```
sudo make install
```That means doing it as root. You can`t just have any software installing itself on your system.

Awesome, thanks a lot!  That did it!

---

