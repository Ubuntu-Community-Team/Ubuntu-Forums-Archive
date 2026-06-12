---
title: "Installing from source"
date: 2009-03-30
forum: New to Ubuntu
---

### Post by I[AM]SMRT on 2009-03-30
So I'm trying to install the latest libmtp7 version but since it's not in the repos I'm trying to install it from source (hardy). So I unpackaged it into /usr/src => ./configure, make, sudo make install.

Now when I try to reinstall banshee (because I uninstalled the earlier version of libmtp7 I had via apt-get) it tells me that additional packages are required and will be installed, namely libmtp7. I thought I had installed it from source, what's going on?

---

### Post by blueridgedog on 2009-03-30
You might get away with re-installing it with checkinstall:

[https://help.ubuntu.com/community/CheckInstall](https://help.ubuntu.com/community/CheckInstall)

It may solve the dependency issue.

---

### Post by I[AM]SMRT on 2009-03-31
I just tried it and it won't work, I don't really understand why.

```
========================= Installation results ===========================
Making install in src
make[1]: Entering directory `/usr/src/libmtp-0.3.6/src'
make[2]: Entering directory `/usr/src/libmtp-0.3.6/src'
test -z "/usr/local/lib" || /bin/mkdir -p "/usr/local/lib"
 /bin/bash ../libtool   --mode=install /usr/bin/install -c  'libmtp.la' '/usr/local/lib/libmtp.la'
/usr/bin/install -c .libs/libmtp.so.8.2.1 /usr/local/lib/libmtp.so.8.2.1
(cd /usr/local/lib && { ln -s -f libmtp.so.8.2.1 libmtp.so.8 || { rm -f libmtp.so.8 && ln -s libmtp.so.8.2.1 libmtp.so.8; }; })
(cd /usr/local/lib && { ln -s -f libmtp.so.8.2.1 libmtp.so || { rm -f libmtp.so && ln -s libmtp.so.8.2.1 libmtp.so; }; })
/usr/bin/install -c .libs/libmtp.lai /usr/local/lib/libmtp.la
/usr/bin/install -c .libs/libmtp.a /usr/local/lib/libmtp.a
chmod 644 /usr/local/lib/libmtp.a
chmod: changing permissions of `/usr/local/lib/libmtp.a': No such file or directory
make[2]: *** [install-libLTLIBRARIES] Error 1
make[2]: Leaving directory `/usr/src/libmtp-0.3.6/src'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/usr/src/libmtp-0.3.6/src'
make: *** [install-recursive] Error 1

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.
```

---

### Post by RetchingRabbit on 2009-03-31
> **'I[AM]SMRT said:**
> So I'm trying to install the latest libmtp7 version but since it's not in the repos I'm trying to install it from source (hardy). So I unpackaged it into /usr/src => ./configure, make, sudo make install.

Now when I try to reinstall banshee (because I uninstalled the earlier version of libmtp7 I had via apt-get) it tells me that additional packages are required and will be installed, namely libmtp7. I thought I had installed it from source, what's going on?
What's going on is that the package management system has no way to know about anything you've installed from source. Perhaps some kind soul will build you a .deb.

---

### Post by anewguy on 2009-03-31
Did you just download source, or did you add a repository and then add the source?  I think in order for what I'm going to suggest to work, it must be in a repository, but you could try the following:

sudo apt-get build-dep <banshee package name>


IF (that's a big if as I don't know if it will work in this case), the apt-get build-dep will gather and install the dependencies needed for a package if they weren't include with a package or if they somehow got deleted after installation.

Good luck!
Dave :)

---

### Post by mc4man on 2009-03-31
If you want to use checkinstall I'd somewhat start over, run a make clean, then make and use this instead
```
sudo checkinstall --fstrans=no
```

while there should be no problem building and installing a couple of points.

First you didn't need to remove libmpt7 because your actually building libmtp8 and they can co exist.
Second I don't believe any of your hardy repo players will use it anyway, they're built to use libmtp7 (it's not an equal or greater situation here

You'd probably need to build your media players also and hope they linked against the higher version. (remove libmtp-dev if installed may help

(after installing built sources one should usually run sudo ldconfig (never hurts

---

### Post by I[AM]SMRT on 2009-03-31
That worked beautifully, thanks.

Yea, it doesn't seem to work with banshee but that's something I have to work on or wait until Jaunty.

---

