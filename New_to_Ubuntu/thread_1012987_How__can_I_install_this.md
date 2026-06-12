---
title: "How  can I install this?"
date: 2008-12-16
forum: New to Ubuntu
---

### Post by DOS4dinner on 2008-12-16
I need this fancy, moded version of DOSBox to get 3D emulation.

All he gives is a .tar.gz with some source code and some shell scripts inside of it.

[It can be downloaded here]("http://www.si-gamer.net/gulikoza/")

I've never installed from source, and I don't know how to use the scripts if they can install it for me.

Thanks!

---

### Post by cmnorton on 2008-12-16
0) Open an X-term

1) Create a directory for the source, and make sure the zipped tar file is in your current directory.

2) cd to that directory

3) tar -xzf ../dos-thingie.tar.gz

4) You should have some files there like a README or readme, perhaps configure, and perhaps a makefile.

Without listing all the files, look for something that will configure and install. 

Probably best to invoke it with sudo, because root will have to install it, but not necessarily build it.

---

### Post by DOS4dinner on 2008-12-16
Inside, amongst source:

okay, I looked at the install readme.

It said to run ./configure, so I did so in the directory,

Now, it came up with this error:

```
checking for SDL - version >= 1.2.0... no
*** Could not run SDL test program, checking why...
*** The test program compiled, but did not run. This usually means
*** that the run-time linker is not finding SDL or finding the wrong
*** version of SDL. If it is not finding SDL, you'll need to set your
*** LD_LIBRARY_PATH environment variable, or edit /etc/ld.so.conf to point
*** to the installed location  Also, make sure you have run ldconfig if that
*** is required on your system
***
*** If you have an old version installed, it is best to remove it, although
*** you may also be able to get things to work by modifying LD_LIBRARY_PATH
configure: error: *** SDL version 1.2.0 not found!
```

I have SDL installed..it says so in synaptic.

---

### Post by taurus on 2008-12-16
You need the developing package, -dev, also.

---

### Post by deputy on 2008-12-16
Looks like you might not have the correct version of SDL installed.

---

### Post by DOS4dinner on 2008-12-16
Craters...I screwed something up. Now no SDL app is working.

would running any of these destroy everything?

1. cp ./libSDL-1.2.so.0.11.1 /usr/local/lib 
2.  ln -s /usr/local/lib/libSDL-1.2.so.0.11.1 /usr/local/lib/libSDL.so
3.  ln -s /usr/local/lib/libSDL-1.2.so.0.11.1 /usr/local/lib/libSDL-1.2.so.0

If so, how can I fix it?

---

### Post by taurus on 2008-12-16
What's the output of this command?

```
ls -la /usr/local/lib
```

---

### Post by DOS4dinner on 2008-12-16
```
total 548
drwxr-xr-x  4 root root    4096 2008-12-16 08:58 .
drwxr-xr-x 10 root root    4096 2008-04-22 10:48 ..
lrwxrwxrwx  1 root root      35 2008-12-16 08:58 libSDL-1.2.so.0 -> /usr/local/lib/libSDL-1.2.so.0.11.1
-rwxr-xr-x  1 root root  538684 2008-12-16 08:56 libSDL-1.2.so.0.11.1
lrwxrwxrwx  1 root root      35 2008-12-16 08:58 libSDL.so -> /usr/local/lib/libSDL-1.2.so.0.11.1
drwxrwsr-x  3 root staff   4096 2008-08-26 11:01 python2.5
drwxr-xr-x  3 root root    4096 2008-10-31 16:31 site_ruby
```

---

### Post by taurus on 2008-12-16
Just remove that file and those two links.

```
cd /usr/local/lib
sudo rm libSDL*
ls -la
```

---

### Post by carml on 2008-12-16
In my opinion there are two options to evaluate:
1.Are you sure that a package for that emulator isn't available?
2.To compile the source maybe you need to install the package build essential. :confused:

---

### Post by DOS4dinner on 2008-12-16
> **taurus said:**
> Just remove that file and those two links.

```
cd /usr/local/lib
sudo rm libSDL*
ls -la
```

That fixed it. Thanks! I'll see if I can install it now.

---

### Post by DOS4dinner on 2008-12-16
Okay...I typed "make" in the directory. Now what? It finished doing whatever it was doing.

It ended with this at the end:
```

i386.cpp: In function ‘float MT32Emu::iir_filter_sse(float, float*, float*)’:
i386.cpp:142: error: unknown register name ‘xmm3’ in ‘asm’
i386.cpp:142: error: unknown register name ‘xmm2’ in ‘asm’
i386.cpp:142: error: unknown register name ‘xmm1’ in ‘asm’
make[3]: *** [i386.o] Error 1
make[3]: Leaving directory `/home/jeff/DOSbuild2/dosbox/src/gui'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/jeff/DOSbuild2/dosbox/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/jeff/DOSbuild2/dosbox'
make: *** [all] Error 2
```

---

### Post by DOS4dinner on 2008-12-16
Okay, I'm probably doing everything wrong. Assuming a clean installation of Ubuntu, what would I need to do?

---

### Post by albinootje on 2008-12-16
> **DOS4dinner said:**
> 
configure: error: *** SDL version 1.2.0 not found![/CODE]

I have SDL installed..it says so in synaptic.

 sudo apt-get install libsdl1.2-dev

---

### Post by DOS4dinner on 2008-12-16
> **albinootje said:**
> sudo apt-get install libsdl1.2-dev

Thanks, but that part was already solved :)

---

### Post by albinootje on 2008-12-16
In 8.10 i've done the following :
sudo apt-get install libsdl1.2-dev libphysfs-dev libsdl-sound1.2-dev libsdl-net1.2-dev libpcap-dev build-essential

compiling now ... (just because i'm curious).

It more or less ends with :

drive_physfs.cpp: In member function ‘virtual void* physfsDrive::opendir(const char*)’:
drive_physfs.cpp:418: error: ‘malloc’ was not declared in this scope
drive_physfs.cpp:422: error: ‘free’ was not declared in this scope
drive_physfs.cpp: In member function ‘virtual void physfsDrive::closedir(void*)’:
drive_physfs.cpp:434: error: ‘free’ was not declared in this scope
drive_physfs.cpp: In constructor ‘physfsDrive::physfsDrive(const char*, Bit16u, Bit8u, Bit16u, Bit16u, Bit8u)’:
drive_physfs.cpp:482: error: ‘free’ was not declared in this scope
drive_physfs.cpp: In member function ‘virtual bool physfsFile::Write(Bit8u*, Bit16u*)’:
drive_physfs.cpp:530: warning: format ‘%i’ expects type ‘int’, but argument 3 has type ‘PHYSFS_sint64’
make[3]: *** [drive_physfs.o] Error 1

Then read the INSTALL file, it basically says "if building from cvs, use ./autogen.sh".
After : make clean ; sudo apt-get install autoconf automake
and running first ./autogen.sh it bailed out at with the same error.

---

