---
title: "Searching for torrentclient"
date: 2010-05-07
forum: New to Ubuntu
---

### Post by Bob Bertrands on 2010-05-07
Hey all

I'm searching for a torrentclient which can be installed WITHOUT USING  ROOT and can be operated using CLI.

I allready tried azureus but sadly can't get the commandline to work.

update: when trying to use azureus vuze as described here:
 [http://wiki.vuze.com/w/Console_UI](http://wiki.vuze.com/w/Console_UI)

I'm getting this error message:

     
     ```
Exception in thread "main" java.lang.NoClassDefFoundError: org/apache/commons/cli/CommandLine
Caused by: java.lang.ClassNotFoundException: org.apache.commons.cli.CommandLine
    at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:323)
    at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:268)
    at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:336)
Could not find the main class: org.gudy.azureus2.ui.common.Main. Program will exit.
```

---

### Post by cavh on 2010-05-07
I can help with the Java classpath error. Please post the output of 

```
ls -l /usr/lib/jvm
```

---

### Post by Bob Bertrands on 2010-05-07
This is the output of /usr/lib/jvm:

```
peer$ ls -l /usr/lib/jvm
total 8
lrwxrwxrwx  1 root root   23 2010-01-30 08:21 java-1.5.0-sun -> java-1.5.0-sun-1.5.0.22
drwxr-xr-x 10 root root 4096 2010-01-30 08:21 java-1.5.0-sun-1.5.0.22
drwxr-xr-x  7 root root 4096 2010-04-08 08:11 java-6-openjdk

```

---

### Post by cavh on 2010-05-07
Okay, we need to update your bash (shell) profile as follows: using your favourite editor, add the following entry to the end of the .bashrc file located in your home directory:

```
export PATH=$PATH:.
```

save the .bashrc file, then log out and back in, and try azureus again.

Please note the period in the filename .bashrc - it's a hidden file and you must type the period.

---

### Post by cavh on 2010-05-07
If the post above doesn't work, please indicate the folder location(s) of the commons-cli, log4j and the Azureus jar files so I can tell you to how to specify these on the command line when starting Azareus.

---

### Post by MrWES on 2010-05-07
> **Bob Bertrands said:**
> Hey all

I'm searching for a torrentclient which can be installed WITHOUT USING  ROOT and can be operated using CLI.

I allready tried azureus but sadly can't get the commandline to work.

update: when trying to use azureus vuze as described here:
 [http://wiki.vuze.com/w/Console_UI](http://wiki.vuze.com/w/Console_UI)

I'm getting this error message:

     
     ```
Exception in thread "main" java.lang.NoClassDefFoundError: org/apache/commons/cli/CommandLine
Caused by: java.lang.ClassNotFoundException: org.apache.commons.cli.CommandLine
    at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:323)
    at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:268)
    at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:336)
Could not find the main class: org.gudy.azureus2.ui.common.Main. Program will exit.
```

Well, you can install Transmission, which can run as a daemon and then manage it from the Web GUI or rTorrent. Here is the web site I used to setup Transmission on my headless server. 
[http://trac.transmissionbt.com/wiki/Scripts]("http://trac.transmissionbt.com/wiki/Scripts")

---

### Post by Bob Bertrands on 2010-05-07
Thanks for the quick reply. Sadly didn't work.

The location of commons-cli:

/usr/share/doc/libcommons-cli-java
/usr/share/java/commons-cli.jar

output of locate log4j:

```
/localhost/packages/eclipse/eclipse-3.5.1/plugins/org.apache.log4j_1.2.13.v200903072027.jar
/localhost/packages/eclipse/eclipse-3.5.1/plugins/com.google.appengine.eclipse.sdkbundle_1.2.5.v200909021031/appengine-java-sdk-1.2.5/config/user/log4j.properties
/localhost/packages/eclipse/eclipse-3.5.1/plugins/com.google.appengine.eclipse.sdkbundle_1.2.5.v200909021031/appengine-java-sdk-1.2.5/demos/new_project_template/src/log4j.properties
/localhost/packages/eclipse/eclipse-3.5.1/plugins/org.apache.ant_1.7.1.v20090120-1145/lib/ant-apache-log4j.jar
/localhost/packages/eclipse/eclipse-3.5.1/plugins/org.apache.axis_1.4.0.v200905122109/lib/log4j.properties
/localhost/packages/eclipse/eclipse-cdt/plugins/org.apache.ant_1.7.0.v200803061910/lib/ant-apache-log4j.jar
/localhost/packages/eclipse/eclipse-pdt/plugins/org.apache.log4j_1.2.13.v200903072027.jar
/localhost/packages/eclipse/eclipse-pdt/plugins/org.apache.ant_1.7.1.v20090120-1145/lib/ant-apache-log4j.jar
/localhost/packages/eclipse/eclipse-pdt/plugins/org.apache.axis_1.4.0.v200905122109/lib/log4j.properties
/localhost/packages/fortran/intel_fc/11.0.069/Compiler/11.0/069/idb/gui/ia32/plugins/org.apache.ant_1.6.5/lib/ant-apache-log4j.jar
/localhost/packages/jee/SUNWappserver/lib/ant/lib/ant-apache-log4j.jar
/localhost/packages/jee/netbeans-6.7.1/harness/testcoverage/cobertura/lib/log4j-1.2.9.jar
/localhost/packages/jee/netbeans-6.7.1/java2/ant/lib/ant-apache-log4j.jar
/localhost/packages/protege/plugins/edu.stanford.smi.protegex.owl/log4j-1.2.12.jar
/localhost/packages/visual_paradigm/VP_Suite4.0/ormlib/log4j.jar

```location of Azureus files:

~/app/vezu/vuze/Azureus2.jar

---

### Post by Bob Bertrands on 2010-05-07
If I can't get azureus to work properly i'll probably do it like MrWES suggested.
Sounds interesting as well.

---

### Post by Ocxic on 2010-05-07
a common mistake with Azureus is that the 32bit version will NOT run on a 64bit OS (and vice versa) make sure your downloading the correct version for your system arch type.

---

### Post by Bob Bertrands on 2010-05-08
I'm using the 64-bit azureus on a 64-bit os

---

### Post by cavh on 2010-05-08
Okay, copy log4.jar into /usr/share/java and try this in a terminal:

```
java -classpath /usr/share/java ~/app/vezu/vuze -jar Azureus2.jar
```

---

### Post by Bob Bertrands on 2010-05-08
Can't put log4j.jar in /usr/share/java/ as I don't have no superuser access

---

### Post by cavh on 2010-05-08
Hmmm, not ideal (although, to be fair, you did mention in your initial post that the app had to run without root access ;). Try running the command nonetheless, it may be that Azareus knows where log4.jar is.

---

### Post by Bob Bertrands on 2010-05-08
```
$ java -classpath /usr/share/java ~/app/vezu/vuze -jar Azureus2.jar
Exception in thread "main" java.lang.NoClassDefFoundError: /home/me/app/vezu/vuze
Caused by: java.lang.ClassNotFoundException: .home.me.app.vezu.vuze
    at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:323)
    at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:268)
    at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:336)
Could not find the main class: /home/me/app/vezu/vuze. Program will exit.

```

The command doesn't have the desired result.

Does this mean java can't find log4.jar file?

---

### Post by Bob Bertrands on 2010-05-09
oops might have made a mistake. Will try again tonight when I have access to  the pc again

---

### Post by Bob Bertrands on 2010-05-10
nope didn't make mistake. If  I execute the command I get this error.

help?

---

### Post by cavh on 2010-05-10
Apologies, I made a typo in the command ('vezu' instead of 'vuze'). The command should read as follows:

```
java -classpath /usr/share/java ~/app/vuze/vuze -jar Azureus2.jar
```

---

### Post by Bob Bertrands on 2010-05-13
The file Azureus2.jar **is** in folder ~/app/**vezu**/vuze/

---

### Post by Dayofswords on 2010-05-13
how about just using deluge?

---

### Post by wojox on 2010-05-13
azureus vuze suck. Try [Command line BitTorrent client]("http://www.cyberciti.biz/tips/linux-command-line-bittorrent-client.html") it's python.

---

### Post by cavh on 2010-05-13
Okay, cd into ~/app/vezu/vuze and then run this command:


```
java -classpath . /usr/share/java -jar Azureus2.jar
```

---

### Post by Gossar on 2010-05-13
> **Dayofswords said:**
> how about just using deluge?

I second using [deluge]("http://deluge-torrent.org/").

---

### Post by Bob Bertrands on 2010-05-15
cavh,

Allready tried that but it doesn't work. I've given up on vuze.

Daysofsword,

I tried installing but far from all dependencies for deluge are met. 
will try installing from source...

---

### Post by Bob Bertrands on 2010-05-16
I've been trying to install transmission (the old transmission installed on the system doesn't allow remote connections)

So I put the upacked the tar.gz file, transferred it to the pc and ran ./configure
Next thing i get this 

```
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking how to create a ustar tar archive... gnutar
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognize dependent libraries... pass_all
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for g77... g77
checking whether we are using the GNU Fortran 77 compiler... yes
checking whether g77 accepts -g... yes
checking the maximum length of command line arguments... 98304
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
checking for g77 option to produce PIC... -fPIC
checking if g77 PIC flag -fPIC works... yes
checking if g77 static flag -static works... yes
checking if g77 supports -c -o file.o... yes
checking whether the g77 linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking whether we are using the GNU C++ compiler... (cached) yes
checking whether g++ accepts -g... (cached) yes
checking dependency style of g++... (cached) gcc3
checking for ANSI C header files... (cached) yes
checking whether time.h and sys/time.h may both be included... yes
checking for lrintf... no
checking for strlcpy... no
checking for strlcat... no
checking for daemon... yes
checking for dirname... yes
checking for basename... yes
checking for void*... yes
checking size of void*... 4
checking for a BSD-compatible install... /usr/bin/install -c
checking whether make sets $(MAKE)... (cached) yes
checking for ranlib... (cached) ranlib
checking for the pthreads library -lpthreads... no
checking whether pthreads work without any flags... no
checking whether pthreads work with -Kthread... no
checking whether pthreads work with -kthread... no
checking for the pthreads library -llthread... no
checking whether pthreads work with -pthread... yes
checking for joinable pthread attribute... PTHREAD_CREATE_JOINABLE
checking if more special flags are required for pthreads... no
checking for library containing socket... none required
checking for library containing gethostbyname... none required
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for OPENSSL... yes
checking for special C compiler options needed for large files... no
checking for _FILE_OFFSET_BITS value needed for large files... 64
checking how to copy va_list... va_copy
configure: invoking libevent's configure script
checking for GTK... no
checking for intltool >= 0.23... 0.36.2 found
checking for perl... /usr/local/bin/perl
checking for iconv... /usr/bin/iconv
checking for msgfmt... /usr/bin/msgfmt
checking for msgmerge... /usr/bin/msgmerge
checking for xgettext... /usr/bin/xgettext
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking for LC_MESSAGES... yes
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking for ngettext in libc... yes
checking for dgettext in libc... yes
checking for bind_textdomain_codeset... yes
checking for msgfmt... /usr/bin/msgfmt
checking for dcgettext... yes
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for wx-config... no
checking host system type... (cached) i686-pc-linux-gnu
configure: creating ./config.status
config.status: creating Makefile
config.status: creating transmission.spec
config.status: creating beos/Makefile
config.status: creating cli/Makefile
config.status: creating daemon/Makefile
config.status: creating libtransmission/Makefile
config.status: creating third-party/Makefile
config.status: creating third-party/miniupnp/Makefile
config.status: creating third-party/libnatpmp/Makefile
config.status: creating macosx/Makefile
config.status: creating wx/Makefile
config.status: creating wx/images/Makefile
config.status: creating gtk/Makefile
config.status: creating gtk/icons/Makefile
config.status: creating po/Makefile.in
config.status: executing depfiles commands
config.status: executing intltool commands
config.status: executing default-1 commands
config.status: executing po/stamp-it commands
=== configuring in third-party/libevent (/home/xxxx/app/transmission-1.06.orig/third-party/libevent)
configure: running /bin/bash ./configure '--prefix=/usr/local'  '--enable-static' '--disable-shared' '-q' --cache-file=/dev/null --srcdir=.
/bin/bash: ./config.guess: No such file or directory
configure: error: cannot guess build type; you must specify one
configure: error: ./configure failed for third-party/libevent

```I checked for configure.guess and it was there.

this is the README file:

```
README for Transmission
=======================

Transmission is a fast, easy, and free BitTorrent client.

It runs on Mac OS X (Cocoa interface),
Linux/NetBSD/FreeBSD/OpenBSD (GTK+ interface)
and BeOS (native interface).

Visit http://www.transmissionbt.com/ for more information.


Building Transmission
=====================

Transmission has an Xcode project file (Transmission.xcodeproj)
for building in Xcode.

Building a Transmission release from the command line:

    $ tar xvfj transmission-1.0.tar.bz2
    $ cd transmission-1.0
    $ ./configure -q && make -s
    $ su (if necessary for the next line)
    $ make install

Building Transmission from SVN (First Time):

    $ svn co svn://svn.m0k.org/Transmission/trunk Transmission
    $ cd Transmission
    $ ./autogen.sh
    $ ./configure -q && make -s

Building Transmission from SVN (Updating):

    $ cd Transmission
    $ svn up
    $ make -s

```

---

### Post by oldos2er on 2010-05-16
1.06 is over two years old, are you sure you need that version?

There are instructions for compiling transmission here: [http://trac.transmissionbt.com/wiki/Building](http://trac.transmissionbt.com/wiki/Building)

---

### Post by Bob Bertrands on 2010-05-18
Used latest version, stuff work's like a charm

Thanks to you all!!!

---

