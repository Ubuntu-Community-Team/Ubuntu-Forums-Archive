---
title: "help installing clanbomber"
date: 2009-02-07
forum: New to Ubuntu
---

### Post by mono-jo on 2009-02-07
hi i HAVE A QUESTION:
how do i install files?
im only 15 years old but i have programed in html and i have recently started java im new to linux but as far as im consern ubuntu is better than xp plz help me
:lolflag:

---

### Post by Mitch9654 on 2009-02-07
Uh... Check the readme of the file?!?!


Well, a better thing is to go to system/admistration/synaptic package manager and search for the program you need in the search whatchamacallit

The package file will download and install to you pc... I mean Ubuntu computer


Mitch9654

---

### Post by leonardo_neo on 2009-02-07
> **mono-jo said:**
> hi i HAVE A QUESTION:
how do i install files?
im only 15 years old but i have programed in html and i have recently started java im new to linux but as far as im consern ubuntu is better than xp plz help me
:lolflag:

I am sorry, but I couldn't comprehend your question well. What file do you want to install?

---

### Post by diablo75 on 2009-02-07
> **mono-jo said:**
> how do i install files?

What exactly are you wanting/trying to install?

---

### Post by avtolle on 2009-02-07
What are you trying to install? Have you looked in Synaptic (System>Administration>Synaptic Package Manager) to see if the package(s) you want are listed there? If they are, mark them for installation and then click on Apply. 

Further, which repositories have you enabled? Take a look at Software Sources (System>Administration>Software Sources) to see which ones are checked; look under the Third Party Software Tab to see if you have any of those enabled. One popular third-party repo is medibuntu. Go to www. medibuntu.org for an overview of what is offered there, and for instructions on how to install that repository.

If you are trying to install Windows .exe files, these won't run natively in Linux; some apps work under Wine (Google is your friend), which may be installed as well.

---

### Post by Alterax on 2009-02-07
Add/Remove Programs, located in the Main menu, is likely your best place to start.  Or have you downloaded a file from a website that you'd like to install?  If so, does it have a .deb extension (these are the best to work with), an .rpm extension (takes a bit more work on Ubuntu), or a .tar.gz extension (bit harder to work with than rpms).

I guess the base question would be, what exactly do you want to install?  And another is, what does it do?  The first answer lets us know which method is easiest, the second lets us know what it is you'd like to do (as there are many programs in the add/remove repositories that may accomplish the same goal)

---

### Post by mono-jo on 2009-02-07
im trying to install clanbomber (i used to love this game) (my first pc was a duel boot between win-2000 and suse linux)
but i dont completely understand this part:

