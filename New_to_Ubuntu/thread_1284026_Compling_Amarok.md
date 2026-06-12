---
title: "Compling Amarok"
date: 2009-10-06
forum: New to Ubuntu
---

### Post by Falc7 on 2009-10-06
I am trying to install Amarok 2.2 by compiling from source,  i am following this guide
[http://amarok.kde.org/wiki/Compiling:2.0](http://amarok.kde.org/wiki/Compiling:2.0)

When i enter this command ```
cmake .. -DCMAKE_INSTALL_PREFIX=`kde4-config --prefix`
``` i get this message ```
josh@josh-laptop:~/amarok-2.2.0/amarok-2.2.0-build$ cmake .. -DCMAKE_INSTALL_PREFIX=`kde4-config --prefix`
-- The C compiler identification is GNU
-- The CXX compiler identification is GNU
-- Check for working C compiler: /usr/bin/gcc
-- Check for working C compiler: /usr/bin/gcc -- works
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
-- Check for working CXX compiler: /usr/bin/c++
-- Check for working CXX compiler: /usr/bin/c++ -- works
-- Detecting CXX compiler ABI info
-- Detecting CXX compiler ABI info - done
-- Looking for dlopen in dl
-- Looking for dlopen in dl - found
CMake Error at /usr/share/cmake-2.6/Modules/FindPackageHandleStandardArgs.cmake:57 (MESSAGE):
  Could NOT find Taglib (missing: TAGLIB_INCLUDES TAGLIB_LIBRARIES)
Call Stack (most recent call first):
  cmake/modules/FindTaglib.cmake:121 (FIND_PACKAGE_HANDLE_STANDARD_ARGS)
  CMakeLists.txt:17 (find_package)


```

What should i do?

---

### Post by PacSci on 2009-10-06
Try installing the package libtag1-dev. It contains the header files for TagLib. Ubuntu often splits packages up into binary files and development headers - the headers are what's necessary to build from source.

---

### Post by Falc7 on 2009-10-06
I'm now getting this```
josh@josh-laptop:~/amarok-2.2.0/amarok-2.2.0-build$ cmake .. -DCMAKE_INSTALL_PREFIX=`kde4-config --prefix`
-- TagLib version not found: version searched :1.6, found 1.5
CMake Error at cmake/modules/FindTaglib.cmake:132 (message):
  Could not find Taglib
Call Stack (most recent call first):
  CMakeLists.txt:17 (find_package)


-- Configuring incomplete, errors occurred!
josh@josh-laptop:~/amarok-2.2.0/amarok-2.2.0-build$ 


```

So i tried ```
josh@josh-laptop:~$ sudo dpki -i libtag1-dev_1.6-3_i386.deb
sudo: dpki: command not found
josh@josh-laptop:~$ sudo dpkg -i libtag1-dev_1.6-3_i386.deb
(Reading database ... 164868 files and directories currently installed.)
Preparing to replace libtag1-dev 1.5-3 (using libtag1-dev_1.6-3_i386.deb) ...
Unpacking replacement libtag1-dev ...
dpkg: dependency problems prevent configuration of libtag1-dev:
 libtag1-dev depends on libtag1c2a (= 1.6-3); however:
  Version of libtag1c2a on system is 1.5-3.
dpkg: error processing libtag1-dev (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libtag1-dev

```

and then ```
josh@josh-laptop:~$ sudo dpkg -i libtag1c2a_1.6-3_i386.deb
dpkg: regarding libtag1c2a_1.6-3_i386.deb containing libtag1c2a:
 libtag1c2a breaks libtag-extras0
  libtag-extras0 (version 0.1.2-0ubuntu1) is present and installed.
dpkg: error processing libtag1c2a_1.6-3_i386.deb (--install):
 installing libtag1c2a would break libtag-extras0, and
 deconfiguration is not permitted (--auto-deconfigure might help)
Errors were encountered while processing:
 libtag1c2a_1.6-3_i386.deb
josh@josh-laptop:~$ 

```

and lastly:```
josh@josh-laptop:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run ‘apt-get -f install’ to correct these.
The following packages have unmet dependencies.
  libtag1-dev: Depends: libtag1c2a (= 1.6-3) but 1.5-3 is installed
E: Unmet dependencies. Try using -f.
josh@josh-laptop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies...Done
The following packages will be REMOVED
  libtag1-dev
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 610kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 164883 files and directories currently installed.)
Removing libtag1-dev ...
josh@josh-laptop:~$ 

```

:(

---

### Post by PacSci on 2009-10-06
Development packages require the exact version of their main packages to be installed. Downloading a .deb that doesn't match the given version is an instant fail. Because of this, you'll need to find a 1.6-3 .deb of the main libtag1 package. Install the main .deb first, then install the -dev .deb.

---

### Post by Paqman on 2009-10-06
> **Falc7 said:**
> 
What should i do?

Don't compile from source. You should always try and stick to the package manager, as it'll keep your system stable. Compiling apps (especially ones with tons of dependencies) is a recipe for borkage IMO.

Amarok 2.2 is available from the Karmic repos. So your options are (in order of preference):

[LIST=1]
[*]Wait until Karmic is released in a couple of weeks
[*]Use the [Project Neon PPA]("https://launchpad.net/~project-neon/+archive/ppa") to install it on Jaunty
[*]Upgrade to the Karmic beta now
[*]Try to install from the Karmic repos
[/LIST]

---

### Post by Falc7 on 2009-10-07
> **Paqman said:**
> Don't compile from source. You should always try and stick to the package manager, as it'll keep your system stable. Compiling apps (especially ones with tons of dependencies) is a recipe for borkage IMO.

Amarok 2.2 is available from the Karmic repos. So your options are (in order of preference):

[LIST=1]
[*]Wait until Karmic is released in a couple of weeks
[*]Use the [Project Neon PPA]("https://launchpad.net/~project-neon/+archive/ppa") to install it on Jaunty
[*]Upgrade to the Karmic beta now
[*]Try to install from the Karmic repos
[/LIST]


Thanks for your help!

---

### Post by Zoot7 on 2009-10-07
> **Paqman said:**
> Don't compile from source. You should always try and stick to the package manager, as it'll keep your system stable. Compiling apps (especially ones with tons of dependencies) is a recipe for borkage IMO.
+1 I try to avoid compiling from source whenever I can.

For future reference if you can't avoid it, one trick to use (for example if you want to compile amarok from source is:
```
sudo apt-get build-dep amarok
```
Chances are you'll be able to satisfy the newer version with the old dependencies, if you can't then well.. you've to go hunting for packages. :)

---

### Post by Genserowski on 2010-06-21
> **PacSci said:**
> Try installing the package libtag1-dev.

THX! It works!

---

