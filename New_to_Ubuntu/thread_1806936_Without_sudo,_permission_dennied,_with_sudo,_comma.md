---
title: "Without sudo, permission dennied, with sudo, command not found"
date: 2011-07-18
forum: New to Ubuntu
---

### Post by evading_nun on 2011-07-18
Hi, first post here, so bear with me!
I'm trying to build apr (as per [this]("http://www.ros.org/wiki/nao/Tutorials/Cross-Compiling#Cross-Compiling_of_non-ROS_modules") tutorial) and I'm getting some problems.
I type *make*, and everything goes ok, then I type *make install* and get the output
> make[1]: Entering directory `/home/gavin/xcomros/apr-1.4.2'
make[1]: Nothing to be done for `local-all'.
make[1]: Leaving directory `/home/gavin/xcomros/apr-1.4.2'
/home/gavin/xcomros/apr-1.4.2/build/mkdir.sh /media/external/ros/ros-deps//lib /media/external/ros/ros-deps//bin /media/external/ros/ros-deps//build-1 \
		     /media/external/ros/ros-deps//lib/pkgconfig /media/external/ros/ros-deps//include/apr-1
/usr/bin/install -c -m 644 /home/gavin/xcomros/apr-1.4.2/include/apr.h /media/external/ros/ros-deps//include/apr-1
/usr/bin/install: cannot remove `/media/external/ros/ros-deps//include/apr-1/apr.h': Permission denied
make: *** [install] Error 1


The problem is obviously the permission denied, so when I try it with *sudo*, the output I get is
> make[1]: Entering directory `/home/gavin/xcomros/apr-1.4.2'
make[1]: Nothing to be done for `local-all'.
make[1]: Leaving directory `/home/gavin/xcomros/apr-1.4.2'
/home/gavin/xcomros/apr-1.4.2/build/mkdir.sh /media/external/ros/ros-deps//lib /media/external/ros/ros-deps//bin /media/external/ros/ros-deps//build-1 \
		     /media/external/ros/ros-deps//lib/pkgconfig /media/external/ros/ros-deps//include/apr-1
/usr/bin/install -c -m 644 /home/gavin/xcomros/apr-1.4.2/include/apr.h /media/external/ros/ros-deps//include/apr-1
for f in /home/gavin/xcomros/apr-1.4.2/include/apr_*.h; do \
	    /usr/bin/install -c -m 644 ${f} /media/external/ros/ros-deps//include/apr-1; \
	done
/bin/bash /home/gavin/xcomros/apr-1.4.2/libtool --mode=install /usr/bin/install -c -m 755 libapr-1.la /media/external/ros/ros-deps//lib
libtool: install: /usr/bin/install -c -m 755 .libs/libapr-1.lai /media/external/ros/ros-deps//lib/libapr-1.la
libtool: install: /usr/bin/install -c -m 755 .libs/libapr-1.a /media/external/ros/ros-deps//lib/libapr-1.a
libtool: install: chmod 644 /media/external/ros/ros-deps//lib/libapr-1.a
libtool: install: i586-linux-ranlib /media/external/ros/ros-deps//lib/libapr-1.a
/home/gavin/xcomros/apr-1.4.2/libtool: line 950: i586-linux-ranlib: command not found
make: *** [install] Error 127


After a bit of jiggery-pokery, I found that *i586-linux-ranlib* is a proper command WITHOUT su privileges, but if I type *sudo i586-linux-ranlib*, I get
> sudo: i586-linux-ranlib: command not found

tl;dr: *make install* needs su privileges to do one thing, but one of the commands it runs won't work with su privileges
Any and all help would be greatly appreciated, if more details are needed, please let me know

---

### Post by lkraemer on 2011-07-18
I'm assuming you have the Linux Headers installed for your Kernel and that
you have build-essential installed.  If you don't then you won't get it
to compile without errors.

**INSTALL REQUIRED SOFTWARE FOR COMPILE:**
Typically you need to install build-essential and the headers for the
kernel you are running, if you are going to compile code.
```

uname -r

```
will tell you the kernel you are currently running.
```

sudo apt-get install build-essential linux-headers-$(uname -r)

```
will install the software needed to compile your code.

You downloaded the source as a packagetoinstall.tar.gz
from there you should extract the source to it's folder or subdirectory.

**TYPICAL COMPILE STEPS: (from within your source directory)**
```

cd /pathtosource
./configure
make clean
make
sudo make install

```

"make clean" won't remove anything on the first compile, but will clean up
on a successive compile.  Sometimes ./configure isn't included in the source.

You can also use checkinstall to build a deb file.

**REF:**
[http://ubuntuguide.org/wiki/Ubuntu:Lucid](http://ubuntuguide.org/wiki/Ubuntu:Lucid)

```

man checkinstall

```


lk

---

### Post by evading_nun on 2011-07-19
Brilliant, that worked perfectly, thank you muchly!
EDIT: 
Turns out I'm a dirty liar, didn't work at all. But I now have more info:
It all built without errors because I forgot to do one of the first steps, i.e.:
> # some basic settings
export TARGETDIR=/media/external #this is where ROS will be installed to, see below
export ROS_ROOT=$TARGETDIR/ros/ros # ROS_ROOT, as usual
export ROS_PACKAGE_PATH=$ROS_ROOT/../stacks # ROS_PACKAGE_PATH, as usual
export CTC_DIR=/path/to/ctc-academics-1.6.13 # path to Aldebaran's cross-compilation toolchain
export ROS_DEPS=$ROS_ROOT/../ros-deps/
export CTC_USR_DIR=$CTC_DIR/staging/geode-linux/usr/
export CTC_BIN_DIR=$CTC_DIR/cross/geode/bin
export PYTHONPATH=$ROS_ROOT/core/roslib/src
export CPATH=$ROS_ROOT/../ros-deps/include/
export GEODE_CXX=$CTC_DIR/cross/geode/bin/i586-linux-g++
export GEODE_CC=$CTC_DIR/cross/geode/bin/i586-linux-gcc
export PATH=$CTC_BIN_DIR:$ROS_ROOT/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
export LD_LIBRARY_PATH=.

# automake compiler/linker flags
export LDFLAGS="-Wl,--sysroot,$CTC_DIR/staging/geode-linux/ -lgcc -L$CTC_DIR/cross/geode/i586-linux/lib/ -L$CTC_DIR/staging/geode-linux/usr/lib  -lc -lstdc++ -ldl"
export CPPFLAGS="--sysroot /$CTC_DIR/staging/geode-linux/ -I/$CTC_DIR/staging/geode-linux/usr/include/ -I/$CTC_DIR/cross/geode/lib/gcc/i586-linux/4.3.3/include/ -I/$CTC_DIR/staging/geode-linux/usr/include/c++/ -I/$CTC_DIR/staging/geode-linux/usr/include/c++/i586-linux/ -I/$CTC_DIR/cross/geode/i586-linux/include/c++/ -I/$CTC_DIR/cross/geode/i586-linux/include/c++/backward/ -I/$CTC_DIR/cross/geode/i586-linux/include/c++/i586-linux -I/$CTC_DIR/cross/geode/i586-linux/include/ -I/$CTC_DIR/staging/geode-linux/usr/lib"
export CFLAGS="-march=geode"
export CXXFLAGS="-march=geode"

So when I do that first (which I believe is necessary to what I'm trying to achieve), I get the *i586-linux-ranlib: command not found* error from before

---