[SIZE="1"]Basic Installation
==================

   These are generic installation instructions.

   The `configure' shell script attempts to guess correct values for
various system-dependent variables used during compilation.  It uses
those values to create a `Makefile' in each directory of the package.
It may also create one or more `.h' files containing system-dependent
definitions.  Finally, it creates a shell script `config.status' that
you can run in the future to recreate the current configuration, a file
`config.cache' that saves the results of its tests to speed up
reconfiguring, and a file `config.log' containing compiler output
(useful mainly for debugging `configure').

   If you need to do unusual things to compile the package, please try
to figure out how `configure' could check whether to do them, and mail
diffs or instructions to the address given in the `README' so they can
be considered for the next release.  If at some point `config.cache'
contains results you don't want to keep, you may remove or edit it.

   The file `configure.in' is used to create `configure' by a program
called `autoconf'.  You only need `configure.in' if you want to change
it or regenerate `configure' using a newer version of `autoconf'.

The simplest way to compile this package is:

  1. `cd' to the directory containing the package's source code and type
     `./configure' to configure the package for your system.  If you're
     using `csh' on an old version of System V, you might need to type
     `sh ./configure' instead to prevent `csh' from trying to execute
     `configure' itself.

     Running `configure' takes a while.  While running, it prints some
     messages telling which features it is checking for.

  2. Type `make' to compile the package.

  3. Type `make install' to install the programs and any data files and
     documentation.

  4. You can remove the program binaries and object files from the
     source code directory by typing `make clean'.  
[/SIZE]

---

### Post by AliTabuger7 on 2009-02-07
sudo apt-get install clanbomber

---

### Post by mono-jo on 2009-02-07
> **AliTabuger7 said:**
> sudo apt-get install clanbomber


i dont understand?

---

### Post by mkvnmtr on 2009-02-07
Open the terminal then copy and past the command and press enter. then when it asks for a password type in your password and press enter. Then wait for it to install. By the way you won't see your password so type it correctly.

---

### Post by mono-jo on 2009-02-07
jow do i intall claN BOMBER 
or just tell me how to folow the instutiuons


Basic Installation
==================

   These are generic installation instructions.

   The `configure' shell script attempts to guess correct values for
various system-dependent variables used during compilation.  It uses
those values to create a `Makefile' in each directory of the package.
It may also create one or more `.h' files containing system-dependent
definitions.  Finally, it creates a shell script `config.status' that
you can run in the future to recreate the current configuration, a file
`config.cache' that saves the results of its tests to speed up
reconfiguring, and a file `config.log' containing compiler output
(useful mainly for debugging `configure').

   If you need to do unusual things to compile the package, please try
to figure out how `configure' could check whether to do them, and mail
diffs or instructions to the address given in the `README' so they can
be considered for the next release.  If at some point `config.cache'
contains results you don't want to keep, you may remove or edit it.

   The file `configure.in' is used to create `configure' by a program
called `autoconf'.  You only need `configure.in' if you want to change
it or regenerate `configure' using a newer version of `autoconf'.

The simplest way to compile this package is:

  1. `cd' to thery containing the package's source code and type
     `./configure' to configure the package for your system.  If you're
     using `csh' on an old version of System V, you might need to type
     `sh ./configure' instead to prevent `csh' from trying to execute
     `configure' itself.

     Running `configure' takes a while.  While running, it prints some
     messages telling which features it is checking for.

  2. Type `make' to compile the package.

  3. Type `make install' to install the programs and any data files and
     documentation.

  4. You can remove the program binaries and object files from the
     source code directory by typing `make clean'.  
:(

---

### Post by taurus on 2009-02-07
Download the source and then unpack it.  Now, change to the new directory and run

```
sudo apt-get update
sudo apt-get install build-essential checkinstall  <-- You need at least the build-essential package if you want to compile anything from source!
./configure
make
sudo make install
-or-
sudo make checkinstall
```

---

### Post by mono-jo on 2009-02-07
elba@elba-desktop:~$ sudo apt-get install clanbomber
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package clanbomber is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  clanbomber-data
E: Package clanbomber has no installation candidate
elba@elba-desktop:~$ 



....? i think somting is wrong :(

---

### Post by carml on 2009-02-07
The program you're looking for seems not to be exsisting as a .deb on the list of the applications avaible on the server of the community.That's why you obtained that result.Did you already downloaded something similar to clanbomber.tar.gz ?

---

### Post by mono-jo on 2009-02-07
i downlaoded a few versions

---

### Post by mono-jo on 2009-02-07
elba@elba-desktop:~$ sudo apt-get install clanbomber-data
Reading package lists... Done
Building dependency tree       
Reading state information... Done
clanbomber-data is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.27-7 linux-headers-2.6.27-7-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
elba@elba-desktop:~$ 


umm what now?

---

### Post by carml on 2009-02-07
Ok,then copy the one you want to use to your desktop.Then unzip it with a rgiht click on the file.Once you've done go to Applications->Accessories->Terminal ,then type there 'cd ~/Desktop/folder'
where folder is the name of the folder you've just created,then type 'sudo /.configure'.Doing so you enter the folder you've just created and execute the automatic command to install the software with the rights of an administrator.Hope I've been clear enough.:)

---

### Post by mono-jo on 2009-02-07
how do i chang the directory

---

### Post by overdrank on 2009-02-07
Please do not create multiple threads on the same issue. Threads merged :)

---

### Post by carml on 2009-02-07
Read my previous post for info on how change directory,but first type in the terminal sudo apt-get install build-essential,as suggested in one of the post. :)

---

### Post by mono-jo on 2009-02-07
elba@elba-desktop:~$ cd ~/Desktop/clanbomber2-0.9.1 sudo/.configure
elba@elba-desktop:~/Desktop/clanbomber2-0.9.1$ 
like this 
and how do i run it?

---

### Post by Mellon on 2009-02-07
what about bomberclone

sudo apt-get install bomberclone

---

### Post by mono-jo on 2009-02-07
i specifically looking for clanbomber as it represents a good memory in my life

---

### Post by carml on 2009-02-07
> **mono-jo said:**
> elba@elba-desktop:~$ cd ~/Desktop/clanbomber2-0.9.1 sudo/.configure
elba@elba-desktop:~/Desktop/clanbomber2-0.9.1$ 
like this and how do i run it?
You have to type cd ~/Desktop/clanbomber2-0.9.1,then press ENTER;once you see '~/Desktop/clanbomber2-0.9.1$' type sudo /.configure,press ENTER,type your password( that's offuscated,so you'll don't see what are you typing);then type make and press ENTER,then type make install and press ENTER.:)

---

### Post by mono-jo on 2009-02-07
elba@elba-desktop:~$ cd ~/Desktop/clanbomber-1.05
elba@elba-desktop:~/Desktop/clanbomber-1.05$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for g++... no
checking for c++... no
checking for gpp... gpp
checking for C++ compiler default output file name... b.out
checking whether the C++ compiler works... configure: error: cannot run C++ compiled programs.
If you meant to cross compile, use `--host'.
See `config.log' for more details.
elba@elba-desktop:~/Desktop/clanbomber-1.05$ --host
bash: --host: command not found
elba@elba-desktop:~/Desktop/clanbomber-1.05$

---

### Post by mono-jo on 2009-02-07
elba@elba-desktop:~/Desktop/clanbomber-1.05$ sudo/.condigure
bash: sudo/.condigure: No such file or directory
elba@elba-desktop:~/Desktop/clanbomber-1.05$ sudo/.configure
bash: sudo/.configure: No such file or directory
elba@elba-desktop:~/Desktop/clanbomber-1.05$ sudo./configure
bash: sudo./configure: No such file or directory
elba@elba-desktop:~/Desktop/clanbomber-1.05$

---

### Post by carml on 2009-02-07
First go to System->Administration->Synaptic Package Manager and look for build-essential,once you found it right click the square near the name,select mark for installation then click on apply in the menù bar.
After you finished downloading,follow the previous suggestions typing 'sudo /.configure' with a space among sudo and / .:)

---

### Post by carml on 2009-02-07
Sorry the command are right,but by error inverted the position of the point;with the correction the command is 'sudo ./configure',copy and paste this one when requested as I and others told before.:)

---

### Post by mono-jo on 2009-02-07
```
elba@elba-desktop:~$ cd ~/Desktop/clanbomber-1.05
elba@elba-desktop:~/Desktop/clanbomber-1.05$ sudo /.configure
sudo: /.configure: command not found
elba@elba-desktop:~/Desktop/clanbomber-1.05$ sudo /.configure
sudo: /.configure: command not found
elba@elba-desktop:~/Desktop/clanbomber-1.05$ sudo /.configure
sudo: /.configure: command not found
elba@elba-desktop:~/Desktop/clanbomber-1.05$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for g++... g++
checking for C++ compiler default output file name... a.out
checking whether the C++ compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for style of include used by make... GNU
checking dependency style of g++... gcc3
checking for gcc... gcc
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking for main in -lz... no
ClanBomber requires zlib to run.
elba@elba-desktop:~/Desktop/clanbomber-1.05$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for g++... g++
checking for C++ compiler default output file name... a.out
checking whether the C++ compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for style of include used by make... GNU
checking dependency style of g++... gcc3
checking for gcc... gcc
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking for main in -lz... no
ClanBomber requires zlib to run.
elba@elba-desktop:~/Desktop/clanbomber-1.05$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for g++... g++
checking for C++ compiler default output file name... a.out
checking whether the C++ compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for style of include used by make... GNU
checking dependency style of g++... gcc3
checking for gcc... gcc
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking for main in -lz... yes
checking for main in -lHermes... no
ClanBomber requires Hermes to run.
elba@elba-desktop:~/Desktop/clanbomber-1.05$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for g++... g++
checking for C++ compiler default output file name... a.out
checking whether the C++ compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for style of include used by make... GNU
checking dependency style of g++... gcc3
checking for gcc... gcc
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking for main in -lz... yes
checking for main in -lHermes... yes
checking for main in -lclanCore... no
ClanBomber requires ClanLib to run.
elba@elba-desktop:~/Desktop/clanbomber-1.05$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for g++... g++
checking for C++ compiler default output file name... a.out
checking whether the C++ compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for style of include used by make... GNU
checking dependency style of g++... gcc3
checking for gcc... gcc
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking for main in -lz... yes
checking for main in -lHermes... yes
checking for main in -lclanCore... yes
checking for main in -lclanApp... yes
checking for main in -lclanDisplay... yes
checking for main in -lclanSound... yes
checking for main in -lclanMikMod... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating clanbomber/Makefile
config.status: creating clanbomber/music/Makefile
config.status: creating clanbomber/maps/Makefile
config.status: creating clanbomber/pics/Makefile
config.status: creating clanbomber/wavs/Makefile
config.status: creating config.h
config.status: executing depfiles commands
elba@elba-desktop:~/Desktop/clanbomber-1.05$ make
make  all-recursive
make[1]: Entering directory `/home/elba/Desktop/clanbomber-1.05'
Making all in clanbomber
make[2]: Entering directory `/home/elba/Desktop/clanbomber-1.05/clanbomber'
Making all in music
make[3]: Entering directory `/home/elba/Desktop/clanbomber-1.05/clanbomber/music'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/elba/Desktop/clanbomber-1.05/clanbomber/music'
Making all in maps
make[3]: Entering directory `/home/elba/Desktop/clanbomber-1.05/clanbomber/maps'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/elba/Desktop/clanbomber-1.05/clanbomber/maps'
Making all in pics
make[3]: Entering directory `/home/elba/Desktop/clanbomber-1.05/clanbomber/pics'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/elba/Desktop/clanbomber-1.05/clanbomber/pics'
Making all in wavs
make[3]: Entering directory `/home/elba/Desktop/clanbomber-1.05/clanbomber/wavs'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/elba/Desktop/clanbomber-1.05/clanbomber/wavs'
make[3]: Entering directory `/home/elba/Desktop/clanbomber-1.05/clanbomber'
if g++ -DPKGDATADIR=\"/usr/local/share/clanbomber/\" -DHAVE_CONFIG_H -I. -I. -I.. -I. -I..    -g -O2 -MT Disease_Fast.o -MD -MP -MF ".deps/Disease_Fast.Tpo" \
	  -c -o Disease_Fast.o `test -f 'Disease_Fast.cpp' || echo './'`Disease_Fast.cpp; \
	then mv -f ".deps/Disease_Fast.Tpo" ".deps/Disease_Fast.Po"; \
	else rm -f ".deps/Disease_Fast.Tpo"; exit 1; \
	fi
In file included from Extra_Koks.h:22,
                 from Disease_Fast.cpp:21:
Extra.h: In member function ‘char* Extra::get_name()’:
Extra.h:38: warning: deprecated conversion from string constant to ‘char*’
if g++ -DPKGDATADIR=\"/usr/local/share/clanbomber/\" -DHAVE_CONFIG_H -I. -I. -I.. -I. -I..    -g -O2 -MT MapTile_Trap.o -MD -MP -MF ".deps/MapTile_Trap.Tpo" \
	  -c -o MapTile_Trap.o `test -f 'MapTile_Trap.cpp' || echo './'`MapTile_Trap.cpp; \
	then mv -f ".deps/MapTile_Trap.Tpo" ".deps/MapTile_Trap.Po"; \
	else rm -f ".deps/MapTile_Trap.Tpo"; exit 1; \
	fi
MapTile_Trap.cpp:25:45: error: ClanLib/Display/Display/surface.h: No such file or directory
MapTile_Trap.cpp: In member function ‘virtual void MapTile_Trap::draw(int, int)’:
MapTile_Trap.cpp:90: error: invalid use of incomplete type ‘struct CL_Surface’
Resources.h:23: error: forward declaration of ‘struct CL_Surface’
MapTile_Trap.cpp: In member function ‘virtual void MapTile_Trap::draw_tiny(int, int, float)’:
MapTile_Trap.cpp:97: error: invalid use of incomplete type ‘struct CL_Surface’
Resources.h:23: error: forward declaration of ‘struct CL_Surface’
make[3]: *** [MapTile_Trap.o] Error 1
make[3]: Leaving directory `/home/elba/Desktop/clanbomber-1.05/clanbomber'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/elba/Desktop/clanbomber-1.05/clanbomber'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/elba/Desktop/clanbomber-1.05'
make: *** [all] Error 2
elba@elba-desktop:~/Desktop/clanbomber-1.05$ make install
Making install in clanbomber
make[1]: Entering directory `/home/elba/Desktop/clanbomber-1.05/clanbomber'
Making install in music
make[2]: Entering directory `/home/elba/Desktop/clanbomber-1.05/clanbomber/music'
make[3]: Entering directory `/home/elba/Desktop/clanbomber-1.05/clanbomber/music'
make[3]: Nothing to be done for `install-exec-am'.
/bin/bash ../../mkinstalldirs /usr/local/share/clanbomber/
mkdir -p -- /usr/local/share/clanbomber/
mkdir: cannot create directory `/usr/local/share/clanbomber/': Permission denied
make[3]: *** [install-data-local] Error 1
make[3]: Leaving directory `/home/elba/Desktop/clanbomber-1.05/clanbomber/music'
make[2]: *** [install-am] Error 2
make[2]: Leaving directory `/home/elba/Desktop/clanbomber-1.05/clanbomber/music'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/elba/Desktop/clanbomber-1.05/clanbomber'
make: *** [install-recursive] Error 1
elba@elba-desktop:~/Desktop/clanbomber-1.05$ make clean
Making clean in clanbomber
make[1]: Entering directory `/home/elba/Desktop/clanbomber-1.05/clanbomber'
Making clean in wavs
make[2]: Entering directory `/home/elba/Desktop/clanbomber-1.05/clanbomber/wavs'
make[2]: Nothing to be done for `clean'.
make[2]: Leaving directory `/home/elba/Desktop/clanbomber-1.05/clanbomber/wavs'
Making clean in pics
make[2]: Entering directory `/home/elba/Desktop/clanbomber-1.05/clanbomber/pics'
make[2]: Nothing to be done for `clean'.
make[2]: Leaving directory `/home/elba/Desktop/clanbomber-1.05/clanbomber/pics'
Making clean in maps
make[2]: Entering directory `/home/elba/Desktop/clanbomber-1.05/clanbomber/maps'
make[2]: Nothing to be done for `clean'.
make[2]: Leaving directory `/home/elba/Desktop/clanbomber-1.05/clanbomber/maps'
Making clean in music
make[2]: Entering directory `/home/elba/Desktop/clanbomber-1.05/clanbomber/music'
make[2]: Nothing to be done for `clean'.
make[2]: Leaving directory `/home/elba/Desktop/clanbomber-1.05/clanbomber/music'
Making clean in .
make[2]: Entering directory `/home/elba/Desktop/clanbomber-1.05/clanbomber'
test -z "clanbomber" || rm -f clanbomber
rm -f *.o core *.core
make[2]: Leaving directory `/home/elba/Desktop/clanbomber-1.05/clanbomber'
make[1]: Leaving directory `/home/elba/Desktop/clanbomber-1.05/clanbomber'
Making clean in .
make[1]: Entering directory `/home/elba/Desktop/clanbomber-1.05'
make[1]: Nothing to be done for `clean-am'.
make[1]: Leaving directory `/home/elba/Desktop/clanbomber-1.05'
elba@elba-desktop:~/Desktop/clanbomber-1.05$ 
```


im stuck again!!!

---

### Post by carml on 2009-02-07
Refresh the page in Firefox and read the posts #27 and # 28.

---

### Post by mono-jo on 2009-02-07
elba@elba-desktop:~$ cd ~/Desktop/clanbomber-1.05
elba@elba-desktop:~/Desktop/clanbomber-1.05$ sudo ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for g++... g++
checking for C++ compiler default output file name... a.out
checking whether the C++ compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for style of include used by make... GNU
checking dependency style of g++... gcc3
checking for gcc... gcc
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking for main in -lz... yes
checking for main in -lHermes... yes
checking for main in -lclanCore... yes
checking for main in -lclanApp... yes
checking for main in -lclanDisplay... yes
checking for main in -lclanSound... yes
checking for main in -lclanMikMod... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating clanbomber/Makefile
config.status: creating clanbomber/music/Makefile
config.status: creating clanbomber/maps/Makefile
config.status: creating clanbomber/pics/Makefile
config.status: creating clanbomber/wavs/Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
elba@elba-desktop:~/Desktop/clanbomber-1.05$



now what?

---

### Post by carml on 2009-02-07
Type make in the terminal,then press ENTER.After if you don't get messages of error type make install and press ENTER

---

### Post by mono-jo on 2009-02-07
i have added th build essentials

---

### Post by carml on 2009-02-07
Ok,into the folder type make and press ENTER,if you don't get messages of error type make install. :)

---

### Post by mono-jo on 2009-02-07
/elba/Desktop/clanbomber-1.05/clanbomber -I.. -I. -I/home/elba/Desktop/clanbomber-1.05    -g -O2 -MT MapTile_Trap.o -MD -MP -MF ".deps/MapTile_Trap.Tpo" \
	  -c -o MapTile_Trap.o `test -f 'MapTile_Trap.cpp' || echo '/home/elba/Desktop/clanbomber-1.05/clanbomber/'`MapTile_Trap.cpp; \
	then mv -f ".deps/MapTile_Trap.Tpo" ".deps/MapTile_Trap.Po"; \
	else rm -f ".deps/MapTile_Trap.Tpo"; exit 1; \
	fi
MapTile_Trap.cpp:25:45: error: ClanLib/Display/Display/surface.h: No such file or directory
MapTile_Trap.cpp: In member function ‘virtual void MapTile_Trap::draw(int, int)’:
MapTile_Trap.cpp:90: error: invalid use of incomplete type ‘struct CL_Surface’
Resources.h:23: error: forward declaration of ‘struct CL_Surface’
MapTile_Trap.cpp: In member function ‘virtual void MapTile_Trap::draw_tiny(int, int, float)’:
MapTile_Trap.cpp:97: error: invalid use of incomplete type ‘struct CL_Surface’
Resources.h:23: error: forward declaration of ‘struct CL_Surface’
make[3]: *** [MapTile_Trap.o] Error 1
make[3]: Leaving directory `/home/elba/Desktop/clanbomber-1.05/clanbomber'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/elba/Desktop/clanbomber-1.05/clanbomber'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/elba/Desktop/clanbomber-1.05'
make: *** [all] Error 2

---

### Post by mono-jo on 2009-02-07
how do i fix these errors?



elba@elba-desktop:~/Desktop/clanbomber-1.05$ make
make  all-recursive
make[1]: Entering directory `/home/elba/Desktop/clanbomber-1.05'
Making all in clanbomber
make[2]: Entering directory `/home/elba/Desktop/clanbomber-1.05/clanbomber'
Making all in music
make[3]: Entering directory `/home/elba/Desktop/clanbomber-1.05/clanbomber/music'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/elba/Desktop/clanbomber-1.05/clanbomber/music'
Making all in maps
make[3]: Entering directory `/home/elba/Desktop/clanbomber-1.05/clanbomber/maps'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/elba/Desktop/clanbomber-1.05/clanbomber/maps'
Making all in pics
make[3]: Entering directory `/home/elba/Desktop/clanbomber-1.05/clanbomber/pics'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/elba/Desktop/clanbomber-1.05/clanbomber/pics'
Making all in wavs
make[3]: Entering directory `/home/elba/Desktop/clanbomber-1.05/clanbomber/wavs'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/elba/Desktop/clanbomber-1.05/clanbomber/wavs'
make[3]: Entering directory `/home/elba/Desktop/clanbomber-1.05/clanbomber'
if g++ -DPKGDATADIR=\"/usr/local/share/clanbomber/\" -DHAVE_CONFIG_H -I. -I/home/elba/Desktop/clanbomber-1.05/clanbomber -I.. -I. -I/home/elba/Desktop/clanbomber-1.05    -g -O2 -MT MapTile_Trap.o -MD -MP -MF ".deps/MapTile_Trap.Tpo" \
	  -c -o MapTile_Trap.o `test -f 'MapTile_Trap.cpp' || echo '/home/elba/Desktop/clanbomber-1.05/clanbomber/'`MapTile_Trap.cpp; \
	then mv -f ".deps/MapTile_Trap.Tpo" ".deps/MapTile_Trap.Po"; \
	else rm -f ".deps/MapTile_Trap.Tpo"; exit 1; \
	fi
MapTile_Trap.cpp:25:45: error: ClanLib/Display/Display/surface.h: No such file or directory
MapTile_Trap.cpp: In member function ‘virtual void MapTile_Trap::draw(int, int)’:
MapTile_Trap.cpp:90: error: invalid use of incomplete type ‘struct CL_Surface’
Resources.h:23: error: forward declaration of ‘struct CL_Surface’
MapTile_Trap.cpp: In member function ‘virtual void MapTile_Trap::draw_tiny(int, int, float)’:
MapTile_Trap.cpp:97: error: invalid use of incomplete type ‘struct CL_Surface’
Resources.h:23: error: forward declaration of ‘struct CL_Surface’
make[3]: *** [MapTile_Trap.o] Error 1
make[3]: Leaving directory `/home/elba/Desktop/clanbomber-1.05/clanbomber'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/elba/Desktop/clanbomber-1.05/clanbomber'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/elba/Desktop/clanbomber-1.05'
make: *** [all] Error 2
elba@elba-desktop:~/Desktop/clanbomber-1.05$

---

### Post by carml on 2009-02-07
I thought it was clear,ok let's go with order: 1.close the terminal;2. then go again to Applications->Accessories->Terminal; 3. type into the terminal 'cd ~/Desktop/folder' where folder is the name of the folder you created when unzipped the file 'clanbomberNumberOfVersion.tar.gz'and press ENTER;4.when you see something similar to 'yourname@ubuntu:~$'type sudo ./configure and press ENTER (probably this will overwrite previous files or claim that the files already exsist); 5.when you see something similar to 'yourname@ubuntu:~$' type make and press ENTER (if nothing appear after any second retry with sudo make);6. when you see something similar to 'yourname@ubuntu:~$'type make install ( or sudo make install if it doesn't work) and when you see something similar to 'yourname@ubuntu:~$' you've finished the installation.:)

