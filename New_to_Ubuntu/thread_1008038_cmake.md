---
title: "cmake ?"
date: 2008-12-11
forum: New to Ubuntu
---

### Post by stevek123 on 2008-12-11
I'm getting along OK in ubuntu but still have trouble with stuff in command line. It'll get easier with time and practice I suppose.... but here I feel like a dummy. I'm pretty sure I've collected/installed all dependencies and this should be easy :shrug: ...I'm trying to install the latest Stellarium 0.10.0 - and it uses cmake instead of configure to generate the make file. When I try, I get this message...

steve@ubuntudesktop:~/Documents/stellarium10.0$ cmake
cmake version 2.4-patch 7
Usage

  cmake [options] <path-to-source>
  cmake [options] <path-to-existing-build>

Command-Line Options
  -C <initial-cache>          = Pre-load a script to populate the cache.
  -D <var>:<type>=<value>     = Create a cmake cache entry.
  -G <generator-name>         = Specify a makefile generator.
  -E                          = CMake command mode.
  -i                          = Run in wizard mode.
  -L[A][H]                    = List non-advanced cached variables.
  -N                          = View mode only.
  -P <file>                   = Process script mode.
  --graphviz=[file]           = Generate graphviz of dependencies.
  --debug-trycompile          = Do not delete the try compile directories..
  --debug-output              = Put cmake in a debug mode.
  --help-command cmd [file]   = Print help for a single command and exit.
  --help-command-list [file]  = List available listfile commands and exit.
  --help-module module [file] = Print help for a single module and exit.
  --help-module-list [file]   = List available modules and exit.
  --copyright [file]          = Print the CMake copyright and exit.
  --help                      = Print usage information and exit.
  --help-full [file]          = Print full help and exit.
  --help-html [file]          = Print full help in HTML format.
  --help-man [file]           = Print a UNIX man page and exit.
  --version [file]            = Show program name/version banner and exit.

Generators

The following generators are available on this platform:
  KDevelop3                   = Generates KDevelop 3 project files.
  Unix Makefiles              = Generates standard UNIX makefiles.

NOTE

CMake no longer configures a project when run with no arguments.  In order to
configure the project in the current directory, run

  cmake .


Not sure what to do here????

---

### Post by Michael.Godawski on 2008-12-11
hi stevek123, 

what happens if you run this code in the stelarium directory:
```
./configure && make && sudo make install
```

---

### Post by stevek123 on 2008-12-11
wow Mike - you're fast! 
I get bashed when I run ./configure.... in the directory where I unloaded the code (stellarium10.0)

and it says in the install file that cmake is used and it is listed in the dependencies

---

### Post by Michael.Godawski on 2008-12-11
I guess I found it here:
run this and have a look at this [guide]("http://stellarium.org/wiki/index.php/Compilation_on_Linux"):
```
cmake ../..
```

---

### Post by jamesrl on 2008-12-11
EDIT: beaten (and gave wrong advice)

---

### Post by stevek123 on 2008-12-11
actually I tried that cmake ../.. and it gave me this...

steve@ubuntudesktop:~/Documents/stellarium10.0$ cmake ../..
CMake Error: The source directory "/home/steve" does not appear to contain CMakeLists.txt.
Specify --help for usage, or press the help button on the CMake GUI.

huh??? FWIW, it is specific in the code i downloaded that I must have cmake 2.4.7 - which I do.

plus I dont know where to find the cmake GUI... not in menus that i can see

and why did it look in /home/steve? should have been /home/steve/documents/stellarium10.0... and it IS there!

---

