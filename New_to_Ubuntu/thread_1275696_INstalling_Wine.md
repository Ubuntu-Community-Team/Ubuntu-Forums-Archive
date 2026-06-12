---
title: "INstalling Wine"
date: 2009-09-26
forum: New to Ubuntu
---

### Post by vlad1975 on 2009-09-26
Hello

Im trying to install the new version of wine. i have extract it but i seem to have problem installing it.

ed@ed-desktop:~$ cd /home/ed/Desktop/wine-1.1.30
ed@ed-desktop:~/Desktop/wine-1.1.30$ ls
aclocal.m4  configure     documentation  LICENSE      Make.rules.in  tools
ANNOUNCE    configure.ac  fonts          LICENSE.OLD  programs       VERSION
AUTHORS     COPYING.LIB   include        loader       README
config.log  dlls          libs           Makefile.in  server
ed@ed-desktop:~/Desktop/wine-1.1.30$ ./config
bash: ./config: No such file or directory
ed@ed-desktop:~/Desktop/wine-1.1.30$ config
bash: config: command not found
ed@ed-desktop:~/Desktop/wine-1.1.30$ ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
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
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for cpp... cpp
checking for the directory containing the Wine tools... $(TOPOBJDIR)
checking for flex... no
configure: error: no suitable flex found. Please install the 'flex' package.

what comman do i need to type to get this installed?

---

### Post by howefield on 2009-09-26
Any reason why you wouldn't add the wine repository and use synaptic to install ?

winehq.org > download > ubuntu > follow the tutorial

---

### Post by 3rdalbum on 2009-09-26
> **vlad1975 said:**
> 
checking for flex... no
configure: error: no suitable flex found. Please install the 'flex' package.

Have you got Flex installed? If you do (it should be installed if you have build-essential?) then you would need to get the latest version of Flex and build that from source.

---

### Post by vlad1975 on 2009-09-26
> Any reason why you wouldn't add the wine repository and use synaptic to install ?

winehq.org > download > ubuntu > follow the tutorial

that only install 1.1.29 version which i have installed
 i am trying to install 1.1.30

how do i install flex?

---

### Post by CatKiller on 2009-09-26
From the release announcement:

> The source is [available now]("http://prdownloads.sourceforge.net/wine/wine-1.1.30.tar.bz2"). Binary packages are in the process of being built, and will appear soon at their respective [download locations]("http://www.winehq.org/download").  


Why not just wait a couple of days?

To install flex just run ```
sudo apt-get install flex
``` Or you could add the WineHQ source repository and then run ```
sudo apt-get build-dep wine
```

---

### Post by 3rdalbum on 2009-09-26
Geez man, that's not even a point version difference... it's a point-point version. If you can't find Flex in the repositories, or you can't find its project page and build it, then you're going to struggle to compile Wine and you might as well just wait for the binaries to become available.

---

### Post by vlad1975 on 2009-09-26
I hear ya... im just getting really frustrated as i cant get City of Heroes working and i was hpong updating wine would do it.. AAGGHHHH!!!! IT DID NOT WORK :(


thanx anyway guys

---

### Post by vlad1975 on 2009-09-26
I hear ya... im just getting really frustrated as i cant get City of Heroes working and i was hoping updating wine would do it.. AAGGHHHH!!!! IT DID NOT WORK :(


thanx anyway guys

---

### Post by Liolikas on 2009-09-26
Look there is regression you have to use .19 wine:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=2980](http://appdb.winehq.org/objectManager.php?sClass=version&iId=2980)

---

