---
title: "Errors were encountered while processing:  initramfs-tools  desktop-base"
date: 2011-06-23
forum: New to Ubuntu
---

### Post by fremantle on 2011-06-23
i keep getting this error when i do and upgrade or installation
> Errors were encountered while processing:
 initramfs-tools
 desktop-base

any ideas?

for example after installing midori

> Setting up libwebkitgtk-1.0-0 (1.3.13-0ubuntu2) ...
Setting up libxss1 (1:1.2.1-1) ...
Setting up libjs-mootools (1.2.5~debian1-2) ...
Setting up midori (0.3.2-0.1ubuntu1) ...
update-alternatives: using /usr/bin/midori to provide /usr/bin/x-www-browser (x-www-browser) in auto mode.
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 initramfs-tools
 desktop-base
E: Sub-process /usr/bin/dpkg returned an error code (1)


---

### Post by Rubi1200 on 2011-06-25
Try running these commands in the terminal:

```
sudo apt-get clean

sudo apt-get install -f

sudo dpkg --configure -a

sudo apt-get update
```

Run them one at a time and if you get errors reported post the exact message here so we can try and figure out what is going on.

Thanks.

---

### Post by wizzsm on 2011-10-13
Same error:

followed the steps - same results - running v Ubuntu 11.04

steve@polyjuice:~$ sudo apt-get clean
steve@polyjuice:~$ 
steve@polyjuice:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up initramfs-tools (0.98.8ubuntu3.1) ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.38-11-generic
E: /usr/share/initramfs-tools/hooks/udev failed with return 1.
update-initramfs: failed for /boot/initrd.img-2.6.38-11-generic
dpkg: error processing initramfs-tools (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 initramfs-tools
E: Sub-process /usr/bin/dpkg returned an error code (1)
steve@polyjuice:~$ 
steve@polyjuice:~$ sudo dpkg --configure -a
Setting up initramfs-tools (0.98.8ubuntu3.1) ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.38-11-generic
E: /usr/share/initramfs-tools/hooks/udev failed with return 1.
update-initramfs: failed for /boot/initrd.img-2.6.38-11-generic
dpkg: error processing initramfs-tools (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 initramfs-tools
steve@polyjuice:~$ 
steve@polyjuice:~$ sudo apt-get update
Ign [http://oss.oracle.com](http://oss.oracle.com) unstable InRelease
Get:1 [http://oss.oracle.com](http://oss.oracle.com) unstable Release.gpg [189 B]                                                                           
Hit [http://oss.oracle.com](http://oss.oracle.com) unstable Release                                                                                         
Ign [http://oss.oracle.com](http://oss.oracle.com) unstable Release                                                                                         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security InRelease                                                                            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease                                                                                       
Ign [http://oss.oracle.com](http://oss.oracle.com) unstable/main i386 Packages/DiffIndex                                                                    
Ign [http://deb.opera.com](http://deb.opera.com) stable InRelease                                                                                          
Ign [http://oss.oracle.com](http://oss.oracle.com) unstable/non-free i386 Packages/DiffIndex                                                                
Ign [http://oss.oracle.com](http://oss.oracle.com) unstable/main TranslationIndex                                                                           
Ign [http://oss.oracle.com](http://oss.oracle.com) unstable/non-free TranslationIndex                                                                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release.gpg                                                                          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg                                                                                     
Hit [http://oss.oracle.com](http://oss.oracle.com) unstable/main i386 Packages                                                                              
Hit [http://oss.oracle.com](http://oss.oracle.com) unstable/non-free i386 Packages                                                                          
Hit [http://deb.opera.com](http://deb.opera.com) stable Release.gpg                                                                                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release                                                                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release                                                                                         
Hit [http://deb.opera.com](http://deb.opera.com) stable Release                                                                                            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Sources                                                                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Sources                                                                                    
Ign [http://oss.oracle.com](http://oss.oracle.com) unstable/main Translation-en_US                                                                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Sources                                                                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Sources                                                                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Sources                                                                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main i386 Packages                                                                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted i386 Packages                                                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main i386 Packages                                                                              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main TranslationIndex                                                                           
Ign [http://oss.oracle.com](http://oss.oracle.com) unstable/main Translation-en                                                                             
Ign [http://oss.oracle.com](http://oss.oracle.com) unstable/non-free Translation-en_US                                                                      
Ign [http://oss.oracle.com](http://oss.oracle.com) unstable/non-free Translation-en                                                                         
Hit [http://deb.opera.com](http://deb.opera.com) stable/non-free i386 Packages                                                                             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe i386 Packages                                                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse i386 Packages                                                             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main TranslationIndex                                                                
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse TranslationIndex                                                          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted TranslationIndex                                                          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe TranslationIndex                                                            
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free TranslationIndex                                                                          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en_US                                                                          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en                                                                             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en_US                                                               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en                                                                  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en_US                                                         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en                                                            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en_US                                                         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en                                                            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en_US                                                           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en                                                              
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Translation-en_US                                                                         
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Translation-en                                                                            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty InRelease                                                                
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates InRelease                                                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty Release.gpg                                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates Release.gpg                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty Release                                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates Release                                                                             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Sources                                                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Sources                                                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Sources                                                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Sources                                                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main i386 Packages                                                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted i386 Packages                                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe i386 Packages                                                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse i386 Packages                                                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main TranslationIndex                                                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse TranslationIndex                                              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted TranslationIndex                                              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe TranslationIndex                                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Sources                                                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Sources                                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Sources                                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Sources                                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main i386 Packages                                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted i386 Packages       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe i386 Packages         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse i386 Packages       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main TranslationIndex          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse TranslationIndex                          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted TranslationIndex                          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe TranslationIndex      
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty InRelease                                                                                       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release.gpg                                                                                     
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release                                                                                         
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Sources                                                                                    
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main i386 Packages                                                                              
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main TranslationIndex                                                                           
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en_US                                                                          
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en                                                                             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Translation-en_US                                                                      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Translation-en                                                                         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Translation-en_US                                                                
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Translation-en                                                                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Translation-en_US                                                                
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Translation-en                                                                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Translation-en_US                                                                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Translation-en                                                                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Translation-en_US                                         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Translation-en            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Translation-en
Ign [http://archive.canonical.com](http://archive.canonical.com) natty InRelease        
Hit [http://archive.canonical.com](http://archive.canonical.com) natty Release.gpg
Hit [http://archive.canonical.com](http://archive.canonical.com) natty Release
Hit [http://archive.canonical.com](http://archive.canonical.com) natty/partner i386 Packages
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner TranslationIndex
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en_US
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en
Fetched 189 B in 1min 36s (2 B/s)
Reading package lists... Done
W: GPG error: [http://oss.oracle.com](http://oss.oracle.com) unstable Release: The following signatures were invalid: KEYEXPIRED 1315142507 KEYEXPIRED 1315142507 KEYEXPIRED 1315142507
steve@polyjuice:~$ 
steve@polyjuice:~$ sudo apt-get clean
steve@polyjuice:~$ 
steve@polyjuice:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up initramfs-tools (0.98.8ubuntu3.1) ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.38-11-generic
E: /usr/share/initramfs-tools/hooks/udev failed with return 1.
update-initramfs: failed for /boot/initrd.img-2.6.38-11-generic
dpkg: error processing initramfs-tools (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 initramfs-tools
E: Sub-process /usr/bin/dpkg returned an error code (1)
steve@polyjuice:~$ 
steve@polyjuice:~$ sudo apt-get install -a
E: Command line option 'a' [from -a] is not known.
steve@polyjuice:~$ sudo dpkg --configure -a
Setting up initramfs-tools (0.98.8ubuntu3.1) ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.38-11-generic
E: /usr/share/initramfs-tools/hooks/udev failed with return 1.
update-initramfs: failed for /boot/initrd.img-2.6.38-11-generic
dpkg: error processing initramfs-tools (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 initramfs-tools
steve@polyjuice:~$ 
steve@polyjuice:~$ sudo apt-get update
Ign [http://oss.oracle.com](http://oss.oracle.com) unstable InRelease
Get:1 [http://oss.oracle.com](http://oss.oracle.com) unstable Release.gpg [189 B]                                                                           
Hit [http://oss.oracle.com](http://oss.oracle.com) unstable Release                                                                                         
Ign [http://oss.oracle.com](http://oss.oracle.com) unstable Release                                                                                         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security InRelease                                                                            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease                                                                                       
Ign [http://oss.oracle.com](http://oss.oracle.com) unstable/main i386 Packages/DiffIndex                                                                    
Ign [http://deb.opera.com](http://deb.opera.com) stable InRelease                                                                                          
Ign [http://oss.oracle.com](http://oss.oracle.com) unstable/non-free i386 Packages/DiffIndex                                                                
Ign [http://oss.oracle.com](http://oss.oracle.com) unstable/main TranslationIndex                                                                           
Ign [http://oss.oracle.com](http://oss.oracle.com) unstable/non-free TranslationIndex                                                                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release.gpg                                                                          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg                                                                                     
Hit [http://oss.oracle.com](http://oss.oracle.com) unstable/main i386 Packages                                                                              
Hit [http://oss.oracle.com](http://oss.oracle.com) unstable/non-free i386 Packages                                                                          
Hit [http://deb.opera.com](http://deb.opera.com) stable Release.gpg                                                                                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release                                                                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release                                                                                         
Hit [http://deb.opera.com](http://deb.opera.com) stable Release                                                                                            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Sources                                                                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Sources                                                                                    
Ign [http://oss.oracle.com](http://oss.oracle.com) unstable/main Translation-en_US                                                                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Sources                                                                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Sources                                                                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Sources                                                                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main i386 Packages                                                                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted i386 Packages                                                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main i386 Packages                                                                              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main TranslationIndex                                                                           
Ign [http://oss.oracle.com](http://oss.oracle.com) unstable/main Translation-en                                                                             
Ign [http://oss.oracle.com](http://oss.oracle.com) unstable/non-free Translation-en_US                                                                      
Ign [http://oss.oracle.com](http://oss.oracle.com) unstable/non-free Translation-en                                                                         
Hit [http://deb.opera.com](http://deb.opera.com) stable/non-free i386 Packages                                                                             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe i386 Packages                                                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse i386 Packages                                                             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main TranslationIndex                                                                
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse TranslationIndex                                                          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted TranslationIndex                                                          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe TranslationIndex                                                            
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free TranslationIndex                                                                          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en_US                                                                          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en                                                                             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en_US                                                               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en                                                                  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en_US                                                         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en                                                            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en_US                                                         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en                                                            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en_US                                                           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en                                                              
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Translation-en_US                                                                         
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Translation-en                                                                            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty InRelease                                                                
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates InRelease                                                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty Release.gpg                                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates Release.gpg                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty Release                                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates Release                                                                             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Sources                                                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Sources                                                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Sources                                                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Sources                                                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main i386 Packages                                                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted i386 Packages                                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe i386 Packages                                                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse i386 Packages                                                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main TranslationIndex                                                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse TranslationIndex                                              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted TranslationIndex                                              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe TranslationIndex                                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Sources                                                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Sources                                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Sources                                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Sources                                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main i386 Packages                                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted i386 Packages       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe i386 Packages         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse i386 Packages       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main TranslationIndex          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse TranslationIndex                          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted TranslationIndex                          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe TranslationIndex      
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty InRelease                                                                                       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release.gpg                                                                                     
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release                                                                                         
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Sources                                                                                    
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main i386 Packages                                                                              
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main TranslationIndex                                                                           
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en_US                                                                          
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en                                                                             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Translation-en_US                                                                      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Translation-en                                                                         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Translation-en_US                                                                
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Translation-en                                                                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Translation-en_US                                                                
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Translation-en                                                                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Translation-en_US                                                                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Translation-en                                                                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Translation-en_US                                         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Translation-en            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Translation-en
Ign [http://archive.canonical.com](http://archive.canonical.com) natty InRelease        
Hit [http://archive.canonical.com](http://archive.canonical.com) natty Release.gpg
Hit [http://archive.canonical.com](http://archive.canonical.com) natty Release
Hit [http://archive.canonical.com](http://archive.canonical.com) natty/partner i386 Packages
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner TranslationIndex
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en_US
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en
Fetched 189 B in 1min 36s (2 B/s)
Reading package lists... Done
W: GPG error: [http://oss.oracle.com](http://oss.oracle.com) unstable Release: The following signatures were invalid: KEYEXPIRED 1315142507 KEYEXPIRED 1315142507 KEYEXPIRED 1315142507
steve@polyjuice:~$ 
steve@polyjuice:~$ sudo apt-get clean
steve@polyjuice:~$ 
steve@polyjuice:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up initramfs-tools (0.98.8ubuntu3.1) ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.38-11-generic
E: /usr/share/initramfs-tools/hooks/udev failed with return 1.
update-initramfs: failed for /boot/initrd.img-2.6.38-11-generic
dpkg: error processing initramfs-tools (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 initramfs-tools
E: Sub-process /usr/bin/dpkg returned an error code (1)
steve@polyjuice:~$ 
steve@polyjuice:~$ sudo apt-get install -a
E: Command line option 'a' [from -a] is not known.
steve@polyjuice:~$ sudo dpkg --configure -a
Setting up initramfs-tools (0.98.8ubuntu3.1) ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.38-11-generic
E: /usr/share/initramfs-tools/hooks/udev failed with return 1.
update-initramfs: failed for /boot/initrd.img-2.6.38-11-generic
dpkg: error processing initramfs-tools (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 initramfs-tools
steve@polyjuice:~$ 
steve@polyjuice:~$ sudo apt-get update
Ign [http://oss.oracle.com](http://oss.oracle.com) unstable InRelease
Get:1 [http://oss.oracle.com](http://oss.oracle.com) unstable Release.gpg [189 B]                                                                           
Hit [http://oss.oracle.com](http://oss.oracle.com) unstable Release                                                                                         
Ign [http://oss.oracle.com](http://oss.oracle.com) unstable Release                                                                                         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security InRelease                                                                            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease                                                                                       
Ign [http://oss.oracle.com](http://oss.oracle.com) unstable/main i386 Packages/DiffIndex                                                                    
Ign [http://deb.opera.com](http://deb.opera.com) stable InRelease                                                                                          
Ign [http://oss.oracle.com](http://oss.oracle.com) unstable/non-free i386 Packages/DiffIndex                                                                
Ign [http://oss.oracle.com](http://oss.oracle.com) unstable/main TranslationIndex                                                                           
Ign [http://oss.oracle.com](http://oss.oracle.com) unstable/non-free TranslationIndex                                                                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release.gpg                                                                          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg                                                                                     
Hit [http://oss.oracle.com](http://oss.oracle.com) unstable/main i386 Packages                                                                              
Hit [http://oss.oracle.com](http://oss.oracle.com) unstable/non-free i386 Packages                                                                          
Hit [http://deb.opera.com](http://deb.opera.com) stable Release.gpg                                                                                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release                                                                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release                                                                                         
Hit [http://deb.opera.com](http://deb.opera.com) stable Release                                                                                            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Sources                                                                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Sources                                                                                    
Ign [http://oss.oracle.com](http://oss.oracle.com) unstable/main Translation-en_US                                                                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Sources                                                                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Sources                                                                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Sources                                                                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main i386 Packages                                                                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted i386 Packages                                                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main i386 Packages                                                                              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main TranslationIndex                                                                           
Ign [http://oss.oracle.com](http://oss.oracle.com) unstable/main Translation-en                                                                             
Ign [http://oss.oracle.com](http://oss.oracle.com) unstable/non-free Translation-en_US                                                                      
Ign [http://oss.oracle.com](http://oss.oracle.com) unstable/non-free Translation-en                                                                         
Hit [http://deb.opera.com](http://deb.opera.com) stable/non-free i386 Packages                                                                             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe i386 Packages                                                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse i386 Packages                                                             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main TranslationIndex                                                                
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse TranslationIndex                                                          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted TranslationIndex                                                          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe TranslationIndex                                                            
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free TranslationIndex                                                                          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en_US                                                                          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en                                                                             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en_US                                                               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en                                                                  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en_US                                                         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en                                                            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en_US                                                         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en                                                            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en_US                                                           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en                                                              
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Translation-en_US                                                                         
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Translation-en                                                                            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty InRelease                                                                
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates InRelease                                                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty Release.gpg                                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates Release.gpg                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty Release                                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates Release                                                                             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Sources                                                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Sources                                                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Sources                                                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Sources                                                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main i386 Packages                                                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted i386 Packages                                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe i386 Packages                                                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse i386 Packages                                                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main TranslationIndex                                                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse TranslationIndex                                              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted TranslationIndex                                              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe TranslationIndex                                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Sources                                                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Sources                                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Sources                                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Sources                                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main i386 Packages                                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted i386 Packages       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe i386 Packages         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse i386 Packages       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main TranslationIndex          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse TranslationIndex                          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted TranslationIndex                          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe TranslationIndex      
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty InRelease                                                                                       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release.gpg                                                                                     
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release                                                                                         
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Sources                                                                                    
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main i386 Packages                                                                              
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main TranslationIndex                                                                           
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en_US                                                                          
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en                                                                             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Translation-en_US                                                                      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Translation-en                                                                         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Translation-en_US                                                                
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Translation-en                                                                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Translation-en_US                                                                
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Translation-en                                                                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Translation-en_US                                                                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Translation-en                                                                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Translation-en_US                                         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Translation-en            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Translation-en
Ign [http://archive.canonical.com](http://archive.canonical.com) natty InRelease        
Hit [http://archive.canonical.com](http://archive.canonical.com) natty Release.gpg
Hit [http://archive.canonical.com](http://archive.canonical.com) natty Release
Hit [http://archive.canonical.com](http://archive.canonical.com) natty/partner i386 Packages
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner TranslationIndex
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en_US
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en
Fetched 189 B in 1min 36s (2 B/s)
Reading package lists... Done
W: GPG error: [http://oss.oracle.com](http://oss.oracle.com) unstable Release: The following signatures were invalid: KEYEXPIRED 1315142507 KEYEXPIRED 1315142507 KEYEXPIRED 1315142507
steve@polyjuice:~$

---

### Post by magnadoodle on 2011-10-19
I don't know if this helps, but I had a similar error.  However when I removed unused kernels using Synaptic, it fixed the problem after reading the workaround from here [https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/798414]("https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/798414")

---

