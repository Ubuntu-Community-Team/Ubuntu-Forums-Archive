---
title: "Trying to install libgpod"
date: 2009-01-28
forum: New to Ubuntu
---

### Post by Pauho on 2009-01-28
Hi,
I've been trying to install libgpod 0.7.0 from a tar.gz. I've run the ./configure and make commands. But when I run make install, i get the following spiel from the terminal:

Making install in src
make[1]: Entering directory `/home/paul/Desktop/libgpod-0.7.0/src'
make[2]: Entering directory `/home/paul/Desktop/libgpod-0.7.0/src'
test -z "/usr/local/lib" || /bin/mkdir -p "/usr/local/lib"
 /bin/bash ../libtool   --mode=install /usr/bin/install -c  'libgpod.la' '/usr/local/lib/libgpod.la'
/usr/bin/install -c .libs/libgpod.so.4.0.0 /usr/local/lib/libgpod.so.4.0.0
/usr/bin/install: cannot create regular file `/usr/local/lib/libgpod.so.4.0.0': Permission denied
make[2]: *** [install-libLTLIBRARIES] Error 1
make[2]: Leaving directory `/home/paul/Desktop/libgpod-0.7.0/src'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/paul/Desktop/libgpod-0.7.0/src'
make: *** [install-recursive] Error 1

Can anyone shed any light on what is going on and how I can fix it?

cheers
Paul

---

### Post by yeats on 2009-01-28
The 0.6.0 version is in the repos - is there a specific reason you want to install from source?

If so, did you look at the README file (or INSTALL file) - there almost always is one with tarballs?  The typical method for installing from source:

```

tar xzf *file*
cd *new directory*
./configure
make
sudo make install

```

> /usr/bin/install: cannot create regular file `/usr/local/lib/libgpod.so.4.0.0': Permission denied

looks like you didn't preface the make install command with sudo.

---

### Post by Pauho on 2009-01-29
Oh God, what an utter newbish mistake to make. 

Thanks for your help!

---

### Post by yeats on 2009-01-30
Hey - we all have to start somewhere.  And compared to MANY others here, I'm a noob myself :-)

---

