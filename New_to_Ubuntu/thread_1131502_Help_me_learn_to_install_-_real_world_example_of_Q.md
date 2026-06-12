---
title: "Help me learn to install - real world example of QTStalker"
date: 2009-04-20
forum: New to Ubuntu
---

### Post by the_pod on 2009-04-20
Hi.  First off, a little background.  I've been using Ubuntu for pushing a year now as my primary system. I can't use it exclusively for work reasons, but for everything else - this is my system.

I'm relatively committed to figuring out how to make Ubuntu work. [complaint] As a somewhat new user that is very comfortable around computers, I find some of the esoteric and self-imposed nonsense of Linux to be annoying, specifically the need for command line codes and the difficult time that new users that are actually quite computer literate have in trying to just learn the basics. [/complaint]

That said I'm ready to roll up my sleeves and figure this out.  What I'm trying to do right now is install the latest version of QTSTalker, a stock program.  The version in the repositories is about 4 iterations old and it seems that the backend has changed significantly.  So... I want to get up to speed with the latest.  Which is the purpose of this thread.

Any help from people is greatly appreciated.  I could probably read a bunch of threads and figure this out but I've read every thread in here that mentioned QTStalker to no avail.  TIA for those willing to take this journey with me and hopefully shed some light for others as well.

---