---

### Post by mono-jo on 2009-02-07
this is what happend:
what now?


```
elba@elba-desktop:~$ cd ~/Desktop/clanbomber-1.05
elba@elba-desktop:~/Desktop/clanbomber-1.05$ sudo ./configure
[sudo] password for elba: 
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for g++... g++
checking for C++ compiler default output file name... a.out
checking whether the C++ compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for style of include used by make... GNU
checking dependency style of g++... gcc3
checking for gcc... gcc
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking for main in -lz... yes
checking for main in -lHermes... yes
checking for main in -lclanCore... yes
checking for main in -lclanApp... yes
checking for main in -lclanDisplay... yes
checking for main in -lclanSound... yes
checking for main in -lclanMikMod... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating clanbomber/Makefile
config.status: creating clanbomber/music/Makefile
config.status: creating clanbomber/maps/Makefile
config.status: creating clanbomber/pics/Makefile
config.status: creating clanbomber/wavs/Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
elba@elba-desktop:~/Desktop/clanbomber-1.05$ make
make  all-recursive
make[1]: Entering directory `/home/elba/Desktop/clanbomber-1.05'
Making all in clanbomber
make[2]: Entering directory `/home/elba/Desktop/clanbomber-1.05/clanbomber'
Making all in music
make[3]: Entering directory `/home/elba/Desktop/clanbomber-1.05/clanbomber/music'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/elba/Desktop/clanbomber-1.05/clanbomber/music'
Making all in maps
make[3]: Entering directory `/home/elba/Desktop/clanbomber-1.05/clanbomber/maps'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/elba/Desktop/clanbomber-1.05/clanbomber/maps'
Making all in pics
make[3]: Entering directory `/home/elba/Desktop/clanbomber-1.05/clanbomber/pics'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/elba/Desktop/clanbomber-1.05/clanbomber/pics'
Making all in wavs
make[3]: Entering directory `/home/elba/Desktop/clanbomber-1.05/clanbomber/wavs'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/elba/Desktop/clanbomber-1.05/clanbomber/wavs'
make[3]: Entering directory `/home/elba/Desktop/clanbomber-1.05/clanbomber'
if g++ -DPKGDATADIR=\"/usr/local/share/clanbomber/\" -DHAVE_CONFIG_H -I. -I. -I.. -I. -I..    -g -O2 -MT MapTile_Trap.o -MD -MP -MF ".deps/MapTile_Trap.Tpo" \
	  -c -o MapTile_Trap.o `test -f 'MapTile_Trap.cpp' || echo './'`MapTile_Trap.cpp; \
	then mv -f ".deps/MapTile_Trap.Tpo" ".deps/MapTile_Trap.Po"; \
	else rm -f ".deps/MapTile_Trap.Tpo"; exit 1; \
	fi
