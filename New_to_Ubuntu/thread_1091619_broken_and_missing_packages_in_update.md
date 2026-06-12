---
title: "broken and missing packages in update"
date: 2009-03-09
forum: New to Ubuntu
---

### Post by Chronicburn on 2009-03-09
hi i'm totally new to Ubuntu, im running Ubuntu 8.10 (Ultimate edition 2.1) and when i try to install te Gtk 2.12 engine or i try to update , i get this weird error: , i copy pasted everything i typed in the terminal

simon@simon-laptop:~$ sudo apt-get update && sudo apt-get upgrade
[sudo] password for simon: 
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release.gpg [307B]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg                   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Translation-en_US        
Get:2 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid Release.gpg [191B]              
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid/main Translation-en_US            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release.gpg                              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Translation-en_US                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release.gpg                              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Translation-en_US                   
Get:3 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release.gpg [307B]                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Translation-en_US                   
Get:4 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg [307B]                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US                     
Get:5 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release.gpg [307B]                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Translation-en_US  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Translation-en_US    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Translation-en_US  
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) intrepid Release.gpg                          
Ign [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) intrepid/main Translation-en_US               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Translation-en_US                   
Get:6 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid Release [1025B]                 
Ign [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) intrepid/restricted Translation-en_US         
Ign [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) intrepid/universe Translation-en_US           
Ign [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) intrepid/multiverse Translation-en_US         
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) intrepid-updates Release.gpg                  
Ign [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) intrepid-updates/main Translation-en_US       
Ign [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) intrepid-updates/restricted Translation-en_US 
Ign [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) intrepid-updates/universe Translation-en_US   
Ign [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) intrepid-updates/multiverse Translation-en_US 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release                       
Get:7 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release [46.7kB]                       
Get:8 [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release.gpg [197B]                
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Translation-en_US              
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) intrepid Release                              
Get:9 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release [27.6kB]                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release                                  
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Translation-en_US          
Get:10 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release [27.6kB]                      
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) intrepid-updates Release                      
Get:11 [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release [11.7kB]                 
Get:12 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release [52.9kB]                        
Get:13 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release [46.7kB]                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages
Err [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid Release
  
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release                                  
  
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release                                  
  
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) intrepid/main Packages                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Packages                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                            
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) intrepid/restricted Packages                  
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) intrepid/main Sources                         
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) intrepid/restricted Sources                   
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) intrepid/universe Packages                    
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) intrepid/universe Sources                     
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) intrepid/multiverse Packages                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                                    
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release                             
  
