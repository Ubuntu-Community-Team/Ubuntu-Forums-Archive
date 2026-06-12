---
title: "Can't install gnu-go from make"
date: 2011-07-13
forum: New to Ubuntu
---

### Post by damien750 on 2011-07-13
Hey there. I'm trying to install gnu-go 2.6 to run a bot on KGS (a go server).

I've downloaded the tar.gz, extracted it, no problems.

I cd to downloads and into the gnugo-2.6 folder. When I ./configure, everything seems to be fine. However, when I sudo make, I get error messages. Tried the same thing with gnugo-3.0.0, and got the same error messages.

```
damien@joseki:~/Downloads/gnugo-3.0.0$ sudo make
make  all-recursive
make[1]: Entering directory `/home/damien/Downloads/gnugo-3.0.0'
Making all in utils
make[2]: Entering directory `/home/damien/Downloads/gnugo-3.0.0/utils'
gcc -DHAVE_CONFIG_H -I. -I. -I..     -g -O2 -c getopt.c
gcc -DHAVE_CONFIG_H -I. -I. -I..     -g -O2 -c getopt1.c
gcc -DHAVE_CONFIG_H -I. -I. -I..     -g -O2 -c random.c
gcc -DHAVE_CONFIG_H -I. -I. -I..     -g -O2 -c gg_utils.c
rm -f libutils.a
ar cru libutils.a getopt.o getopt1.o random.o gg_utils.o 
ranlib libutils.a
make[2]: Leaving directory `/home/damien/Downloads/gnugo-3.0.0/utils'
Making all in sgf
make[2]: Entering directory `/home/damien/Downloads/gnugo-3.0.0/sgf'
gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../engine     -I../utils     -I../interface    -g -O2 -Wall -W -Wpointer-arith -Wbad-function-cast -Wcast-qual -Wcast-align -Wwrite-strings -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wp,-lang-c89 -c sgfgen.c
cc1: error: unrecognized command line option "-lang-c89"
make[2]: *** [sgfgen.o] Error 1
make[2]: Leaving directory `/home/damien/Downloads/gnugo-3.0.0/sgf'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/damien/Downloads/gnugo-3.0.0'
make: *** [all-recursive-am] Error 2
damien@joseki:~/Downloads/gnugo-3.0.0$ 

```I know gnu-go has much newer versions that I can run, and have with no problem: but I'm specifically trying to run this older version which is easier for new players. Any advice?
I've googled the error "cc1: error: unrecognized command line option "-lang-c89"" to no avail.

---

### Post by damien750 on 2011-07-13
Bump after an hour

---

### Post by jtarin on 2011-07-13
Try commands:
```
./configure
```
```
make
```
```
sudo make install
```

---

### Post by damien750 on 2011-07-13
> **jtarin said:**
> Try commands:
```
./configure
``````
make
``````
sudo make install
```

I did, but when I run 'make', I get the error messages shown above. I tried going ahead and running 'make install' anyways, but errors return again, citing the problem with "-lang-c89"

---

### Post by jtarin on 2011-07-13
It is **not** "sudo make"....it's "make".
It is **not** "make install"....it's "sudo make install".

Do you have the Gnat compiler installed?
Have you tried "alien" to make it into a .deb package?

---

### Post by damien750 on 2011-07-14
> **jtarin said:**
> It is **not** "sudo make"....it's "make".
It is **not** "make install"....it's "sudo make install".

Do you have the Gnat compiler installed?
Have you tried "alien" to make it into a .deb package?

Thanks for your help so far, jtarin.

I made sure I correctly typed "make" and "sudo make install", but the error still occurred.
I did a sudo apt-get update and installed alien. I ran alien and turned the gnugo-2.6 into a deb. When I opened it, it popped up in ubuntu software center. I installed it via the "install" button. Everything seemed fine, but when I entered the command "gnugo" in console, it acted like the program was still uninstalled. 
```
damien@joseki:~$ gnugo
The program 'gnugo' is currently not installed.  You can install it by typing:
sudo apt-get install gnugo
damien@joseki:~$ 

```(If I do sudo apt-get install gnugo, it will install the latest version, something like 3.8..)
 I ran the gnugo-2.6.deb through ubuntu software center again, and the option wasn't "install" but "reinstall" so it seems to think it's currently installed.

Also, I don't know what Gnat is, but I installed Gnat (GNU Ada Translator, right) via ubuntu software center as well.

---

### Post by el_koraco on 2011-07-14
try ```
sudo apt-get build-dep gnugo
```
wait for it to do its thing, and then try to compile it.

---

### Post by mikejonesey on 2011-07-14
if the dependancies don't fix it the remove all instances of "-lang-c89" and try and build again, maybee its a compile option thats not required it the more uptodate dependancies...

---