MapTile_Trap.cpp:25:45: error: ClanLib/Display/Display/surface.h: No such file or directory
MapTile_Trap.cpp: In member function ‘virtual void MapTile_Trap::draw(int, int)’:
MapTile_Trap.cpp:90: error: invalid use of incomplete type ‘struct CL_Surface’
Resources.h:23: error: forward declaration of ‘struct CL_Surface’
MapTile_Trap.cpp: In member function ‘virtual void MapTile_Trap::draw_tiny(int, int, float)’:
MapTile_Trap.cpp:97: error: invalid use of incomplete type ‘struct CL_Surface’
Resources.h:23: error: forward declaration of ‘struct CL_Surface’
make[3]: *** [MapTile_Trap.o] Error 1
make[3]: Leaving directory `/home/elba/Desktop/clanbomber-1.05/clanbomber'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/elba/Desktop/clanbomber-1.05/clanbomber'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/elba/Desktop/clanbomber-1.05'
make: *** [all] Error 2
elba@elba-desktop:~/Desktop/clanbomber-1.05$ sudo make
make  all-recursive
make[1]: Entering directory `/home/elba/Desktop/clanbomber-1.05'
Making all in clanbomber
make[2]: Entering directory `/home/elba/Desktop/clanbomber-1.05/clanbomber'
Making all in music
make[3]: Entering directory `/home/elba/Desktop/clanbomber-1.05/clanbomber/music'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/elba/Desktop/clanbomber-1.05/clanbomber/music'
Making all in maps
make[3]: Entering directory `/home/elba/Desktop/clanbomber-1.05/clanbomber/maps'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/elba/Desktop/clanbomber-1.05/clanbomber/maps'
Making all in pics
make[3]: Entering directory `/home/elba/Desktop/clanbomber-1.05/clanbomber/pics'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/elba/Desktop/clanbomber-1.05/clanbomber/pics'
Making all in wavs
make[3]: Entering directory `/home/elba/Desktop/clanbomber-1.05/clanbomber/wavs'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/elba/Desktop/clanbomber-1.05/clanbomber/wavs'
make[3]: Entering directory `/home/elba/Desktop/clanbomber-1.05/clanbomber'
if g++ -DPKGDATADIR=\"/usr/local/share/clanbomber/\" -DHAVE_CONFIG_H -I. -I. -I.. -I. -I..    -g -O2 -MT MapTile_Trap.o -MD -MP -MF ".deps/MapTile_Trap.Tpo" \
	  -c -o MapTile_Trap.o `test -f 'MapTile_Trap.cpp' || echo './'`MapTile_Trap.cpp; \
	then mv -f ".deps/MapTile_Trap.Tpo" ".deps/MapTile_Trap.Po"; \
	else rm -f ".deps/MapTile_Trap.Tpo"; exit 1; \
	fi
