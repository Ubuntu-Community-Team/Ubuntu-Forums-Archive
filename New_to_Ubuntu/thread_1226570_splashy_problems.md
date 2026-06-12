---
title: "splashy problems"
date: 2009-07-29
forum: New to Ubuntu
---

### Post by stalkier on 2009-07-29
I am trying to install everything to use splashy to create custom usplash themes. I am using this page for instructions: [http://maketecheasier.com/create-install-your-own-usplash-theme-in-ubuntu/2009/01/25](http://maketecheasier.com/create-install-your-own-usplash-theme-in-ubuntu/2009/01/25)

Here is the error I am getting
```
john@john-desktop:~$ gksu gedit /etc/apt/sources.list
john@john-desktop:~$ sudo apt-get update
Hit http://us.archive.ubuntu.com jaunty Release.gpg
Ign http://us.archive.ubuntu.com jaunty/main Translation-en_US                 
Ign http://us.archive.ubuntu.com jaunty/restricted Translation-en_US           
Ign http://us.archive.ubuntu.com jaunty/universe Translation-en_US             
Ign http://us.archive.ubuntu.com jaunty/multiverse Translation-en_US           
Hit http://us.archive.ubuntu.com jaunty-updates Release.gpg                    
Ign http://us.archive.ubuntu.com jaunty-updates/main Translation-en_US         
Ign http://us.archive.ubuntu.com jaunty-updates/restricted Translation-en_US   
Ign http://us.archive.ubuntu.com jaunty-updates/universe Translation-en_US     
Ign http://us.archive.ubuntu.com jaunty-updates/multiverse Translation-en_US   
Get:1 http://us.archive.ubuntu.com jaunty-proposed Release.gpg [189B]          
Ign http://us.archive.ubuntu.com jaunty-proposed/restricted Translation-en_US  
Ign http://us.archive.ubuntu.com jaunty-proposed/main Translation-en_US        
Ign http://us.archive.ubuntu.com jaunty-proposed/multiverse Translation-en_US  
Ign http://us.archive.ubuntu.com jaunty-proposed/universe Translation-en_US    
Hit http://us.archive.ubuntu.com jaunty Release                                
Hit http://us.archive.ubuntu.com jaunty-updates Release                        
Get:2 http://us.archive.ubuntu.com jaunty-proposed Release [49.6kB]            
Hit http://us.archive.ubuntu.com jaunty/main Packages                          
Hit http://us.archive.ubuntu.com jaunty/restricted Packages                    
Hit http://us.archive.ubuntu.com jaunty/main Sources                           
Hit http://us.archive.ubuntu.com jaunty/restricted Sources                     
Hit http://us.archive.ubuntu.com jaunty/universe Packages                      
Hit http://us.archive.ubuntu.com jaunty/universe Sources                       
Hit http://us.archive.ubuntu.com jaunty/multiverse Packages                    
Hit http://us.archive.ubuntu.com jaunty/multiverse Sources                     
Hit http://us.archive.ubuntu.com jaunty-updates/main Packages                  
Hit http://us.archive.ubuntu.com jaunty-updates/restricted Packages            
Hit http://us.archive.ubuntu.com jaunty-updates/main Sources                   
Hit http://us.archive.ubuntu.com jaunty-updates/restricted Sources             
Hit http://us.archive.ubuntu.com jaunty-updates/universe Packages              
Hit http://us.archive.ubuntu.com jaunty-updates/universe Sources               
Hit http://us.archive.ubuntu.com jaunty-updates/multiverse Packages            
Hit http://us.archive.ubuntu.com jaunty-updates/multiverse Sources             
Get:3 http://us.archive.ubuntu.com jaunty-proposed/restricted Packages [966B]  
Get:4 http://us.archive.ubuntu.com jaunty-proposed/main Packages [19.9kB]      
Get:5 http://us.archive.ubuntu.com jaunty-proposed/multiverse Packages [5008B] 
Get:6 http://us.archive.ubuntu.com jaunty-proposed/universe Packages [7679B]   
Get:7 http://ftp.us.debian.org unstable Release.gpg [835B]                     
Ign http://ftp.us.debian.org unstable/main Translation-en_US                   
Get:8 http://ftp.us.debian.org unstable Release [99.8kB]                       
Hit http://security.ubuntu.com jaunty-security Release.gpg                     
Ign http://security.ubuntu.com jaunty-security/main Translation-en_US     
Hit http://packages.medibuntu.org jaunty Release.gpg                      
Ign http://packages.medibuntu.org jaunty/free Translation-en_US           
Ign http://security.ubuntu.com jaunty-security/restricted Translation-en_US
Ign http://security.ubuntu.com jaunty-security/universe Translation-en_US 
Ign http://security.ubuntu.com jaunty-security/multiverse Translation-en_US
Hit http://security.ubuntu.com jaunty-security Release                    
Ign http://packages.medibuntu.org jaunty/non-free Translation-en_US        
Hit http://packages.medibuntu.org jaunty Release                            
Hit http://security.ubuntu.com jaunty-security/main Packages                
Hit http://packages.medibuntu.org jaunty/free Packages
Ign http://ftp.us.debian.org unstable Release                         
Hit http://security.ubuntu.com jaunty-security/restricted Packages    
Hit http://security.ubuntu.com jaunty-security/main Sources          
Hit http://security.ubuntu.com jaunty-security/restricted Sources    
Hit http://security.ubuntu.com jaunty-security/universe Packages     
Hit http://packages.medibuntu.org jaunty/non-free Packages           
Get:9 http://ftp.us.debian.org unstable/main Packages [6053kB]       
Hit http://security.ubuntu.com jaunty-security/universe Sources
Hit http://security.ubuntu.com jaunty-security/multiverse Packages
Hit http://security.ubuntu.com jaunty-security/multiverse Sources
Fetched 6237kB in 25s (246kB/s)                                                
Reading package lists... Done
W: GPG error: http://ftp.us.debian.org unstable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 9AA38DCD55BE302B
W: You may want to run apt-get update to correct these problems
john@john-desktop:~$ sudo apt-get install splashy splashy-themes
Reading package lists... Done
Building dependency tree       
Reading state information... Done
splashy-themes is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  splashy: Depends: libdirectfb-1.2-0 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
john@john-desktop:~$ apt-get -f install
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
john@john-desktop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libdirectfb-1.2-0 splashy
Suggested packages:
  console-common
The following NEW packages will be installed:
  libdirectfb-1.2-0 splashy
0 upgraded, 2 newly installed, 0 to remove and 790 not upgraded.
1 not fully installed or removed.
Need to get 2351kB of archives.
After this operation, 4186kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  libdirectfb-1.2-0 splashy
Install these packages without verification [y/N]? y
Get:1 http://ftp.us.debian.org unstable/main libdirectfb-1.2-0 1.2.7-2 [1140kB]
Get:2 http://ftp.us.debian.org unstable/main splashy 0.3.13-5 [1210kB]
Fetched 2351kB in 9s (244kB/s)                                                 
Selecting previously deselected package libdirectfb-1.2-0.
(Reading database ... 127903 files and directories currently installed.)
Unpacking libdirectfb-1.2-0 (from .../libdirectfb-1.2-0_1.2.7-2_i386.deb) ...
Unpacking splashy (from .../splashy_0.3.13-5_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/splashy_0.3.13-5_i386.deb (--unpack):
 trying to overwrite `/etc/lsb-base-logging.sh', which is also in package lsb-base
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/splashy_0.3.13-5_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
john@john-desktop:~$ sudo apt-get install libglade2-dev libsplashy1-dev build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  build-essential: Depends: g++ (>= 4:4.3.1) but it is not going to be installed
                   Depends: dpkg-dev (>= 1.13.5) but it is not going to be installed
  libglade2-dev: Depends: libgtk2.0-dev (>= 2.0.6) but it is not going to be installed
                 Depends: libxml2-dev but it is not going to be installed
  libsplashy1-dev: Depends: libsplashy1 (= 0.3.13-5) but 0.3.13-3ubuntu1 is to be installed
                   Depends: libglib2.0-dev but it is not going to be installed
                   Depends: libdirectfb-dev but it is not going to be installed
  splashy-themes: Depends: splashy (>= 0.3.12-1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
john@john-desktop:~$ 
```

Does anyone know how to fix this? Or perhaps an easier way to install everything for Splashy?? Thanks in advance.

---

### Post by philcamlin on 2009-07-29
try running with sudo liike 

sudo apt-get update 

and 

sudo apt-get -f install

---

### Post by stalkier on 2009-07-29
> **philcamlin said:**
> try running with sudo liike 

sudo apt-get update 

and 

sudo apt-get -f install

I still get this

```
john@john-desktop:~$ sudo apt-get update
Get:1 http://ftp.us.debian.org unstable Release.gpg [835B]
Ign http://ftp.us.debian.org unstable/main Translation-en_US                   
Get:2 http://ftp.us.debian.org unstable Release [94.4kB]                       
Hit http://us.archive.ubuntu.com jaunty Release.gpg                            
Ign http://us.archive.ubuntu.com jaunty/main Translation-en_US                 
Ign http://us.archive.ubuntu.com jaunty/restricted Translation-en_US           
Ign http://us.archive.ubuntu.com jaunty/universe Translation-en_US             
Ign http://us.archive.ubuntu.com jaunty/multiverse Translation-en_US           
Hit http://us.archive.ubuntu.com jaunty-updates Release.gpg                    
Ign http://us.archive.ubuntu.com jaunty-updates/main Translation-en_US         
Ign http://us.archive.ubuntu.com jaunty-updates/restricted Translation-en_US   
Ign http://us.archive.ubuntu.com jaunty-updates/universe Translation-en_US     
Ign http://us.archive.ubuntu.com jaunty-updates/multiverse Translation-en_US   
Hit http://us.archive.ubuntu.com jaunty-proposed Release.gpg                   
Ign http://us.archive.ubuntu.com jaunty-proposed/restricted Translation-en_US  
Ign http://us.archive.ubuntu.com jaunty-proposed/main Translation-en_US        
Ign http://us.archive.ubuntu.com jaunty-proposed/multiverse Translation-en_US  
Ign http://us.archive.ubuntu.com jaunty-proposed/universe Translation-en_US    
Hit http://us.archive.ubuntu.com jaunty Release                                
Hit http://us.archive.ubuntu.com jaunty-updates Release                        
Ign http://ftp.us.debian.org unstable Release                                  
Hit http://us.archive.ubuntu.com jaunty-proposed Release                       
Get:3 http://ftp.us.debian.org unstable/main Packages [6059kB]                 
Hit http://us.archive.ubuntu.com jaunty/main Packages                          
Hit http://us.archive.ubuntu.com jaunty/restricted Packages                    
Hit http://us.archive.ubuntu.com jaunty/main Sources                           
Hit http://us.archive.ubuntu.com jaunty/restricted Sources                     
Hit http://us.archive.ubuntu.com jaunty/universe Packages                      
Hit http://us.archive.ubuntu.com jaunty/universe Sources                       
Hit http://us.archive.ubuntu.com jaunty/multiverse Packages                    
Hit http://us.archive.ubuntu.com jaunty/multiverse Sources                     
Hit http://us.archive.ubuntu.com jaunty-updates/main Packages                  
Hit http://us.archive.ubuntu.com jaunty-updates/restricted Packages            
Hit http://us.archive.ubuntu.com jaunty-updates/main Sources                   
Hit http://us.archive.ubuntu.com jaunty-updates/restricted Sources             
Hit http://us.archive.ubuntu.com jaunty-updates/universe Packages              
Hit http://us.archive.ubuntu.com jaunty-updates/universe Sources               
Hit http://us.archive.ubuntu.com jaunty-updates/multiverse Packages            
Hit http://us.archive.ubuntu.com jaunty-updates/multiverse Sources             
Hit http://us.archive.ubuntu.com jaunty-proposed/restricted Packages           
Hit http://us.archive.ubuntu.com jaunty-proposed/main Packages                 
Hit http://us.archive.ubuntu.com jaunty-proposed/multiverse Packages           
Hit http://us.archive.ubuntu.com jaunty-proposed/universe Packages             
Hit http://security.ubuntu.com jaunty-security Release.gpg                     
Ign http://security.ubuntu.com jaunty-security/main Translation-en_US          
Hit http://packages.medibuntu.org jaunty Release.gpg                           
Ign http://packages.medibuntu.org jaunty/free Translation-en_US                
Ign http://security.ubuntu.com jaunty-security/restricted Translation-en_US    
Ign http://security.ubuntu.com jaunty-security/universe Translation-en_US      
Ign http://security.ubuntu.com jaunty-security/multiverse Translation-en_US    
Hit http://security.ubuntu.com jaunty-security Release                         
Ign http://packages.medibuntu.org jaunty/non-free Translation-en_US            
Hit http://packages.medibuntu.org jaunty Release         
Hit http://security.ubuntu.com jaunty-security/main Packages                  
Hit http://packages.medibuntu.org jaunty/free Packages   
Hit http://security.ubuntu.com jaunty-security/restricted Packages
Hit http://security.ubuntu.com jaunty-security/main Sources                    
Hit http://security.ubuntu.com jaunty-security/restricted Sources              
Hit http://security.ubuntu.com jaunty-security/universe Packages               
Hit http://packages.medibuntu.org jaunty/non-free Packages                     
Hit http://security.ubuntu.com jaunty-security/universe Sources                
Hit http://security.ubuntu.com jaunty-security/multiverse Packages             
Hit http://security.ubuntu.com jaunty-security/multiverse Sources              
Fetched 6155kB in 28s (217kB/s)                                                
Reading package lists... Done
W: GPG error: http://ftp.us.debian.org unstable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 9AA38DCD55BE302B
W: You may want to run apt-get update to correct these problems
john@john-desktop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  splashy
Suggested packages:
  console-common
The following NEW packages will be installed:
  splashy
0 upgraded, 1 newly installed, 0 to remove and 800 not upgraded.
2 not fully installed or removed.
Need to get 0B/1210kB of archives.
After this operation, 1843kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  splashy
Install these packages without verification [y/N]? y
(Reading database ... 127967 files and directories currently installed.)
Unpacking splashy (from .../splashy_0.3.13-5_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/splashy_0.3.13-5_i386.deb (--unpack):
 trying to overwrite `/etc/lsb-base-logging.sh', which is also in package lsb-base
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/splashy_0.3.13-5_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
john@john-desktop:~$ 

```

Does anyone know how I can uninstall the things I do not need. (things for splashy etc) and then reinstall usplash dep. etc

---

### Post by pgar23 on 2009-10-18
I am following the same Tutorial from maketech.com and I am also receiving the error;

```
dpkg: error processing /var/cache/apt/archives/splashy_0.3.13-5_i386.deb (--unpack):
 trying to overwrite `/etc/lsb-base-logging.sh', which is also in package lsb-base
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/splashy_0.3.13-5_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

What is the meaning of this error and is there a workaround or solution to this?

---

