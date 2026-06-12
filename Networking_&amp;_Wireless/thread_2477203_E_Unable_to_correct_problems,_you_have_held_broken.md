---
title: "E: Unable to correct problems, you have held broken packages."
date: 2022-07-18
forum: Networking &amp; Wireless
---

### Post by chat-4432 on 2022-07-18
i cant install srsran [https://www.srslte.com/download](https://www.srslte.com/download)
when i 
sudo apt-get install srsran -y
it shows

```
Reading package lists... DoneBuilding dependency tree... Done
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 srsran : Depends: srsenb (>= 22.04-0ubuntu1~srsran5~22.04) but it is not installable
          Depends: srsenb (< 22.04.0~) but it is not installable
          Depends: srsue (>= 22.04-0ubuntu1~srsran5~22.04) but it is not installable
          Depends: srsue (< 22.04.0~) but it is not installable
          Depends: srsepc (>= 22.04-0ubuntu1~srsran5~22.04) but it is not installable
          Depends: srsepc (< 22.04.0~) but it is not installable
E: Unable to correct problems, you have held broken packages.



```
what should i do ??

---

### Post by TheFu on 2022-07-18
if you run 
```
sudo apt update
sudo apt full-upgrade
```
do both of those finish without **any** errors?
Fix those first.

---

### Post by chat-4432 on 2022-07-18
i try 
$ sudo apt update
sudo apt full-upgrade
> Hit:1 [https://download.docker.com/linux/ubuntu](https://download.docker.com/linux/ubuntu) jammy InRelease
Hit:2 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) jammy InRelease
Hit:3 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) jammy-updates InRelease
Hit:4 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) jammy-backports InRelease
Hit:5 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) jammy-security InRelease
Hit:6 [https://ppa.launchpadcontent.net/softwareradiosystems/srsran/ubuntu](https://ppa.launchpadcontent.net/softwareradiosystems/srsran/ubuntu) jammy InRelease
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
All packages are up to date.
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


without error
show same error
$ sudo apt-get install srsran -y
> 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 srsran : Depends: srsenb (>= 22.04-0ubuntu1~srsran5~22.04) but it is not installable
          Depends: srsenb (< 22.04.0~) but it is not installable
          Depends: srsue (>= 22.04-0ubuntu1~srsran5~22.04) but it is not installable
          Depends: srsue (< 22.04.0~) but it is not installable
          Depends: srsepc (>= 22.04-0ubuntu1~srsran5~22.04) but it is not installable
          Depends: srsepc (< 22.04.0~) but it is not installable
E: Unable to correct problems, you have held broken packages.
what should i do ??

---

### Post by deadflowr on 2022-07-19
No arm packages were built for the srsran PPA.
Only amd64 packages.

---

### Post by chat-4432 on 2022-07-19
> **deadflowr said:**
> No arm packages were built for the srsran PPA.
Only amd64 packages.
i thought it was work for [COLOR=#404040][FONT=Lato] aarch64 image[/FONT][/COLOR]
[https://docs.srslte.com/en/latest/app_notes/source/pi4/source/index.html#introduction](https://docs.srslte.com/en/latest/app_notes/source/pi4/source/index.html#introduction)
my ubuntu is like 
```
Welcome to Ubuntu 22.04 LTS (GNU/Linux 5.15.0-1012-raspi aarch64)
```

---

### Post by deadflowr on 2022-07-19
> i thought it was work for aarch64 image

Sure.
But you'd need to compile and build it from source.

The PPA only built amd64 packages.

---

### Post by chat-4432 on 2022-07-19
> **deadflowr said:**
> Sure.
But you'd need to compile and build it from source.

can you suggest me for this ? using VM ??

---

### Post by deadflowr on 2022-07-19
The link you posted in post #5 shows exactly how to install it from source.
Just follow it carefully.

---

### Post by chat-4432 on 2022-07-22
> **deadflowr said:**
> The link you posted in post #5 shows exactly how to install it from source.
Just follow it carefully.
[COLOR=#000000] I changed to install zmq but idk which library is require for [/COLOR][COLOR=#404040][FONT=SFMono-Regular]libzmq/srsran do you know how to check for that ?? [/FONT][/COLOR][https://docs.srslte.com/en/latest/ap...rce/index.html]("https://docs.srslte.com/en/latest/app_notes/source/zeromq/source/index.html")

---

### Post by chat-4432 on 2022-07-22
when i try 
cmake [COLOR=#666666]../
it show 


cc1: all warnings being treated as errors
make[2]: *** [lib/src/phy/fec/CMakeFiles/srsran_fec.dir/build.make:608: lib/src/phy/fec/CMakeFiles/srsran_fec.dir/turbo/turbodecoder.c.o] Error 1
make[1]: *** [CMakeFiles/Makefile2:4485: lib/src/phy/fec/CMakeFiles/srsran_fec.dir/all] Error 2


[/COLOR]

---

### Post by TheFu on 2022-07-22
> **chat-4432 said:**
> [COLOR=#000000] I changed to install zmq but idk which library is require for [/COLOR][COLOR=#404040][FONT=SFMono-Regular]libzmq/srsran do you know how to check for that ?? [/FONT][/COLOR][https://docs.srslte.com/en/latest/ap...rce/index.html]("https://docs.srslte.com/en/latest/app_notes/source/zeromq/source/index.html")

You can look for the file on the system or look for the package, usually the -dev version is needed which includes the library and the header files.
How to perform software development tasks really isn't what this forum is about.
apt search, apt-query, or any of the 10+ other ways to search for packages. Your choice.
find, locate, or just browsing around in the normal directory areas for where libraries and headers are often placed can all work.  Because I strive to only install packages from official sources to avoid lots of other issues, I'd look under /usr/lib/ first, then inside the package manager.  If the library isn't in a repo, or the required version isn't in a repo, then I'd have to decide if I want to risk forcing the installation of a non-core repo library or not.  The answer depends on the reputation of the project team for screwing up systems and how different the library version is.  If it is older than the version in the repo, I'd setup a little build area to keep it away from the rest of the system. Don't want old libraries contaminating my systems.  If it is newer than the repo, but the same in the z and y versions of the z.y.x  naming scheme, I'd probably go with the newer version. If it is newer in either the z or the y numbers, I wouldn't install it and would need the hassle of setting up a separate build area.  How to setup a separate build area is really about controlling the order of LD_LIBRARY_PATH information and modifying the build scripts/Makefiles, if they use those.  Explaining further is something I'll let someone else do or you can learn about Unix software development from the hundreds of books available on the subject.

Learning these things happens through experience, reading, and being around other people doing similar stuff.  Of course, every development team will do things in a slightly different way, so if there are 1,000,000 different projects, then there are 1,000,000 different ways to do things.  Most are very similar, but slightly different because every project is a little different.

There are language specific forums and usually there are README, INSTALL, and other documentation created by the project team, though I haven't looked at the SRS stuff.

I can understand if this is frustrating.  You didn't expect that installing 1 program you'd like to use would entail all this extra stuff.  Usually it doesn't, but with niche software and teams that are rapidly coding for more features, this is common on Unix and has been this way for 40+ yrs.  In the early 1990s when I was learning, everything was shipped as source code. The only program that was available as a binary was the platform C compiler/linker. In BSD-style Unix, the compiler was included with the OS and free. The next year, in SysV Unix, the platform compiler was a $1500 addon.  That's when gcc became really popular.  So, I pulled gcc down for my platform and the first thing I did was compile the version of gcc I needed with the options I needed.  Then I'd start using that version to compile hundreds of other programs from source code, manually hunting down all the dependencies and compiling those into programs or libraries first.  Makefiles would know about dependencies, but it didn't magically get the libraries and compile them. That was all manual.

And that's were you are today with this project.  Hopefully, there aren't too many dependencies. I recall some projects would require 20 libraries before we could even attempt to link a program. It was a hassle and I was being paid as a software developer, not a build-engineer. Big waste of my time, IMO, but it had to be done.  At the time, I was supporting 12 different platforms, so it had to be done on 11 platforms while the rest of my team kept working on the code on their SunOS systems.  Did I mention that our HDDs were 1GB (or smaller) at the time?  This had to hold the OS, compilers, all the source code, editors, and personal files.  I was forever running out of room on my OSF/1 (DEC Alpha) box.  I didn't have room for both emacs and all the code for why I was there being paid.

---

### Post by TheFu on 2022-07-22
> **chat-4432 said:**
> when i try 

```
$ cmake ../

cc1: all warnings being treated as errors
make[2]: *** [lib/src/phy/fec/CMakeFiles/srsran_fec.dir/build.make:608: lib/src/phy/fec/CMakeFiles/srsran_fec.dir/turbo/turbodecoder.c.o] Error 1
make[1]: *** [CMakeFiles/Makefile2:4485: lib/src/phy/fec/CMakeFiles/srsran_fec.dir/all] Error 2
```


I cleaned up what you posted for readability.

The input to a cmake is a CMakefile, not a directory.  Make usually depends on being in the correct PWD.  Now, I've barely used cmake in my life. I'm from an age when we used gmake and Makefiles, so I never learned cmake.

If it were me, after a quick cmake manpage scan, I'd try
```
$ cd ..
$ cmake --build ./  
```
The build-mode accepts a directory as input.

---

### Post by chat-4432 on 2022-07-22
i think it was my mistake not cmake  but make command
what about this error ?
i do following this video
[https://youtu.be/W8hPPQmQ9-0?t=570](https://youtu.be/W8hPPQmQ9-0?t=570)
when i try 
make
it shows
cc1: all warnings being treated as errors
make[2]: *** [lib/src/phy/fec/CMakeFiles/srsran_fec.dir/build.make:608: lib/src/                                                                              
phy/fec/CMakeFiles/srsran_fec.dir/turbo/turbodecoder.c.o] Error 1
make[1]: *** [CMakeFiles/Makefile2:4485: lib/src/phy/fec/CMakeFiles/srsran_fec.d                                                                              
ir/all] Error 2
make: *** [Makefile:166: all] Error 2

what should i do ??

---

### Post by TheFu on 2022-07-23
Make/gmake uses "Makefiles".
CMake uses Cmakefiles.  Read the documentation to know which you are suppose to be using.

I won't be looking at a video. Sorry.

---

### Post by chat-4432 on 2022-07-24
> **TheFu said:**
> I cleaned up what you posted for readability.

The input to a cmake is a CMakefile, not a directory.  Make usually depends on being in the correct _PWD_.  Now, I've barely used cmake in my life. I'm from an age when we used gmake and Makefiles, so I never learned cmake.

If it were me, after a quick cmake manpage scan, I'd try
```
$ cd ..
$ cmake --build ./  
```
The build-mode accepts a directory as input.
what dose it mean PWD ?

---

### Post by chat-4432 on 2022-07-24
i also got this when i 
[COLOR=#666666]./[/COLOR]autogen[COLOR=#666666].[/COLOR]sh 
warning: The macro `AC_TRY_RUN' is obsolete.configure.ac:1028: You should run autoupdate.

but when i try autoupdate it broke installation

---

### Post by TheFu on 2022-07-24
> **chat-4432 said:**
> what dose it mean PWD ?

Present
Working
Directory

Sometimes called CWD, Current Working Directory.  There is a command, pwd, that returns the answer.  You can check if $PWD is set. On many UNIX systems, the $CWD is maintained with the same result.  

Please start with this resource to fill in the gaps: [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php)  We all have knowledge gaps, since nobody learns everything in the same order.  Plus, commands are updated from time to time, so people who looked up command options in 1995 will discover new options in 2022 which might make life easier.  The last ten years, many normal Unix commands added the -h switch for "human readable" output or sorting. Those changes let me drop about 10 aliases.

---

### Post by chat-4432 on 2022-07-24
i try cd .. 
to srsran folder 
then cmake --build ./
```
Error: could not load cache
```

---

### Post by TheFu on 2022-07-24
Details matter.  The command you used isn't the one I posted in #12 above. A single space in the wrong place completely changes everything.

---

### Post by chat-4432 on 2022-07-27
i just brought rpi 4 [https://docs.srsran.com/en/latest/app_notes/source/hw_packs/source/index.html#zmq](https://docs.srsran.com/en/latest/app_notes/source/hw_packs/source/index.html#zmq)
i still got the same error when i try command
make 
```
cc1: all warnings being treated as errors
make[2]: *** [lib/src/phy/fec/CMakeFiles/srsran_fec.dir/build.make:608: lib/src/phy/fec/CMakeFiles/srsran_fec.dir/turbo/turbodecoder.c.o] Error 1
make[1]: *** [CMakeFiles/Makefile2:4485: lib/src/phy/fec/CMakeFiles/srsran_fec.dir/all] Error 2
make: *** [Makefile:166: all] Error 2
```
what should i do ??

---

### Post by chat-4432 on 2022-07-30
anyone know how to Cross Compiler x86 on my ARM ?

---