MapTile_Trap.cpp:25:45: error: ClanLib/Display/Display/surface.h: No such file or directory
MapTile_Trap.cpp: In member function ‘virtual void MapTile_Trap::draw(int, int)’:
MapTile_Trap.cpp:90: error: invalid use of incomplete type ‘struct CL_Surface’
Resources.h:23: error: forward declaration of ‘struct CL_Surface’
MapTile_Trap.cpp: In member function ‘virtual void MapTile_Trap::draw_tiny(int, int, float)’:
MapTile_Trap.cpp:97: error: invalid use of incomplete type ‘struct CL_Surface’
Resources.h:23: error: forward declaration of ‘struct CL_Surface’
make[3]: *** [MapTile_Trap.o] Error 1
make[3]: Leaving directory `/home/elba/Desktop/clanbomber-1.05/clanbomber'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/elba/Desktop/clanbomber-1.05/clanbomber'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/elba/Desktop/clanbomber-1.05'
make: *** [all] Error 2
elba@elba-desktop:~/Desktop/clanbomber-1.05$ make install
Making install in clanbomber
make[1]: Entering directory `/home/elba/Desktop/clanbomber-1.05/clanbomber'
Making install in music
make[2]: Entering directory `/home/elba/Desktop/clanbomber-1.05/clanbomber/music'
make[3]: Entering directory `/home/elba/Desktop/clanbomber-1.05/clanbomber/music'
make[3]: Nothing to be done for `install-exec-am'.
/bin/bash ../../mkinstalldirs /usr/local/share/clanbomber/
mkdir -p -- /usr/local/share/clanbomber/
mkdir: cannot create directory `/usr/local/share/clanbomber/': Permission denied
make[3]: *** [install-data-local] Error 1
make[3]: Leaving directory `/home/elba/Desktop/clanbomber-1.05/clanbomber/music'
make[2]: *** [install-am] Error 2
make[2]: Leaving directory `/home/elba/Desktop/clanbomber-1.05/clanbomber/music'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/elba/Desktop/clanbomber-1.05/clanbomber'
make: *** [install-recursive] Error 1
elba@elba-desktop:~/Desktop/clanbomber-1.05$ sudo make install
Making install in clanbomber
make[1]: Entering directory `/home/elba/Desktop/clanbomber-1.05/clanbomber'
Making install in music
make[2]: Entering directory `/home/elba/Desktop/clanbomber-1.05/clanbomber/music'
make[3]: Entering directory `/home/elba/Desktop/clanbomber-1.05/clanbomber/music'
make[3]: Nothing to be done for `install-exec-am'.
/bin/bash ../../mkinstalldirs /usr/local/share/clanbomber/
mkdir -p -- /usr/local/share/clanbomber/
/usr/bin/install -c -m 644 bud.mod /usr/local/share/clanbomber/bud.mod
make[3]: Leaving directory `/home/elba/Desktop/clanbomber-1.05/clanbomber/music'
make[2]: Leaving directory `/home/elba/Desktop/clanbomber-1.05/clanbomber/music'
Making install in maps
make[2]: Entering directory `/home/elba/Desktop/clanbomber-1.05/clanbomber/maps'
make[3]: Entering directory `/home/elba/Desktop/clanbomber-1.05/clanbomber/maps'
make[3]: Nothing to be done for `install-exec-am'.
/bin/bash ../../mkinstalldirs /usr/local/share/clanbomber/maps/
mkdir -p -- /usr/local/share/clanbomber/maps/
/usr/bin/install -c -m 644 Crammed.map /usr/local/share/clanbomber/maps/Crammed.map
/bin/bash ../../mkinstalldirs /usr/local/share/clanbomber/maps/
/usr/bin/install -c -m 644 Hole_Run.map /usr/local/share/clanbomber/maps/Hole_Run.map
/bin/bash ../../mkinstalldirs /usr/local/share/clanbomber/maps/
/usr/bin/install -c -m 644 Obstacle_Race.map /usr/local/share/clanbomber/maps/Obstacle_Race.map
/bin/bash ../../mkinstalldirs /usr/local/share/clanbomber/maps/
/usr/bin/install -c -m 644 Prison_Cells.map /usr/local/share/clanbomber/maps/Prison_Cells.map
/bin/bash ../../mkinstalldirs /usr/local/share/clanbomber/maps/
/usr/bin/install -c -m 644 Small_Standard.map /usr/local/share/clanbomber/maps/Small_Standard.map
/bin/bash ../../mkinstalldirs /usr/local/share/clanbomber/maps/
/usr/bin/install -c -m 644 Tiny_Standard.map /usr/local/share/clanbomber/maps/Tiny_Standard.map
/bin/bash ../../mkinstalldirs /usr/local/share/clanbomber/maps/
/usr/bin/install -c -m 644 Football.map /usr/local/share/clanbomber/maps/Football.map
/bin/bash ../../mkinstalldirs /usr/local/share/clanbomber/maps/
/usr/bin/install -c -m 644 Kitchen.map /usr/local/share/clanbomber/maps/Kitchen.map
/bin/bash ../../mkinstalldirs /usr/local/share/clanbomber/maps/
/usr/bin/install -c -m 644 Whole_Mess.map /usr/local/share/clanbomber/maps/Whole_Mess.map
/bin/bash ../../mkinstalldirs /usr/local/share/clanbomber/maps/
/usr/bin/install -c -m 644 Redirection.map /usr/local/share/clanbomber/maps/Redirection.map
/bin/bash ../../mkinstalldirs /usr/local/share/clanbomber/maps/
/usr/bin/install -c -m 644 Bloody_Ring.map /usr/local/share/clanbomber/maps/Bloody_Ring.map
/bin/bash ../../mkinstalldirs /usr/local/share/clanbomber/maps/
/usr/bin/install -c -m 644 Four_Instance.map /usr/local/share/clanbomber/maps/Four_Instance.map
/bin/bash ../../mkinstalldirs /usr/local/share/clanbomber/maps/
/usr/bin/install -c -m 644 Ghostbear.map /usr/local/share/clanbomber/maps/Ghostbear.map
/bin/bash ../../mkinstalldirs /usr/local/share/clanbomber/maps/
/usr/bin/install -c -m 644 Hard_Work.map /usr/local/share/clanbomber/maps/Hard_Work.map
/bin/bash ../../mkinstalldirs /usr/local/share/clanbomber/maps/
/usr/bin/install -c -m 644 Meeting.map /usr/local/share/clanbomber/maps/Meeting.map
/bin/bash ../../mkinstalldirs /usr/local/share/clanbomber/maps/
/usr/bin/install -c -m 644 Overkill.map /usr/local/share/clanbomber/maps/Overkill.map
/bin/bash ../../mkinstalldirs /usr/local/share/clanbomber/maps/
/usr/bin/install -c -m 644 Sixty_Nine.map /usr/local/share/clanbomber/maps/Sixty_Nine.map
/bin/bash ../../mkinstalldirs /usr/local/share/clanbomber/maps/
/usr/bin/install -c -m 644 Boiling_Egg.map /usr/local/share/clanbomber/maps/Boiling_Egg.map
/bin/bash ../../mkinstalldirs /usr/local/share/clanbomber/maps/
/usr/bin/install -c -m 644 Bomb_Attack.map /usr/local/share/clanbomber/maps/Bomb_Attack.map
/bin/bash ../../mkinstalldirs /usr/local/share/clanbomber/maps/
/usr/bin/install -c -m 644 Arena.map /usr/local/share/clanbomber/maps/Arena.map
/bin/bash ../../mkinstalldirs /usr/local/share/clanbomber/maps/
/usr/bin/install -c -m 644 Big_Block.map /usr/local/share/clanbomber/maps/Big_Block.map
/bin/bash ../../mkinstalldirs /usr/local/share/clanbomber/maps/
/usr/bin/install -c -m 644 Big_Standard.map /usr/local/share/clanbomber/maps/Big_Standard.map
/bin/bash ../../mkinstalldirs /usr/local/share/clanbomber/maps/
/usr/bin/install -c -m 644 Blast_Matrix.map /usr/local/share/clanbomber/maps/Blast_Matrix.map
/bin/bash ../../mkinstalldirs /usr/local/share/clanbomber/maps/
/usr/bin/install -c -m 644 Death_Corridor.map /usr/local/share/clanbomber/maps/Death_Corridor.map
/bin/bash ../../mkinstalldirs /usr/local/share/clanbomber/maps/
/usr/bin/install -c -m 644 Dilemma.map /usr/local/share/clanbomber/maps/Dilemma.map
/bin/bash ../../mkinstalldirs /usr/local/share/clanbomber/maps/
/usr/bin/install -c -m 644 FearCircle.map /usr/local/share/clanbomber/maps/FearCircle.map
/bin/bash ../../mkinstalldirs /usr/local/share/clanbomber/maps/
/usr/bin/install -c -m 644 FearCircle_Remix.map /usr/local/share/clanbomber/maps/FearCircle_Remix.map
/bin/bash ../../mkinstalldirs /usr/local/share/clanbomber/maps/
/usr/bin/install -c -m 644 FireWheels.map /usr/local/share/clanbomber/maps/FireWheels.map
/bin/bash ../../mkinstalldirs /usr/local/share/clanbomber/maps/
/usr/bin/install -c -m 644 Huge_Standard.map /usr/local/share/clanbomber/maps/Huge_Standard.map
/bin/bash ../../mkinstalldirs /usr/local/share/clanbomber/maps/
/usr/bin/install -c -m 644 Juicy_Lucy.map /usr/local/share/clanbomber/maps/Juicy_Lucy.map
/bin/bash ../../mkinstalldirs /usr/local/share/clanbomber/maps/
/usr/bin/install -c -m 644 MungoBane.map /usr/local/share/clanbomber/maps/MungoBane.map
/bin/bash ../../mkinstalldirs /usr/local/share/clanbomber/maps/
/usr/bin/install -c -m 644 Snake_Race.map /usr/local/share/clanbomber/maps/Snake_Race.map
/bin/bash ../../mkinstalldirs /usr/local/share/clanbomber/maps/
/usr/bin/install -c -m 644 Broken_Heart.map /usr/local/share/clanbomber/maps/Broken_Heart.map
make[3]: Leaving directory `/home/elba/Desktop/clanbomber-1.05/clanbomber/maps'
make[2]: Leaving directory `/home/elba/Desktop/clanbomber-1.05/clanbomber/maps'
Making install in pics
make[2]: Entering directory `/home/elba/Desktop/clanbomber-1.05/clanbomber/pics'
make[3]: Entering directory `/home/elba/Desktop/clanbomber-1.05/clanbomber/pics'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/elba/Desktop/clanbomber-1.05/clanbomber/pics'
make[2]: Leaving directory `/home/elba/Desktop/clanbomber-1.05/clanbomber/pics'
Making install in wavs
make[2]: Entering directory `/home/elba/Desktop/clanbomber-1.05/clanbomber/wavs'
make[3]: Entering directory `/home/elba/Desktop/clanbomber-1.05/clanbomber/wavs'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/elba/Desktop/clanbomber-1.05/clanbomber/wavs'
make[2]: Leaving directory `/home/elba/Desktop/clanbomber-1.05/clanbomber/wavs'
make[2]: Entering directory `/home/elba/Desktop/clanbomber-1.05/clanbomber'
if g++ -DPKGDATADIR=\"/usr/local/share/clanbomber/\" -DHAVE_CONFIG_H -I. -I. -I.. -I. -I..    -g -O2 -MT MapTile_Trap.o -MD -MP -MF ".deps/MapTile_Trap.Tpo" \
	  -c -o MapTile_Trap.o `test -f 'MapTile_Trap.cpp' || echo './'`MapTile_Trap.cpp; \
	then mv -f ".deps/MapTile_Trap.Tpo" ".deps/MapTile_Trap.Po"; \
	else rm -f ".deps/MapTile_Trap.Tpo"; exit 1; \
	fi
MapTile_Trap.cpp:25:45: error: ClanLib/Display/Display/surface.h: No such file or directory
MapTile_Trap.cpp: In member function ‘virtual void MapTile_Trap::draw(int, int)’:
MapTile_Trap.cpp:90: error: invalid use of incomplete type ‘struct CL_Surface’
Resources.h:23: error: forward declaration of ‘struct CL_Surface’
MapTile_Trap.cpp: In member function ‘virtual void MapTile_Trap::draw_tiny(int, int, float)’:
MapTile_Trap.cpp:97: error: invalid use of incomplete type ‘struct CL_Surface’
Resources.h:23: error: forward declaration of ‘struct CL_Surface’
make[2]: *** [MapTile_Trap.o] Error 1
make[2]: Leaving directory `/home/elba/Desktop/clanbomber-1.05/clanbomber'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/elba/Desktop/clanbomber-1.05/clanbomber'
make: *** [install-recursive] Error 1
```

---

### Post by carml on 2009-02-07
Let's try if all went good:type 'cd /usr/bin'and press ENTER;
then type ls and copy and paste the result.

---

### Post by mono-jo on 2009-02-07
elba@elba-desktop:~/Desktop/clanbomber2-0.9.1$ cd /usr/bin
elba@elba-desktop:/usr/bin$

---

### Post by carml on 2009-02-07
> **mono-jo said:**
> elba@elba-desktop:~/Desktop/clanbomber2-0.9.1$ cd /usr/bin
elba@elba-desktop:/usr/bin$
now type 'ls ' and copy and past the result.

---

