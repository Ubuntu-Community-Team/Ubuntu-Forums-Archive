---
title: "installing tar-gz files"
date: 2010-05-06
forum: New to Ubuntu
---

### Post by Norman Thom on 2010-05-06
I could use some help installing tar.gz packages.
I've read "Installing anything on Ubuntu", all the posts on installation I could find and still have no idea what I'm doing

The items I want to install are the mplayerplug-in and quicktime 4 Linux 2.0.0

I've opened the terminal and typed cd after the prompt then dragged and dropped the mplayerplug-in folder to the terminal and hit enter.
This I believe should change the directory to the mplayerplug-in folder
I then typed ./configure  next prompt typed 'make' and next typed 'install' and here is what I get

***-desktop:~/Desktop/mplayerplug-in$ ./configure
checking for g++... g++
checking for C++ compiler default output file name... a.out
checking whether the C++ compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for gcc... gcc
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for a BSD-compatible install... /usr/bin/install -c
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
configure: Determining mozilla/firefox packages to build against
checking for MOZPLUG... no
configure: WARNING: mozilla-plugin not found
checking for MOZPLUG... no
configure: WARNING: firefox-plugin not found
checking for MOZPLUG... no
configure: WARNING: seamonkey-plugin not found
checking for MOZPLUG... no
configure: WARNING: xulrunner-plugin not found
checking for MOZPLUG... no
configure: WARNING: libxul not found
checking for MOZPLUG... no
configure: WARNING: iceape-plugin not found
configure: error: Unable to find mozilla or firefox development files
desktop:~/Desktop/mplayerplug-in$ make
make: *** No targets specified and no makefile found.  Stop.
-desktop:~/Desktop/mplayerplug-in$ make install
cat install.sh >install 
chmod a+x install ***


Can anybody help me

Norm

---

### Post by mike2357 on 2010-05-06
There's no exact science for getting this right, and it's going to probably involve some trial and error.  The "configure" script bombed out with an error message about not being able to find mozilla or firefox development files.  So I'd run Synaptic and  install firefox-dev, which contains development files for firefox.  I'd then run "./configure" again and see if I got any farther.  I wouldn't be surprised if it bombed again on something else, but you could look in Synaptic for a package ending in -dev, install it, and then see that happens.  Good luck.

---

