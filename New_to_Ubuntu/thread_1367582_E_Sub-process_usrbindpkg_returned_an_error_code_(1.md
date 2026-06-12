---
title: "E: Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2009-12-29
forum: New to Ubuntu
---

### Post by karlmp on 2009-12-29
```
sudo aptitude update && sudo aptitude dist-upgrade
Get:1 http://dl.google.com stable Release.gpg [189B]                                                
Ign http://dl.google.com stable/main Translation-en_US                                              
Hit http://security.ubuntu.com karmic-security Release.gpg                                          
Ign http://security.ubuntu.com karmic-security/main Translation-en_US                               
Get:2 http://dl.google.com stable Release [2,540B]                                                  
Ign http://security.ubuntu.com karmic-security/restricted Translation-en_US                         
Ign http://security.ubuntu.com karmic-security/universe Translation-en_US                           
Ign http://security.ubuntu.com karmic-security/multiverse Translation-en_US                         
Hit http://security.ubuntu.com karmic-security Release                                              
Get:3 http://dl.google.com stable/main Packages [867B]                                              
Hit http://security.ubuntu.com karmic-security/main Packages                                        
Hit http://security.ubuntu.com karmic-security/restricted Packages                                  
Hit http://security.ubuntu.com karmic-security/main Sources                                         
Hit http://security.ubuntu.com karmic-security/restricted Sources                                   
Hit http://security.ubuntu.com karmic-security/universe Packages                                    
Hit http://security.ubuntu.com karmic-security/universe Sources                                     
Hit http://security.ubuntu.com karmic-security/multiverse Packages                                  
Hit http://security.ubuntu.com karmic-security/multiverse Sources                                   
Hit http://deb.opera.com stable Release.gpg                                                         
Ign http://deb.opera.com stable/non-free Translation-en_US                                          
Hit http://deb.opera.com stable Release                                                             
Ign http://deb.opera.com stable/non-free Packages                                                   
Ign http://deb.opera.com stable/non-free Packages                                                   
Hit http://deb.opera.com stable/non-free Packages                                                   
Hit http://ve.archive.ubuntu.com karmic Release.gpg                                                 
Ign http://ve.archive.ubuntu.com karmic/main Translation-en_US                                      
Ign http://ve.archive.ubuntu.com karmic/restricted Translation-en_US                                
Ign http://ve.archive.ubuntu.com karmic/universe Translation-en_US                                  
Ign http://ve.archive.ubuntu.com karmic/multiverse Translation-en_US                                
Hit http://ve.archive.ubuntu.com karmic-updates Release.gpg                                         
Ign http://ve.archive.ubuntu.com karmic-updates/main Translation-en_US                              
Ign http://ve.archive.ubuntu.com karmic-updates/restricted Translation-en_US                        
Ign http://ve.archive.ubuntu.com karmic-updates/universe Translation-en_US                          
Ign http://ve.archive.ubuntu.com karmic-updates/multiverse Translation-en_US                        
Hit http://ve.archive.ubuntu.com karmic Release                                                     
Hit http://ve.archive.ubuntu.com karmic-updates Release                                             
Hit http://ppa.launchpad.net karmic Release.gpg                                                     
Ign http://ppa.launchpad.net karmic/main Translation-en_US                                          
Hit http://ve.archive.ubuntu.com karmic/main Packages                                               
Hit http://ve.archive.ubuntu.com karmic/restricted Packages                                         
Hit http://ve.archive.ubuntu.com karmic/main Sources                                                
Hit http://ve.archive.ubuntu.com karmic/restricted Sources                                          
Hit http://ve.archive.ubuntu.com karmic/universe Packages                                           
Hit http://ppa.launchpad.net karmic Release.gpg                                                     
Ign http://ppa.launchpad.net karmic/main Translation-en_US                                          
Hit http://ppa.launchpad.net karmic Release.gpg                                                     
Ign http://ppa.launchpad.net karmic/main Translation-en_US                                          
Hit http://ppa.launchpad.net karmic Release.gpg                                                     
Ign http://ppa.launchpad.net karmic/main Translation-en_US                                          
Hit http://ppa.launchpad.net karmic Release.gpg                                                     
Ign http://ppa.launchpad.net karmic/main Translation-en_US                                          
Hit http://ppa.launchpad.net karmic Release                                                         
Hit http://ve.archive.ubuntu.com karmic/universe Sources                                            
Hit http://ve.archive.ubuntu.com karmic/multiverse Packages                                         
Hit http://ve.archive.ubuntu.com karmic/multiverse Sources                                          
Hit http://ve.archive.ubuntu.com karmic-updates/main Packages                                       
Hit http://ve.archive.ubuntu.com karmic-updates/restricted Packages                                 
Hit http://ve.archive.ubuntu.com karmic-updates/main Sources                                        
Hit http://ve.archive.ubuntu.com karmic-updates/restricted Sources                                  
Hit http://ve.archive.ubuntu.com karmic-updates/universe Packages                                   
Hit http://ve.archive.ubuntu.com karmic-updates/universe Sources                                    
Hit http://ve.archive.ubuntu.com karmic-updates/multiverse Packages                                 
Hit http://ppa.launchpad.net karmic Release                                                         
Hit http://ppa.launchpad.net karmic Release                                                         
Hit http://ppa.launchpad.net karmic Release                                                         
Hit http://ppa.launchpad.net karmic Release                                                         
Hit http://ve.archive.ubuntu.com karmic-updates/multiverse Sources                                  
Hit http://ppa.launchpad.net karmic/main Packages                                                   
Hit http://ppa.launchpad.net karmic/main Sources                                                    
Hit http://ppa.launchpad.net karmic/main Packages                                                   
Hit http://ppa.launchpad.net karmic/main Packages                                                   
Hit http://ppa.launchpad.net karmic/main Packages                                                   
Hit http://ppa.launchpad.net karmic/main Packages                                                   
Fetched 3,596B in 10s (343B/s)                                                                      
Reading package lists... Done                                                                       

Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
The following partially installed packages will be configured:
  python-gst0.10 python-rdflib
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Setting up python-gst0.10 (0.10.17-1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing python-gst0.10 (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up python-rdflib (2.4.0-5ubuntu1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing python-rdflib (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 python-gst0.10
 python-rdflib
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done

```  :(

---

### Post by Paqman on 2009-12-30
Try putting this into a terminal:
```
sudo dpkg --configure -a
```

Looks like you've got a couple of packages which aren't configuring properly.

---

### Post by karlmp on 2009-12-30
I tried that and still the same

BTW this is kubuntu

---

### Post by kellemes on 2009-12-30
Couple of links to similar problems and fixes..
[http://ubuntuforums.org/showthread.php?t=1336548]("http://ubuntuforums.org/showthread.php?t=1336548")
[http://www.khattam.info/2009/08/04/solved-subprocess-pre-removal-script-returned-error-exit-status-2-error/]("http://www.khattam.info/2009/08/04/solved-subprocess-pre-removal-script-returned-error-exit-status-2-error/")
[https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/374136]("https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/374136")

---

### Post by Soul-Sing on 2009-12-30
```
gksudo nautilus
```

navigate via nautilus to: /var/lib/dpkg/info
do a search on: python-gst0.10 python-rdflib
(search-option: above-right on your screen.)
remove them.
close nautilus

```
sudo apt-get update
```
event.: sudo apt-get install python-gst0.10
        sudo apt-get install python-rdflib

---

### Post by karlmp on 2009-12-30
thank you kellemes, the first link fixed it

**thank you all**

---

### Post by SkyHookers on 2011-02-05
> **leoquant said:**
> ```
gksudo nautilus
```

navigate via nautilus to: /var/lib/dpkg/info
do a search on: Python-gst0.10 python-rdflib
(search-option: Above-right on your screen.)
remove them.
Close nautilus

```
sudo apt-get update
```
event.: Sudo apt-get install python-gst0.10
        sudo apt-get install python-rdflib

tnank you ssssooooo much! I did have problem with opera and gnome-colors-common

---

### Post by raw937 on 2013-03-05
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/ 

Tried to install R script -

I did this command first 
sudo apt-get install r-base


But, I forgot to do this command first - sudo apt-get update


So, I killed sudo apt-get install r-base

Then this is what I got after I ran this command rawiii@rawiii-K55A:~$ sudo dpkg --configure -a

Setting up man-db (2.6.1-2ubuntu1) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing man-db (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of debhelper:
 debhelper depends on man-db (>= 2.5.1-1); however:
  Package man-db is not configured yet.
dpkg: error processing debhelper (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of dh-translations:
 dh-translations depends on debhelper; however:
  Package debhelper is not configured yet.
dpkg: error processing dh-translations (--configure):
 dependency problems - leaving unconfigured
Setting up r-base-core (2.14.1-1) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing r-base-core (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of r-base:
 r-base depends on r-base-core (>= 2.14.1-1); however:
  Package r-base-core is not configured yet.
dpkg: error processing r-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of r-cran-mass:
 r-cran-mass depends on r-base-core (>= 2.14.0); however:
  Package r-base-core is not configured yet.
dpkg: error processing r-cran-mass (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of r-cran-matrix:
 r-cran-matrix depends on r-base-core (>= 2.14.0); however:
  Package r-base-core is not configured yet.
dpkg: error processing r-cran-matrix (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of r-cran-kernsmooth:
 r-cran-kernsmooth depends on r-base-core (>= 2.14.0); however:
  Package r-base-core is not configured yet.
 r-cran-kernsmooth depends on r-cran-mass; however:
  Package r-cran-mass is not configured yet.
dpkg: error processing r-cran-kernsmooth (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of r-cran-mgcv:
 r-cran-mgcv depends on r-base-core (>= 2.14.0); however:
  Package r-base-core is not configured yet.
 r-cran-mgcv depends on r-cran-matrix; however:
  Package r-cran-matrix is not configured yet.
dpkg: error processing r-cran-mgcv (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of r-cran-foreign:
 r-cran-foreign depends on r-base-core (>= 2.14.0); however:
  Package r-base-core is not configured yet.
dpkg: error processing r-cran-foreign (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of r-cran-codetools:
 r-cran-codetools depends on r-base-core (>= 2.12.1); however:
  Package r-base-core is not configured yet.
dpkg: error processing r-cran-codetools (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of r-cran-class:
 r-cran-class depends on r-base-core (>= 2.12.0); however:
  Package r-base-core is not configured yet.
 r-cran-class depends on r-cran-mass; however:
  Package r-cran-mass is not configured yet.
dpkg: error processing r-cran-class (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of r-cran-nlme:
 r-cran-nlme depends on r-base-core (>= 2.13.1); however:
  Package r-base-core is not configured yet.
dpkg: error processing r-cran-nlme (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of cdbs:
 cdbs depends on dh-translations; however:
  Package dh-translations is not configured yet.
dpkg: error processing cdbs (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of r-cran-cluster:
 r-cran-cluster depends on r-base-core (>> 2.13.2); however:
  Package r-base-core is not configured yet.
dpkg: error processing r-cran-cluster (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of r-cran-survival:
 r-cran-survival depends on r-base-core (>= 2.13.2); however:
  Package r-base-core is not configured yet.
dpkg: error processing r-cran-survival (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of r-cran-boot:
 r-cran-boot depends on r-base-core (>= 2.14.0); however:
  Package r-base-core is not configured yet.
dpkg: error processing r-cran-boot (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of r-cran-spatial:
 r-cran-spatial depends on r-base-core (>= 2.14.0); however:
  Package r-base-core is not configured yet.
dpkg: error processing r-cran-spatial (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of r-cran-rpart:
 r-cran-rpart depends on r-base-core (>= 2.13.0); however:
  Package r-base-core is not configured yet.
 r-cran-rpart depends on r-cran-survival; however:
  Package r-cran-survival is not configured yet.
dpkg: error processing r-cran-rpart (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of r-base-dev:
 r-base-dev depends on r-base-core (>= 2.14.1-1); however:
  Package r-base-core is not configured yet.
 r-base-dev depends on cdbs; however:
  Package cdbs is not configured yet.
dpkg: error processing r-base-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of r-base-html:
 r-base-html depends on r-base-core; however:
  Package r-base-core is not configured yet.
dpkg: error processing r-base-html (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of r-recommended:
 r-recommended depends on r-base-core (>= 2.14.1-1); however:
  Package r-base-core is not configured yet.
 r-recommended depends on r-cran-boot (>= 1.2.19); however:
  Package r-cran-boot is not configured yet.
 r-recommended depends on r-cran-cluster (>= 1.9.6-2); however:
  Package r-cran-cluster is not configured yet.
 r-recommended depends on r-cran-foreign (>= 0.7-2); however:
  Package r-cran-foreign is not configured yet.
 r-recommended depends on r-cran-kernsmooth (>= 2.2.14); however:
  Package r-cran-kernsmooth is not configured yet.
 r-recommended depends on r-cran-mgcv (>= 1.1.5); however:
  Package r-cran-mgcv is not configured yet.
 r-recommended depends on r-cran-nlme (>= 3.1.52); however:
  Package r-cran-nlme is not configured yet.
 r-recommended depends on r-cran-rpart (>= 3.1.20); however:
  Package r-cran-rpart is not configured yet.
 r-recommended depends on r-cran-survival (>= 2.13.2-1); however:
  Package r-cran-survival is not configured yet.
 r-recommended depends on r-cran-mass; however:
  Package r-cran-mass is not configured yet.
 r-recommended depends on r-cran-class; however:
  Package r-cran-class is not configured yet.
 r-recommended depends on r-cran-spatial; however:
  Package r-cran-spatial is not configured yet.
 r-recommended depends on r-cran-codetools; however:
  Package r-cran-codetools is not configured yet.
 r-recommended depends on r-cran-matrix; however:
  Package r-cran-matrix is not configured yet.
dpkg: error processing r-recommended (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of r-cran-lattice:
 r-cran-lattice depends on r-base-core (>= 2.14.0); however:
  Package r-base-core is not configured yet.
dpkg: error processing r-cran-lattice (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of r-cran-nnet:
 r-cran-nnet depends on r-base-core (>> 2.13.2-1); however:
  Package r-base-core is not configured yet.
dpkg: error processing r-cran-nnet (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 man-db
 debhelper
 dh-translations
 r-base-core
 r-base
 r-cran-mass
 r-cran-matrix
 r-cran-kernsmooth
 r-cran-mgcv
 r-cran-foreign
 r-cran-codetools
 r-cran-class
 r-cran-nlme
 cdbs
 r-cran-cluster
 r-cran-survival
 r-cran-boot
 r-cran-spatial
 r-cran-rpart
 r-base-dev
 r-base-html
 r-recommended
 r-cran-lattice
 r-cran-nnet

tried  sudo apt-get update
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/

I could use the gksudo nautilus but I don't know which files to delete?

Cheers
Rick

---

### Post by wildmanne39 on 2013-03-05
Old thread closed! please start a new thread if you need to you can link to this thread.
Thanks

---

