---
title: "make install help"
date: 2009-09-15
forum: New to Ubuntu
---

### Post by DavidFourer on 2009-09-15
I'm trying to compile source code for the first time.  It's a little utility that does something for my printer.

First I unzipped the file
```
david@david-laptop:~/Desktop/chipset$ ls
chipset.c  chipset.h  Makefile
```
I went to Synaptic and installed build-essential.

Then
```
david@david-laptop:~/chipset$ ./configure
bash: ./configure: No such file or directory
```
What gives?  I decided to try this:
```
david@david-laptop:~/chipset$ sudo aptitude install build-essential
[sudo] password for david: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
The following packages will be REMOVED:
  liblink-grammar4{u} link-grammar-dictionaries-en{u} 
  linux-headers-2.6.28-11{u} linux-headers-2.6.28-11-generic{u} menu{u} 
0 packages upgraded, 0 newly installed, 5 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 78.3MB will be freed.
Do you want to continue? [Y/n/?] n
Abort.
```
These are old linux headers.  I'm running 2.6.28.15.  Still it made me nervous so I aborted. why does it want to remove files?

Ubuntuguid.org/wiki says I should also run:    
```
* Make sure you have all the necessary development tools
 (i.e. libraries, compilers, headers): 

sudo apt-get install build-essential
sudo apt-get install linux-headers-`uname -r`

        Note: "uname -r" lists the current kernel you are using
```
If I already have the kernel running, why would I apt-get install it?

I just don't want to mess up my system.
Thanks.

---

### Post by sunchiqua on 2009-09-15
```
make
sudo make install

```

---

### Post by wojox on 2009-09-15
```
make -f Makefile
```

It's just trying to purge old header files. Just compare the numbers.

---

### Post by DavidFourer on 2009-09-15
I did run "make".  There were errors, so I think the code is just bad.  
I just wonder why I can't run ./configure.  Is that important?
The rest I think I can forget about.

---

### Post by wojox on 2009-09-15
*   You run configure (you usually have to type ./configure as most people don't have the current directory in their search path). This builds a new Makefile.
    * Type make This builds the program. That is, make would be executed, it would look for the first target in Makefile and do what the instructions said. The expected end result would be to build an executable program.
    * Now, as root, type make install. This again invokes make, make finds the target install in Makefile and files the directions to install the program.

---