### Post by the_pod on 2009-04-20
As a primer, instructions are found at:  [http://qtstalker.sourceforge.net/install.html](http://qtstalker.sourceforge.net/install.html)

I'm going to be installing from source so that I can actually figure this out.

```

Installation
Requirements

    * A Linux or FreeBSD compatible or Mac OS X operating system.
    * Qt development library. At least Qt 3.3.* version. Qt 4 not yet supported.
    * Berkeley DB database. At least db-4.1 version. FreeBSD users are required to use the 4.3 version.
    * TA-Lib Technical Analysis Library. At least ta-lib-0.3.0 version. See below.

When upgrading Qtstalker from a previous source version, see the notes below.

See notes below about where stuff gets installed.
Installing via packages

Packages are available for some operating systems:

    * Debian packages

Installing from source

Note: Package users can ignore the following advice as this will be done automatically by the package installer.

Important (Qt): Ensure that Qt is installed properly. Also ensure that the $QTDIR environment variable is set (see below). Also ensure that 'qmake' and friends are available (e.g. add $QTDIR/bin to your $PATH).

Important (DB): Ensure that Berkeley DB is installed properly. If you installed Berkeley DB at a non-standard location, then edit the Qtstalker "configure" file (e.g. "INCLUDEPATH += /opt/local/include/db4").
And some installations miss symbolic links in the lib directory.

Important (TA-Lib): Ensure that TA-Lib is installed properly. Also ensure that the 'ta-lib-config' program is available on your $PATH
Hint for Ubuntu / Debian users

You need to install these packages before:

    * build-essential (meta package for compiler etc.)
    * libdb4.4-dev (for Berkely)
    * qt3-dev-tools (for qmake)
    * libqt3-mt-dev (this will also select much more packages to install, don't be afraid)

Install TA-Lib

Since version 0.34 of Qtstalker you must install TA-Lib separately before you install Qtstalker itself. In previous versions, TA-Lib was included in the Qtstalker source tree, but not now. You can download the source of TA-Lib e.g. with the command...

wget http://prdownloads.sourceforge.net/ta-lib/ta-lib-0.4.0-src.tar.gz

...entered in your terminal. Unpack the downloaded file, cd into the extracted folder and compile/install TA-Lib with the sequence

   1. ./configure
   2. make
   3. make install (as root)
   4. There may also need to modify something if an error like this appears when you start Qtstalker ...

      /usr/local/bin/qtstalker: error while loading shared libraries: libqtstalker.so.0: cannot open shared object file: No such file or directory

      To fix this add /usr/local/lib to your /etc/ld.so.conf file and run ldconfig -v (as root).

If you installed TA-Lib at a non-standard location, then edit the Qtstalker "configure" file (e.g. "INCLUDEPATH += /opt/local/include/ta-lib").

Also ensure that the 'ta-lib-config' program is available on your $PATH
Install Qtstalker
For Linux users

See important pre-requisite notes above.

    * Ensure that your shell QTDIR environment variable is set to point to the location of the root Qt directory. This setting is usually something like this: 'export QTDIR=/usr/lib/qt' or something similar to this. Failure to set this properly will result in make errors.
    * Unpack the Qtstalker source.
    * ./configure (this will create the Makefile)
    * make
    * make install (as root)

If you get errors about undefined symbols when you start qtstalker, then add /usr/local/lib to your /etc/ld.so.conf file and run ldconfig -v (as root).
For FreeBSD users

See important pre-requisite notes above.

    * Set a few environment variables in your shell.
      Enter this: 'export QTDIR=/usr/X11R6'
      Then enter this 'export QMAKESPEC=/usr/local/share/qt/mkspecs/freebsd-g++'.
      Failure to set these variables properly will result in make errors.
    * Unpack the Qtstalker source.
    * ./configure (this will create the Makefile)
    * make
    * make install (as root)

For Macintosh OS X users (Tiger 10.4+)

See important pre-requisite notes above.

Note: By default Qtstalker will only look for supporting libraries etc. under /usr/local/ so Mac users will need to tell Qtstalker via the "configure" file where to look for these. We cannot give explicit instructions because you might install some bits via Fink and other bits via MacPorts, etc. so the following notes are just a guide.

    * Get Berkeley DB using MacPorts.org (which would install stuff under /opt directory) or Fink.sf.net (which would install stuff under /sw directory)
      We have reports of needing e.g. 'cd /opt/local/lib; ln -s libdb-4.2.dylib libdb.dylib')
    * Get TA-Lib source and install as described above.
    * Get "Qt for Aqua" (i.e. not for X11). Trolltech says must be at least qt-3.3.5 version. You can get this via Fink, or MacPorts, or direct from Trolltech.
    * Set your shell QTDIR environment variable to point where you installed Qt.
      e.g. 'export QTDIR=/sw/lib/qt3mac' or something similar.
      Failure to set this properly will result in make errors.
    * Unpack the Qtstalker source.
    * Edit the "configure" file to be something like:
      qmake "DEFINES += QT_NO_COMPAT" "CONFIG += qt" "macx:INCLUDEPATH += /opt/local/include/db4" "macx:LIBS += -L/opt/local/lib" -o Makefile qtstalker.pro
    * ./configure (this will create the Makefile)
    * make
    * sudo make install
    * To start, type 'open /usr/local/bin/qtstalker.app'

Where does stuff get installed

    * The executable 'qtstalker' will be copied to the /usr/local/bin directory
    * The plugins will be copied to /usr/local/lib/qtstalker directory
    * The translation files will be copied to /usr/local/share/qtstalker/i18n directory
    * The docs will be copied to /usr/local/share/doc/qtstalker/html directory (see toc.html for the table of contents)

The user workspace is in your home at ~/.qtstalker/data1/ directory.

The user settings are persistent. On most platforms they are stored in the ~/.qt/qtstalkerrc plain-text file. On "Mac OS X" they are stored in a binary plist. See notes.
Updating from a previous version

If you are updating from a previous source version already installed on your system, it is best that you first uninstall the previous version first before you install the upgraded version. Doing this will better ensure a problem-free upgrade. Many upgrade errors can be caused by old plugins and libraries hanging around complicating things. You can uninstall the old version by doing 'sudo make uninstall' from the top directory of the old source install.
Updating from 0.33 to 0.35

When the newly installed 0.35 program starts, it will automatically upgrade the internal database used with 0.33 to a new format. The new user workspace will be ~/.qtstalker/data1/ and the old ~/.qtstalker/data0/ will remain in case you need it.

If you cancel the upgrade process, then you will need to clean up. Remove the ~/.qtstalker/data1/ directory and edit Qtstalker settings to set the "Version" back to 0.33 and each "data1" path back to "data0".

Version 0.32 and older are not supported, so you would need to import your raw data with the Quote plugins and add new indicators.
Using the current development source

See instructions for using CVS. 

```

---

### Post by the_pod on 2009-04-20
Let's focus on this:

```

Note: Package users can ignore the following advice as this will be done automatically by the package installer.

Important (Qt): Ensure that Qt is installed properly. Also ensure that the $QTDIR environment variable is set (see below). Also ensure that 'qmake' and friends are available (e.g. add $QTDIR/bin to your $PATH).

Important (DB): Ensure that Berkeley DB is installed properly. If you installed Berkeley DB at a non-standard location, then edit the Qtstalker "configure" file (e.g. "INCLUDEPATH += /opt/local/include/db4").
And some installations miss symbolic links in the lib directory.

Important (TA-Lib): Ensure that TA-Lib is installed properly. Also ensure that the 'ta-lib-config' program is available on your $PATH
Hint for Ubuntu / Debian users

You need to install these packages before:

    * build-essential (meta package for compiler etc.)
    * libdb4.4-dev (for Berkely)
    * qt3-dev-tools (for qmake)
    * libqt3-mt-dev (this will also select much more packages to install, don't be afraid)

```

**Question:  **What?  I have no idea what the very first part of the directions mean:

```

Important (Qt): Ensure that Qt is installed properly. Also ensure that the $QTDIR environment variable is set (see below). Also ensure that 'qmake' and friends are available (e.g. add $QTDIR/bin to your $PATH).

Important (DB): Ensure that Berkeley DB is installed properly. If you installed Berkeley DB at a non-standard location, then edit the Qtstalker "configure" file (e.g. "INCLUDEPATH += /opt/local/include/db4").
And some installations miss symbolic links in the lib directory.

Important (TA-Lib): Ensure that TA-Lib is installed properly. Also ensure that the 'ta-lib-config' program is available on your $PATH  
```

Much of the rest of the directions are self explanatory.  However, I don't know what an "environment variable" is, what "qmake" refers to, or how to edit my $PATH.  Can someone break this down in lay speak and tell me what to do?

Also, if someone could tell me why Linux non-repository installs get so convoluted just because I want to know, that'd be good, but I guess not absolutely necessary.

Thanks!  Once I get these things figured out then I'll plow forward with the rest.

---

### Post by R3N3G4D3 on 2009-07-15
Hey, I stumbled upon your thread trying to setup qtstalker 0.36 myself. Figured I'd help out, especially since you solved my problem for Berkley DB dependency (I didn't read the README, just did the usual configure, make, install followed by a google search after a failed compile :lolflag:). Not sure if you still need help though.

