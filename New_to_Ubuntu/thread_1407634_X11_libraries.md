---
title: "X11 libraries"
date: 2010-02-15
forum: New to Ubuntu
---

### Post by coldfusion1313 on 2010-02-15
I was compiling fvwm and I got this error:
```
X11 libraries or header files could not be found.  Please make
sure the X11 development package is installed on your system.
If it is definitely installed, try setting the include and library
paths with the --x-include and --x-libraries options of configure.
Fvwm can not be compiled without the X11 development environment

Aborting.

```Where can I find these files?

---

### Post by Perfect Storm on 2010-02-15
```
sudo apt-get install libx11-dev
```

---

### Post by coldfusion1313 on 2010-02-15
I installed al the X11 lib, then I rebooted. But I still got the same error message.

---

### Post by Perfect Storm on 2010-02-15
can you please give full terminal output.

---

### Post by coldfusion1313 on 2010-02-15
```

mark@zvrff:~/build/fvwm-2.4.20$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable command logging... no
checking whether to enable debugging messages... no
checking whether to enable multibyte character support (experimental)... no
checking whether to enable compound text conversion support... yes
checking imagepath... /usr/include/X11/bitmaps:/usr/include/X11/pixmaps
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
checking for library containing strerror... none required
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
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
checking minix/config.h usability... no
checking minix/config.h presence... no
checking for minix/config.h... no
checking for X... no

X11 libraries or header files could not be found.  Please make
sure the X11 development package is installed on your system.
If it is definitely installed, try setting the include and library
paths with the --x-include and --x-libraries options of configure.
Fvwm can not be compiled without the X11 development environment

Aborting.

```

---

### Post by Perfect Storm on 2010-02-15
You know that Fvwm is in ubuntu's repositories?

---

### Post by alfsagen on 2012-10-08
Hello,
I have the same problem installing certain apps, e.g. soapUI (install shell script 'soapUI-x32-4.5.1.sh'). First, I thought the problem was related to Java version, and I uninstalled OpenJDK and rather upgraded to Oracle/Sun Java 1.7_07. However, this didn't fix the problem, and I keep getting error message saying that GUI couldn't be shown due to lack of X11 server. (Note that I'm running Unity front-end, and the shell script is triggered from a terminal started under Unity.)

This is the error message from the soapUI installer script + result of 'sudo apt-get install libx11-dev':

alfs@Miraculix:~$ bash Downloads/soapUI-x32-4.5.1.sh 
Unpacking JRE ...
Preparing JRE ...
Starting Installer ...
Could not display the GUI. This application needs access to an X Server.
*******************************************************************
You can also run this application in console mode without
access to an X server by passing the argument -c
*******************************************************************
alfs@Miraculix:~$

alfs@Miraculix:~$ sudo apt-get install libx11-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libx11-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
alfs@Miraculix:~$

I have a slight suspicion that the problem is caused by my machine running 64 bit version of X11 whereas the app requires 32 bit. However, I have been running soapUI succesfully until last update pushed from Ubuntu's 'System Update'.

Any ideas?

Thanks a lot!
/alfs

---

### Post by Bucky Ball on 2012-10-08
***Thread Closed***

***Reason:*** Old

@ alf: Please post a new thread outlining your problem. You could copy and edit this post to a new thread.

From the Code of Conduct:

> If a post is older than a year or so and hasn't had a new reply in that  time, instead of replying to it, create a new thread. In the software  world, a lot can change in a very short time, and doing things this way  makes it more likely that you will find the best information. You may  link to the original discussion in the new thread if you think it may be  helpful.

I will immediately arrange to get your screen  name changed and you will be hearing from one of the staff about this. This is for your own security. Please, ***never*** include personal details in posts or elsewhere. ;)

---

### Post by Elfy on 2012-10-08
> **Bucky Ball said:**
> I will immediately arrange to get your screen  name changed and you will be hearing from one of the staff about this. This is for your own security. Please, ***never*** include personal details in posts or elsewhere. ;)

@ [email]alf.sagen@gmail.com[/email] - if you want to change you username to not use your e-mail address please post in RC with 3 alternatives and one of us will look for you.

It's possible that you would get attention from spam at the e-mail address.

---

