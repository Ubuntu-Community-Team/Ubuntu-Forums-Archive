---
title: "&quot;Can't find file or directory&quot; when the file exists"
date: 2011-06-16
forum: New to Ubuntu
---

### Post by TheHideousBirdchild on 2011-06-16
[IMG]http://i54.tinypic.com/skzzfk.png[/IMG]
(Sincerest apologies for the image file, I'm running Ubuntu in VMWare Fusion and I don't know if and/or how to keep copied text constant between this dumb iMac and Ubuntu. 6_9)

But um yes, I'm very new to Ubuntu, but despite be greatest efforts puzzling this together on my own, I have made very little progress.  The problem here appears to be in the last lines:
```

In file included from precompiled.h:23:0:
common.h:43:27: fatal error: boost/array.hpp: No such file or directory
compilation terminated.
make: *** [obj/fracplanet.gch/c++] Error 1
```I have the appropriate Boost libs installed, and can locate array.hpp within them manually and through the command prompt; it is only when I try to use it like this that it cannot be found.  What am I doing wrong, and are there other problems up in that brick of an image that I've missed?

Oh and I should've posted this in the first place, but I'm trying to install Fracplanet.

---

### Post by jtarin on 2011-06-16
Before you run configure take a look at your configure file in a text editor and it more than likely lists the "PATH=" to the application....change it to reflect yours. Before you run configure again in that directory....run...."make clean"

---

### Post by jtarin on 2011-06-16
I can tell you now that your going to have trouble configuring most anything new on such an outdated version of Ubuntu.

---

### Post by TheHideousBirdchild on 2011-06-16
No, I'm sorry but this *is* the newest release as far as I can tell; I'm running 11.04.

I searched through both the configure file and the makefile and neither of them turned up any results for PATH=.  Any other ideas?

---

### Post by deconstrained on 2011-06-16
This problem can most often be fixed by installing the 'development' packages (their names often end in "-dev") affiliated with the dependencies of the program you're trying to build from scratch; they should install header files to locations that are in the compiler's include path. For instance: the package libqt4-dev, according to "apt-cache show libqt4-dev":
> This package contains the header development files and development programs used for building Qt 4 applications.
So, you could start by firing up Synaptic or Ubuntu Software center and searching around for the libraries/programs that whatever you're trying to build depends on, and installing the development packages for them.

Some background: You notice this in the output -- 
```
boost/array.hpp
```
That's a *relative* path, as opposed to an *absolute* path (which would begin with a "/"). Thus, you must ask: what's it relative to?

When you run a compiler, there are some environment variables that dictate which paths are included as starting points for relative paths in the search for header files. If there's a header file that exists but isn't found, it's because no path can be constructed with the relative path provided in the Makefile and any of the paths in the path environment variables that actually leads to the header file.

---

### Post by TheHideousBirdchild on 2011-06-16
Thank you so much, but as far as I can tell I don't seem to be missing any libraries or anything; I found three that looked promising but none appear to have changed anything.

Also, I... can't make heads or tails of the latter half of your post.  The only place I got any results for searching "array", ".hpp", or "boost" was:
```

LIBS = $(SUBLIBS) -L/usr/lib -L/user/X11R6/lib -lboost_program_options -lQtOpenGL -lQtGui -lQtCore -lGLU -lGL -lpthread
```

Is this significant at all?

---

### Post by deconstrained on 2011-06-17
Did the source come with a configuration script of some sort? Have you reviewed the "README" and/or "INSTALL" files for instructions specific to building and installing that particular software (because it can differ from program to program)? Most respectable software source packages come with these files.

> **TheHideousBirdchild said:**
> Also, I... can't make heads or tails of the latter half of your post.
Which part of it? A basic understanding of paths, i.e. the difference between a relative path and an absolute path, is rather essential to using a computer (especially a Linux/Unix one) and yet so few computer people do and they end up confusing themselves.

About the rest of the second half:

Environment variables are set in the Makefile, the option flags passed to the compiler, the shell that you're using when you compile, the configuration of the compiler, or any combination of them. You generally should not have to mess with them manually when building something from scratch; if you have all the necessary dependencies *and* the header files of the shared libraries that the software needs in order to run properly, you'll be able to build it. The software package manager (in this case Debian's **apt**) should configure those packages, and the environment variables, so that any software you compile that requires the libraries/header files should be able to find them when you run the "configure" script (an executable you'll find in most source tarballs). That script will then set up the Makefile for properly building the source.

---

### Post by TheHideousBirdchild on 2011-06-17
There *is* a configure script; running it and then "make" does the same thing as ./BUILD.  The readme does not contain any notes at all about the program's requirements, nor does configure or the Makefile.  The website I obtained this from says that this should be trivial to build, and I cannot find anybody else who's had problems, which makes me think the problem is something very, very noobish.

All I need to know is why it can't find a file that's there; I understand the difference between relative and absolute, but I don't know why you've told me everything else that you've told me and I don't know how else to word that.

---

### Post by jtarin on 2011-06-17
There are .deb packages available....did you not try one of those?

From the web site:
> Assuming you have Qt and qmake (and a correctly set up gcc of course), it's trivial to build. 

---

### Post by TheHideousBirdchild on 2011-06-17
I've tried all three ("lenny", "karmic", and "jaunty") .deb files that are usable on my copy of Ubuntu; none appear to make a difference, or at least change the ultimate result of "no such file or directory".  (What exactly do these files do, out of curiosity?  Oh *god* I'm such a noob, I know...)

---

### Post by TheHideousBirdchild on 2011-06-17
Nevermind, I'm not sure how I solved the problem, but it's working now!  Thank you for your patience with me...

---

### Post by jtarin on 2011-06-17
> **TheHideousBirdchild said:**
> (What exactly do these files do, out of curiosity?  Oh *god* I'm such a noob, I know...)Think of those files as tools that you use to build. Qt and qmake are normally found in the KDE environment. On Gnome you need to install them.

---