Ign [http://repoubuntusoftware.info](http://repoubuntusoftware.info) intrepid Release.gpg                        
Ign [http://repoubuntusoftware.info](http://repoubuntusoftware.info) intrepid/all Translation-en_US              
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release                                  
  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Packages           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Sources        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Packages
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) intrepid/multiverse Sources
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages
  404 Not Found
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) intrepid-updates/main Packages
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) intrepid-updates/restricted Packages
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) intrepid-updates/main Sources
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) intrepid-updates/restricted Sources
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) intrepid-updates/universe Packages
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) intrepid-updates/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Sources    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Packages 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Sources  
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) intrepid-updates/multiverse Packages
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) intrepid-updates/multiverse Sources
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages
Ign [http://repoubuntusoftware.info](http://repoubuntusoftware.info) intrepid Release
Ign [http://repoubuntusoftware.info](http://repoubuntusoftware.info) intrepid/all Packages
Hit [http://repoubuntusoftware.info](http://repoubuntusoftware.info) intrepid/all Packages
Fetched 13.4kB in 0s (14.0kB/s)
Reading package lists... Done
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 778978B00F7992B0

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 60D11217247D1CFF

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 632D16BB0C713DA6
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 43C0AFF0D7FAE680

W: Failed to fetch [http://ppa.launchpad.net/project-neon/ubuntu/dists/intrepid/Release](http://ppa.launchpad.net/project-neon/ubuntu/dists/intrepid/Release)  

W: Failed to fetch [http://wine.budgetdedicated.com/apt/dists/intrepid/Release](http://wine.budgetdedicated.com/apt/dists/intrepid/Release)  

W: Failed to fetch [http://ppa.launchpad.net/openoffice-pkgs/ubuntu/dists/intrepid/Release](http://ppa.launchpad.net/openoffice-pkgs/ubuntu/dists/intrepid/Release)  

W: Failed to fetch [http://ppa.launchpad.net/team-xbmc-intrepid/ubuntu/dists/intrepid/Release](http://ppa.launchpad.net/team-xbmc-intrepid/ubuntu/dists/intrepid/Release)  

W: Failed to fetch [http://packages.medibuntu.org/dists/intrepid/Release](http://packages.medibuntu.org/dists/intrepid/Release)  

W: Failed to fetch [http://ppa.launchpad.net/googlegadgets/ubuntu/dists/intrepid/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/googlegadgets/ubuntu/dists/intrepid/main/binary-amd64/Packages.gz)  404 Not Found

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  libcairo2 mplayer
The following packages will be upgraded:
  pidgin-libnotify
1 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
Need to get 17.9kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  pidgin-libnotify
Install these packages without verification [y/N]? y
Err [http://repoubuntusoftware.info](http://repoubuntusoftware.info) intrepid/all pidgin-libnotify 0.13-1~getdeb1
  404 Not Found
Failed to fetch [http://repoubuntusoftware.info/./pidgin-libnotify_0.13-1~getdeb1_amd64.deb](http://repoubuntusoftware.info/./pidgin-libnotify_0.13-1~getdeb1_amd64.deb)  404 Not Found
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
simon@simon-laptop:~$ sudo apt-get install build-essential auto-apt checkinstallReading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
auto-apt is already the newest version.
checkinstall is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
simon@simon-laptop:~$ cd /home/simon/Desktop/aurora-1.5
simon@simon-laptop:~/Desktop/aurora-1.5$ /home/simon/Desktop/aurora-1.5
bash: /home/simon/Desktop/aurora-1.5: is a directory
simon@simon-laptop:~/Desktop/aurora-1.5$ auto-apt run ./configure --prefix=/usr -enable-animation
Entering auto-apt mode: ./configure --prefix=/usr -enable-animation
Exit the command to leave auto-apt mode.
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
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
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking whether make sets $(MAKE)... (cached) yes
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
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
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
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
checking the maximum length of command line arguments... 1572864
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
checking whether the gcc linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld -m elf_x86_64
checking if the linker (/usr/bin/ld -m elf_x86_64) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for GTK... no
configure: error: GTK+-2.10 is required to compile aurora
simon@simon-laptop:~/Desktop/aurora-1.5$ sudo apt-get install libgtk2.0-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libgtk2.0-dev: Depends: libgtk2.0-0 (= 2.14.4-0ubuntu1) but 2.14.4-0ubuntu2 is to be installed
                 Depends: libpango1.0-dev (>= 1.20) but it is not going to be installed
                 Depends: libcairo2-dev but it is not going to be installed
E: Broken packages
simon@simon-laptop:~/Desktop/aurora-1.5$ cd
simon@simon-laptop:~$ sudo dpkg --configure -ain terminal
dpkg: conflicting actions -i (--install) and -

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
simon@simon-laptop:~$ sudo apt-get intall -f
E: Invalid operation intall
simon@simon-laptop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
simon@simon-laptop:~$ 













what went wrong?

---

### Post by taurus on 2009-03-09
Did you really have Jaunty's repos in your /etc/apt/sources.list?

```
cat /etc/apt/sources.list
```

---

### Post by Chronicburn on 2009-03-09
eh no? i checked that command ( cat /etc/apt/sources.list )  and it gives:

simon@simon-laptop:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081029.2)]/ intrepid main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid main restricted #Added by software-properties
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://be.archive.ubuntu.com/ubuntu/](http://be.archive.ubuntu.com/ubuntu/) intrepid main restricted
deb-src [http://be.archive.ubuntu.com/ubuntu/](http://be.archive.ubuntu.com/ubuntu/) intrepid restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://be.archive.ubuntu.com/ubuntu/](http://be.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted
deb-src [http://be.archive.ubuntu.com/ubuntu/](http://be.archive.ubuntu.com/ubuntu/) intrepid-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://be.archive.ubuntu.com/ubuntu/](http://be.archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://be.archive.ubuntu.com/ubuntu/](http://be.archive.ubuntu.com/ubuntu/) intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://be.archive.ubuntu.com/ubuntu/](http://be.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb [http://be.archive.ubuntu.com/ubuntu/](http://be.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://be.archive.ubuntu.com/ubuntu/](http://be.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
deb-src [http://be.archive.ubuntu.com/ubuntu/](http://be.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
simon@simon-laptop:~$ 




so thats everything from intrepid (8.10) ?

and something i forgot to say in my first post: i got the AMD64 (64bit) edition




EDIT: why is there something about Jaunty in the first post? (the terminal commands in my first post)

---

### Post by taurus on 2009-03-09
What's the output of this command?

```
ls -la /etc/apt/sources.list.d
```

p.s.  Did you add a third party repo, ppa.launchpad.net, to your source list?

---

### Post by scratman on 2009-03-09
Could it be something as mundane as a lack of internet connection?

---

### Post by Chronicburn on 2009-03-09
i didnt add any repositories myself, just everything standard,(i run ubuntu ultimate edition so lots of stuff was pre-installed)

and the command outcome is: simon@simon-laptop:~$ ls -la /etc/apt/sources.list.d
total 80
drwxr-xr-x 2 root root 4096 2009-03-09 20:12 .
drwxr-xr-x 4 root root 4096 2009-03-09 20:12 ..
-rw-r--r-- 1 root root   79 2009-03-09 20:13 amarok-nightly.sources.list
-rw-r--r-- 1 root root   79 2009-03-09 20:13 amarok-nightly.sources.list.save
-rw-r--r-- 1 root root   70 2009-03-09 20:13 compiz.sources.list
-rw-r--r-- 1 root root   70 2009-03-09 20:13 compiz.sources.list.save
-rw-r--r-- 1 root root   80 2009-03-09 20:13 google_gadgets.sources.list
-rw-r--r-- 1 root root   80 2009-03-09 20:13 google_gadgets.sources.list.save
-rw-r--r-- 1 root root  229 2009-03-09 20:13 medibuntu.list
-rw-r--r-- 1 root root  229 2009-03-09 20:13 medibuntu.list.save
-rw-r--r-- 1 root root   87 2009-03-09 20:13 openoffice.sources.list
-rw-r--r-- 1 root root   87 2009-03-09 20:13 openoffice.sources.list.save
-rw-r--r-- 1 root root   67 2009-03-09 20:13 songbird.sources.list
-rw-r--r-- 1 root root   67 2009-03-09 20:13 songbird.sources.list.save
-rw-r--r-- 1 root root   72 2009-03-09 20:13 ultimate.sources.list
-rw-r--r-- 1 root root   72 2009-03-09 20:13 ultimate.sources.list.save
-rw-r--r-- 1 root root   62 2009-03-09 20:13 wine.sources.list
-rw-r--r-- 1 root root   62 2009-03-09 20:13 wine.sources.list.save
-rw-r--r-- 1 root root   86 2009-03-09 20:13 xbmc.sources.list
-rw-r--r-- 1 root root   86 2009-03-09 20:13 xbmc.sources.list.save
simon@simon-laptop:~$

---

### Post by Chronicburn on 2009-03-09
> **scratman said:**
> Could it be something as mundane as a lack of internet connection?

no certainly not, some packages DO update in update manager (firefox 3.07 updated as example, i remember this one) so that should be no problem

---

### Post by taurus on 2009-03-09
```
http://ppa.launchpad.net **[COLOR="Red"]jaunty[/COLOR]** Release
```

Maybe have a look in /etc/apt/sources.list.d/ultimate.sources.list.

```
cat /etc/apt/sources.list.d/ultimate.sources.list
```

---

### Post by Chronicburn on 2009-03-09
simon@simon-laptop:~$ cat /etc/apt/sources.list.d/ultimate.sources.list
deb [http://repoubuntusoftware.info/](http://repoubuntusoftware.info/) intrepid all #Ultimate Edition Repo
simon@simon-laptop:~$ 



still only intrepids

---

### Post by taurus on 2009-03-09
Look at all those *.list in /etc/apt/sources.list.d.

---

### Post by Chronicburn on 2009-03-09
nothing which contains jaunty, only amarok and onther programs and ultimate resources (ultimate edition i suppose?)

---

### Post by Chronicburn on 2009-03-09
but nvm (probably) , im gonna format my pc and install the normal ubuntu intrepid, in the meantime i found out that the ultimate edition takes more memory than normal one and my sound is very lossy (even with ALSA)

so thx for trying to help, i hope i dont have this problem on intrepid when i formatted

---

