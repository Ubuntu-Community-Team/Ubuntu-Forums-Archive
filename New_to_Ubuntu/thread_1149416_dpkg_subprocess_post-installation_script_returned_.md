---
title: "dpkg: subprocess post-installation script returned error exit status 1"
date: 2009-05-05
forum: New to Ubuntu
---

### Post by SeventHorcrux on 2009-05-05
I know this has been posted before but I have looked and tried everything and cannot find anything that works!!! I just switched to 9.04, from 8.10, but this was a problem before too. I just can't update anything because I can't open synaptic.

robert@robert-laptop:~$ sudo dpkg --configure -a
Setting up initramfs-tools (0.92bubuntu29) ...
update-initramfs: deferring update (trigger activated)

Setting up linux-image-2.6.28-11-generic (2.6.28-11.42) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.28-11-generic
cpio: ./bin/udevinfo: Cannot stat: No such file or directory
update-initramfs: failed for /boot/initrd.img-2.6.28-11-generic
Failed to create initrd image.
dpkg: error processing linux-image-2.6.28-11-generic (--configure):
 subprocess post-installation script returned error exit status 2
Setting up linux-image-2.6.28-3-rt (2.6.28-3.12) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.28-3-rt
cpio: ./bin/udevinfo: Cannot stat: No such file or directory
update-initramfs: failed for /boot/initrd.img-2.6.28-3-rt
Failed to create initrd image.
dpkg: error processing linux-image-2.6.28-3-rt (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.28-3-rt:
 linux-restricted-modules-2.6.28-3-rt depends on linux-image-2.6.28-3-rt; however:
  Package linux-image-2.6.28-3-rt is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.28-3-rt (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.28-11-generic; however:
  Package linux-image-2.6.28-11-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
Setting up linux-image-2.6.28-11-server (2.6.28-11.42) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.28-11-server
cpio: ./bin/udevinfo: Cannot stat: No such file or directory
update-initramfs: failed for /boot/initrd.img-2.6.28-11-server
Failed to create initrd image.
dpkg: error processing linux-image-2.6.28-11-server (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-restricted-modules-rt:
 linux-restricted-modules-rt depends on linux-restricted-modules-2.6.28-3-rt; however:
  Package linux-restricted-modules-2.6.28-3-rt is not configured yet.
dpkg: error processing linux-restricted-modules-rt (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.28.11.15); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.28-11-generic:
 linux-restricted-modules-2.6.28-11-generic depends on linux-image-2.6.28-11-generic; however:
  Package linux-image-2.6.28-11-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.28-11-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.28-11-server:
 linux-restricted-modules-2.6.28-11-server depends on linux-image-2.6.28-11-server; however:
  Package linux-image-2.6.28-11-server is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.28-11-server (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic:
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.28-11-generic; however:
  Package linux-restricted-modules-2.6.28-11-generic is not configured yet.
dpkg: error processing linux-restricted-modules-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-server:
 linux-image-server depends on linux-image-2.6.28-11-server; however:
  Package linux-image-2.6.28-11-server is not configured yet.
dpkg: error processing linux-image-server (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-server:
 linux-server depends on linux-image-server (= 2.6.28.11.15); however:
  Package linux-image-server is not configured yet.
dpkg: error processing linux-server (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules:
 linux-restricted-modules depends on linux-restricted-modules-generic (= 2.6.28.11.15); however:
  Package linux-restricted-modules-generic is not configured yet.
dpkg: error processing linux-restricted-modules (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-server:
 linux-restricted-modules-server depends on linux-restricted-modules-2.6.28-11-server; however:
  Package linux-restricted-modules-2.6.28-11-server is not configured yet.
dpkg: error processing linux-restricted-modules-server (--configure):
 dependency problems - leaving unconfigured
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.27-7-server
cpio: ./bin/udevinfo: Cannot stat: No such file or directory
update-initramfs: failed for /boot/initrd.img-2.6.27-7-server
dpkg: subprocess post-installation script returned error exit status 1
robert@robert-laptop:~$ sudo apt-get update
Hit [http://mirrors.us.kernel.org](http://mirrors.us.kernel.org) jaunty Release.gpg
Ign [http://mirrors.us.kernel.org](http://mirrors.us.kernel.org) jaunty/restricted Translation-en_US
Ign [http://mirrors.us.kernel.org](http://mirrors.us.kernel.org) jaunty/main Translation-en_US
Ign [http://mirrors.us.kernel.org](http://mirrors.us.kernel.org) jaunty/universe Translation-en_US
Ign [http://mirrors.us.kernel.org](http://mirrors.us.kernel.org) jaunty/multiverse Translation-en_US
Hit [http://mirrors.us.kernel.org](http://mirrors.us.kernel.org) jaunty-updates Release.gpg
Ign [http://mirrors.us.kernel.org](http://mirrors.us.kernel.org) jaunty-updates/restricted Translation-en_US
Ign [http://mirrors.us.kernel.org](http://mirrors.us.kernel.org) jaunty-updates/main Translation-en_US         
Ign [http://mirrors.us.kernel.org](http://mirrors.us.kernel.org) jaunty-updates/universe Translation-en_US     
Ign [http://mirrors.us.kernel.org](http://mirrors.us.kernel.org) jaunty-updates/multiverse Translation-en_US   
Hit [http://mirrors.us.kernel.org](http://mirrors.us.kernel.org) jaunty-security Release.gpg                   
Ign [http://mirrors.us.kernel.org](http://mirrors.us.kernel.org) jaunty-security/restricted Translation-en_US  
Ign [http://mirrors.us.kernel.org](http://mirrors.us.kernel.org) jaunty-security/main Translation-en_US        
Ign [http://mirrors.us.kernel.org](http://mirrors.us.kernel.org) jaunty-security/universe Translation-en_US    
Ign [http://mirrors.us.kernel.org](http://mirrors.us.kernel.org) jaunty-security/multiverse Translation-en_US  
Hit [http://mirrors.us.kernel.org](http://mirrors.us.kernel.org) jaunty-proposed Release.gpg                   
Ign [http://mirrors.us.kernel.org](http://mirrors.us.kernel.org) jaunty-proposed/restricted Translation-en_US  
Ign [http://mirrors.us.kernel.org](http://mirrors.us.kernel.org) jaunty-proposed/multiverse Translation-en_US  
Ign [http://mirrors.us.kernel.org](http://mirrors.us.kernel.org) jaunty-proposed/universe Translation-en_US    
Ign [http://mirrors.us.kernel.org](http://mirrors.us.kernel.org) jaunty-proposed/main Translation-en_US        
Hit [http://mirrors.us.kernel.org](http://mirrors.us.kernel.org) jaunty-backports Release.gpg                  
Ign [http://mirrors.us.kernel.org](http://mirrors.us.kernel.org) jaunty-backports/restricted Translation-en_US 
Ign [http://mirrors.us.kernel.org](http://mirrors.us.kernel.org) jaunty-backports/main Translation-en_US       
Ign [http://mirrors.us.kernel.org](http://mirrors.us.kernel.org) jaunty-backports/multiverse Translation-en_US 
Ign [http://mirrors.us.kernel.org](http://mirrors.us.kernel.org) jaunty-backports/universe Translation-en_US   
Hit [http://mirrors.us.kernel.org](http://mirrors.us.kernel.org) jaunty Release                                
Hit [http://mirrors.us.kernel.org](http://mirrors.us.kernel.org) jaunty-updates Release                        
Hit [http://mirrors.us.kernel.org](http://mirrors.us.kernel.org) jaunty-security Release                       
Hit [http://mirrors.us.kernel.org](http://mirrors.us.kernel.org) jaunty-proposed Release                       
Hit [http://mirrors.us.kernel.org](http://mirrors.us.kernel.org) jaunty-backports Release                      
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release.gpg                            
Ign [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Translation-en_US              
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg [307B]                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US                     
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) free Release.gpg                             
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) free/non-free Translation-en_US              
Hit [http://mirrors.us.kernel.org](http://mirrors.us.kernel.org) jaunty/restricted Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports Release.gpg                
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/main Translation-en_US     
Hit [http://mirrors.us.kernel.org](http://mirrors.us.kernel.org) jaunty/main Packages                          
Hit [http://mirrors.us.kernel.org](http://mirrors.us.kernel.org) jaunty/restricted Sources                     
Hit [http://mirrors.us.kernel.org](http://mirrors.us.kernel.org) jaunty/main Sources                           
Hit [http://mirrors.us.kernel.org](http://mirrors.us.kernel.org) jaunty/multiverse Sources                     
Hit [http://mirrors.us.kernel.org](http://mirrors.us.kernel.org) jaunty/universe Sources                       
Hit [http://mirrors.us.kernel.org](http://mirrors.us.kernel.org) jaunty/universe Packages                      
Hit [http://mirrors.us.kernel.org](http://mirrors.us.kernel.org) jaunty/multiverse Packages                    
Hit [http://mirrors.us.kernel.org](http://mirrors.us.kernel.org) jaunty-updates/restricted Packages            
Hit [http://mirrors.us.kernel.org](http://mirrors.us.kernel.org) jaunty-updates/main Packages                  
Hit [http://mirrors.us.kernel.org](http://mirrors.us.kernel.org) jaunty-updates/restricted Sources             
Hit [http://mirrors.us.kernel.org](http://mirrors.us.kernel.org) jaunty-updates/main Sources                   
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release                                
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg [307B]                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US                     
Get:3 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg [307B]                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US                     
Get:4 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg [307B]                       
Hit [http://mirrors.us.kernel.org](http://mirrors.us.kernel.org) jaunty-updates/multiverse Sources             
Hit [http://mirrors.us.kernel.org](http://mirrors.us.kernel.org) jaunty-updates/universe Sources               
Hit [http://mirrors.us.kernel.org](http://mirrors.us.kernel.org) jaunty-updates/universe Packages              
Hit [http://mirrors.us.kernel.org](http://mirrors.us.kernel.org) jaunty-updates/multiverse Packages            
Hit [http://mirrors.us.kernel.org](http://mirrors.us.kernel.org) jaunty-security/restricted Packages           
Hit [http://mirrors.us.kernel.org](http://mirrors.us.kernel.org) jaunty-security/main Packages                 
Hit [http://mirrors.us.kernel.org](http://mirrors.us.kernel.org) jaunty-security/restricted Sources            
Hit [http://mirrors.us.kernel.org](http://mirrors.us.kernel.org) jaunty-security/main Sources                  
Hit [http://mirrors.us.kernel.org](http://mirrors.us.kernel.org) jaunty-security/multiverse Sources            
Hit [http://mirrors.us.kernel.org](http://mirrors.us.kernel.org) jaunty-security/universe Sources              
Hit [http://mirrors.us.kernel.org](http://mirrors.us.kernel.org) jaunty-security/universe Packages             
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) free Release                                 
Hit [http://mirrors.us.kernel.org](http://mirrors.us.kernel.org) jaunty-security/multiverse Packages           
Hit [http://mirrors.us.kernel.org](http://mirrors.us.kernel.org) jaunty-proposed/restricted Packages           
Hit [http://mirrors.us.kernel.org](http://mirrors.us.kernel.org) jaunty-proposed/multiverse Packages           
Hit [http://mirrors.us.kernel.org](http://mirrors.us.kernel.org) jaunty-proposed/universe Packages             
Hit [http://mirrors.us.kernel.org](http://mirrors.us.kernel.org) jaunty-proposed/main Packages                 
Hit [http://mirrors.us.kernel.org](http://mirrors.us.kernel.org) jaunty-proposed/restricted Sources            
Hit [http://mirrors.us.kernel.org](http://mirrors.us.kernel.org) jaunty-proposed/multiverse Sources            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/universe Translation-en_US 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports Release                    
Hit [http://mirrors.us.kernel.org](http://mirrors.us.kernel.org) jaunty-proposed/universe Sources              
Hit [http://mirrors.us.kernel.org](http://mirrors.us.kernel.org) jaunty-proposed/main Sources                  
Hit [http://mirrors.us.kernel.org](http://mirrors.us.kernel.org) jaunty-backports/restricted Packages          
Hit [http://mirrors.us.kernel.org](http://mirrors.us.kernel.org) jaunty-backports/main Packages                
Hit [http://mirrors.us.kernel.org](http://mirrors.us.kernel.org) jaunty-backports/multiverse Packages          
Hit [http://mirrors.us.kernel.org](http://mirrors.us.kernel.org) jaunty-backports/universe Packages            
Hit [http://mirrors.us.kernel.org](http://mirrors.us.kernel.org) jaunty-backports/restricted Sources           
Hit [http://mirrors.us.kernel.org](http://mirrors.us.kernel.org) jaunty-backports/main Sources                 
Hit [http://mirrors.us.kernel.org](http://mirrors.us.kernel.org) jaunty-backports/multiverse Sources           
Hit [http://mirrors.us.kernel.org](http://mirrors.us.kernel.org) jaunty-backports/universe Sources             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US                     
Ign [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Packages                       
Get:5 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release [52.9kB]               
Get:6 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release [74.6kB]                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                                    
Get:7 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release [52.9kB]                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                                    
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) free/non-free Packages                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/main Packages              
Ign [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Sources              
Get:8 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release [31.1kB]               
Get:9 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release [52.9kB]                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                                    
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) free/non-free Packages                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/restricted Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/main Sources               
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Packages                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/restricted Sources         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/universe Sources           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/multiverse Sources         
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) free/non-free Packages                       
  404 Not Found [IP: 88.191.82.11 80]
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Sources              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages
  404 Not Found
Fetched 1233B in 1s (645B/s)
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2A8E3034D018A4CE
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY C9F2BA9509399DB5
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7889D725DA6DEEAA
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3F2A5EE4B796B6FE
W: Failed to fetch [http://packages.medibuntu.org/jaunty/dists/free/non-free/binary-i386/Packages](http://packages.medibuntu.org/jaunty/dists/free/non-free/binary-i386/Packages)  404 Not Found [IP: 88.191.82.11 80]

W: Failed to fetch [http://ppa.launchpad.net/q-funk/ubuntu/dists/jaunty/main/binary-i386/Packages](http://ppa.launchpad.net/q-funk/ubuntu/dists/jaunty/main/binary-i386/Packages)  404 Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.


and sources.list:

# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) jaunty restricted main
deb-src [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) jaunty restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) jaunty-updates restricted main
deb-src [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) jaunty-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) jaunty universe
deb [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) jaunty multiverse
deb [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) jaunty-security restricted main
deb-src [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) jaunty-security restricted main multiverse universe #Added by software-properties
deb [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) jaunty-security universe
deb [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) jaunty-proposed restricted multiverse universe main
deb-src [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) jaunty-proposed restricted multiverse universe main #Added by software-properties
deb [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) jaunty-security multiverse
# deb [http://ppa.launchpad.net/tualatrix/ubuntu](http://ppa.launchpad.net/tualatrix/ubuntu) jaunty main # disabled on upgrade to jaunty
# deb [http://packages.medibuntu.org/intrepid](http://packages.medibuntu.org/intrepid) free non-free
deb [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) jaunty-backports restricted main multiverse universe
deb-src [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) jaunty-backports restricted main multiverse universe #Added by software-properties
deb [http://packages.medibuntu.org/jaunty](http://packages.medibuntu.org/jaunty) free non-free
deb [http://ppa.launchpad.net/freenx-team/ubuntu](http://ppa.launchpad.net/freenx-team/ubuntu) jaunty main
deb [http://ppa.launchpad.net/gnomefreak/ubuntu](http://ppa.launchpad.net/gnomefreak/ubuntu) jaunty main
deb [http://ppa.launchpad.net/q-funk/ubuntu](http://ppa.launchpad.net/q-funk/ubuntu) jaunty main
deb [http://ppa.launchpad.net/globalmenu-team/ubuntu](http://ppa.launchpad.net/globalmenu-team/ubuntu) jaunty main
deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) jaunty main
deb [http://ppa.launchpad.net/netbook-remix-team/ubuntu](http://ppa.launchpad.net/netbook-remix-team/ubuntu) jaunty main



Any help would be MUCH appreciated, for all it's worth I have spent a tremendous amount of time on this.:popcorn:

---

### Post by jobbesat on 2009-05-05
Between other problems, I see you have GPG errors, so let's try to solve them typing in a terminal:
```
gpg --keyserver hkp://subkeys.pgp.net --recv-keys XXXXXXXXXXXX
gpg --export --armor  XXXXXXXXXXXX | sudo apt-key add -
```

where XXXXXXXXX is the number you have as errors, which specifically are:
> 2A8E3034D018A4CE
C9F2BA9509399DB5
7889D725DA6DEEAA
3F2A5EE4B796B6FE

so type the same 2 commands I wrote above for 4 times changing the numbers.
Let me know if something changed.

---

