---
title: "How to install MAKEFILE"
date: 2009-04-23
forum: New to Ubuntu
---

### Post by TomErwin on 2009-04-23
I am an absolute "new bee" though I been using Ubuntu for a couple of weeks now, I can not get to install "makefile" files...
I have a sn9c102 webcam. I got the driver which was this compressed file... [http://www.linux-projects.org/downloads/sn9c1xx-1.48.tar.gz](http://www.linux-projects.org/downloads/sn9c1xx-1.48.tar.gz)
I don't know how to install the 'makefile' thing. 
Please point me out how I can install this... as simple and specific as you ever can. please do not asume that I know much. I know how to use "Terminal". I guess that's all I can do with Ubuntu :(
Thanks in advance...

---

### Post by aeiah on 2009-04-23
providing you have the kernel headers and such for your kernel (you can get them from within synaptic) then the usual method for compiling is:

- unpack the tar either on the commandline or gui

- navigate to the folder from the terminal (with the cd command)

- most programs will have a readme or install that tells you what to do but its almost always, from the terminal whilst in the directory you unpacked the tar to:

```

./configure
make
sudo make install

```

---

### Post by tedrogers on 2009-11-25
I need help on this too...I've always had problems compiling source code. I have build-essential installed and 'dpkg -l build-essential' proves this as far as I can tell:

```
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                 Version                              Description
+++-====================================-====================================-========================================================================================
ii  build-essential                      11.4                                 Informational list of build-essential packages
```

I'm trying to install a file called 'kwiirk-wbfs-977437d.tar.gz' and it is already uncompressed. I have gone to the terminal and navigated to the correct folder.

When I do './configure' I get this:

```
bash: ./configure: No such file or directory
```

When I do 'make' I get *all* of this:

```
gcc -Wall -W -O3 -Ilibwbfs -I. -DLARGE_FILES -D_FILE_OFFSET_BITS=64 -c tools.c -o tools.o 
tools.c:8:25: error: openssl/md5.h: No such file or directory
tools.c:9:25: error: openssl/aes.h: No such file or directory
tools.c:10:25: error: openssl/sha.h: No such file or directory
tools.c: In function ‘md5’:
tools.c:69: warning: implicit declaration of function ‘MD5’
tools.c: In function ‘sha’:
tools.c:74: warning: implicit declaration of function ‘SHA1’
tools.c: In function ‘aes_cbc_dec’:
tools.c:104: error: ‘AES_KEY’ undeclared (first use in this function)
tools.c:104: error: (Each undeclared identifier is reported only once
tools.c:104: error: for each function it appears in.)
tools.c:104: error: expected ‘;’ before ‘aes_key’
tools.c:106: warning: implicit declaration of function ‘AES_set_decrypt_key’
tools.c:106: error: ‘aes_key’ undeclared (first use in this function)
tools.c:107: warning: implicit declaration of function ‘AES_cbc_encrypt’
tools.c:107: error: ‘AES_DECRYPT’ undeclared (first use in this function)
tools.c: In function ‘aes_cbc_enc’:
tools.c:112: error: ‘AES_KEY’ undeclared (first use in this function)
tools.c:112: error: expected ‘;’ before ‘aes_key’
tools.c:114: warning: implicit declaration of function ‘AES_set_encrypt_key’
tools.c:114: error: ‘aes_key’ undeclared (first use in this function)
tools.c:115: error: ‘AES_ENCRYPT’ undeclared (first use in this function)
tools.c: In function ‘do_yaz0’:
tools.c:335: warning: unused parameter ‘in_size’
make: *** [tools.o] Error 1
```

And when I do 'sudo make install' I get this:

```
make: *** No rule to make target `install'. Stop.
```

HELP!

Thanks.

---

### Post by Some Penguin on 2009-11-25
A makefile is simply a set of instructions.  It's not a package to install.  A makefile essentially defines targets (one of which is possibly a default target), each of which may depend on other targets or files.  The 'make' program simply accepts the target, determines which targets need to be built and in what order, and follows the associated instructions.

These instructions tend to relate to just compilation, linking, and copying.  They tend to *not* involve anything that will automagically detect and fetch missing libraries and header files, so reading the instructions and making sure that you have already installed all prerequisites (and desired optional dependencies, if such exist) is necessary.

For the multitude of programs set up for autoconf, the 'configure / make / make install' sequence *is* usual.  That's a sequence; if one of the steps fails, you shouldn't really bother proceeding with the previous one.  'configure', which may perhaps need to be run as 'sh configure' or './configure', typically checks your system configuration, alerts you to missing packages, and (if no problems are found) writes an appropriate Makefile.    If there isn't a 'configure' script, it's probably not an autoconf package and you should be reading the package-specific instructions, which you should be in any case.  Some may have multiple configuration setups for different operating systems, some may require manual editing of Makefiles and header files, and so forth.

And when you see something like 'openssl/aes.h is missing', that tells you that you're probably missing a package (perhaps along the lines of openssl or openssl-dev), or maybe you have an openssl package but it wasn't built to support functionality that the package you're trying to build requires.  You need to either build and install openssl (and with the -dev package, if there are both a -dev and non-dev; the latter may be missing the header files used to build more packages and just contain the associated libraries), or you need to tweak the configuration of your present build to remove that dependency (if possible).  Don't expect every package to be set up the same way, although autoconf *is* fairly common these days.

---

### Post by tedrogers on 2009-11-26
Well thanks for explaining that to me...I feel I understand a little better now.

I'll give it a shot!

---

