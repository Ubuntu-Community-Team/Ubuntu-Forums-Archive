---
title: "[SOLVED] update manually all the time, then errors??"
date: 2008-12-24
forum: New to Ubuntu
---

### Post by broekskw on 2008-12-24
hi everyone, i get this update manually all the time window pop up saying see attached screen shot, then when i do update manually after update takes i get this other error window pop up see attached screen shot
so how would one go about fixing this problem:lolflag:

thanks for any input in advance :popcorn:

---

### Post by bodhi.zazen on 2008-12-24
Did you install something from outside the repositories ?

What version of Ubuntu ?

Try :

```
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by broekskw on 2008-12-24
thanks for your reply bodhi.zazen here are the output from the following commands
 code
sudo apt-get update
[sudo] password for broekskw: 
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg                             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg                      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_CA           
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release.gpg                            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_CA     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_CA       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_CA     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release                          
Get:1 [http://ftp.debian.org](http://ftp.debian.org) etch Release.gpg [386B]                            
Ign [http://ftp.debian.org](http://ftp.debian.org) etch/main Translation-en_CA                          
Get:2 [http://ftp.debian.org](http://ftp.debian.org) etch Release [58.2kB]                              
Ign [http://ftp.debian.org](http://ftp.debian.org) etch Release                                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages                    
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_CA               
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Translation-en_CA                 
Hit [http://ftp.debian.org](http://ftp.debian.org) etch/main Packages                                   
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release                                 
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages                        
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Translation-en_CA             
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Sources                         
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release                                
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Packages                          
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Packages                      
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Sources                           
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Sources                       
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy Release.gpg                             
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy Release.gpg                          
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy/main Translation-en_CA               
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main Translation-en_CA                  
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/restricted Translation-en_CA            
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy Release                              
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/universe Translation-en_CA              
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/multiverse Translation-en_CA            
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates Release.gpg                     
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/main Translation-en_CA          
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy/main Packages                        
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy/main Sources                         
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy/main Packages                        
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/restricted Translation-en_CA    
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/universe Translation-en_CA      
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/multiverse Translation-en_CA    
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-backports Release.gpg                   
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-backports/main Translation-en_CA        
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-backports/restricted Translation-en_CA  
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-backports/universe Translation-en_CA    
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-backports/multiverse Translation-en_CA  
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-proposed Release.gpg                    
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-proposed/restricted Translation-en_CA   
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-proposed/main Translation-en_CA         
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-proposed/multiverse Translation-en_CA   
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-proposed/universe Translation-en_CA     
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy Release                                 
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates Release                         
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-backports Release                       
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-proposed Release                        
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main Packages                           
Err [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty Release.gpg                            
  Could not resolve 'medibuntu.sos-sts.com'
Err [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/free Translation-en_CA                 
  Could not resolve 'medibuntu.sos-sts.com'
Err [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/non-free Translation-en_CA             
  Could not resolve 'medibuntu.sos-sts.com'
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/restricted Packages                     
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/restricted Sources                      
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main Sources                            
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/multiverse Sources                      
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/universe Sources                        
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/universe Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/multiverse Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/main Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/restricted Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/main Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/multiverse Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/universe Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-backports/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-backports/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-backports/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-backports/multiverse Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-backports/main Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-backports/restricted Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-backports/universe Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-backports/multiverse Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-proposed/restricted Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-proposed/main Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-proposed/multiverse Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-proposed/universe Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-proposed/restricted Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-proposed/main Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-proposed/multiverse Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-proposed/universe Sources
Fetched 387B in 35s (11B/s)
Reading package lists... Done
W: GPG error: [http://ftp.debian.org](http://ftp.debian.org) etch Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A70DAF536070D3A1 NO_PUBKEY B5D0C804ADB11277
W: Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/Release.gpg](http://medibuntu.sos-sts.com/repo/dists/feisty/Release.gpg)  Could not resolve 'medibuntu.sos-sts.com'

W: Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/i18n/Translation-en_CA.bz2](http://medibuntu.sos-sts.com/repo/dists/feisty/free/i18n/Translation-en_CA.bz2)  Could not resolve 'medibuntu.sos-sts.com'

W: Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/i18n/Translation-en_CA.bz2](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/i18n/Translation-en_CA.bz2)  Could not resolve 'medibuntu.sos-sts.com'

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems
broekskw@broekskw-desktop:~$ 

 

and 
code
do apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  friendly-recovery startup-tasks system-services ubuntu-minimal upstart
  upstart-compat-sysv upstart-logd
The following NEW packages will be installed:
  busybox linux-headers-2.6.24-23 linux-headers-2.6.24-23-generic
  linux-image-2.6.24-23-generic linux-restricted-modules-2.6.24-23-generic
  linux-ubuntu-modules-2.6.24-23-generic sysvinit sysvinit-utils
The following packages will be upgraded:
  initramfs-tools initscripts linux-generic linux-headers-generic
  linux-image-generic linux-restricted-modules-generic
6 upgraded, 8 newly installed, 7 to remove and 0 not upgraded.
Need to get 52.3MB of archives.
After this operation, 197MB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  sysvinit-utils sysvinit initramfs-tools initscripts
Install these packages without verification [y/N]? n 
E: Some packages could not be authenticated
broekskw@broekskw-desktop:~$ 
code


so what did i do:confused:

---

### Post by bodhi.zazen on 2008-12-24
Well a few comments.

First you are running a "mixed" system in that you are adding repositories. You need to take great care when doing this, especially with the Debian repos. Mixing repos can cause breakage.

Second you are getting that error because you have not imported the GPG key and have answered "no" to install anyways (you can answer yes or import the keys)..

See this wiki page :

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

I also suggest you look into pinning.

[http://jaqque.sbih.org/kplug/apt-pinning.html](http://jaqque.sbih.org/kplug/apt-pinning.html)

The mediabuntu repos are obviously off as well, check the url or disable them.

---

### Post by kansasnoob on 2008-12-24
> **broekskw said:**
> thanks for your reply bodhi.zazen here are the output from the following commands
 code
sudo apt-get update
[sudo] password for broekskw: 
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg                             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg                      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_CA           
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release.gpg                            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_CA     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_CA       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_CA     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release                          
Get:1 [http://ftp.debian.org](http://ftp.debian.org) etch Release.gpg [386B]                            
Ign [http://ftp.debian.org](http://ftp.debian.org) etch/main Translation-en_CA                          
Get:2 [http://ftp.debian.org](http://ftp.debian.org) etch Release [58.2kB]                              
Ign [http://ftp.debian.org](http://ftp.debian.org) etch Release                                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages                    
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_CA               
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Translation-en_CA                 
Hit [http://ftp.debian.org](http://ftp.debian.org) etch/main Packages                                   
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release                                 
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages                        
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Translation-en_CA             
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Sources                         
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release                                
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Packages                          
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Packages                      
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Sources                           
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Sources                       
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy Release.gpg                             
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy Release.gpg                          
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy/main Translation-en_CA               
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main Translation-en_CA                  
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/restricted Translation-en_CA            
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy Release                              
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/universe Translation-en_CA              
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/multiverse Translation-en_CA            
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates Release.gpg                     
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/main Translation-en_CA          
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy/main Packages                        
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy/main Sources                         
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy/main Packages                        
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/restricted Translation-en_CA    
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/universe Translation-en_CA      
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/multiverse Translation-en_CA    
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-backports Release.gpg                   
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-backports/main Translation-en_CA        
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-backports/restricted Translation-en_CA  
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-backports/universe Translation-en_CA    
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-backports/multiverse Translation-en_CA  
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-proposed Release.gpg                    
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-proposed/restricted Translation-en_CA   
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-proposed/main Translation-en_CA         
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-proposed/multiverse Translation-en_CA   
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-proposed/universe Translation-en_CA     
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy Release                                 
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates Release                         
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-backports Release                       
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-proposed Release                        
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main Packages                           
Err [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty Release.gpg                            
  Could not resolve 'medibuntu.sos-sts.com'
Err [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/free Translation-en_CA                 
  Could not resolve 'medibuntu.sos-sts.com'
Err [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/non-free Translation-en_CA             
  Could not resolve 'medibuntu.sos-sts.com'
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/restricted Packages                     
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/restricted Sources                      
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main Sources                            
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/multiverse Sources                      
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/universe Sources                        
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/universe Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/multiverse Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/main Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/restricted Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/main Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/multiverse Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/universe Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-backports/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-backports/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-backports/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-backports/multiverse Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-backports/main Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-backports/restricted Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-backports/universe Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-backports/multiverse Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-proposed/restricted Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-proposed/main Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-proposed/multiverse Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-proposed/universe Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-proposed/restricted Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-proposed/main Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-proposed/multiverse Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-proposed/universe Sources
Fetched 387B in 35s (11B/s)
Reading package lists... Done
W: GPG error: [http://ftp.debian.org](http://ftp.debian.org) etch Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A70DAF536070D3A1 NO_PUBKEY B5D0C804ADB11277
W: Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/Release.gpg](http://medibuntu.sos-sts.com/repo/dists/feisty/Release.gpg)  Could not resolve 'medibuntu.sos-sts.com'

W: Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/i18n/Translation-en_CA.bz2](http://medibuntu.sos-sts.com/repo/dists/feisty/free/i18n/Translation-en_CA.bz2)  Could not resolve 'medibuntu.sos-sts.com'

W: Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/i18n/Translation-en_CA.bz2](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/i18n/Translation-en_CA.bz2)  Could not resolve 'medibuntu.sos-sts.com'

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems
broekskw@broekskw-desktop:~$ 

 

and 
code
do apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  friendly-recovery startup-tasks system-services ubuntu-minimal upstart
  upstart-compat-sysv upstart-logd
The following NEW packages will be installed:
  busybox linux-headers-2.6.24-23 linux-headers-2.6.24-23-generic
  linux-image-2.6.24-23-generic linux-restricted-modules-2.6.24-23-generic
  linux-ubuntu-modules-2.6.24-23-generic sysvinit sysvinit-utils
The following packages will be upgraded:
  initramfs-tools initscripts linux-generic linux-headers-generic
  linux-image-generic linux-restricted-modules-generic
6 upgraded, 8 newly installed, 7 to remove and 0 not upgraded.
Need to get 52.3MB of archives.
After this operation, 197MB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  sysvinit-utils sysvinit initramfs-tools initscripts
Install these packages without verification [y/N]? n 
E: Some packages could not be authenticated
broekskw@broekskw-desktop:~$ 
code


so what did i do:confused:

A few things look odd to me:

The first:
> Get:1 [http://ftp.debian.org](http://ftp.debian.org) etch Release.gpg [386B]                            
Ign [http://ftp.debian.org](http://ftp.debian.org) etch/main Translation-en_CA                          
Get:2 [http://ftp.debian.org](http://ftp.debian.org) etch Release [58.2kB]                              
Ign [http://ftp.debian.org](http://ftp.debian.org) etch Release                                         

The second:
> Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy Release.gpg                          
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy/main Translation-en_CA               

The third:
> Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy/main Packages                        
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy/main Sources                         
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy/main Packages                        

The fourth:
> Err [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty Release.gpg                            
  Could not resolve 'medibuntu.sos-sts.com'
Err [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/free Translation-en_CA                 
  Could not resolve 'medibuntu.sos-sts.com'
Err [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/non-free Translation-en_CA             

Anyway I'd go to System > Administration > Software Sources and click on the Third Party tab. Then "untick" any repos that are NOT Hardy, then update again and see what happens.

You may then want to "update" some of those Repos, like for instance install the Hardy Medibuntu Repo along with the gpg key, etc.

---

### Post by kansasnoob on 2008-12-24
Listen to bodhi.zazen!

He knows a gazillion times more than I!

---

### Post by bodhi.zazen on 2008-12-24
> **kansasnoob said:**
> Listen to bodhi.zazen!

He knows a gazillion times more than I!

LOL, I doubt that. Nice observations.

---

### Post by broekskw on 2008-12-24
so i screwed up really bad then:confused:, not to sure as how i did this, i think it was when i followed a post some time ago about updating my system

will give all a try and keep you all updated

again a million thanks to all:popcorn:

---

### Post by broekskw on 2008-12-24
ok did this 

Anyway I'd go to System > Administration > Software Sources and click on the Third Party tab. Then "untick" any repos that are NOT Hardy, then update again and see what happens.
 and then updated thing looked ok but i think i deleted all my "authentication keys by mistake (just call me a dumass)because at 
sudo apt-get update
 at the end i get this
code 
W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: GPG error: [http://mirrors.cat.pdx.edu](http://mirrors.cat.pdx.edu) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://mirrors.cat.pdx.edu](http://mirrors.cat.pdx.edu) hardy-updates Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://mirrors.cat.pdx.edu](http://mirrors.cat.pdx.edu) hardy-backports Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://mirrors.cat.pdx.edu](http://mirrors.cat.pdx.edu) hardy-security Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://mirrors.cat.pdx.edu](http://mirrors.cat.pdx.edu) hardy-proposed Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: You may want to run apt-get update to correct these problems
code

ran apt-get update with the same errors

also bodhi.zazen looked at the pinning site but not to sure as what and how to get this to work on my system; is this a general guide or is there a step by step in more detail on this

also was told to type "code: then hit enter the past by terminal stuff and then type code at the end to make the terminal in a diff window from my text but must be doing it wrong as all is together

:lolflag:

---

### Post by broekskw on 2008-12-24
most fixed by hitting "restore default" in software source but just one left with no key

 GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

is this one important or just forget this one???:confused:

---

### Post by broekskw on 2008-12-24
ok did lots of reading and searching the web and found out how to correct this, lots to this ubuntu that do not understand looks like have to take baby steps :popcorn: 

hope everyone here has a great xmas and safe new year:lolflag:

---

