---
title: "How to force install of intltool .40.0 or greater?"
date: 2008-12-26
forum: New to Ubuntu
---

### Post by JDuc on 2008-12-26
I'm trying to figure out how to install intltool .40.0 or greater.

I've downloaded both .40.1 and .40.5 and supposidly installed both, yet when I go to the synaptic manager, I don't show either as being installed.  I have uninstalled .37.1 via the synaptic package manager before trying this.

When I try to install a particular plug-in for a program, it still comes up and tells me that I need a version of intltool that is .40.0 or newer.

How can I make this happen?

---

### Post by JDuc on 2008-12-27
bump....anyone?

---

### Post by taurus on 2008-12-27
How did you install those two versions, .40.1 and .40.5?

---

### Post by JDuc on 2008-12-27
through the terminal.

---

### Post by taurus on 2008-12-27
As in .deb, .rpm, or .tar.gz/bz2?

---

### Post by JDuc on 2008-12-27
sorry, I didn't understand.

.tar.gz

I've unpackaged the folder and called the ./configure file via the terminal.

---

### Post by taurus on 2008-12-27
No error message when you tried to build it from source, especially the ./configure?  Look in /usr/local/lib to see if there is anything in there.

```
ls -la /usr/local/lib
```
Again, if you build it from source, it will not show up in add/remove or synaptic.

---

### Post by JDuc on 2008-12-27
Thanks for your reply.

When I try and use the ./configure command for the intltool-0.40.5 folder, I'm told the following:
```
~/Desktop/intltool-0.40.5$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
configure: creating ./config.status
config.status: creating Makefile
config.status: creating doc/Makefile
config.status: creating intltool.spec
config.status: creating intltoolize
config.status: creating tests/Makefile
config.status: creating tests/cases/Makefile
config.status: creating tests/results/Makefile
config.status: creating tests/selftest.pl
```When I enter:
```
ls -la /usrlocal/lib
```I get the following:

```
ls: cannot access /usrlocal/lib: No such file or directory
```Yet, when I try to install the bot-sentry plugin for Pidgin, I'm told the following, after entering ./configure for that folder as well:

```
~/Desktop/bot-sentry-1.3.0$ ./cofigure
bash: ./cofigure: No such file or directory
jan@Dell:~/Desktop/bot-sentry-1.3.0$ ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
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
checking for prefix by checking for pidgin... /usr/bin/pidgin
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
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl.exe... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking whether we are using the GNU C++ compiler... no
checking whether g++ accepts -g... no
checking dependency style of g++... none
checking for g77... no
checking for xlf... no
checking for f77... no
checking for frt... no
checking for pgf77... no
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for xlf90... no
checking for f90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for gfortran... no
checking for g95... no
checking for xlf95... no
checking for f95... no
checking for fort... no
checking for ifort... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for ftn... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
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
checking whether to build static libraries... no
configure: creating libtool
appending configuration tag "CXX" to libtool
appending configuration tag "F77" to libtool
checking for intltool >= 0.40.0... ./configure: line 20319: intltool-update: command not found
 found
configure: error: Your intltool is too old.  You need intltool 0.40.0 or later.
```If I can figure out how to install all of this via Synaptic, I would prefer that  How can I do that?

---

### Post by taurus on 2008-12-27
Which release are you running?  Here's a screenshot of synaptic (intrepid).

---

### Post by JDuc on 2008-12-27
ok - I was chatting with a friend who is familiar with Linux, he linked me to this page: [http://www.linuxfromscratch.org/blfs/view/stable/general/intltool.html](http://www.linuxfromscratch.org/blfs/view/stable/general/intltool.html)

I followed those directions and it seems to have worked.  Of course, I was then presented with this error:

```
configure: error: GNU gettext tools not found; required for intltool
```

So I had to install gettext too....

So far, not a single thing I've tried to do with Ubuntu has been easy.  Every single set of directions that I've come acrosss has lead me to some error message within the first few steps.

Hopefully this will change...lol

---

### Post by JDuc on 2008-12-27
> **taurus said:**
> Which release are you running?  Here's a screenshot of synaptic (intrepid).

After installing the 40.5 version using the instructions in the link I provided above, it still shows up as intltool 37.1 and intltool-debian 35.0.

---

### Post by taurus on 2008-12-27
Are you running Hardy?

---

### Post by JDuc on 2008-12-27
Yes.

---

### Post by rajeshkallur on 2012-09-11
I still have this issue..(newbie here) And no clues from the link your friend gave as well. HELP! 

Rajesh

---

### Post by oldos2er on 2012-09-11
Please start a new thread; this one's four years old.

"If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful."

---

