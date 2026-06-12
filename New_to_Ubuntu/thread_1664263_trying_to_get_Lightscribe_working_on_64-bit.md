---
title: "trying to get Lightscribe working on 64-bit"
date: 2011-01-10
forum: New to Ubuntu
---

### Post by eyeofreason on 2011-01-10
I'm using 64 bit Ubuntu-Mint based on lucid. I would like to use my lightscribe. Can someone point me in the right direction. I have put Google to work but only find this  [http://sourceforge.net/projects/qlscribe/](http://sourceforge.net/projects/qlscribe/) and I can't seem to compile it properly. If that is the best way then I can post my results when i try to compile the .tar.gz. 

All help is much appreciated thank you in advance.

---

### Post by yeats on 2011-01-10
Can you paste in your compile errors here (in CODE tags)?

> I'm using 64 bit Ubuntu-Mint based on lucid.

Have you asked on the Linux Mint forums?

---

### Post by eyeofreason on 2011-01-10
I have not posted on Mint forums. I have just started trying it. I may have to try that. 

Here are the instructions given in the "installation" file. 

> 
Qt lightScribe Installaton instructions
=======================================

To compile and install, first download release from [http://qlscribe.sourceforge.net/](http://qlscribe.sourceforge.net/)
or check out project from subversion repository for particular release:

     svn co [https://qlscribe.svn.sourceforge.net/svnroot/qlscribe/tags/release-N.M](https://qlscribe.svn.sourceforge.net/svnroot/qlscribe/tags/release-N.M) qlscribe

or if you want to test latest development version:

     svn co [https://qlscribe.svn.sourceforge.net/svnroot/qlscribe/trunk](https://qlscribe.svn.sourceforge.net/svnroot/qlscribe/trunk) qlscribe

Then go to the source directory and type:

    mkdir build
    cd build
    cmake ..

(If you want to install in a different path, use instead:
    cmake .. -DCMAKE_INSTALL_PREFIX=/install/path)
    make
    sudo make install

If cmake fails to find lightScribe API specify environment variable LIGHTSCRIBEDIR:

    LIGHTSCRIBEDIR=/opt/lightscribe cmake ..

Include files should be in ${LIGHTSCRIBEDIR}/include and lib in ${LIGHTSCRIBEDIR}/lib

You need manually install dbus config and service files. They are located in INSTALL_PATH/share/qlscribe
So on my ubuntu system I do 
    sudo cp /usr/local/share/qlscribe/lightscribe.conf /etc/dbus-1/system.d/ 
    sudo cp /usr/local/share/qlscribe/org.lightscribe.Manager.service /usr/share/dbus-1/system-services/
    sudo /etc/init.d/dbus reload

Your system may have different path please refer dbus system daemon documentation

You need to download lightScribe SDK for qlscribe to build and lightScribe runtime
for qlscribe to run. For details see lightScribe webpage:

     [http://www.lightscribe.org/](http://www.lightscribe.org/)

Enjoy!



I downloaded the file and extracted it to my home folder.
I installed "cmake"

```
-- The CXX compiler identification is unknown
CMake Error: your CXX compiler: "CMAKE_CXX_COMPILER-NOTFOUND" was not found.   Please set CMAKE_CXX_COMPILER to a valid compiler path or name.
CMake Error at /usr/share/cmake-2.8/Modules/FindQt4.cmake:728 (MESSAGE):
  Could NOT find QtCore header
Call Stack (most recent call first):
  src/CMakeLists.txt:21 (FIND_PACKAGE)

```

thanks for the help.

---

### Post by yeats on 2011-01-10
Looks like you're missing a C++ compiler.  Try installing the build-essential package.  It's a meta-package that pulls in a number of commonly-needed development tools (intended for building Debian packages, but it's a nice shortcut).

```
sudo apt-get install build-essential
```

Then try the instructions again and post back.

---

### Post by eyeofreason on 2011-01-10
Ok, I installed build-essentials .
 
```
~/qlscribe-0.14/build $ cmake ..
CMake Error at /usr/share/cmake-2.8/Modules/FindQt4.cmake:728 (MESSAGE):
  Could NOT find QtCore header
Call Stack (most recent call first):
  src/CMakeLists.txt:21 (FIND_PACKAGE)


-- Configuring incomplete, errors occurred!
```

---

### Post by deanjm1963 on 2011-01-10
If you're just after a simple labler, go to [http://www.lightscribe.com/]("http://www.lightscribe.com/") and download the deb files for both the system software and simple-labeler.

Copy them to a temporary folder or somewhere you can find them easily.

You need to install ia32-libs.

At a terminal

```
sudo dpkg -i --force-architecture /path_to_lightscribe_debs/*.deb
```

That should have you up and running.

There is the laCie labeler if you want more fancy stuff, but it takes a week to burn a disk.

Hope this helps.

---

### Post by yeats on 2011-01-10
```
~/qlscribe-0.14/build $ cmake ..
CMake Error at /usr/share/cmake-2.8/Modules/FindQt4.cmake:728 (MESSAGE):
  Could NOT find QtCore header
Call Stack (most recent call first):
  src/CMakeLists.txt:21 (FIND_PACKAGE)


-- Configuring incomplete, errors occurred!
```

If you do want to continue installing this from source, when you hit these sorts of errors, you can usually search the repositories with keywords from the error (either via Synaptic Package Manager or by doing 

```
apt-cache search <keywords>
```)

In this case qtcore.  I would install libqt4-core and see if that allows installation to continue.

Of course, it sounds like the other poster has given you a good option that would certainly be easier ;-)

---

### Post by eyeofreason on 2011-01-12
Simple labeler works fine. Thanks to both of you!

---

