---
title: "Installing kMyMoney"
date: 2008-12-28
forum: New to Ubuntu
---

### Post by mrcactu5 on 2008-12-28
So I went to sourceforge ( kmymoney2.sourceforge.net ) and downloaded the files for kMyMoney.  When I tried to compile on Kubuntu 8.10 I couldn't get past configure.   Perhaps, there is a more direct way using **install**?  I hope someone here knows the right incantation.
- John

```
./configure
```
then the command line spits out
```
checking build system type... i686-pc-linux-gnu         
checking host system type... i686-pc-linux-gnu          
checking target system type... i686-pc-linux-gnu        
checking for a BSD-compatible install... /usr/bin/install -c
checking for -p flag to install... yes                      
checking whether build environment is sane... yes           
/bin/bash: /home/john/Program: No such file or directory    
configure: WARNING: `missing' script is too old or missing  
checking for a thread-safe mkdir -p... /bin/mkdir -p        
checking for gawk... no                                     
checking for mawk... mawk                                   
checking whether make sets $(MAKE)... yes                   
checking for kde-config... /usr/bin/kde-config              
checking where to install... /usr (as returned by kde-config)
checking for style of include used by make... GNU            
checking for gcc... gcc                                      
checking for C compiler default output file name... a.out    
checking whether the C compiler works... yes                 
checking whether we are cross compiling... no                
checking for suffix of executables...                        
checking for suffix of object files... o                     
checking whether we are using the GNU C compiler... yes      
checking whether gcc accepts -g... yes                       
checking for gcc option to accept ISO C89... none needed     
checking dependency style of gcc... gcc3                     
checking how to run the C preprocessor... gcc -E             
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
checking whether gcc is blacklisted... no
checking whether g++ supports -Wmissing-format-attribute... no
checking whether gcc supports -Wmissing-format-attribute... yes
checking whether g++ supports -Wundef... no
checking whether g++ supports -Wno-long-long... no
checking whether g++ supports -Wno-non-virtual-dtor... no
checking how to run the C++ preprocessor... /lib/cpp
configure: error: C++ preprocessor "/lib/cpp" fails sanity check
See `config.log' for more details.

```

---

### Post by Pollox on 2008-12-28
It looks like the program you're trying to install is in the ubuntu repository, so you can just get it through your package manager (it looks like kubuntu uses a program called "Adept" for that), or just do "sudo apt-get install kmymoney2" in terminal.

---

### Post by moonoo on 2008-12-28
If you really want to build the application from source (which is what you are doing) then you need the gcc which is in the repositories 
e.g. 

sudo apt-get install gcc

otherwise do like Pollox suggests.:)

---

### Post by Michael.Godawski on 2008-12-28
hi,

pollox is right 
kmymoney2 is indeed in the repositories. You can install the version .9.2 from Synaptic.

Try to check add/remove and Synaptic if the package is available before attempting to compile the source.

---

### Post by mrcactu5 on 2008-12-29
Here is my session 
```
sudo apt-get install kmymoney2
[sudo] password for john:
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package kmymoney2
```

---

### Post by mrcactu5 on 2008-12-29
nm.  I went to adept, clicked "fetch package lists".  It downloaded the names of the packages *then* I was able to get it without building.

---

### Post by Midahed on 2008-12-29
I think it's well worth getting to grips with building KMyMoney from source.  The cutting-edge version (CVS-HEAD) is advancing very quickly and is way ahead of what's in the repositories.  

If you really don't want to build from source, there's a guy who creates a deb package from CVS on a regular basis - I think his name is Clay.  You can find details in the KMM developer and user mailing lists, links to which can be found on the KMyMoney website:-

 [http://kmymoney2.sourceforge.net/index-home.html](http://kmymoney2.sourceforge.net/index-home.html)

Mike

---