### Post by mono-jo on 2009-02-07
```
dumpkeys                               rarian-example
dvd-ram-control                        rarian-sk-config
dvd+rw-booktype                        rarian-sk-extract
dvd+rw-format                          rarian-sk-gen-uuid
dvd+rw-mediainfo                       rarian-sk-get-cl
dvipdf                                 rarian-sk-get-content-list
dwell-click-applet                     rarian-sk-get-extended-content-list
edit                                   rarian-sk-get-scripts
editor                                 rarian-sk-install
editres                                rarian-sk-migrate
eject                                  rarian-sk-preinstall
ekiga                                  rarian-sk-rebuild
ekiga-config-tool                      rarian-sk-update
ekiga-helper                           rcp
enc2xs                                 rdesktop
enchant                                rdfpipe
enchant-lsmod                          rdfproc
env                                    readelf
envsubst                               readom
eog                                    recode-sr-latin
epmd                                   red
eps2eps                                redland-db-upgrade
eqn                                    rename
erl                                    rename.ul
erlc                                   renice
erl_call                               reset
esc-m                                  resize
escript                                resizecons
esd                                    rev
esdcat                                 revpath
esdcompat                              rfcomm
esdctl                                 rgrep
esddsp                                 rhythmbox
esdfilt                                rhythmbox-client
esdloop                                rlogin
esdmon                                 rlwrap
esdplay                                routef
esdrec                                 routel
esdsample                              rpcclient
espeak                                 rpcgen
espeak-synthesis-driver                rpcinfo
espeak-synthesis-driver.bin            rpl8
evince                                 rsh
evince-thumbnailer                     rss-glx_install
evolution                              rstart
evolution-addressbook-export           rstartd
ex                                     rsync
exchange-connector-setup-2.24          rtstat
expand                                 runcon
expiry                                 run_erl
expr                                   run-mailcap
extlinux                               run-with-aspell
factor                                 rview
faillog                                rvim
fc-cache                               s2p
fc-cat                                 sane-find-scanner
fc-list                                sas_disk_blink
fc-match                               savelog
festival-synthesis-driver              scanimage
file                                   scim
file-roller                            scim-bridge
find                                   scim-config-agent
find2perl                              scim-setup
findsmb                                scp
finger                                 screen
firefox                                screendump
firefox-3.0                            screenlets
flock                                  screenletsd
fmt                                    screenlets-daemon
fold                                   screenlets-manager
font2c                                 screenlets-packager
fontconfig-voodoo                      script
fonttosfnt                             scriptreplay
foo2hiperc                             scrollkeeper-config
foo2hiperc-wrapper                     scrollkeeper-extract
foo2hp                                 scrollkeeper-gen-seriesid
foo2hp2600-wrapper                     scrollkeeper-get-cl
foo2lava                               scrollkeeper-get-content-list
foo2lava-wrapper                       scrollkeeper-get-extended-content-list
foo2oak                                scrollkeeper-get-index-from-docpath
foo2oak-wrapper                        scrollkeeper-get-toc-from-docpath
foo2qpdl                               scrollkeeper-get-toc-from-id
foo2qpdl-wrapper                       scrollkeeper-install
foo2slx                                scrollkeeper-preinstall
foo2slx-wrapper                        scrollkeeper-rebuilddb
foo2xqx                                scrollkeeper-uninstall
foo2xqx-wrapper                        scrollkeeper-update
foo2zjs                                scsi_logging_level
foo2zjs-icc2ps                         scsi_mandat
foo2zjs-pstops                         scsi_readcap
foo2zjs-wrapper                        scsi_ready
foomatic-combo-xml                     scsi_satl
foomatic-compiledb                     scsi_start
foomatic-configure                     scsi_stop
foomatic-datafile                      scsi_temperature
foomatic-perl-data                     sctp_darn
foomatic-ppdfile                       sctp_test
foomatic-ppd-options                   sdiff
foomatic-printjob                      sdptool
foomatic-rip                           seahorse
foomatic-searchprinter                 seahorse-agent
free                                   seahorse-daemon
freetype-config                        seahorse-preferences
fribidi                                seahorse-tool
from                                   see
fslsfonts                              select-default-iwrap
f-spot                                 select-editor
f-spot-import                          sensible-browser
f-spot-sqlite-upgrade                  sensible-editor
fstobdf                                sensible-pager
ftp                                    seq
funzip                                 service
g++                                    services-admin
g++-4.3                                sessreg
gacutil                                setarch
gamma4scanimage                        setfacl
gcalctool                              setkeycodes
gcc                                    setleds
gcc-4.3                                setlogcons
gccmakedep                             setmetamode
gconf-editor                           setpci
gconf-merge-tree                       setsid
gconfsharp2-schemagen                  setterm
gconftool                              setxkbmap
gconftool-2                            sftp
gcore                                  sg
gcov                                   sg_dd
gcov-4.3                               sg_emc_trespass
gdb                                    sg_format
gdbserver                              sg_get_config
gdbtui                                 sg_ident
gdebi                                  sginfo
gdebi-gtk                              sg_inq
gdialog                                sg_logs
gdk-pixbuf-csource                     sg_luns
gdk-pixbuf-query-loaders               sg_map
gdm-dmx-reconnect-proxy                sg_map26
gdmdynamic                             sgm_dd
gdmflexiserver                         sg_modes
gdmphotosetup                          sg_opcodes
gdm-signal                             sgp_dd
gdmthemetester                         sg_persist
gdmXnest                               sg_prevent
gdmXnestchooser                        sg_raw
gedit                                  sg_rbuf
gencat                                 sg_rdac
genisoimage                            sg_read
geqn                                   sg_read_buffer
GET                                    sg_readcap
getconf                                sg_read_long
geteltorito                            sg_reassign
getent                                 sg_requests
getfacl                                sg_reset
gethostip                              sg_rmsn
getkeycodes                            sg_rtpg
getopt                                 sg_sat_identify
gettext                                sg_scan
gettextize                             sg_senddiag
gettext.sh                             sg_ses
getweb                                 sg_start
gfloppy                                sg_sync
ggz-config                             sg_test_rwbuf
ggz-wrapper                            sg_turs
ghostscript                            sg_verify
gimp                                   sg_vpd
gimp-2.6                               sg_write_buffer
gimp-console                           sg_write_long
gimp-console-2.6                       sg_wr_mode
gipddecode                             sha1sum
gist                                   sha224sum
gksu                                   sha256sum
gksudo                                 sha384sum
gksu-properties                        sha512sum
glib-genmarshal                        shares-admin
glib-gettextize                        shasum
glib-mkenums                           showconsolefont
glxdemo                                showfont
glxgears                               showkey
glxheads                               showrgb
glxinfo                                shred
gmenu-simple-editor                    shuf
gnome-about                            size
gnome-about-me                         skill
gnome-appearance-properties            slabtop
gnome-app-install                      slogin
gnome-at-mobility                      slxdecode
gnome-at-properties                    smartdimmer
gnome-at-visual                        smbcacls
gnome-audio-profiles-properties        smbclient
gnome-calculator                       smbcquotas
gnome-character-map                    smbget
gnome-control-center                   smbpasswd
gnome-default-applications-properties  smbspool
gnome-desktop-item-edit                smbtar
gnome-dictionary                       smbtree
gnome-display-properties               smproxy
gnome-doc-prepare                      snice
gnome-doc-tool                         soelim
gnome-eject                            soffice
gnome-help                             software-properties-gtk
gnome-keybinding-properties            solid-hardware
gnome-keyboard-properties              sopranocmd
gnome-keyring                          sopranod
gnome-keyring-daemon                   sort
gnome-language-selector                speaker-test
gnome-mount                            speechd-synthesis-driver
gnome-mouse-properties                 splain
gnome-nettool                          split
gnome-network-preferences              splitfont
gnome-open                             sprof
gnome-panel                            sqlite
gnome-panel-screenshot                 sqlite3
gnome-pilot-make-password              ssh
gnome-power-bugreport.sh               ssh-add
gnome-power-cmd.sh                     ssh-agent
gnome-power-manager                    ssh-argv0
gnome-power-manager-inhibit            ssh-askpass
gnome-power-preferences                ssh-copy-id
gnome-power-statistics                 ssh-keygen
gnome-screensaver                      ssh-keyscan
gnome-screensaver-command              ssh-vulnkey
gnome-screensaver-preferences          start_embedded
gnome-screenshot                       startx
gnome-search-tool                      stat
gnome-session                          stl2gts
gnome-session-properties               strace
gnome-session-save                     strfile
gnome-settings-daemon                  strings
gnome-sound-properties                 strip
gnome-sound-recorder                   sudo
gnome-system-log                       sudoedit
gnome-system-monitor                   sum
gnome-terminal                         synclient
gnome-terminal.wrapper                 syndaemon
gnome-text-editor                      syslinux
gnome-typing-monitor                   syslinux2ansi
gnome-umount                           system-config-printer
gnomevfs-cat                           system-config-printer-applet
gnomevfs-copy                          system-tools-backends
gnomevfs-df                            tac
gnomevfs-info                          tail
gnomevfs-ls                            tap2deb
gnomevfs-mkdir                         tap2rpm
gnomevfs-monitor                       tapconvert
gnomevfs-mv                            tasksel
gnomevfs-rm                            taskset
gnome-video-thumbnailer                tbl
gnome-volume-control                   tee
gnome-window-properties                telnet
gnome-wm                               telnet.netkit
gobject-query                          test
gpasswd                                testparm
gpg                                    test-speech
gpg-convert-from-106                   tgz
gpgsplit                               tic
gpgv                                   t-im
gpg-zip                                time
gpic                                   time-admin
gpilot-applet                          tkconch
gpilotd                                tload
gpilotd-control-applet                 toc2cddb
gpilotd-session-wrapper                toc2cue
gpilot-install-file                    toe
gpp                                    tomboy
gprof                                  tomboy-panel
groff                                  top
grog                                   torrentinfo-console
grops                                  toshset
grotty                                 totem
groups                                 totem-audio-preview
growisofs                              totem-gstreamer
gs                                     totem-gstreamer-audio-preview
gsbj                                   totem-gstreamer-video-indexer
gsdj                                   totem-gstreamer-video-thumbnailer
gsdj500                                totem-video-indexer
gslj                                   touch
gslp                                   tput
gsnd                                   tr
gst                                    tracepath
gst-convert                            tracepath6
gst-doc                                traceroute6
gst-feedback-0.10                      traceroute6.iputils
gst-inspect-0.10                       tracker-applet
gst-launch-0.10                        trackerd
gst-load                               tracker-extract
gst-package                            tracker-files
gstreamer-codec-install                tracker-meta-folder
gstreamer-properties                   tracker-preferences
gst-reload                             tracker-query
gst-sunit                              tracker-search
gst-typefind-0.10                      tracker-search-tool
gst-visualise-0.10                     tracker-stats
gst-xmlinspect-0.10                    tracker-status
gst-xmllaunch-0.10                     tracker-tag
gtbl                                   tracker-thumbnailer
gtester                                transmission
gtester-report                         trial
gtf                                    troff
gtk-builder-convert                    tsclient
gtk-query-immodules-2.0                tset
gtk-update-icon-cache                  tsort
gtk-window-decorator                   tty
gts2dxf                                twistd
gts2oogl                               tzselect
gts2stl                                ubuntu-bug
gtscheck                               ucf
gtscompare                             ucfq
gtstemplate                            ucfr
gtstransform                           ucs2any
gucharmap                              udevinfo
gvfs-cat                               ul
gvfs-copy                              unattended-upgrade
gvfs-info                              unexpand
gvfs-less                              unicode_stop
gvfs-ls                                uniq
gvfs-mkdir                             unlink
gvfs-monitor-dir                       unlzma
gvfs-monitor-file                      unopkg
gvfs-mount                             unstr
gvfs-move                              untex
gvfs-open                              unzip
gvfs-rename                            unzipsfx
gvfs-rm                                updatedb
gvfs-save                              updatedb.mlocate
gvfs-trash                             update-desktop-database
gvfs-tree                              update-manager
h2ph                                   update-mime-database
h2xs                                   update-notifier
hal-device                             update-pciids
hal-disable-polling                    update-perl-sax-parsers
hal-find-by-capability                 uptime
hal-find-by-property                   usb-creator
hal-get-property                       usb_printerid
hal-is-caller-locked-out               users
hal-is-caller-privileged               users-admin
hal-lock                               uuidgen
hal-set-property                       uxterm
hal-setup-keymap                       uz
hcitool                                vertex
hd                                     vi
head                                   view
HEAD                                   viewres
helpztags                              vim
hexdump                                vimdiff
hipercdecode                           vim.tiny
host                                   vinagre
hostid                                 vino-passwd
hp-align                               vino-preferences
hp-check                               vmmouse_detect
hp-clean                               vmstat
hp-colorcal                            volname
hp-fab                                 w
hp-firmware                            w3m
hpijs                                  w3mman
hp-info                                wall
hp-levels                              watch
hp-makecopies                          wc
hp-makeuri                             wftopfa
hp-print                               wget
hp-probe                               whatis
hp-scan                                whereis
hp-sendfax                             which
hp-setup                               whiptail
hp-systray                             who
hp-testpage                            whoami
hp-timedate                            whois
hp-toolbox                             wings3d
hp-unload                              withsctp
html2text                              wodim
hwtest-gtk                             word-list-compress
i386                                   wpa_passphrase
i486-linux-gnu-cpp                     w.procps
i486-linux-gnu-cpp-4.3                 write
i486-linux-gnu-g++                     wvAbw
i486-linux-gnu-g++-4.3                 wvCleanLatex
i486-linux-gnu-gcc                     wvConvert
i486-linux-gnu-gcc-4.3                 wvdial
iceauth                                wvdialconf
iconv                                  wvDocBook
id                                     wvDVI
iecset                                 wvHtml
ijs_pxljr                              wvLatex
im                                     wvMime
imake                                  wvPDF
imlib-config                           wvPS
im-switch                              wvRTF
info                                   wvSummary
infobrowser                            wvText
infocmp                                wvVersion
infokey                                wvWare
infotocap                              wvWml
install                                www-browser
instmodsh                              X
invest-chart                           X11
ionice                                 x11perf
ipcrm                                  x11perfcomp
ipcs                                   xargs
ipod-read-sysinfo-extended             xauth
isodump                                xbiff
isoinfo                                xbrlapi
isovfy                                 xcalc
ispell-wrapper                         xclipboard
jockey-gtk                             xclock
join                                   xcmsdb
k3d                                    xconsole
k3d-bin                                xcursorgen
k3d-bug-buddy                          xcutsel
k3d-config                             xdg-desktop-icon
k3d-make-module-proxy                  xdg-desktop-menu
k3d-makempeg                           xdg-email
k3d-renderframe                        xdg-icon-resource
k3d-renderjob                          xdg-mime
k3d-sl2xml                             xdg-open
k3d-uuidgen                            xdg-screensaver
kbuildsycoca4                          xdg-user-dir
kcmshell4                              xdg-user-dirs-gtk-update
kcookiejar4                            xdg-user-dirs-update
kde4                                   xditview
kde4-config                            xdpyinfo
kde4-menu                              xdriinfo
kdebugdialog                           xedit
kde-cp                                 xev
kded4                                  xeyes
kdeinit4                               xfd
kdeinit4_shutdown                      xfontsel
kdeinit4_wrapper                       xfsinfo
kde-mv                                 xft-config
kde-open                               xgamma
kfile4                                 xgc
khelpcenter                            xgettext
khotnewstuff4                          xhost
kiconfinder                            xinit
killall                                xinput
kioclient                              xkbbell
kjs                                    xkbcomp
kjscmd                                 xkbevd
kmimetypefinder                        xkbprint
knotify4                               xkbvleds
koi8rxterm                             xkbwatch
kquitapp                               xkill
kreadconfig                            xload
kross                                  xlogo
kshell4                                xlsatoms
kstart                                 xlsclients
ksvgtopng                              xlsfonts
ktraderclient                          xmag
ktrash                                 xman
kuiserver                              xmessage
kwalletd                               xmkmf
kwrapper4                              xml2po
kwriteconfig                           xmlcatalog
l2ping                                 xmllint
last                                   xmodmap
lastb                                  xmore
lastlog                                Xorg
launchmany-console                     xpath
launchmany-curses                      xpcshell-1.9
launchpad-integration                  xprop
lavadecode                             xqxdecode
lcf                                    xrandr
ld                                     xrdb
ldd                                    xrefresh
less                                   xsane
lessecho                               xscreensaver-getimage
lessfile                               xscreensaver-getimage-file
lesskey                                xscreensaver-getimage-video
lesspipe                               xscreensaver-gl-helper
lexgrog                                xscreensaver-text
lftp                                   x-session-manager
lftpget                                xset
libmikmod-config                       xsetmode
libnetcfg                              xsetpointer
libpng12-config                        xsetroot
libpng-config                          xsltproc
line                                   xsm
link                                   xstdcmap
linux32                                xsubpp
linux64                                xterm
listres                                x-terminal-emulator
lndir                                  xtrapchar
lnstat                                 xtrapin
loadkeys                               xtrapinfo
loadunimap                             xtrapout
locale                                 xtrapproto
localedef                              xtrapreset
locate                                 xtrapstats
lockfile-create                        xulrunner
lockfile-remove                        xulrunner-1.9
lockfile-touch                         xvidtune
logger                                 xvinfo
logname                                xwd
look                                   x-window-manager
lorder                                 xwininfo
lore                                   xwud
lp                                     x-www-browser
lpoptions                              xxd

lppasswd                               yafray
lpq                                    yelp
lpr                                    yes
lprm                                   yorick
lpstat                                 zdump
lsattr                                 zenity
lsb_release                            zip
lshal                                  zipcloak
lshw                                   zipgrep
lsof                                   zipinfo
lspci                                  zipnote
lspgpot                                zipsplit
lss16toppm                             zjsdecode
lsusb                                  zsoelim
ltrace
```
elba@elba-desktop:/usr/bin$