Basically an environmental variable is a global system variable (usually in all caps). For example, $PATH is an example of an environmental variable that Linux uses to find many programs (that way you can type "firefox" instead of "/usr/bin/firefox"). To check if the variable like $QTDIR is set just run "echo $QTDIR", if you get a blank line it's not set. To set it in bash just type "QTDIR=/path/to/qt/goes/here" filling in the path appropriately.

As far as qmake, qt3-dev-tools from Synaptic takes care of that.

Also, the reason non-repo installs are cumbersome is because you're actually compiling the application from source-code (on Windows that's done for you by the developer, and repo installs are actually pre-compiled for you by Ubuntu community).

---

### Post by swoody on 2009-07-15
the_pod: Sorry, but I can't help you out with your questions. However, I wanted to post here, in hopes of helping you out in the long run. It sounds like you are very knowledgable about computers in general. That's a very good thing! However, I think you still may be able to benefit from checking out the Free Ubuntu Beginner's Guide. It's a great resource when you're learning the ropes, or just touching up on your Linux skills. You can find the link in my signature, and download the .pdf from their website :)

---

### Post by mlamorey on 2009-08-16
I have been through the install a couple times. 'echo $QTDIR' always returns a blank line. but the program seems to work. the description from R3N3G4D3 definetly covers the whole "$PATH" issues. I cannot remember where $PATH is set.

I'm pretty sure that $QTDIR is something for Qt and if Qt was installed via synaptic it will be somewhere that is in you path.

Cheers

---

### Post by begarkitta on 2010-05-08
I am an absolute ubuntu beginner. I have just started and have not been using Windows for almost a month now. I stumbled on Qtstalker but do not know how to set NSE as Exchange. I have been struggling to historical EOD into my program. Any help!!!??? Please?

---

### Post by sadaruwan12 on 2010-05-08
> **mlamorey said:**
> I have been through the install a couple times. 'echo $QTDIR' always returns a blank line. but the program seems to work. the description from R3N3G4D3 definetly covers the whole "$PATH" issues. I cannot remember where $PATH is set.

I'm pretty sure that $QTDIR is something for Qt and if Qt was installed via synaptic it will be somewhere that is in you path.

Cheers

I think $QTDIR stands for the Qt installation directory and for its path.

---