### Post by mc4man on 2008-12-11
see here (from install text in source

[http://stellarium.org/wiki/index.php/Compilation_on_Linux](http://stellarium.org/wiki/index.php/Compilation_on_Linux)

---

### Post by Michael.Godawski on 2008-12-11
ok, the latest version in synaptics is 0.9.1-4. This will work for sure, but let's try to compile this one. I am downloading the sourceright now to check it.

---

### Post by Michael.Godawski on 2008-12-11
hey mc4man, 
I have posted this guide already in my previous posts, but nonetheless you are allowed to think with us :p

stevek123
did you follow all the steps in the guide, like installing all the dependencies:
```
sudo apt-get install build-essential libfreetype6-dev cmake libpng12-dev zlib1g-dev \
     libglu1-mesa-dev libgl1-mesa-dev gcc g++ gettext libboost-dev libboost-thread-dev \
     libjpeg-dev libboost-filesystem-dev subversion libqt4-dev graphviz doxygen qt4-designer
```

---

### Post by stevek123 on 2008-12-11
yah Mike - I already run 0.9... but wanted the upgrade - told you I'm a dummy... missed the step to make the build directory. OOPS. it wanted to cmake but gave me this error...

CMake Error: The installed Qt version 4.3.4 is too old, at least version 4.4.1 is required
-- Configuring done

Guess I didnt get all depends... BUT qt4.4.1 is NOT listed in synaptic. Now what ???
FWIW I'm running hardy...

---

### Post by stevek123 on 2008-12-11
> **Michael.Godawski said:**
> hey mc4man, 
I have posted this guide already in my previous posts, but nonetheless you are allowed to think with us :p

stevek123
did you follow all the steps in the guide, like installing all the dependencies:
```
sudo apt-get install build-essential libfreetype6-dev cmake libpng12-dev zlib1g-dev \
     libglu1-mesa-dev libgl1-mesa-dev gcc g++ gettext libboost-dev libboost-thread-dev \
     libjpeg-dev libboost-filesystem-dev subversion libqt4-dev graphviz doxygen qt4-designer
```

Yes Mike - I ran that

---

### Post by Michael.Godawski on 2008-12-11
Well on this page, it seems there are the newer versions:

[http://trolltech.com/downloads/opensource/appdev](http://trolltech.com/downloads/opensource/appdev)

But I cannot download them, page load error. And they seem to be very large like 100MB; if we had to compile them it would take many hours. 

So I am not really convinced now if compiling the latest releases of stellarium is worth the hassle, are you?

---

### Post by stevek123 on 2008-12-11
I'm a telescope geek - and stellarium really rocks!!! I use 2 other versions almost every day and have for several years. Several upgrades in this version are worth the hassle (light pollution controls especially) - and I'm such a noob at this 'build' stuff that the effort is good learning. Thanks so much for the help tho!!!

---

### Post by Michael.Godawski on 2008-12-11
no problem, I am still here and thinking and thinking...

---

### Post by Michael.Godawski on 2008-12-11
perhaps this:

[http://www.cmake.org/cmake/help/runningcmake.html](http://www.cmake.org/cmake/help/runningcmake.html)


run this in the stellarium dir:

```
ccmake .    
make
```or 

```
cmake .
make
```do not forget the DOT

---

### Post by stevek123 on 2008-12-11
> **Michael.Godawski said:**
> perhaps this:

[http://www.cmake.org/cmake/help/runningcmake.html](http://www.cmake.org/cmake/help/runningcmake.html)


run this in the stellarium dir:

```
ccmake .    
make
```or 

this gives me the option to change to different cmake version....

```
cmake .
make
```do not forget the DOT

this gives me same error message about qt4.3 too old

I'm downloading 4.4.1 source code while I type. Maybe I'll try that path (YUK!!!) another option I might try is to edit the config files in the stellarium source code to accept the older version of qt. Might work & might not...

gotta take the kids to school in a couple of hours - time to nap... I'll be back...

---

### Post by SeanHodges on 2008-12-11
> **stevek123 said:**
> this gives me same error message about qt4.3 too old

I'm downloading 4.4.1 source code while I type. Maybe I'll try that path (YUK!!!) another option I might try is to edit the config files in the stellarium source code to accept the older version of qt. Might work & might not...

gotta take the kids to school in a couple of hours - time to nap... I'll be back...

It seems you've already discovered that the version of QT that comes with Ubuntu 8.04 (Hardy Heron) is too old for the latest version of Stellarium... The correct version (QT 4.4) is available in the "backports" repository:

See the package here: [http://packages.ubuntu.com/hardy-backports/qt4-doc](http://packages.ubuntu.com/hardy-backports/qt4-doc)

Information on how to install it here: [https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

Give a shout if you have trouble installing it, using the backports repository will be *much* easier than compiling the whole of QT from source.

I can't see any other dependencies that will be out-of-date, so once you get QT 4.4 installed it should compile OK.

---

### Post by stevek123 on 2008-12-11
Hey Sean - thanks - backports repository, never knew to look there. Interesting! Bummer tho. Best they offer is qt4.4.0 and stellarium requires "at least 4.4.1".

---

### Post by scotty64 on 2008-12-31
> **stevek123 said:**
> Hey Sean - thanks - backports repository, never knew to look there. Interesting! Bummer tho. Best they offer is qt4.4.0 and stellarium requires "at least 4.4.1".

Steve: No problem. There is a simple tweak to compile stellarium with 4.4.0:

- Unpack stellarium-0.10.0.tgz and go into the stellarium-0.10.0 directory.
- gedit CMakeLists.txt
- Find the line SET(QT_MIN_VERSION "4.4.1") and modify it to
  SET(QT_MIN_VERSION "4.4.0")
- build stellarium  as explained in
[http://stellarium.org/wiki/index.php/Compilation_on_Linux](http://stellarium.org/wiki/index.php/Compilation_on_Linux)

works excellent here!
Happy New Year and happy Stellarium...

---