---

### Post by carml on 2009-02-07
I tried to compile the program on my PC and it didn't compile.There's a file named make into the folder clanbomber? (I think there's,but I'm unsure).I also made a search and maybe you need the package highlighted in the following image.I found it on System->Administration->Synaptic package manager,I hope this one can solve the problems,because the description says that package is needed to run programs created with it.:confused:

---

### Post by mono-jo on 2009-02-07
umm i cant find the package 
what about remote support ?

---

### Post by carml on 2009-02-07
What do you mean by remote support?

---

### Post by mono-jo on 2009-02-07
when u use the remtote desktop viewer to acess my desktop 
and then you try and fix the problem  without my unxeperiance-ness standing in the way
Synaptic package manager

---

### Post by carml on 2009-02-07
I would do it,but I don't know how to use it. :(
I've found a solution:there's a version written for Windows,download it,then in System->Administration->Synaptic Package Managerlook for a package called 'wine' so you'll don't need to compile the sources to have got a functional game. ;)

---

### Post by mono-jo on 2009-02-07
ok 
go
applications -> Internet ->remote desktop viewer
the type in at connect
<snip>

---

### Post by carml on 2009-02-07
Thanks,but I found a quicker solution: download the version for Windows,then go on System->Administration->Synaptic package manager and look for a package called 'Wine',if you install it you'll don't need to compile the sources to have got a functional game. :)

