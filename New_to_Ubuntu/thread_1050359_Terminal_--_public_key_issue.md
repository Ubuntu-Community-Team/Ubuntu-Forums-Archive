---
title: "Terminal -- public key issue"
date: 2009-01-25
forum: New to Ubuntu
---

### Post by adobrakic on 2009-01-25
I get this when I run update:

```
ado@ado-desktop:~$ sudo apt-get update
[sudo] password for ado: 
Hit http://archive.ubuntu.com intrepid Release.gpg
Ign http://archive.ubuntu.com intrepid/main Translation-en_US                  
Hit http://security.ubuntu.com intrepid-security Release.gpg                   
Ign http://security.ubuntu.com intrepid-security/main Translation-en_US        
Ign http://packages.linuxmint.com felicia Release.gpg                          
Hit http://packages.medibuntu.org intrepid Release.gpg                         
Ign http://packages.medibuntu.org intrepid/free Translation-en_US              
Ign http://archive.ubuntu.com intrepid/restricted Translation-en_US            
Ign http://archive.ubuntu.com intrepid/universe Translation-en_US              
Ign http://archive.ubuntu.com intrepid/multiverse Translation-en_US            
Hit http://archive.ubuntu.com intrepid-updates Release.gpg                     
Ign http://archive.ubuntu.com intrepid-updates/main Translation-en_US          
Ign http://archive.ubuntu.com intrepid-updates/restricted Translation-en_US    
Ign http://archive.ubuntu.com intrepid-updates/universe Translation-en_US      
Ign http://archive.ubuntu.com intrepid-updates/multiverse Translation-en_US    
Hit http://archive.ubuntu.com intrepid-backports Release.gpg                   
Hit http://archive.canonical.com intrepid Release.gpg                          
Ign http://archive.canonical.com intrepid/partner Translation-en_US            
Get:1 http://ppa.launchpad.net intrepid Release.gpg [307B]                     
Ign http://ppa.launchpad.net intrepid/main Translation-en_US                   
Ign http://security.ubuntu.com intrepid-security/restricted Translation-en_US  
Ign http://security.ubuntu.com intrepid-security/universe Translation-en_US    
Ign http://security.ubuntu.com intrepid-security/multiverse Translation-en_US  
Hit http://security.ubuntu.com intrepid-security Release                       
Ign http://packages.linuxmint.com felicia/main Translation-en_US               
Ign http://packages.linuxmint.com felicia/upstream Translation-en_US           
Ign http://packages.linuxmint.com felicia/import Translation-en_US             
Ign http://packages.medibuntu.org intrepid/non-free Translation-en_US          
Hit http://packages.medibuntu.org intrepid Release                             
Hit http://archive.ubuntu.com intrepid-proposed Release.gpg                    
Hit http://archive.ubuntu.com intrepid Release                                 
Hit http://archive.ubuntu.com intrepid-updates Release                         
Hit http://archive.canonical.com intrepid Release                              
Get:2 http://ppa.launchpad.net intrepid Release [27.6kB]                       
Get:3 http://packages.linuxmint.com felicia Release [7819B]                    
Hit http://security.ubuntu.com intrepid-security/main Packages                 
Ign http://ppa.launchpad.net intrepid Release                                  
Hit http://packages.medibuntu.org intrepid/free Packages                       
Hit http://archive.ubuntu.com intrepid-backports Release                       
Hit http://archive.ubuntu.com intrepid-proposed Release                        
Hit http://archive.ubuntu.com intrepid/main Packages                           
Hit http://archive.ubuntu.com intrepid/restricted Packages                     
Hit http://security.ubuntu.com intrepid-security/restricted Packages           
Hit http://security.ubuntu.com intrepid-security/universe Packages             
Hit http://security.ubuntu.com intrepid-security/multiverse Packages           
Hit http://security.ubuntu.com intrepid-security/main Sources                  
Hit http://archive.ubuntu.com intrepid/universe Packages                       
Hit http://archive.ubuntu.com intrepid/multiverse Packages                     
Hit http://archive.ubuntu.com intrepid/main Sources                            
Hit http://archive.ubuntu.com intrepid/restricted Sources                      
Hit http://archive.ubuntu.com intrepid/universe Sources                        
Hit http://archive.canonical.com intrepid/partner Packages                     
Hit http://archive.ubuntu.com intrepid/multiverse Sources                      
Ign http://ppa.launchpad.net intrepid/main Packages                            
Hit http://packages.medibuntu.org intrepid/non-free Packages                   
Hit http://security.ubuntu.com intrepid-security/restricted Sources            
Hit http://security.ubuntu.com intrepid-security/universe Sources              
Hit http://security.ubuntu.com intrepid-security/multiverse Sources            
Hit http://archive.ubuntu.com intrepid-updates/main Packages                   
Hit http://archive.ubuntu.com intrepid-updates/restricted Packages   
Hit http://archive.ubuntu.com intrepid-updates/universe Packages     
Hit http://archive.ubuntu.com intrepid-updates/multiverse Packages             
Hit http://archive.ubuntu.com intrepid-updates/main Sources                    
Hit http://winff.org intrepid Release.gpg                                      
Ign http://winff.org intrepid/universe Translation-en_US                       
Ign http://ppa.launchpad.net intrepid/main Sources                   
Ign http://packages.linuxmint.com felicia/main Packages              
Hit http://archive.ubuntu.com intrepid-updates/restricted Sources    
Hit http://archive.ubuntu.com intrepid-updates/universe Sources      
Hit http://archive.ubuntu.com intrepid-updates/multiverse Sources    
Hit http://archive.ubuntu.com intrepid-backports/main Sources        
Hit http://archive.ubuntu.com intrepid-backports/restricted Sources  
Hit http://archive.ubuntu.com intrepid-backports/universe Sources    
Hit http://archive.ubuntu.com intrepid-backports/multiverse Sources            
Hit http://archive.ubuntu.com intrepid-proposed/main Sources                   
Hit http://archive.ubuntu.com intrepid-proposed/restricted Sources   
Hit http://archive.ubuntu.com intrepid-proposed/universe Sources     
Hit http://archive.ubuntu.com intrepid-proposed/multiverse Sources   
Ign http://packages.linuxmint.com felicia/upstream Packages          
Hit http://ppa.launchpad.net intrepid/main Packages                  
Hit http://winff.org intrepid Release          
Ign http://packages.linuxmint.com felicia/import Packages          
Hit http://ppa.launchpad.net intrepid/main Sources
Hit http://packages.linuxmint.com felicia/main Packages
Hit http://packages.linuxmint.com felicia/upstream Packages
Hit http://packages.linuxmint.com felicia/import Packages
Hit http://winff.org intrepid/universe Packages
Fetched 8127B in 2s (2761B/s)
Reading package lists... Done
W: GPG error: http://ppa.launchpad.net intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY C71839136CF5CE97
W: You may want to run apt-get update to correct these problems
ado@ado-desktop:~$ 

```

I did what it says, and I still get the same thing.

---

### Post by Zip247 on 2009-01-25
See this thread....

[http://ubuntuforums.org/showthread.php?t=1046158](http://ubuntuforums.org/showthread.php?t=1046158)

wdecker

---

