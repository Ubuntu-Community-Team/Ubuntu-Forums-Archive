---
title: "amsn"
date: 2009-01-27
forum: New to Ubuntu
---

### Post by zigzagff17 on 2009-01-27
Ok, i would like to stay in touch with friends and family so i downloaded amsn and   ActiveTcl8.5.5.0.287690-linux-ix86-threaded.tar.gz, no i installed (right clicked on install.sh) and installed it to a new folder called 'progs' actually in zigzag/progs. then used the terminal and went to the msn folder in 'documents' and did ./configure but got this

zigzag@zigzag-laptop:~/Documents/msn$ ./configure
checking for prefix by checking for wish... no
expr: syntax error
./configure: line 1966: test: too many arguments
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
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
configure: error: You need a C++ compiler (g++) to compiler aMSN. Please install g++ and try again
 
I thought the Tcl8.5 was a compiler or did i install it wrong?

---

### Post by zigzagff17 on 2009-01-27
ok i figured out i installed tcl8.5 wrong, but don't know how to remove it and where i should put it.

---

### Post by binbash on 2009-01-27
install g++

---

### Post by talsemgeest on 2009-01-27
> **zigzagff17 said:**
> Ok, i would like to stay in touch with friends and family so i downloaded amsn and   ActiveTcl8.5.5.0.287690-linux-ix86-threaded.tar.gz, no i installed (right clicked on install.sh) and installed it to a new folder called 'progs' actually in zigzag/progs. then used the terminal and went to the msn folder in 'documents' and did ./configure but got this

zigzag@zigzag-laptop:~/Documents/msn$ ./configure
checking for prefix by checking for wish... no
expr: syntax error
./configure: line 1966: test: too many arguments
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
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
configure: error: You need a C++ compiler (g++) to compiler aMSN. Please install g++ and try again
 
I thought the Tcl8.5 was a compiler or did i install it wrong?
Well, from the look of the error, try running ```
sudo apt-get install build-essential
``` then try compiling again.

---

### Post by talsemgeest on 2009-01-27
> **binbash said:**
> install g++
Yep, g++ is contained in the build-essential package, along with other things you need to compile software. :)

---

### Post by binbash on 2009-01-27
you will also need tk-dev package

---

### Post by m_duck on 2009-01-27
It would be easier to install amsn via synaptic. Just search for amsn and click install then apply. This will also install all of its dependencies like tcl, tk etc and will keep the package up to date. You can also install via command line using:```
sudo apt-get install amsn
```

---

### Post by talsemgeest on 2009-01-27
> **m_duck said:**
> It would be easier to install amsn via synaptic. Just search for amsn and click install then apply. This will also install all of its dependencies like tcl, tk etc and will keep the package up to date. You can also install via command line using:```
sudo apt-get install amsn
```
However, some people prefer to install the bleeding edge version of their software, and all the new features that come with it. ;)

---

### Post by m_duck on 2009-01-27
True, though it seems as though the latest version on the amsn site is the same as the one in the Intrepid repos, though I've made the assumption that zigzag is running Intrepid... :p

---

### Post by zigzagff17 on 2009-01-27
sudo apt-get install amsn

I am trying this and seems to be doing something good.
I am not into getting all the bleeding parts of stuff ... YET :D
I am totally new to this OS, don't get me wrong its a bit different and more manual code input, but its a challenge so gives me something to do.

Z

---

### Post by zigzagff17 on 2009-01-27
zigzag@zigzag-laptop:~$ sudo apt- get install amsn
[sudo] password for zigzag: 
sudo: apt-: command not found
zigzag@zigzag-laptop:~$ sudo apt-get install amsn
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  amsn-data libsnack2 tcl-tls tcl8.5 tk8.5
Suggested packages:
  docker tclsh libsnack2-doc tclreadline
The following NEW packages will be installed:
  amsn amsn-data libsnack2 tcl-tls tcl8.5 tk8.5
0 upgraded, 6 newly installed, 0 to remove and 222 not upgraded.
Need to get 6580kB of archives.
After this operation, 20.5MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid/universe amsn-data 0.97.2~debian-0ubuntu3 [3225kB]
Get:2 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid/main tcl8.5 8.5.3-1 [1537kB]       
Get:3 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid/main tk8.5 8.5.3-3 [1111kB]        
Get:4 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid/universe tcl-tls 1.5.0.dfsg-9 [70.7kB]
Get:5 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid/universe libsnack2 2.2.10-dfsg1-6 [366kB]
Get:6 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid/universe amsn 0.97.2~debian-0ubuntu3 [271kB]
Fetched 6580kB in 8min48s (12.4kB/s)                                           
Selecting previously deselected package amsn-data.
(Reading database ... 99820 files and directories currently installed.)
Unpacking amsn-data (from .../amsn-data_0.97.2~debian-0ubuntu3_all.deb) ...
Selecting previously deselected package tcl8.5.
Unpacking tcl8.5 (from .../tcl8.5_8.5.3-1_i386.deb) ...
Selecting previously deselected package tk8.5.
Unpacking tk8.5 (from .../tk8.5_8.5.3-3_i386.deb) ...
Selecting previously deselected package tcl-tls.
Unpacking tcl-tls (from .../tcl-tls_1.5.0.dfsg-9_i386.deb) ...
Selecting previously deselected package libsnack2.
Unpacking libsnack2 (from .../libsnack2_2.2.10-dfsg1-6_i386.deb) ...
Selecting previously deselected package amsn.
Unpacking amsn (from .../amsn_0.97.2~debian-0ubuntu3_i386.deb) ...
Processing triggers for man-db ...
Setting up amsn-data (0.97.2~debian-0ubuntu3) ...
Setting up tcl8.5 (8.5.3-1) ...

Setting up tk8.5 (8.5.3-3) ...

Setting up tcl-tls (1.5.0.dfsg-9) ...

Setting up libsnack2 (2.2.10-dfsg1-6) ...
Setting up amsn (0.97.2~debian-0ubuntu3) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
zigzag@zigzag-laptop:~$ 



OK NOW WHAT ... lol

---

### Post by zigzagff17 on 2009-01-27
found it ... applications/internet

---

### Post by talsemgeest on 2009-01-27
> **zigzagff17 said:**
> sudo apt-get install amsn

I am trying this and seems to be doing something good.
I am not into getting all the bleeding parts of stuff ... YET :D
I am totally new to this OS, don't get me wrong its a bit different and more manual code input, but its a challenge so gives me something to do.

Z
Ok, in that case, it is better not to be downloading programs your self. Pretty much everything you could need is contained within add/remove programs. That way it handles everything for you, downloading, installing, updating etc...

---