---

### Post by mpsii on 2009-02-07
Seriously folks... I am working on this... there is a better way than wine, for the love of Linus...

---

### Post by mpsii on 2009-02-07
This was done on Jaunty with clanbomber2 as downloaded from the sourceforge page.

I had to install the directfb libraries. I installed versions 1 and 2. Also, FusionSound was needed.

Then, in the clanbomber2-0.9.1 directory:
```

$ ./configure
$ make

```

I got the following:
```
mschemerii@moonos-vm:~/Desktop/clanbomber2-0.9.1$ make
make  all-recursive
make[1]: Entering directory `/home/mschemerii/Desktop/clanbomber2-0.9.1'
Making all in clanbomber
make[2]: Entering directory `/home/mschemerii/Desktop/clanbomber2-0.9.1/clanbomber'
Making all in maps
make[3]: Entering directory `/home/mschemerii/Desktop/clanbomber2-0.9.1/clanbomber/maps'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/mschemerii/Desktop/clanbomber2-0.9.1/clanbomber/maps'
Making all in pics
make[3]: Entering directory `/home/mschemerii/Desktop/clanbomber2-0.9.1/clanbomber/pics'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/mschemerii/Desktop/clanbomber2-0.9.1/clanbomber/pics'
Making all in wavs
make[3]: Entering directory `/home/mschemerii/Desktop/clanbomber2-0.9.1/clanbomber/wavs'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/mschemerii/Desktop/clanbomber2-0.9.1/clanbomber/wavs'
make[3]: Entering directory `/home/mschemerii/Desktop/clanbomber2-0.9.1/clanbomber'
if g++ -DHAVE_CONFIG_H -I. -I. -I.. -D_REENTRANT -I/usr/include/directfb   -D_REENTRANT -I/usr/include/fusionsound -I/usr/include/directfb   -DDATADIR=\"/usr/local/share/clanbomber2/\"   -g -O2 -MT Bomb.o -MD -MP -MF ".deps/Bomb.Tpo" -c -o Bomb.o Bomb.cpp; \
	then mv -f ".deps/Bomb.Tpo" ".deps/Bomb.Po"; else rm -f ".deps/Bomb.Tpo"; exit 1; fi
In file included from ClanBomber.h:22,
                 from Bomb.cpp:19:
Resources.h:47: error: ‘__u8’ has not been declared
Resources.h:48: error: ‘__u8’ has not been declared
In file included from ClanBomber.h:50,
                 from Bomb.cpp:19:
clanstring.h: In member function ‘char* CL_String::get_string()’:
clanstring.h:337: warning: deprecated conversion from string constant to ‘char*’
In file included from Bomb.h:25,
                 from Bomb.cpp:22:
GameObject.h: At global scope:
GameObject.h:140: error: ‘__u8’ does not name a type
GameObject.h:141: error: ‘__u8’ does not name a type
In file included from Bomb.cpp:24:
Explosion.h: In member function ‘char* Explosion::get_name()’:
Explosion.h:37: warning: deprecated conversion from string constant to ‘char*’
make[3]: *** [Bomb.o] Error 1
make[3]: Leaving directory `/home/mschemerii/Desktop/clanbomber2-0.9.1/clanbomber'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/mschemerii/Desktop/clanbomber2-0.9.1/clanbomber'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/mschemerii/Desktop/clanbomber2-0.9.1'
make: *** [all] Error 2

```

Then, I tried with Clanbomber-1.05 (the older version). I had to install Hermes and Clanlib. I got the following with the make command:
```
mschemerii@moonos-vm:~/Desktop/clanbomber-1.05$ make
make  all-recursive
make[1]: Entering directory `/home/mschemerii/Desktop/clanbomber-1.05'
Making all in clanbomber
make[2]: Entering directory `/home/mschemerii/Desktop/clanbomber-1.05/clanbomber'
Making all in music
make[3]: Entering directory `/home/mschemerii/Desktop/clanbomber-1.05/clanbomber/music'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/mschemerii/Desktop/clanbomber-1.05/clanbomber/music'
Making all in maps
make[3]: Entering directory `/home/mschemerii/Desktop/clanbomber-1.05/clanbomber/maps'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/mschemerii/Desktop/clanbomber-1.05/clanbomber/maps'
Making all in pics
make[3]: Entering directory `/home/mschemerii/Desktop/clanbomber-1.05/clanbomber/pics'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/mschemerii/Desktop/clanbomber-1.05/clanbomber/pics'
Making all in wavs
make[3]: Entering directory `/home/mschemerii/Desktop/clanbomber-1.05/clanbomber/wavs'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/mschemerii/Desktop/clanbomber-1.05/clanbomber/wavs'
make[3]: Entering directory `/home/mschemerii/Desktop/clanbomber-1.05/clanbomber'
if g++ -DPKGDATADIR=\"/usr/local/share/clanbomber/\" -DHAVE_CONFIG_H -I. -I. -I.. -I. -I..    -g -O2 -MT Disease_Fast.o -MD -MP -MF ".deps/Disease_Fast.Tpo" \
	  -c -o Disease_Fast.o `test -f 'Disease_Fast.cpp' || echo './'`Disease_Fast.cpp; \
	then mv -f ".deps/Disease_Fast.Tpo" ".deps/Disease_Fast.Po"; \
	else rm -f ".deps/Disease_Fast.Tpo"; exit 1; \
	fi
In file included from Extra_Koks.h:22,
                 from Disease_Fast.cpp:21:
Extra.h: In member function ‘char* Extra::get_name()’:
Extra.h:38: warning: deprecated conversion from string constant to ‘char*’
if g++ -DPKGDATADIR=\"/usr/local/share/clanbomber/\" -DHAVE_CONFIG_H -I. -I. -I.. -I. -I..    -g -O2 -MT MapTile_Trap.o -MD -MP -MF ".deps/MapTile_Trap.Tpo" \
	  -c -o MapTile_Trap.o `test -f 'MapTile_Trap.cpp' || echo './'`MapTile_Trap.cpp; \
	then mv -f ".deps/MapTile_Trap.Tpo" ".deps/MapTile_Trap.Po"; \
	else rm -f ".deps/MapTile_Trap.Tpo"; exit 1; \
	fi
MapTile_Trap.cpp:25:45: error: ClanLib/Display/Display/surface.h: No such file or directory
MapTile_Trap.cpp: In member function ‘virtual void MapTile_Trap::draw(int, int)’:
MapTile_Trap.cpp:90: error: invalid use of incomplete type ‘struct CL_Surface’
Resources.h:23: error: forward declaration of ‘struct CL_Surface’
MapTile_Trap.cpp: In member function ‘virtual void MapTile_Trap::draw_tiny(int, int, float)’:
MapTile_Trap.cpp:97: error: invalid use of incomplete type ‘struct CL_Surface’
Resources.h:23: error: forward declaration of ‘struct CL_Surface’
make[3]: *** [MapTile_Trap.o] Error 1
make[3]: Leaving directory `/home/mschemerii/Desktop/clanbomber-1.05/clanbomber'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/mschemerii/Desktop/clanbomber-1.05/clanbomber'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/mschemerii/Desktop/clanbomber-1.05'
make: *** [all] Error 2

```

---

### Post by carml on 2009-02-08
@ mpsii
I'm glad there's a fully Linux solution,but I didn't know the necessary libraries I guessed the compiler was missing,so I posted a surely functional solution.:)
Did you check if the program run,after you compiled it?

---

### Post by mpsii on 2009-02-08
> **carml said:**
> @ mpsii
I'm glad there's a fully Linux solution,but I didn't know the necessary libraries I guessed the compiler was missing,so I posted a surely functional solution.:)
Did you check if the program run,after you compiled it?

@ carml
That is okay... I just get frustrated when the natural response to a difficult compile is "install the windows version with wine".

No, it did not run, due to the compile errors. I am unsure why the compile errors occurred. There is a deprecated conversion of a constant to a string. I don't know if this is the GCC version complaining or a library complaint or what.

Unless someone else has something to add, I would suggest contacting the developers of the game and ask their input. The same error for both version 1 and version 2 of the game cannot be coincidence.

---

### Post by _rsl_ on 2009-03-03
This might be a bit late but you can try the version at [http://savannah.nongnu.org/projects/clanbomber/](http://savannah.nongnu.org/projects/clanbomber/) . Please note that is quite buggy but is in active and slow development and IMO is a lot easier to compile.

---

