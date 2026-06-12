---
title: "Error with package installations"
date: 2009-01-07
forum: New to Ubuntu
---

### Post by Terpsichore on 2009-01-07
I'm a new Ubuntu 8.10 user who has just transferred over from windows, and I tried to install a set of updates which caused my computer to crash on me. 
Later, when I tried to install a software package using Synaptic I encountered an error similar to the one below. Upon attempting to correct this error by reinstalling/removing/completely removing libfltk1.1, I kept getting the below error message.

Selecting previously deselected package libfltk1.1.
(Reading database ... dpkg: error processing /var/cache/apt/archives/libfltk1.1_1.1.9-4_i386.deb (--unpack):
 files list file for package `libt1-5' is missing final newline
Errors were encountered while processing:
 /var/cache/apt/archives/libfltk1.1_1.1.9-4_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

Can anybody possibly help me out on fixing this problem?
Many thanks.

---

### Post by Michael.Godawski on 2009-01-07
hi,

what happens if you run these commands in terminal

```
sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a
```

please post the output.

---

### Post by Terpsichore on 2009-01-07
Results of those commands are:

sudo apt-get update
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid Release.gpg
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/main Translation-en_GB               
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/restricted Translation-en_GB         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/universe Translation-en_GB           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/multiverse Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates Release.gpg
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/main Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/restricted Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/universe Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/multiverse Translation-en_GB
Get: 1 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg [189B]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid Release                            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Translation-en_GB      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Translation-en_GB  
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release.gpg                       
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Translation-en_GB            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates Release                      
Get: 2 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release [44.0kB]           
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Translation-en_GB          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/main Packages                        
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release
Get: 3 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Packages [1785B]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/restricted Packages             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/main Packages                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/restricted Packages          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/universe Packages            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/multiverse Packages          
Get: 4 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Packages [46.1kB]     
Get: 5 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Packages [1330B]
Get: 6 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Packages [17.9kB]
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Packages               
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Packages
Get: 7 [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Sources [3402B]             
Get: 8 [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Sources [8066B]        
Fetched 123kB in 1s (64.4kB/s)
Reading package lists... Done

sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 206 not upgraded.
1 not fully installed or removed.
Need to get 0B/460kB of archives.
After this operation, 0B of additional disk space will be used.
(Reading database ... dpkg: error processing /var/cache/apt/archives/libfltk1.1_1.1.9-4_i386.deb (--unpack):
 files list file for package `libt1-5' is missing final newline
Errors were encountered while processing:
 /var/cache/apt/archives/libfltk1.1_1.1.9-4_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

sudo dpkg --configure -a
dpkg: error processing libfltk1.1 (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
Errors were encountered while processing:
 libfltk1.1
katherine@ubuntu:~$

---

### Post by Michael.Godawski on 2009-01-07
hm
and what happens if you try to purge the package and reinstall it again.



```
sudo apt-get purge libfltk1.1
sudo apt-get install libfltk1.1
```

---

### Post by Terpsichore on 2009-01-07
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  libfltk1.1*
0 upgraded, 0 newly installed, 1 to remove and 206 not upgraded.
1 not fully installed or removed.
After this operation, 1122kB disk space will be freed.
Do you want to continue [Y/n]? Y
dpkg: error processing libfltk1.1 (--purge):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 libfltk1.1
E: Sub-process /usr/bin/dpkg returned an error code (1)

And the reinstall result remained the same as before :\

---

### Post by Elfy on 2009-01-07
could you run this and post the result please 

```
sudo dpkg -C
```

---

### Post by Terpsichore on 2009-01-07
katherine@ubuntu:~$ sudo dpkg -C
The following packages are in a mess due to serious problems during
installation. They must be reinstalled for them (and any packages
that depend on them) to function properly:
 libfltk1.1           Fast Light Toolkit - shared libraries

(p.s. I love your sig Forestpixie)

---

### Post by Elfy on 2009-01-07
OK - can yourun this from a terminal and post the output please

```
sudo dpkg -s libfltk1.1
```

and thanks :)

---

### Post by JoshuaRL on 2009-01-07
Another option is to go to System->Administration->Synaptic Package Manager.  Then go to the filters, and select the broken packages filter.  It should show libfltk1.1 there, so let it fix that package for you.  It may take a while, but Synaptic is really good at fixing stuff.  It's saved me a couple of times when dpkg and APT had issues.

---

