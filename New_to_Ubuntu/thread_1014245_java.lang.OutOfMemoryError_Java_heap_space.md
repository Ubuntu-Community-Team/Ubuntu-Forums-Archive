---
title: "java.lang.OutOfMemoryError: Java heap space"
date: 2008-12-17
forum: New to Ubuntu
---

### Post by sah302 on 2008-12-17
Forgive me if this is posted in the wrong forum, I posted it here because I am a total beginner.

Hi all, I just started using ubuntu yesterday, and so far I think it's really cool! Of course it has been a struggle learning some stuff coming from Windows but thanks to my google-fu (and mostly this site) I have been managing well enough.

However, recently I have come across a problem I can't seem to find a solution for.

I have been trying to get replay ([http://replay.origo.ethz.ch/](http://replay.origo.ethz.ch/)) up and running on my new ubuntu box. I did everything they outlined here: [http://www.replay.ethz.ch/docs/manual/installation/release/linux](http://www.replay.ethz.ch/docs/manual/installation/release/linux)

But I can an error when executing the sudo ant thirdparty command.

This is the error that I get:

BUILD FAILED
/home/sah302/replay-0.5/thirdparty/build/scripts/thirdparty.xml:153: The following error occurred while executing this line:
/home/sah302/replay-0.5/thirdparty/build/scripts/thirdparty.xml:226: java.lang.OutOfMemoryError: Java heap space

Thank you in advance for any help.

---

### Post by Shhnap on 2008-12-17
Ok try these two things for me:

Applications -> Accessories -> Terminal

In the terminal:

```
sudo apt-get install autoconf automake libtool pkgconfig gcc gcc-c++ yacc ruby

```
Then:

System -> Administration -> Synaptic Package Manager -> Search

Query: ```
sun-java6
```

Tick every box you see and click apply.


Now try and install replay again. Hope that works. :)

---

### Post by sah302 on 2008-12-17
Ah I forgot to mentioned I have grabbed all those apps.

However, after checking all the java stuff. It got further than before! Woot, but now another error =/. Here is the output:

 [exec] /usr/share/automake-1.10/am/depend2.am: am__fastdepCXX does not appear in AM_CONDITIONAL
     [exec] /usr/share/automake-1.10/am/depend2.am:   The usual way to define `am__fastdepCXX' is to add `AC_PROG_CXX'
     [exec] /usr/share/automake-1.10/am/depend2.am:   to `configure.in' and run `aclocal' and `autoconf' again.
     [exec] plugins/mpeg4ip/Makefile.am: C++ source seen but `CXX' is undefined
     [exec] plugins/mpeg4ip/Makefile.am:   The usual way to define `CXX' is to add `AC_PROG_CXX'
     [exec] plugins/mpeg4ip/Makefile.am:   to `configure.in' and run `autoconf' again.
     [exec] Makefile.am: installing `./INSTALL'

BUILD FAILED
/home/sah302/replay-0.5/thirdparty/build/scripts/thirdparty.xml:158: The following error occurred while executing this line:
/home/sah302/replay-0.5/thirdparty/build/scripts/thirdparty.xml:440: exec returned: 1

It seems something isn't configured right?

---

### Post by Shhnap on 2008-12-17
Ok, in the source directory try running

aclocal
autoconf

Then try again. :) Maybe we'll get further.

---

### Post by Hospadar on 2008-12-17
EDIT: it might be something else now that I see your further errors.


The issue is the jvm (the java virtual machine) doesn't have enough memory, you'll need to allocate it more.
I have no experience, but from this page:
[http://ant.apache.org/manual/running.html](http://ant.apache.org/manual/running.html)
It looks like you can set an environment variable ANT_OPTS that ant will read and pass as arguments to the jvm.

so try:```
ANT_OPTS=-Xmx512m
sudo ant thirdparty
```if it still happens, try upping the memory even more (change 512 to something bigger, 768 or 1024 maybe).
If it won't run on 1024, Most likely I'm wrong about how ANT_OPTS work.  But maybe google around for stuff like "ant passing arguments options to jvm" etc.

---

### Post by sah302 on 2008-12-17
Oh no! now it only made it to 1minute 44 seconds after putting in that memory variable, before doing a BUILD FAIL, last time it got to 5 minutes ><.

Output this time:

libfaad.download:

libfaad.make:
     [echo] Building libfaad 2.6.1
     [echo] Bootstrapping libfaad build environment
     [exec] /usr/share/automake-1.10/am/depend2.am: am__fastdepCXX does not appear in AM_CONDITIONAL
     [exec] /usr/share/automake-1.10/am/depend2.am:   The usual way to define `am__fastdepCXX' is to add `AC_PROG_CXX'
     [exec] /usr/share/automake-1.10/am/depend2.am:   to `configure.in' and run `aclocal' and `autoconf' again.
     [exec] plugins/mpeg4ip/Makefile.am: C++ source seen but `CXX' is undefined
     [exec] plugins/mpeg4ip/Makefile.am:   The usual way to define `CXX' is to add `AC_PROG_CXX'
     [exec] plugins/mpeg4ip/Makefile.am:   to `configure.in' and run `autoconf' again.

BUILD FAILED
/home/sah302/replay-0.5/thirdparty/build/scripts/thirdparty.xml:158: The following error occurred while executing this line:
/home/sah302/replay-0.5/thirdparty/build/scripts/thirdparty.xml:440: exec returned: 1


I tried using those commands for aclocal and autoconf in the source directory, and got the following:

aclocal: `configure.ac' or `configure.in' is required
autoconf: no input file

---

### Post by Shhnap on 2008-12-17
um whoops about the thing that the other guy suggested. I don't know how to solve that one. Maybe somebody else can help. And try inputting the config files into autoconf and aclocal. It's been a while since i used them, i forget how they work.

(Sorry I know that that's lame help)

---

### Post by sah302 on 2008-12-17
I am not quite sure what you mean? Put what config files into where? I thought aclocal and autoconf were commands not places ><. I am  newb. Also just looking up even though it stopped much earlier in the build. The error is the exact same as the one posted a few posts up. It seems like I need to add AC_PROG_CXX in configure.in and then I need to run aclocal and autoconf again. But where is this configure.in? I can't seem to locate it.

---

