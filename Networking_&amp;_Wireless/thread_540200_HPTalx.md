---
title: "HPTalx"
date: 2007-09-01
forum: Networking &amp; Wireless
---

### Post by GranpaDan on 2007-09-01
I haven't been able to find HPTalx in any of the repositories through Synaptic. I thought it would be in multiverse, but a search didn't turn up anything. I was wondering if anyone out there has been able to successfully install HPTalx in UBUNTU.

HPTalx is a Linux communication software between a PC and a HP Calculator (Mine is a HP 50g).

Thanks if anyone has any tips.

---

### Post by exp(x) on 2007-09-07
I just compiled it today, but I had to add a few lines in the source files to make it recognize the 50G. Attached is a patch of the changes I made. Just put it in the hptalx-1.3.0 directory and run ```
patch -p0 < hptalx-50g.patch.txt
```

[ATTACH]42839[/ATTACH]

---

### Post by GranpaDan on 2007-09-11
Thank you so much exp(x). I'll give it a try.

---

### Post by diegopereira on 2007-09-12
Hello friends
I can't use HPtalx
when I click Connect, the program closes..
can anybody help me??

I downloaded the version 1.3.0
unpack that,
./configure
make
make install

when it runs, it looks for something in /home/diego/.hptalx
but that folder does not exist..
and when I click connect, give the msg: (core dumped)

My tests are coming and I need this program

Thanks

Sorry for my english...
I'm from Brazil

---

### Post by GranpaDan on 2007-09-15
Sorry,

After reading the README from the downloaded hptalx 1.3.0, I realized the instructions are well over my newbie head. I'm going to have to wait until some dumbed down instructions come out, and just use the data transfer on MSXP for now. Hopefully, someone with more knowledge can install it in the ubuntu repositories someday that can easily be accessed through synaptic.

---

### Post by GranpaDan on 2007-10-30
Problem Solved !!

Another milestone in my personal quest to become independent of WXP

Here's how I did it:

1. Clicked on the deb download to download HPTalx 1.3.1a on the HPtalx download web page:
[http://hptalx.sourceforge.net/download.shtml](http://hptalx.sourceforge.net/download.shtml)

2. After downloading, open it with the automatic gdebi-gtk program. As I recall, this will automatically install hptalx.

3. You can run hptalx from terminal by typing "hptalx" after the prompt.

4. After starting hptalx, go to File, Setup, and set Connection Settings to USB Mode. I would save this setting for the future, otherwise it will default to serial mode>

5. On the HP 50g calculator, press the APPS button, go to I/O functions on the menu, Transfer..., and set Type to Kermit (the latest version of HPtalx wuill not work in XModem).

6. Press and hold the orange right shift arrow key and press the right directional key. You should see "Awaiting Server Cmd." on the calculator.

7. On the HPtalx program, press ctrl-B, or click Connect, Connect. 

8. The HPtalx program then should find and list the files on your HP 50g calculator, and you should be able to transfer files back and forth, just like you would on the HP supplied Conn4 program that only works on windows.

Worked for me anyway :)

---

### Post by YoungCthulhu on 2007-11-05
Thanx GrandpaDan,

Worked for me too!  HP50g connected to Linux!  Geek heaven!

Cheers

---

### Post by graz848 on 2007-11-23
Hello, I have a hp49g+, and i downloaded too the .deb of hptalx 1.3.1a.
It seems to work, it connects to the calculator, but... when it gets the file list, all the files appear as "?" in the column "type". That is, the program doesn't recognize the file types, nor can tell directories from files! In fact, if I double click to a dir in order to view its content, it downloads it instead in my computer... well, i dont think this was supposed to be...
This happens on both my desktop and laptop.
You don't have this problem? Please, tell me...

---

### Post by H-Radical on 2007-12-16
Hi all,

thanks for the excellent information you've shared. I got my calculator connected using hptalx. It is a 50g and I really need to update its ROM because it can't solve polynomials with complex numbers. I know that only the older versions supported this function but they didn't support the 50g; the new versions (mine is 1.3.1a) which support the 50g, don't support ROM upgrade. I was wondering if anyone here has found the solution to this?

Cheers,

---

### Post by babylonx on 2008-02-21
Hi, I'm a newbie and I have Ubuntu 7.10 64bit installed. When I try with the deb package it says that I have the wrong architecture of course. I tried with the source code version and when I try to configure

```
$ sudo ./configure
```

I receive an error that I don't have glib-2.0 installed

```

checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking whether make sets $(MAKE)... (cached) yes
checking for ranlib... ranlib
checking for a sed that does not truncate output... /bin/sed
checking for kermit... ./configure: line 3888: error:: command not found
no
checking for docbook2html... no
checking for docbook2txt... no
checking for docbook2man... no
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.19... yes
checking for GLIB... configure: error: Package requirements (glib-2.0 >= 2.4.0) were not met:

No package 'glib-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GLIB_CFLAGS
and GLIB_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

I don't know which packages I need and I think that I have glib installed... Any ideas what I am doing wrong?

Thank you!

---

